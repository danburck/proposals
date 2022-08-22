# Creating a Proposal

## Local

```bash
# make proposal
evmosd tx gov submit-proposal software-upgrade "v8.0.0" \
--title "Evmos Local v8 Upgrade" \
--deposit 500000aevmos \
--upgrade-height 1200000 \
--upgrade-info '{"binaries":{"darwin/arm64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Darwin_arm64.tar.gz","darwin/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Darwin_x86_64.tar.gz","linux/arm64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Linux_arm64.tar.gz","linux/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Linux_x86_64.tar.gz","windows/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Windows_x86_64.zip"}}' \
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
evmosd tx gov submit-proposal software-upgrade "v8.0.0" \
--title "Evmos Testnet v8.0.0 Upgrade" \
--upgrade-height 4600000 \
--upgrade-info '{"binaries":{"darwin/arm64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Darwin_arm64.tar.gz","darwin/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Darwin_x86_64.tar.gz","linux/arm64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Linux_arm64.tar.gz","linux/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Linux_x86_64.tar.gz","windows/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Windows_x86_64.zip"}}' \
--description "## Author\n\nDaniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team\n\n## Software Upgrade being scheduled with this proposal\n\nIf successful, this proposal will schedule an Evmos software upgrade at block height [4,600,000](https://testnet.mintscan.io/evmos-testnet/blocks/4600000) from it's current version [v7.0.0](https://github.com/tharsis/evmos/releases/tag/v7.0.0) to [v8.0.0](https://github.com/tharsis/evmos/releases/tag/v8.0.0).\n\n## Motivation\n\nBy proposing a scheduled upgrade, we want to implement a smooth and transparent upgrade process, that is first proposed on testnet and then on mainnet. Software upgrades generally aim to improve current performance and add new features to the Evmos chain. For more information on the types of upgrades, please visit our [Software Upgrade Guide](https://docs.evmos.org/validators/upgrades/overview.html).\n\n## Impact\n\nOn a high level, the v8.0.0 software includes the following improvements:\n\n* Feesplit module: Developers can register their smart contracts and earn rewards everytime someone interacts with their registered smart contract\n* Upgrade to Ethermint [v0.19.0](https://github.com/evmos/ethermint/releases/tag/v0.19.0): Improves JSON-RPC reliability and maintainability\n* Upgrade ibc-go to [v3.2.0](https://github.com/cosmos/ibc-go/releases/tag/v3.2.0) and Cosmos SDK to [v0.45.7]\n\nA full changelog can be found [here](https://github.com/tharsis/evmos/releases/tag/v8.0.0).\n\n## Testing\n\nThe Evmos core team created an End-to-End testing suite that performs the software upgrade locally. These tests have been completed successfully for this upgrade. The instructions on how to run the End-to-End testing suite can be found [here](https://github.com/ramacarlucho/evmos/blob/rama%2Fe2e_clean/tests/e2e/README.md).\n" \
--from=a1 \
--fees=7000000000000atevmos --gas=700000 -b block --chain-id=evmos_9000-4 \
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
evmosd tx gov submit-proposal software-upgrade "v8.0.0" \
--title "Evmos Mainnet v8.0.0 Upgrade" \
--upgrade-height 3620000 \
--upgrade-info '{"binaries":{"darwin/arm64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Darwin_arm64.tar.gz","darwin/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Darwin_x86_64.tar.gz","linux/arm64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Linux_arm64.tar.gz","linux/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Linux_x86_64.tar.gz","windows/x86_64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Windows_x86_64.zip"}}' \
--description "## Author\n\nDaniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team\n\n## Software Upgrade being scheduled with this proposal\n\nIf successful, this proposal will schedule an Evmos software upgrade at block height [3,620,000](https://www.mintscan.io/evmos/blocks/3620000) from it's current version [v7.0.0](https://github.com/tharsis/evmos/releases/tag/v7.0.0) to [v8.0.0](https://github.com/tharsis/evmos/releases/tag/v8.0.0).\n\n## Motivation\n\nBy proposing a scheduled upgrade, we want to implement a smooth and transparent upgrade process, that is first proposed on testnet and then on mainnet. Software upgrades generally aim to improve current performance and add new features to the Evmos chain. For more information on the types of upgrades, please visit our [Software Upgrade Guide](https://docs.evmos.org/validators/upgrades/overview.html).\n\n## Impact\n\nOn a high level, the v8.0.0 software includes the following improvements:\n\n* Feesplit module: Developers can register their smart contracts and earn rewards everytime someone interacts with their registered smart contract\n* Upgrade to Ethermint [v0.19.0](https://github.com/evmos/ethermint/releases/tag/v0.19.0): Improves JSON-RPC reliability and maintainability\n* Upgrade ibc-go to [v3.2.0](https://github.com/cosmos/ibc-go/releases/tag/v3.2.0) and Cosmos SDK to [v0.45.7]\n\nA full changelog can be found [here](https://github.com/tharsis/evmos/releases/tag/v8.0.0).\n\n## Testing\n\nThe Evmos core team created an End-to-End testing suite that performs the software upgrade locally. These tests have been completed successfully for this upgrade. The instructions on how to run the End-to-End testing suite can be found [here](https://github.com/ramacarlucho/evmos/blob/rama%2Fe2e_clean/tests/e2e/README.md).\n\n## Discussion\n\nBefore voting, please follow and discuss this proposal using the official [discussion on commonwealth](https://commonwealth.im/evmos/discussion/6653-evmos-software-upgrade-v800)." \
--from=commonwealth \
--fees=26000000000000000aevmos --gas=700000 -b block --chain-id=evmos_9001-2 \
--node=https://tendermint.bd.evmos.org:26657
```

0.02503153
26000000000000000

# Description Template

```markdown
## Author

Daniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team

## Software Upgrade being scheduled with this proposal

If successful, this proposal will schedule an Evmos software upgrade at block height [3,620,000](https://www.mintscan.io/evmos/blocks/3620000) from it's current version [v7.0.0](https://github.com/tharsis/evmos/releases/tag/v7.0.0) to [v8.0.0](https://github.com/tharsis/evmos/releases/tag/v8.0.0).

## Motivation

By proposing a scheduled upgrade, we want to implement a smooth and transparent upgrade process, that is first proposed on testnet and then on mainnet. Software upgrades generally aim to improve current performance and add new features to the Evmos chain. For more information on the types of upgrades, please visit our [Software Upgrade Guide](https://docs.evmos.org/validators/upgrades/overview.html).

## Impact

On a high level, the v8.0.0 software includes the following improvements:

* Feesplit module: Developers can register their smart contracts and earn rewards everytime someone interacts with their registered smart contract
* Upgrade to Ethermint [v0.19.0](https://github.com/evmos/ethermint/releases/tag/v0.19.0): Improves JSON-RPC reliability and maintainability
* Upgrade ibc-go to [v3.2.0](https://github.com/cosmos/ibc-go/releases/tag/v3.2.0) and Cosmos SDK to [v0.45.7]

A full changelog can be found [here](https://github.com/tharsis/evmos/releases/tag/v8.0.0).

## Testing

The Evmos core team created an End-to-End testing suite that performs the software upgrade locally. These tests have been completed successfully for this upgrade. The instructions on how to run the End-to-End testing suite can be found [here](https://github.com/ramacarlucho/evmos/blob/rama%2Fe2e_clean/tests/e2e/README.md).

## Discussion

Before voting, please follow and discuss this proposal using the official [discussion on commonwealth](https://commonwealth.im/evmos/discussion/6653-evmos-software-upgrade-v800).
```


```json
{
  "binaries":{
  "darwin/arm64":"https://github.com/tharsis/evmos/releases/download/d/evmos_8.0.0_Darwin_arm64.tar.gz",
  "darwin/x86_64":"https://github.com/tharsis/evmos/releases/download/v8.0.0/evmos_8.0.0_Darwin_x86_64.tar.gz",
  "linux/arm64":"https://github.com/tharsis/evmos/releases/download/v8.0.0/evmos_8.0.0_Linux_arm64.tar.gz",
  "linux/x86_64":"https://github.com/tharsis/evmos/releases/download/v8.0.0/evmos_8.0.0_Linux_x86_64.tar.gz",
  "windows/x86_64":"https://github.com/tharsis/evmos/releases/download/v8.0.0/evmos_8.0.0_Windows_x86_64.zip"
  }
}
```