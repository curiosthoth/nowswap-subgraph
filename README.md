# Nowswap Subgraph (Mintswap)

This is a fork of Uniswap V2 Subgraph with some light modifications.
It deploys to Mintswap on (The Graph)[https://www.thegraph.com]

## Key Entity Overviews

#### NowswapFactory

Contains data across all of Nowswap. This entity tracks important things like total liquidity (in ETH and USD, see below), all time volume, transaction count, number of pairs and more.

#### Token

Contains data on a specific token. This token specific data is aggregated across all pairs, and is updated whenever there is a transaction involving that token.

#### Pair

Contains data on a specific pair.

#### Transaction

Every transaction on Nowswap is stored. Each transaction contains an array of mints, burns, and swaps that occured within it.

#### Mint, Burn, Swap

These contain specifc information about a transaction. Things like which pair triggered the transaction, amounts, sender, recipient, and more. Each is linked to a parent Transaction entity.

## Example Queries

### Querying Aggregated Nowswap Data

This query fetches aggredated data from all Nowswap pairs and tokens, to give a view into how much activity is happening within the whole protocol.

```graphql
{
  nowswapFactories(first: 1) {
    pairCount
    totalVolumeUSD
    totalLiquidityUSD
  }
}
```

## Deploy

```bash
yarn codegen && yarn build && yarn deploy
```
