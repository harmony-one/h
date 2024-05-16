# Most Profitable Trades on GMX

In this analysis, I delved into the top 1000 users and the most profitable trades on GMX perpetual (Avalanche, Arbitrum).

View my [Dune Dashboard](https://dune.com/rikaharmony/gmx-dydx-stats).

## Dataset:
The dataset used is `gmx.perpetual_trades`, accessible [here](https://dune.com/data/gmx.perpetual_trades).

## Total Profit and Loss:
Profit and Loss (PnL) was calculated by subtracting `fee_usd` from `volume_usd`.

![Total PnL](https://github.com/harmony-one/h/assets/27670355/f84b2bb1-49fb-4bde-905f-c4538579c19b)

![Total PnL](https://github.com/harmony-one/h/assets/27670355/c2e37295-60a8-4b78-988e-2bffda3a2786)

## Average Profit and Loss:
The average PnL was calculated using the `AVG()` function.

![Average PnL](https://github.com/harmony-one/h/assets/27670355/8eb5581a-426b-4b5c-8e64-c6354faabd9d)

![Average PnL](https://github.com/harmony-one/h/assets/27670355/807fca79-0685-4f97-b91b-0f9e64066d79)

## Average Profit and Loss for Top 1000 Traders:
I identified the top 1000 traders based on their net PnL and calculated their average PnL across each market pair.

![Top 1000 Traders PnL](https://github.com/harmony-one/h/assets/27670355/11b8fcca-b57c-418d-aa7c-21083d35f72c)

![Top 1000 Traders PnL](https://github.com/harmony-one/h/assets/27670355/1c00d183-3cfd-44f2-abe3-c0565d103ac4)

## Market Distribution for Top 1000 Traders:
This query determines the total PnL for each market pair among the top 1000 traders and calculates the percentage of each trader's PnL contributed by each market pair.

![Market Distribution](https://github.com/harmony-one/h/assets/27670355/b1be0064-98ca-4925-9a0a-2a7f820b416f)

![Market Distribution](https://github.com/harmony-one/h/assets/27670355/d633c1b5-cc07-4143-9770-267b56fd69b8)

## Correlation Analysis:
Additionally, I explored the Pearson correlation between PnL in different market pairs to identify any correlations.

![Correlation Analysis](https://github.com/harmony-one/h/assets/27670355/4bda947d-7460-4009-9c23-caef81c45290)

## Next Steps:
Further investigation is required to find datasets for dydx v3 as they were not available on Dune.

