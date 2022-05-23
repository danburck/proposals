## Author

Daniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team

## Parameter being changed with this proposal

If successful, this proposal will enable the inflation module on Evmos by changing the `ParamStoreKeyEnableInflation` parameter from `false` to `true`. This proposal has a voting time of 5 days.

## Motivation

When the chain initially launched, the inflation module was enabled and new Evmos tokens were minted and allocated according to the Evmos Token Model once a day until the chain halted. After the halt, Evmos relaunched with the inflation module disabled for two main reasons:

* ensure that the chain is secure and chain upgrades are successful
* give more time to those who hadn't been able to claim their airdrop

## Impact

Now, that several upgrades have passed successfully on-chain and more users have claimed their airdrop, inflation could be enabled. Enabling this module activates

* staking rewards,
* usage incentives and
* community pool allocation.

## Discussion

Before voting, please follow and discuss this proposal using the official [discussion on commonwealth](https://commonwealth.im/evmos/discussion/4965-enable-inflation-module). For an in-depth explanation of the module, please refer to the [specification](https://docs.evmos.org/modules/inflation/).

## Testing on Testnet

With [proposal 28](https://testnet.mintscan.io/evmos-testnet/proposals/28) the inflation module has already been enabled on Testnet. Please take part in testing its correctness by

* staking tokens: You should receive staking rewards once a day
* interacting with registered usage incentives: You should be able to query your gas meters after interacting with an incentivized smart contract. Once a week, your gas meters are reset and you receive Evmos tokens from the incentives pool based on how much gas you spent on interacting with incentivized smart contracts. The incentives pool fills up once a day through inflation
* querying the community pool: a part of inflation is allocated in the community pool once a day. Query the community pool to make sure it's increasing according to the [Evmos Token Model](https://evmos.blog/the-evmos-token-model-edc07014978b).

Note, that the team allocation of the Evmos Token Model is not handled through inflation but instead was implemented with vesting accounts.