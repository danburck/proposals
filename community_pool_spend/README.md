# Creating a Proposal (Evmos v8.2.0)

## Local

```bash
evmosd tx gov submit-proposal community-pool-spend recover_ibc.json --from=mykey --fees=40aevmos -b block --gas=auto
```

## Mainnet

```bash
evmosd tx gov submit-proposal community-pool-spend recover_ibc.json \
--from=commonwealth --keyring-backend=os \
--fees=26000000000000000aevmos --gas=700000 -b block --chain-id=evmos_9001-2 \
--node=https://tendermint.bd.evmos.org:26657
```

## Description

```markdown
# Community Pool Spend: Recover IBC tokens from Airdrop
​
## Author
​
Daniel Burckhardt ([@danburck](https://twitter.com/danburck)), Evmos Core Team
​
## Motivation
​
Evmos’ [Rektdrop](https://medium.com/evmos/the-evmos-rektdrop-abbe931ba823) pioneered a new model for distributing tokens. As announced on the [Evmos dashboard](https://app.evmos.org/mission-control), the Rektdrop ended on Block [5074187](https://www.mintscan.io/evmos/blocks/5074187) (30 September 2022 at 16:06:40 UTC) and clawed back of all unclaimed tokens, returning them to the Evmos Community Pool.
​
During this process, the [IBC module account](https://www.mintscan.io/evmos/account/evmos1a53udazy8ayufvy0s434pfwjcedzqv345dnt3x) was falsely targeted for clawback and transferred all $EVMOS tokens from the IBC module account to the Evmos Community Pool. At the time of the clawback, this account held a balance of ~3.2 million EVMOS tokens (3167501226339726493675414aevmos).
​
To remediate this unexpected transfer of funds, we propose to return the funds from the Evmos Community Pool back to the IBC module account with this proposal.
​
## Impact
​
The EVMOS tokens on the IBC module account represent the total amount of EVMOS tokens, that have been sent to other chains over IBC. If there is insufficient balance on this account, users cannot return their EVMOS to the Evmos chain using IBC. The Community Pool Spend outlined in this proposal would regain the balance on the IBC module account and allow users again to transfer all their EVMOS tokens from other Comsmos chains back to the Evmos chain via IBC.
​
The bug additionally resulted in falsely targeting some additional user accounts during the clawback and transferred these accounts tokens back to the community pool as well. We’ve moved quickly to identify the wallets affected and amounts that each are owed. We are currently planning an additional upgrade that returns these funds as well.
​
## Requested amount
​
The requested amount to be returned to the IBC module account is determined by comparing the account balance one block before the clawback and after the block after the clawback.
​
Before clawback:
​
```bash
evmos@evmostest:~/evmos8.2.0/bin$ ./evmosd q bank balances evmos1a53udazy8ayufvy0s434pfwjcedzqv345dnt3x --height 5074186
balances:
- amount: "3167501226339726493675414"
  denom: aevmos
- amount: "100"
  denom: ibc/25813B5DF7C0AF9FB79A71EF8E67FE4E182A03BB4145D248DADFAF74006835B2
- amount: "11000"
  denom: ibc/5CC0E9B98B8C719E3378F941B40A4FAC9F750A155F3788E4C449144C08EA4537
- amount: "12274000"
  denom: ibc/693989F95CF3279ADC113A6EF21B02A51EC054C95A9083F2E290126668149433
- amount: "12000000000000000"
  denom: ibc/6B3FCE336C3465D3B72F7EFB4EB92FC521BC480FE9653F627A0BD0237DF213F3
- amount: "1000000"
  denom: ibc/7F0C2CB6E79CC36D29DA7592899F98E3BEFD2CF77A94340C317032A78812393D
- amount: "2310000"
  denom: ibc/A4DB47A9D3CF9A068D454513891B526702455D3EF08FB9EB558C561F9DC2B701
- amount: "100000000000000000"
  denom: ibc/D8921A62D207159A25FFEA0DB4E7DB623A095219B60D99768CCE9D3DF66122C7
pagination:
  next_key: null
  total: "0"
```
​
Afer clawback:
​
```bash
evmos@evmostest:~/evmos8.2.0/bin$ ./evmosd q bank balances evmos1a53udazy8ayufvy0s434pfwjcedzqv345dnt3x --height 5074187
balances:
- amount: "100"
  denom: ibc/25813B5DF7C0AF9FB79A71EF8E67FE4E182A03BB4145D248DADFAF74006835B2
- amount: "11000"
  denom: ibc/5CC0E9B98B8C719E3378F941B40A4FAC9F750A155F3788E4C449144C08EA4537
- amount: "12274000"
  denom: ibc/693989F95CF3279ADC113A6EF21B02A51EC054C95A9083F2E290126668149433
- amount: "12000000000000000"
  denom: ibc/6B3FCE336C3465D3B72F7EFB4EB92FC521BC480FE9653F627A0BD0237DF213F3
- amount: "1000000"
  denom: ibc/7F0C2CB6E79CC36D29DA7592899F98E3BEFD2CF77A94340C317032A78812393D
- amount: "2310000"
  denom: ibc/A4DB47A9D3CF9A068D454513891B526702455D3EF08FB9EB558C561F9DC2B701
- amount: "100000000000000000"
  denom: ibc/D8921A62D207159A25FFEA0DB4E7DB623A095219B60D99768CCE9D3DF66122C7
pagination:
  next_key: null
  total: "0"
```
​
The entire Emvos balance of 3167501226339726493675414aevmos was transferred to the community pool after the clawback.
​
## Learnings
​
The Evmos team will publish a detailed post-mortem document to reflect on what led to this event and how it could have been prevented. These reflections have helped us to improve our team's testing processes a lot in the past and build resilient software. We apologize for any inconvenience that this might have caused and are open to any further questions on this topic.

```
