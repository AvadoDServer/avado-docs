---
title: Gnosis
description: Instructions on how to start validating on the Gnosis Beacon chain
aliases: [/en/tutorials/gnosis_beacon_chain]
---

{{< figure src="gnowledge_avado.jpg" >}}
{{< toc >}}

## Running a Gnosis chain node

Since the Gnosis merge to _Proof of Stake_ on December 7 2022, Gnosis requires two Avado packages to run:
1. An execution client: [Nethermind-Gnosis](http://my.ava.do/#/installer/nethermind-gnosis.avado.dnp.dappnode.eth)
2. A consensus client: [Teku-Gnosis](http://my.ava.do/#/installer/teku-gnosis.avado.dnp.dappnode.eth)

Once installed, both packages start syncing automatically. 

⏳ Be patient: Syncing takes some time. You will see high CPU usage for a while. (As a point of reference: on an Avado i7, Nethermind-gnosis took about 12 hours of high CPU usage (sync from scratch). Teku-gnosis took 24 hours to drop from ~200% to ~100% CPU usage.)

### Teku-Gnosis

Teku-Gnosis reports its status on <http://teku-gnosis.my.ava.do>.

😀 What you should see:
   * **Status**: "Syncing x %" or "In Sync" (If you see "Syncing 100%", it means Teku is synced, but it is waiting for Nethermind-Gnosis to be in sync)
   * **Connected Peers**: number bigger than 0
  
🧐 What you prefer not to see:
* **"Inbound: 0"**: This means you have no inbound peers, so port `9006` (used for p2p communication) is closed from the outside. Manually open this port on your router if your are not using UPnP.

🙁 What you don't want to see:
* **"Waiting for the beacon chain to become ready"**: It is Ok for this message to appear when you open the page. But it should the status after a few seconds. If this messages persists, Teku-Gnosis could not start. Check the [logs](http://my.ava.do/#/Packages/teku-gnosis.avado.dnp.dappnode.eth/detail) for a clue.

### Nethermind-Gnosis

Syncing Nethermind takes a lot of time (>140 GB of data), so you will need patience. You can check that it is making progress, by looking at the block numbers in <http://nethermind-gnosis.my.ava.do>, or the disk size or logs in <http://my.ava.do/#/Packages/nethermind-gnosis.avado.dnp.dappnode.eth/detail>.

## Set up a Validator on the Gnosis Beacon Chain

Most users also run a validator on the Gnosis Chain. This requires you to run a node, deposit GNO and configure your validators.

{{< hint type=important >}}
Proceed at your own risk. YOU take all risks associated with using this software and it is possible that you could lose your funds. You are solely responsible for your stake.

Visiting the official Gnosis Beacon Chain Deposit website is the ONLY way you should make the deposit. Do not attempt to manually send funds to the deposit contract or your will lose your funds.
{{< /hint >}}

### Step 0 :  Set up Metamask for the Gnosis (formerly xDai) network and Obtain GNO

There are a number of ways to obtain GNO. Do your own research and proceed at your own risk. It is highly recommended that if you don't already have GNO on the ETH mainnet that you do not purchase it on the mainnet or else you will end up by far more in gas fees than you should be to bridge it across to the Gnosis chain. If you have GNO on the mainnet already, you can bridge it to the Gnosis chain by going to <https://omni.xdaichain.com/bridge>.

One easy and cost effective way to obtain GNO on the Gnosis chain (formerly xDai) is to bridge Dai from the ETH mainnet to the Gnosis chain using [The Gnosis Chain Bridge](https://bridge.gnosischain.com/). When you bridge Dai to xDai, you will then already have the xDai in your wallet that is needed to pay the gas on transactions of the Gnosis chain (which only cost fractions of a cent!).

 {{< figure src="inkedbridge_li.jpg" >}}

Then once you have xDai in the account you wish to use to make your validator deposit, you can use [Honeyswap](https://honeyswap.org/) or [CowSwap](https://cowswap.exchange/#/swap) or to swap xDai for GNO. Remember that for each validator you plan to run on the Gnosis Beacon Chain, you will need exactly 1 GNO. It is highly recommended that you start with 1 validator so that you can become familiar with this process before you try to run more.

You can import the GNO token to Metamask by visiting https://blockscout.com/xdai/mainnet/token/0x9C58BAcC331c9aa871AFD802DB6379a98e80CEdb/token-transfers
and then clikcing on the fox to import the token to Metamask.

 {{< figure src="import_gno_token.jpg" >}}

 {{< figure src="mm_gno_token.jpg" >}}

### Step 1 : Create your validators keys with Gnosis Wagyu

Wagyu is a Desktop GUI application that makes it easy to generate validator keys. Download Waygu from
<https://github.com/alexpeterson91/Gnosis-Wagyu-Key-Gen/releases>

Unzip the app and start the application. (If MacOs complains that the developer cannot be verified, right click and select "open")

{{< figure src="gnosis_wagyu.png" >}}
{{< figure src="gnosis_wagyu_finish.png" >}}


A wizard will guide you through the process.

{{< hint type=important >}}
If this is your first validator, have a pen and paper ready to write things down. This is important before you proceed. You will be writing down passwords and a 24 word mnemonic phrase which are **your responsibility** to keep safe throughout your staking journey. **If you lose the 24 word mnemonic phrase, no one will be able to help you and you will not be able to withdraw your funds when withdrawals are enabled.**
{{< /hint >}}

{{< hint type=info >}}
Note that if you wish to create more keys later on using the key generator, if you use the same keystore password for all future keys that you create and stake with on the Avado, it will make your life easier if you ever have to re-import all your keys to the validator client. Just take care to manage your passwords and mnenonic phrases carefully when creating future validator keys.

Note that if you wish to run more than 1 validator, the EASIEST way to do this is to create a new keystore, deposit data and a new mnemonic phrase for each individual validator and then make individual deposits of 1 GNO each. You can create multiple keys in a batch using the existing key generator, and that will generate multiple keys with ONE deposit data file. Only do this if you have enough funds to make the deposit for the number of keys you generate or you will have a bad time when you get to Step #5. Whatever you do, keep careful track of whatever keys you make and keep them and the other files together and consider some type of naming scheme so you don't get confused later on.

**You have been warned!**
{{< /hint >}}

### Step 2 : Configure your fee recipient address

Open the [settings page](http://teku-gnosis.my.ava.do/settings) and enter the address where you want to receive the fees of your proposed blocks. Most users use their MetaMask address here, but of course you can also specify a hard wallet address.

{{< hint type=important >}}
🔥 Don't skip this step. Your validators will run if you forget this step, but all block fees will be burned. 🔥
{{< /hint >}}


### Step 3 : Import Your Key to the Validator Wallet on your Avado

{{< hint type=important >}}
It is highly recommended that before you proceed to the next steps that you ensure that your Gnosis Beacon chain is synced. To do this, simply open the Gnosis beacon chain package and scroll down to inspect the logs. An example of what your logs will look like when the chain is in sync is shown below.
{{< /hint >}}

It is recommended that you import the keystore file to the validator wallet before you make the deposit to ensure that the validator will accept your keystore file before you lock your funds into the deposit contract. 

Import your keys: Open the [Avado Teku Gnosis package](http://teku-gnosis.my.ava.do/), open the **Add validator** box and (per key):
  * Click **Choose keystore file...** and select your keystore file
  * Enter the corresponding password
  * Click **Add validator**
  * Repeat for all your keys. If your keys all have the same password, you leave the password field as is, and immediately click **Add Validator** after selecting the next keystore file.

{{< figure src="add_validator.png" >}}

### Step 4 : Visit the Gnosis Beacon Chain deposit website to make your deposit to the staking contract

{{< hint type=danger >}}
Warning! Visiting the official Gnosis Beacon Chain Deposit website is the **ONLY** way you should make the desposit. **Do not attempt to manually send funds to the deposit contract or your will lose your funds.**
{{< /hint >}}

Make sure your Metamask is set on the Gnosis chain (or xDai) as we discussed in Step 0.

Visit the [Gnosis Beacon Chain Deposit website](https://deposit.gnosischain.com/) and verify that the URL is https://deposit.gnosischain.com/ and then connect your Metamask wallet. Make sure your wallet is set to the Gnosis/xDai network.

 {{< figure src="deposit_1.jpg" >}}

**Now, it is time to make the deposit.**

Open the validator_keys folder that was created in Step 1. Drag the deposit data file (**and only the deposit_data file**) into the window that is showing on the Deposit page. Wait for it to confirm the deposit data. Note that this screenshot was taken from an older version of the deposit site and it is no longer required to swap to mGNO prior to making the deposit. As long as you have at least 1 GNO in your wallet when you import the deposit data file, the wizard will do the swap for you behind the curtain. 

 {{< figure src="inkeddeposit_5_li.jpg" >}}

Then you may click on **Deposit**.

You will be asked to check three boxes to acknowledge that you have a pulse.

 {{< figure src="deposit_6.jpg" >}}

Let the deposit complete.

 {{< figure src="inkeddeposit_7_li.jpg" >}}

That is it for the deposit. Give it time to process, it takes about 2-4 hours for the deposit to be recognized by the GBC. 

Check the status of your validators on the Gnosis Beacon Chain Dashboard. You can do this by clicking the green bar with the 📡 logo.

{{< figure src="teku-gnosis.png" >}}

At this point, your validator should start making attestations automatically when it becomes active as long as you leave the Gnosis Beacon Chain and Validator packages running 24/7.

## Common issues

Check the [Teku-Gnosis logs](http://my.ava.do/#/Packages/teku-gnosis.avado.dnp.dappnode.eth/detail) and the [Nethermind-Gnosis logs](http://my.ava.do/#/Packages/nethermind-gnosis.avado.dnp.dappnode.eth/detail):

### Nethermind-Gnosis

Problem: `nginx: [emerg] cannot load certificate ...`
: Fix: Restart Nethermind-gnosis

Proble: `Failed to create CoreCLR, HRESULT: 0x80070008`
: Fix: Make sure the Dappmanager core package is up to date (i.e. newer than 0.0.42)

### Teku-Gnosis

Problem: `Waiting for the JWT Token`
: Fix: Restart Nethermind (and check the Nethermind logs for errors listed above)

Problem: `Connected Peers: 0`
: Fix: Make sure Teku Gnosis is up to date (i.e. new than 0.0.1)

## AVADO support channel
Telegram: [AVADO - Gnosis Staking](https://t.me/AvadoXDAI)


## Useful Links
* Main Gnosis Chain website: <https://www.gnosis.io>
* Gnosis Chain documentation: <https://docs.gnosischain.com>
* Gnosis Beacon Chain explorer: <https://beacon.gnosischain.com>
* Gnosis Chain Explorer: <https://gnosisscan.io>
* Gnosis Chain Blockscout: <https://blockscout.com/xdai/mainnet>