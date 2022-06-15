# Creating a Proposal

## Local

```bash
# make proposal
evmosd tx gov submit-proposal software-upgrade "v5.0.0" \
--title "Evmos Local v5 Upgrade" \
--deposit 500000aevmos \
--upgrade-height 1200000 \
--upgrade-info '{"binaries":{"darwin/arm64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Darwin_arm64.tar.gz","darwin/x86_64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Darwin_x86_64.tar.gz","linux/arm64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Linux_arm64.tar.gz","linux/x86_64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Linux_x86_64.tar.gz","windows/x86_64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Windows_x86_64.zip"}}' \
--description "TODO" \
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
evmosd tx gov submit-proposal software-upgrade "v5.0.0" \
--title "Evmos Testnet v5.0.0 Upgrade" \
--upgrade-height 1762500 \
--upgrade-info '{"binaries":{"darwin/arm64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Darwin_arm64.tar.gz","darwin/x86_64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Darwin_x86_64.tar.gz","linux/arm64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Linux_arm64.tar.gz","linux/x86_64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Linux_x86_64.tar.gz","windows/x86_64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Windows_x86_64.zip"}}' \
--description "## Author\n​\nDaniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team\n​\n## Software Upgrade being scheduled with this proposal\n​\nIf successful, this proposal will schedule an Evmos software upgrade from it's current version [`v4.1.0`](https://github.com/tharsis/evmos/releases/tag/v4.0.1) to [`v5.0.0`](https://github.com/tharsis/evmos/releases/tag/v5.0.0) on the Evmos Testnet. This proposal has a voting time of 12 hours.\n​\n## Motivation\n​\nBy proposing a scheduled upgrade, we want to implement a smooth and transparent upgrade process, that is first proposed on testnet and then on mainnet. Software upgrades generally aim to improve current perfomance and add new features on the Evmos chain. For more information on the types of upgrades, please visit our [Software Upgrade Guide](https://docs.evmos.org/validators/upgrades/overview.html).\n​\n## Impact\n​\nOn a high level, the `v5.0.0` software includes the following improvements:\n​\n* ERC20 module: Improve coin denomination display and allow coins with `erc20/` names to be sent over IBC\n* Improve congestion issues for EVM transactions on Ethermint\n* Add observability for Evmos modules to measure performance\n​\nSoftware upgrades also allow changing the state or parameters. The following migrations are included in this upgrade:\n​\n* Update Tendermint Consensus Evidence params to prepare moving to a block time of 2 seconds\n* Update faulty IBC denom traces for denominations with `erc20/`\n* Resolve Airdrop claims: A few users tokens are still locked due to issues with the airdrop. By swapping claimed actions we allow the users to migrate the records via IBC if needed or mark the Evm action as completed for the Keplr users who are not able to complete it. Since no actual claiming of action is occurring, balance will remain unchanged\n* Migrates the claims record of a specific early contributor (Blockchain at Berkeley) from one address to another. See https://medium.com/evmos/the-evmos-rektdrop-abbe931ba823 for details about Early Contributors.\n* Set the MinGasPrice to 25,000,000,000aevmos => view [discussion](https://commonwealth.im/evmos/discussion/5073-global-min-gas-price-value-for-cosmos-sdk-and-evm-transaction-choosing-a-value)\n​\nA full changelog can be found [here](https://github.com/tharsis/evmos/releases/tag/v5.0.0).\n​\n## Testing\n​\nThe Evmos core team created a End-to-End testing suite that perfoms the software upgrade locally. These tests have been performed successfully for this upgrade. The instructions on how to run the End-to-End testing suite can be found [here](https://github.com/ramacarlucho/evmos/blob/rama%2Fe2e_clean/tests/e2e/README.md)." \
--from=a1 \
--fees=80atevmos --gas=auto -b block --chain-id=evmos_9000-4 \
--node=https://tendermint.bd.evmos.dev:26657

# place deposit
evmosd tx gov deposit <PROPOSALID> 1000000000000000000atevmos \
--from=hot2 \
--fees=80atevmos --gas=auto -b block --chain-id=evmos_9000-4 \
--node=https://tendermint.bd.evmos.dev:26657
```

## Mainnet

Use [stringify](https://jsonformatter.org/json-stringify-online) and markdown to convert your description into a one line string.

```bash
# Make proposal
evmosd tx gov submit-proposal software-upgrade "v5.0.0" \
--title "Evmos Mainnet v5.0.0 Upgrade" \
--upgrade-height 837500 \
--upgrade-info '{"binaries":{"darwin/arm64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Darwin_arm64.tar.gz","darwin/x86_64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Darwin_x86_64.tar.gz","linux/arm64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Linux_arm64.tar.gz","linux/x86_64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Linux_x86_64.tar.gz","windows/x86_64":"https://github.com/tharsis/evmos/releases/download/v5.0.0/evmos_5.0.0_Windows_x86_64.zip"}}' \
--description "## Author\n\nDaniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team\n\n## Software Upgrade being scheduled with this proposal\n\nIf successful, this proposal will schedule an Evmos mainnet software upgrade at block height [837,500](https://www.mintscan.io/evmos/blocks/837500) (around 3pm UTC next Monday) from it's current version [v4.1.0](https://github.com/tharsis/evmos/releases/tag/v4.0.1) to [v5.0.0](https://github.com/tharsis/evmos/releases/tag/v5.0.0). This proposal has a voting time of 5 days.\n\n## Motivation\n\nBy proposing a scheduled upgrade, we want to implement a smooth and transparent upgrade process, that is first proposed on testnet and then on mainnet. Software upgrades generally aim to improve current performance and add new features to the Evmos chain. For more information on the types of upgrades, please visit our [Software Upgrade Guide](https://docs.evmos.org/validators/upgrades/overview.html).\n\n## Impact\n\nOn a high level, the 'v5.0.0' software includes the following improvements:\n\n* ERC20 module: Improve coin denomination display and allow coins with 'erc20/' names to be sent over IBC\n* Improve congestion issues for EVM transactions on Ethermint through the 'MinGasPrice' and 'MinGasMultiplier' fee market parameters\n* Add observability for Evmos and Ethermint modules to measure performance\n* Cosmos SDK and IBC dependency updates\n\nSoftware upgrades also allow changing the state or parameters. The following migrations are included in this upgrade:\n\n* Update Tendermint Consensus Evidence params to prepare to move to a block time of 2 seconds\n* Update faulty IBC denomination traces for denominations with 'erc20/'\n* Resolve Airdrop claims: A few users' tokens are still locked due to issues with the airdrop. By swapping claimed actions we allow the users to migrate the records via IBC if needed or mark the Evm action as completed for the Keplr users who are not able to complete it. Since no actual claiming of action is occurring, the balance will remain unchanged\n* Migrates the claims record of a specific early contributor (Blockchain at Berkeley) from one address to another. See the [Rektdrop blog post](https://medium.com/evmos/the-evmos-rektdrop-abbe931ba823) for details about Early Contributors\n* Set the 'MinGasPrice' param value to '25,000,000,000aevmos' (view [discussion](https://commonwealth.im/evmos/discussion/5073-global-min-gas-price-value-for-cosmos-sdk-and-evm-transaction-choosing-a-value))\n* The EVM now only refunds 50% of the leftover gas\n\nA full changelog can be found [here](https://github.com/tharsis/evmos/releases/tag/v5.0.0).\n\n## Testing\n\nThe Evmos core team created an End-to-End testing suite that performs the software upgrade locally. These tests have been completed successfully for this upgrade. The instructions on how to run the End-to-End testing suite can be found [here](https://github.com/ramacarlucho/evmos/blob/rama%2Fe2e_clean/tests/e2e/README.md). Additionally, the upgrade is performed and on testnet with [testnet proposal #34](https://testnet.mintscan.io/evmos-testnet/proposals/34).\n\n## Discussion\n\nBefore voting, please follow and discuss this proposal using the official [discussion on commonwealth](https://commonwealth.im/evmos/discussion/5467-evmos-software-upgrade-v500)." \
--from=commonwealth \
--fees=80aevmos --gas=auto -b block --chain-id=evmos_9001-2 \
--node=https://rpc-evmos-ia.notional.ventures:443
```

# Description Template

```markdown
## Author

Daniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team

## Software Upgrade being scheduled with this proposal

If successful, this proposal will schedule an Evmos mainnet software upgrade at block height [837,500](https://www.mintscan.io/evmos/blocks/837500) (around 3pm UTC next Monday) from it's current version [v4.1.0](https://github.com/tharsis/evmos/releases/tag/v4.0.1) to [v5.0.0](https://github.com/tharsis/evmos/releases/tag/v5.0.0). This proposal has a voting time of 5 days.

## Motivation

By proposing a scheduled upgrade, we want to implement a smooth and transparent upgrade process, that is first proposed on testnet and then on mainnet. Software upgrades generally aim to improve current performance and add new features to the Evmos chain. For more information on the types of upgrades, please visit our [Software Upgrade Guide](https://docs.evmos.org/validators/upgrades/overview.html).

## Impact

On a high level, the `v5.0.0` software includes the following improvements:

* ERC20 module: Improve coin denomination display and allow coins with `erc20/` names to be sent over IBC
* Improve congestion issues for EVM transactions on Ethermint through the `MinGasPrice` and `MinGasMultiplier` fee market parameters
* Add observability for Evmos and Ethermint modules to measure performance
* Cosmos SDK and IBC dependency updates

Software upgrades also allow changing the state or parameters. The following migrations are included in this upgrade:

* Update Tendermint Consensus Evidence params to prepare to move to a block time of 2 seconds
* Update faulty IBC denomination traces for denominations with `erc20/`
* Resolve Airdrop claims: A few users' tokens are still locked due to issues with the airdrop. By swapping claimed actions we allow the users to migrate the records via IBC if needed or mark the Evm action as completed for the Keplr users who are not able to complete it. Since no actual claiming of action is occurring, the balance will remain unchanged
* Migrates the claims record of a specific early contributor (Blockchain at Berkeley) from one address to another. See the [Rektdrop blog post](https://medium.com/evmos/the-evmos-rektdrop-abbe931ba823) for details about Early Contributors
* Set the `MinGasPrice` param value to `25,000,000,000aevmos` (view [discussion](https://commonwealth.im/evmos/discussion/5073-global-min-gas-price-value-for-cosmos-sdk-and-evm-transaction-choosing-a-value))
* The EVM now only refunds 50% of the leftover gas

A full changelog can be found [here](https://github.com/tharsis/evmos/releases/tag/v5.0.0).

## Testing

The Evmos core team created an End-to-End testing suite that performs the software upgrade locally. These tests have been completed successfully for this upgrade. The instructions on how to run the End-to-End testing suite can be found [here](https://github.com/ramacarlucho/evmos/blob/rama%2Fe2e_clean/tests/e2e/README.md). Additionally, the upgrade is performed and on testnet with [testnet proposal #34](https://testnet.mintscan.io/evmos-testnet/proposals/34).

## Discussion

Before voting, please follow and discuss this proposal using the official [discussion on commonwealth](https://commonwealth.im/evmos/discussion/5467-evmos-software-upgrade-v500).
```
