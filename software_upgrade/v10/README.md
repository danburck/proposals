# `v9.1.0` -> `v10`

Note that signing gov proposals with `--keyring-backend=os` might not be supported.

## Local

```bash
# make proposal
evmosd tx gov submit-proposal software-upgrade "v10.0.0-rc1" \
--title "Evmos Local v10.0.0-rc1 Upgrade" \
--deposit 500000aevmos \
--upgrade-height 1100 \
--upgrade-info '{"binaries":{"darwin/arm64":"https://github.com/evmos/evmos/releases/download/v10.0.0-rc1/evmos_10.0.0-rc1_Darwin_arm64.tar.gz","darwin/amd64":"https://github.com/evmos/evmos/releases/download/v10.0.0-rc1/evmos_10.0.0-rc1_Darwin_amd64.tar.gz","linux/arm64":"https://github.com/evmos/evmos/releases/download/v10.0.0-rc1/evmos_10.0.0-rc1_Linux_arm64.tar.gz","linux/amd64":"https://github.com/evmos/evmos/releases/download/v10.0.0-rc1/evmos_10.0.0-rc1_Linux_amd64.tar.gz","windows/x86_64":"https://github.com/evmos/evmos/releases/download/v10.0.0-rc1/evmos_10.0.0-rc1_Windows_x86_64.zip"}}' \
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
evmosd tx gov submit-proposal software-upgrade "v10.0.0-rc1" \
--title "Evmos Testnet v10.0.0-rc1 Upgrade" \
--upgrade-height 8700000 \
--upgrade-info '{"binaries":{"darwin/arm64":"https://github.com/evmos/evmos/releases/download/v10.0.0-rc1/evmos_10.0.0-rc1_Darwin_arm64.tar.gz","darwin/amd64":"https://github.com/evmos/evmos/releases/download/v10.0.0-rc1/evmos_10.0.0-rc1_Darwin_amd64.tar.gz","linux/arm64":"https://github.com/evmos/evmos/releases/download/v10.0.0-rc1/evmos_10.0.0-rc1_Linux_arm64.tar.gz","linux/amd64":"https://github.com/evmos/evmos/releases/download/v10.0.0-rc1/evmos_10.0.0-rc1_Linux_amd64.tar.gz","windows/x86_64":"https://github.com/evmos/evmos/releases/download/v10.0.0-rc1/evmos_10.0.0-rc1_Windows_x86_64.zip"}}' \
--description "## Author\n\nDaniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team\n\n## Software Upgrade being scheduled with this proposal\n\nIf successful, this proposal will schedule an Evmos software upgrade at block height [8,700,000](https://testnet.mintscan.io/evmos-testnet/blocks/8700000) from it's current version [v9.1.0](https://github.com/tharsis/evmos/releases/tag/v9.1.0) to [v10.0.0-rc1](https://github.com/tharsis/evmos/releases/tag/v10.0.0-rc1).\n\n## Motivation\n\nBy proposing a scheduled upgrade, we want to implement a smooth and transparent upgrade process, that is first proposed on Testnet using release candidates (rc) and then on Mainnet. Software upgrades generally aim to improve performance and add new features to the Evmos chain. For more information on the types of upgrades, please visit our [Software Upgrade Guide](https://docs.evmos.org/validators/upgrades/overview.html).\n\n## Impact\n\nOn a high level, the v10.0.0-rc1 software includes the following improvements:\n\nThis is a dedicated release candidate for the Cosmos SDK v0.46 series. It also contains minor improvements and bug fixes:\n\n* ERC20 proposals to register ERC20 tokens and Cosmos coins now can receive multiple denominations\n* Prioritized mempool support for Cosmos and Ethereum txs\n* EIP-1559 now also supports native Cosmos transactions\n* EIP-712 fixes for all major Cosmos messages (eg: MsgGrant for restake support)\n* Ethereum Tx indexer\n\nA full changelog can be found [here](https://github.com/tharsis/evmos/releases/tag/v10.0.0-rc1).\n\n## Testing\n\nPrior to this proposal the version v10.0.0-rc1 with an an End-to-End testing suite that performs the software upgrade locally. These tests have been completed successfully for this upgrade. The instructions on how to run the End-to-End testing suite can be found [here](https://github.com/evmos/evmos/pull/1028)." \
--from=a1 --keyring-backend=test \
--fees=17500000000000000atevmos --gas=700000 -b block \
--chain-id=evmos_9000-4 \
--node=https://tendermint.bd.evmos.dev:26657


# place deposit yourself or let other validators place it
evmosd tx gov deposit <PROPOSALID> 1000000000000000000atevmos \
--from=hot2 \
--fees=80atevmos --gas=auto -b block --chain-id=evmos_9000-4 \
--node=https://tendermint.bd.evmos.dev:26657
```

## Description

```markdown
## Author

Daniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team

## Software Upgrade being scheduled with this proposal

If successful, this proposal will schedule an Evmos software upgrade at block height [8,700,000](https://testnet.mintscan.io/evmos-testnet/blocks/8700000) from it's current version [v9.1.0](https://github.com/tharsis/evmos/releases/tag/v9.1.0) to [v10.0.0-rc1](https://github.com/tharsis/evmos/releases/tag/v10.0.0-rc1).

## Motivation

By proposing a scheduled upgrade, we want to implement a smooth and transparent upgrade process, that is first proposed on Testnet using release candidates (rc) and then on Mainnet. Software upgrades generally aim to improve performance and add new features to the Evmos chain. For more information on the types of upgrades, please visit our [Software Upgrade Guide](https://docs.evmos.org/validators/upgrades/overview.html).

## Impact

On a high level, the v10.0.0-rc1 software includes the following improvements:

This is a dedicated release candidate for the Cosmos SDK v0.46 series. It also contains minor improvements and bug fixes:

* ERC20 proposals to register ERC20 tokens and Cosmos coins now can receive multiple denominations
* Prioritized mempool support for Cosmos and Ethereum txs
* EIP-1559 now also supports native Cosmos transactions
* EIP-712 fixes for all major Cosmos messages (eg: MsgGrant for restake support)
* Ethereum Tx indexer

A full changelog can be found [here](https://github.com/tharsis/evmos/releases/tag/v10.0.0-rc1).

## Testing

Prior to this proposal the version v10.0.0-rc1 with an an End-to-End testing suite that performs the software upgrade locally. These tests have been completed successfully for this upgrade. The instructions on how to run the End-to-End testing suite can be found [here](https://github.com/evmos/evmos/pull/1028).
```

<!--
## Mainnet

Use [stringify](https://jsonformatter.org/json-stringify-online) and markdown to convert your description into a one line string.

```bash
# Make proposal
evmosd tx gov submit-proposal software-upgrade "v10.0.0-rc1" \
--title "Evmos Mainnet v10.0.0-rc1 Upgrade" \
--upgrade-height 4655500 \
--upgrade-info '{"binaries":{"darwin/arm64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.1.0_Darwin_arm64.tar.gz","darwin/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.1.0_Darwin_x86_64.tar.gz","linux/arm64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.1.0_Linux_arm64.tar.gz","linux/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.1.0_Linux_x86_64.tar.gz","windows/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.1.0_Windows_x86_64.zip"}}' \
--description "## Author\n\nDaniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team\n\n## Software Upgrade being scheduled with this proposal\n\nIf successful, this proposal will schedule an Evmos software upgrade at block height [4,655,500](https://www.mintscan.io/evmos/blocks/4655500) from it's current version [v7.0.0](https://github.com/tharsis/evmos/releases/tag/v7.0.0) to [v10.0.0-rc1](https://github.com/tharsis/evmos/releases/tag/v10.0.0-rc1).\n\n## Motivation\n\nBy proposing a scheduled upgrade, we want to implement a smooth and transparent upgrade process, that is first proposed on testnet and then on mainnet. Software upgrades generally aim to improve current performance and add new features to the Evmos chain. For more information on the types of upgrades, please visit our [Software Upgrade Guide](https://docs.evmos.org/validators/upgrades/overview.html).\n\n## Impact\n\nOn a high level, the v10.0.0-rc1 software includes the following improvements:\n\n* [Feesplit module](https://docs.evmos.org/modules/feesplit/): Developers can register their smart contracts and earn rewards everytime someone interacts with their registered smart contract\n* Upgrade to Ethermint [v0.19.2](https://github.com/evmos/ethermint/releases/tag/v0.19.2): Improves JSON-RPC reliability and maintainability and bumps SDK, Tendermint and IAVL dependencies and adds supports for optional params on EIP712\n* Upgrade ibc-go to [v3.2.0](https://github.com/cosmos/ibc-go/releases/tag/v3.2.0) and Cosmos SDK to [v0.45.7]\n\nA full changelog can be found [here](https://github.com/tharsis/evmos/releases/tag/v10.0.0-rc1).\n\n## Testing\n\nPrior to this proposal the version v10.0.0-rc1 is been upgraded to and tested on the [Evmos Testnet](https://testnet.mintscan.io/evmos-testnet/proposals/72).\n\nAdditionally, the Evmos core team created an End-to-End testing suite that performs the software upgrade locally. These tests have been completed successfully for this upgrade. The instructions on how to run the End-to-End testing suite can be found [here](https://github.com/ramacarlucho/evmos/blob/rama%2Fe2e_clean/tests/e2e/README.md).\n\n## Discussion\n\nBefore voting, please follow and discuss this proposal using the official [discussion on commonwealth](https://commonwealth.im/evmos/discussion/6653-evmos-software-upgrade-v810)." \
--from=commonwealth \
--fees=26000000000000000aevmos --gas=700000 -b block --chain-id=evmos_9001-2 \
--node=https://tendermint.bd.evmos.org:26657
```



## Mainnet

```markdown
## Author

Daniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team

## Software Upgrade being scheduled with this proposal

If successful, this proposal will schedule an Evmos software upgrade at block height [4,655,500](https://www.mintscan.io/evmos/blocks/4655500) from it's current version [v7.0.0](https://github.com/tharsis/evmos/releases/tag/v7.0.0) to [v10.0.0-rc1](https://github.com/tharsis/evmos/releases/tag/v10.0.0-rc1).

## Motivation

By proposing a scheduled upgrade, we want to implement a smooth and transparent upgrade process, that is first proposed on testnet and then on mainnet. Software upgrades generally aim to improve current performance and add new features to the Evmos chain. For more information on the types of upgrades, please visit our [Software Upgrade Guide](https://docs.evmos.org/validators/upgrades/overview.html).

## Impact

On a high level, the v10.0.0-rc1 software includes the following improvements:

* [Feesplit module](https://docs.evmos.org/modules/feesplit/): Developers can register their smart contracts and earn rewards everytime someone interacts with their registered smart contract
* Upgrade to Ethermint [v0.19.2](https://github.com/evmos/ethermint/releases/tag/v0.19.2): Improves JSON-RPC reliability and maintainability and bumps SDK, Tendermint and IAVL dependencies and adds supports for optional params on EIP712
* Upgrade ibc-go to [v3.2.0](https://github.com/cosmos/ibc-go/releases/tag/v3.2.0) and Cosmos SDK to [v0.45.7]

A full changelog can be found [here](https://github.com/tharsis/evmos/releases/tag/v10.0.0-rc1).

## Testing

Prior to this proposal the version v10.0.0-rc1 is been upgraded to and tested on the [Evmos Testnet](https://testnet.mintscan.io/evmos-testnet/proposals/72).

Additionally, the Evmos core team created an End-to-End testing suite that performs the software upgrade locally. These tests have been completed successfully for this upgrade. The instructions on how to run the End-to-End testing suite can be found [here](https://github.com/ramacarlucho/evmos/blob/rama%2Fe2e_clean/tests/e2e/README.md).

## Discussion

Before voting, please follow and discuss this proposal using the official [discussion on commonwealth](https://commonwealth.im/evmos/discussion/6653-evmos-software-upgrade-v810).
``` -->
