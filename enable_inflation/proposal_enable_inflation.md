# Local

```bash
# make proposal
evmosd tx gov submit-proposal param-change ./proposal_enable_inflation.json \
--from=mykey \
--fees=80aevmos --gas=auto -b block --chain-id=evmos_9000-1

# get proposals
evmosd query gov proposals

# place deposit
evmosd tx gov deposit 1 1000000000000000000aevmos \
--from=mykey \
--fees=80aevmos --gas=auto -b block

# Vote for a proposal
evmosd tx gov vote 1 yes \
--from mykey \
--fees=80aevmos --gas=auto -b block
```

# Testnet

```bash
# Make proposal
evmosd tx gov submit-proposal param-change ./proposal_enable_inflation_testnet.json \
--from=hot2 \
--fees=80atevmos --gas=auto -b block --chain-id=evmos_9000-4 \
--node=https://tendermint.bd.evmos.dev:26657

# place deposit
evmosd tx gov deposit <PROPOSALID> 1000000000000000000atevmos \
--from=hot2 \
--fees=80atevmos --gas=auto -b block --chain-id=evmos_9000-4 \
--node=https://tendermint.bd.evmos.dev:26657
```

# Mainnet

Use [stringify](https://jsonformatter.org/json-stringify-online) and markdown to convert your description into a one line string.

```bash
# Make proposal
evmosd tx gov submit-proposal param-change ./proposal_enable_inflation_mainnet.json \
--from=commonwealth \
--fees=80aevmos --gas=auto -b block --chain-id=evmos_9001-2 \
--node=https://tendermint.bd.evmos.org:26657
```