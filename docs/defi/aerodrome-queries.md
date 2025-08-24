# Aerodrome LP Analysis Queries

## Query 1: Basic Position Lifecycle

Track position ownership from creation to closure.

```sql
SELECT 
  m.token_id,
  m.pool_address,
  m.owner as original_owner,
  COALESCE(t.to_address, m.owner) as current_owner,
  m.tick_lower,
  m.tick_upper, 
  m.amount as liquidity,
  CASE WHEN t.token_id IS NOT NULL THEN 1 ELSE 0 END as was_transferred,
  CASE WHEN b.token_id IS NOT NULL THEN 'CLOSED' ELSE 'ACTIVE' END as status,
  CASE 
    WHEN b.timestamp IS NOT NULL 
    THEN EXTRACT(EPOCH FROM (b.timestamp - m.timestamp)) / 86400
    ELSE EXTRACT(EPOCH FROM (CURRENT_TIMESTAMP - m.timestamp)) / 86400
  END as duration_days
FROM aerodrome_mints m
LEFT JOIN (
  SELECT DISTINCT ON (token_id) token_id, to_address, timestamp
  FROM aerodrome_lp_transfers ORDER BY token_id, timestamp DESC
) t ON m.token_id = t.token_id
LEFT JOIN aerodrome_burns b ON m.token_id = b.token_id
WHERE m.owner NOT LIKE '%handler%' AND m.owner NOT LIKE '%gauge%'
ORDER BY m.timestamp DESC;
```

---

## Query 2: Detailed Ownership Chain

Show step-by-step ownership changes for each position.

```sql
WITH ownership_timeline AS (
  SELECT token_id, pool_address, owner as wallet_address, 'MINT' as event_type, timestamp as event_time, 1 as sequence_order
  FROM aerodrome_mints
  UNION ALL
  SELECT token_id, pool_address, to_address as wallet_address, 'TRANSFER' as event_type, timestamp as event_time, 2 as sequence_order
  FROM aerodrome_lp_transfers
  UNION ALL
  SELECT token_id, pool_address, owner as wallet_address, 'BURN' as event_type, timestamp as event_time, 3 as sequence_order
  FROM aerodrome_burns
),
numbered_events AS (
  SELECT *, ROW_NUMBER() OVER (PARTITION BY token_id ORDER BY event_time, sequence_order) as ownership_step
  FROM ownership_timeline
),
ownership_durations AS (
  SELECT 
    ne1.token_id, ne1.wallet_address, ne1.event_type, ne1.event_time as ownership_start, ne1.ownership_step,
    ne2.event_time as ownership_end, ne2.wallet_address as next_owner, ne2.event_type as next_event,
    CASE 
      WHEN ne2.event_time IS NOT NULL 
      THEN EXTRACT(EPOCH FROM (ne2.event_time - ne1.event_time)) / 86400.0
      ELSE EXTRACT(EPOCH FROM (CURRENT_TIMESTAMP - ne1.event_time)) / 86400.0
    END as ownership_days
  FROM numbered_events ne1
  LEFT JOIN numbered_events ne2 ON ne1.token_id = ne2.token_id AND ne2.ownership_step = ne1.ownership_step + 1
  WHERE ne1.event_type IN ('MINT', 'TRANSFER')
)
SELECT 
  token_id, ownership_step, wallet_address as owner, event_type as how_acquired,
  ownership_start, ownership_end, next_owner, next_event as how_lost,
  ROUND(ownership_days, 2) as ownership_duration_days,
  CASE 
    WHEN ownership_step = 1 THEN 'ORIGINAL_CREATOR'
    WHEN next_event IS NULL THEN 'CURRENT_OWNER' 
    WHEN next_event = 'BURN' THEN 'FINAL_OWNER'
    ELSE 'INTERMEDIATE_OWNER'
  END as owner_role
FROM ownership_durations
ORDER BY token_id, ownership_step;
```
