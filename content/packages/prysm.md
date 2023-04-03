---
title: Prysm
description: Setting up an ETH2.0 validator
tags: [eth, ethereum, prysm, tutorial]
aliases: [/en/tutorials/prysmvalidator]
---
{{< figure src="avatar.png" >}}

{{< toc >}}

{{< hint type=important title="Withdrawals update" >}}
Exciting news: Ethereum staking withdrawals are coming soon. [Read more]({{< ref "/specials/withdrawals" >}})
{{< /hint >}}

{{< hint type=note title="Prysm UI deprecation notice" >}}
The Prysm team is deprecating its web UI. 
{{< figure src="deprecation.png" >}}

Don't worry! Avado will introduce a new UI (similar to Teku's UI), before the Prysm UI is removed.
{{< /hint >}}


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

### Import Your Key to the Validator Wallet on the Avado

As a result of the [Key Generator process]({{< relref eth2keygen >}}), you now have a _keystore file_ and you are now ready to import this file em to the Avado by following the steps in the video below.

{{< youtube yx0kKSZTgRk >}}

1. Open the Validator package on the Avado:
  {{< figure src="open_val.png" >}}
2. After agreeing and opening the Prysm web dashboard, you will then be propmted to create a wallet on the Avado to hold your validator keys. Select Imported Wallet.
  {{< figure src="imported_wallet.png" >}}
3. Next, you will be prompted to import the keystore file that you created using the key generator. Simply drag the keystore file into the window where indicated and click continue. Do **not** drag the whole folder into the window, open the extracted folder and drag in only the keystore file or files if doing more than one.
  {{< figure src="import_keystore.png" >}}
4. Then you will be prompted to enter your keystore password. This is the same password that you used when you created the key with the key generator.
  {{< figure src="keystore_unlock.png" >}}
5. Lastly, you will be prompted to enter a wallet password. This password is used by the Avado to encrypt your validator wallet and should be a secure password but does not carry the same stringent requirements as the password in the previous step.
  {{< figure src="wallet_password.png" >}}

After you hit continue, if you have done everything correctly, you will be taken to the web UI and you should see this in the upper right hand corner:
  {{< figure src="beacon_status.png" >}}

At this point, your validator should start making attestations automatically when it becomes active as long as you leave the Beacon Chain and Validator packages running 24/7. You can log out of the Prysm Web UI but simply leave your Avado on with the required packages (ETH1, Beacon Chain and Vaildator) running. You can monitor the status of your validator at beaconcha.in or beaconscan.com

{{< hint type=tip title=success >}}
**If you have followed all the steps up to this point, congratulations you will be validating very soon!!!**
{{< /hint >}}

{{< hint type=tip title=success >}}
It is strongly recommended that you use <https://beaconcha.in> to monitor your validator, rather than relying on the prysm web UI. You can and should search your validator public key number on beaconcha.in soon after you have completed the deposit. To get your validator public key number, open the keystore json file with a text editor and you will see it. Copy it to your clipboard and then search it on beaconcha.in and bookmark this page as you will likely want to end up coming back to it daily to monitor your validator performance.
{{< /hint >}}


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



## Troubleshooting

There is a known issue with the prysm web UI and the Brave browser. If you are using Brave, please make sure you turn the shields off for this page or it will not read correctly.

 {{< figure src="switch2.jpg" >}}

Here is the list of common errors you may see in red at the bottom of the screen after creating the validator through the Web UI:

**500 is wrong password on your keystore file.** The keystore password you entered when importing your key to the Avado through the Prysm Web UI does not match the password you used when you created your keystore file. You can double check the keystore password by looking in the folder generated by the key generator and there is a text file called password that you can check on.

**400 is password not meeting requirements for the web UI.** This is the second prompt for a password that you come to when setting up the Prysm Web UI. This is the most common error BY FAR and it is due to the stringent password requirments of the Prysm Web UI. If you are getting this error, start over with the validator setup and pay careful attention to the password you choose for the Prysm Web UI. A recommended password format is 8-10 characters. Here is a sample of a valid password, you will use a different one. Fs<6@tx8

**0 beacon chain not ready.** Check that the Beacon Chain is installed and running and is synced. If it is not, you should either wait until it is synced or you should reinstall the Beacon Chain package from scratch by clicking on remove volume and then let the Beacon Chain reinstall with the default settings.
 {{< figure src="beacon_sync.png" >}}

 {{< figure src="remove_vol.png" >}}

If after importing your validator key to the Prysm Web UI, you see this error in the upper right hand corner but the Beacon Chain and Validator logs look okay, please try using another browser to access the Prysm Web UI. There have been several instances of people having problems accessing the Prysm Web UI with the Brave browser and at this time, Avado is not able to fix this as it is related to the Prysm Web UI backend which is not under the control of Avado.

 {{< figure src="beacon_unknown.jpg" >}}

Sometimes it may be necessary to restart the Beacon Chain and Validator packages if you start missing attestations and can't figure out why. Simply press restart for the Beacon Chain and Validator and let them reload, then monitor your Validator status on beaconcha.in or beaconscan.com to see if your validator resumes it's duties.
 {{< figure src="restart_client.png" >}}

If you are unable to resolve any other errors you are having, please reach out on the telegram channel and we will add reseolved issues to this guide as the solutions become known.


## AVADO support channel
Telegram: [AVADO - Ethereum Club](https://t.me/joinchat/IdBKSAiIvw-q1-1p)




