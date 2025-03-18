### How to create Shadow Pool Subgraph (Sonic mainnet)

1. Install NodeJS 23 and graph cli:

https://nodejs.org/en/download

```shell
npm install -g @graphprotocol/graph-cli@0.96.0
```
2. Check installed versions:
```shell
❯ node -v
v23.3.0

❯ graph -v
@graphprotocol/graph-cli/0.96.0 darwin-arm64 node-v23.3.0
```
3. Create new subgraph in Subgraph Studio. Let's use the name "sonic-shadow".
https://thegraph.com/studio/

4. Follow instructions:
```shell
graph init sonic-shadow
```

Follow instructions:
```shell
type "sonic", select Sonic Mainnet · sonic
Source ❯ Smart contract · default
Subgraph slug › sonic-shadow
Directory to create the subgraph in › sonic-shadow
Contract address › 0x324963c267c354c7660ce8ca3f5f167e05649970

 Fetching ABI from contract API...
✔ Fetching start block from contract API...
✔ Fetching contract name from contract API...
? Start block › 1949593

Contract name › RamsesV3Pool
Index contract events as entities (Y/n) › true
Add another contract? (y/N) · false
```

5. Publish sugraph to Graph network
```shell
cd sonic-shadow

graph auth <deploy key>

graph codegen && graph build

graph deploy sonic-shadow
```

```shell
Deployed to https://thegraph.com/studio/subgraph/sonic-shadow

Subgraph endpoints:
Queries (HTTP):     https://api.studio.thegraph.com/query/91182/sonic-shadow/v0.0.2
```

6. Open subgraph studio dashboard and check sync status
https://thegraph.com/studio/subgraph/sonic-shadow/playground

7. Run test query is subgraph is synced
```
{
  mints(
    first: 1, orderBy:blockNumber, orderDirection:desc,
    where:{
      blockNumber_gt: 14470930,
      blockNumber_lt: 14470940
    }
  ) {
    id
    transactionHash
    blockNumber
    sender
  }
}
```
