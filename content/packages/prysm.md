---
title: Prysm
description: Setting up an ETH2.0 validator
tags: [eth, ethereum, prysm, tutorial]
aliases: [/en/tutorials/prysmvalidator]
---
{{< figure src="avatar.png" >}}

{{< toc >}}


[Prysm](https://docs.prylabs.network/) is an Ethereum proof-of-stake client written in Go by Prysmatic Labs.

Prysm is split in two Avado packages:
1. The consenus client: **Prysm ETH2.0 Beacon Chain**
2. The validator client: **Prysm ETH2.0 Validator**

You only need the first package to run a full Ethereum node. If want to stake, you need the Validator package too.

## Installation

Before running the Teku consensus client, you need to install and run the [geth execution client]({{< relref "geth" >}}).

Installing Prysm is as simple as navigating to the [DappStore](http://my.ava.do/#/installer), and clicking the **Install** button for both the **Prysm ETH2.0 Beacon Chain** and **Prysm ETH2.0 Validator** package.


Next you need to configure the “Fee recipient address”. This is the address where you will receive the priority fees of transactions in the blocks you propose:
   * Open the *Beacon Chain* package: <http://prysm-beacon-chain-prater.my.ava.do/settings>
   * Enter the fee recipient address
   * Click **Apply changes**
 
{{< figure src="../prysm/prysm_fee_recipient.png" >}}

Once you have installed the Prysm consensus client, the beacon chain will sync automatically. The beacon chain may take a few hours to sync the first time you install, depending on the size of the Beacon Chain at the time you are installing.

## Run a validator

To run a validator, you need to [create Validator keys first]({{< relref eth2keygen >}})

{{< hint type=important >}}
Proceed at your own risk. You are solely responsible for your stake.
{{< /hint >}}

### Import Your key store file

As a result of the [Key Generator process]({{< relref eth2keygen >}}), you now have a _keystore file_ and you are now ready to import this file em to the Avado by following the steps in the video below.

To run a validator, you need to [create Validator keys first]({{< relref eth2keygen >}})

1. To add a validator click the **Add validator** field to expand it:
   {{< figure src="../teku/add_validator.png" >}}
   {{< figure src="../teku/add_validator_exp.png" >}}
2. Next, click **Choose keystore file...** and browse to the keystore file (json) you downloaded from the [Key generator package]({{< relref "packages/eth2keygen#download" >}})
3. Enter the keystore password
4. (Optional) If you have a slashing protection file, upload the file here.
5. Finally click **Add validator** to add the validator

{{< hint type=info >}}
You can also set a different fee recipient address for each validator. This is required if you mix full validators with [Rocket Pool validators]({{< relref "rocketpool" >}})
{{< /hint >}}


{{< hint type=tip title=success >}}
It is strongly recommended that you use <https://beaconcha.in> to monitor your validator.

There are plenty of hyperlinks on the Avado UI, that take you straight to the information about your validators on this website.
{{< /hint >}}


## Exit validators

{{< hint type=warning title=Warning >}}
⚠️ Please make sure you understand the consequences of performing a validator exit. This action cannot be reverted.
{{< /hint >}}

1. Open the **Prysm UI**
2. Click the **Exit Validator** button 
   {{< figure src="../prysm/exit_button.png" >}}
4. Type `agree` into **Confirmation** field
5. Click **Exit validator**
    {{< figure src="../prysm/exit_confirm.png" >}}

After a while, the [status of the validator](http://prysm-beacon-chain-mainnet.my.ava.do/) will change from `active_ongoing` over `active_exiting` to `exited_unslashed`

{{< figure src="../prysm/exit_before.png" >}}
{{< figure src="../prysm/exit_after.png" >}}
{{< figure src="../prysm/exit_after2.png" >}}

## Checkpoint sync

Prysm enables you to be up and running in only a few minutes by downloading a recent finalized checkpoint state from a trusted source rather than syncing from genesis.

### Configure

[EthStaker](https://ethstaker.cc/) runs a server that offers recent checkpoint snapshots. To use it, add following arguments to the `EXTRA_OPTS` field on <http://my.ava.do/#/Packages/prysm-beacon-chain-mainnet.avado.dnp.dappnode.eth/detail>:
```
--checkpoint-sync-url=https://beaconstate.ethstaker.cc
--genesis-beacon-api-url=https://beaconstate.ethstaker.cc
```

If your Prysm already started syncing from genesis: click **Reset** to make sure **checkpoint sync** is used.

### Check

You can verify the checkpoint sync by opening the check page. 
Check the state root of the displayed trusted sources make sure the state root matches. If all state roots match, all is good. You can find more trusted sources on <https://eth-clients.github.io/checkpoint-sync-endpoints/>



## AVADO support channel
Telegram: [AVADO - Ethereum Club](https://t.me/joinchat/IdBKSAiIvw-q1-1p)




