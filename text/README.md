# Creating a Text Proposal

This guide provides an example on how to create text proposals on Evmos. To avoid mistakes I recommend double checking every flag and creating the proposal locally first. Note, that if you submit the proposal over CLI, first confirm if the proposal [has been submitted or failed](https://app.evmos.org/governance) before trying again.

## Local

```bash
# make proposal
evmosd tx gov submit-proposal \
--title="Test Text Proposal"  \
--description="testing" \
--type="Text" \
--deposit 1000000000000000000aevmos \
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

## Testnet

```bash
evmosd tx gov submit-proposal \
--title="Test Text Proposal"  \
--description="testing" \
--type="Text" \
--from=a1 --keyring-backend=os \
--deposit 10000000000000000000atevmos \
--fees=7000000000000atevmos --gas=700000 -b block --chain-id=evmos_9000-4 \
--node=https://tendermint.bd.evmos.dev:26657


# place deposit yourself or let other validators place it
evmosd tx gov deposit 90 10000000000000000000atevmos \
--from=a1 --keyring-backend=test \
--fees=17500000000000000atevmos --gas=auto -b block --chain-id=evmos_9000-4 \
--node=https://tendermint.bd.evmos.dev:26657
```


evmosd tx gov deposit 90 1000000000000000000aevmos \
--from=a1 --keyring-backend=os \
--fees=80aevmos --gas=auto -b block