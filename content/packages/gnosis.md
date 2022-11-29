---
title: Gnosis
description: Instructions on how to start validating on the Gnosis Beacon chain
aliases: [/en/tutorials/gnosis_beacon_chain]
---

{{< toc >}}

# 🚀 The merge 🚀

🗓️ *[The Gnosis Merge](https://docs.gnosischain.com/specs/hard-forks/merge) is currently scheduled for ~ Wednesday the **7th of December 2022**. Please be sure to update your nodes before **November 30th.***

{{< hint type=caution title="Slashing risk" >}}
⚠️ Never run the same key on two different validators at the same time. ⚠️ 
This is a slashable offense. So be careful in the next steps.
{{< /hint >}}

What you have to do:
1. 🦉 Make sure your **Nethermind Gnosis** ("Execution client") package is up to date: you should have version `0.0.20` or newer.
2. ⚠️ The old Gnosis package (Prysm-based) is no longer support, so you have to replace it with **Teku-Gnosis**:
   1. 👀 Verify you have a backup of your **deposit files** and **passwords** (If you don't, do *not* proceed to the next step and [ask for help](#avado-support-channel) instead) 
   2. 🚮 Remove the **Gnosis Validator** and **Gnosis Beacon Chain** packages:
       * Open the "[Gnosis Beacon Chain management page](http://my.ava.do/#/Packages/prysm-gnosis-beacon-chain.avado.dnp.dappnode.eth/detail)" and click **Remove**
       * Open the "[Gnosis Validator management page](http://my.ava.do/#/Packages/prysm-gnosis-validator.avado.dnp.dappnode.eth/detail)" and click **Remove**
   4. ➕ Install the **Teku-Gnosis** package from the [DappStore](http://my.ava.do/#/installer/teku-gnosis.avado.dnp.dappnode.eth)
   5. ✏️ Configure you **fee recipient address**: Open the [Settings page](http://teku-gnosis.my.ava.do/settings) and enter the address where you want to receive the fees of your proposed blocks.
   6. 🔑 Import your keys: Open the [Avado Teku Gnosis package](http://teku-gnosis.my.ava.do/), open the **Add validator** box and (per key):
      * Click **Choose keystore file...** and select your keystore file
      * Enter the corresponding password
      * Click **Add validator**
      * Repeat for all your keys. If your keys all have the same password, you leave the password field as is, and immediately click **Add Validator** after selecting the next keystore file.
  7. 🧑‍💻 Check the status:
     * Check peers: You should have both **inbound** and **outbound** peers. If you only have outbound peers, check your firewall.
     * Check your validators on the Gnosis Beacon Chain Dashboard. You can do this by clicking the green bar with the 📡 logo.

{{< figure src="teku-gnosis.png" >}}

{{< hint type=important >}}
The Gnosis chain is moving to Proof of Stake soon. The information below will be outdated soon.
{{< /hint >}}

# Set up a Validator on the Gnosis Beacon Chain


{{< hint type=important >}}
It is not difficult to follow the steps in this guide to start staking on the Gnosis beacon chain but it involves a few steps to configure your Metamask wallet for the Gnosis network (formerly xDai) and to bridge funds from the ETH mainnet across to the Gnosis network. These steps can feel intimdating at first but it is really not that hard if you follow the guide and soon it will all make sense and you will enjoy the luxury of operating on an ETH sidechain with ulta-low transaction fees in xDai.
{{< /hint >}}

{{< hint type=tip title=success >}}
Avado makes it easy. At no point in following this Avado guide will you ever need to access a command line to run a script. Official Gnosis docs are here and you can and should read them but be warned, the methods are complicated! Read the Gnosis docs but return to this guide for the "easy" method. https://docs.gnosischain.com/
{{< /hint >}}


Getting started from scratch (fresh install) ***Owl memes are encouraged as we build our Gnowledge!***

{{< figure src="gnowledge_avado.jpg" >}}

{{< hint type=tip title=success >}}
 This guide describes the steps of generating keys using the Gnosis GBC Key Generator package and then accessing the official Gnosis Beacn Chain Deposit website to complete the deposit to the Gnosis Beacon Chain deposit contract 0x0B98057eA310F4d31F2a452B414647007d1645d9 

{{< /hint >}}

{{< hint type=important >}}
Proceed at your own risk. It is very Important to note that this software is still in the Alpha phase of testing, not even beta yet. It might be buggy, things might not work, and be aware that if by knowing this you still want to use it, YOU take all risks associated with using this software and it is possible that ytou could lose your funds. You are solely responsible for your stake.

{{< /hint >}}

{{< hint type=danger >}}
Visiting the official Gnosis Beacn Chain Deposit website is the ONLY way you should make the desposit. Do not attempt to manually send funds to the deposit contract or your will lose your funds.

{{< /hint >}}



## Step 0 :  Set up Metamask for the Gnosis (formerly xDai) network and Obtain GNO

First you should set up your Metamask for the Gnosis (xDai) Network. 

**Quick Methods**
[Chainlist.org](https://chainlist.org/) Click xDai to add You may still need to add https://blockscout.com/ as the Block Explorer.

https://sushi.com/ With MetaMask enabled on Ethereum, click on the network dropdown and select xDai. MetaMask will ask for approval to add the xDai chain.

**Manual instructions** can also be found here: https://www.xdaichain.com/for-users/wallets/metamask/metamask-setup

 {{< figure src="chainlist.jpg" >}}

 {{< figure src="xdai_mm.jpg" >}}

## Obtaining GNO

There are a number of ways to obtain GNO. Do your own research and proceed at your own risk. It is highly recommeded that if you don't already have GNO on the ETH mainnet that you do not purchase it on the mainnet or else you will end up by far more in gas fees than you should be to bridge it across to the Gnosis network. If you have GNO on the mainnet already, you can bridge it to the Gnosis network by going to https://omni.xdaichain.com/bridge

One easy and cost effective way to obtain GNO on the Gnosis network (formerly xDai) is to bridge Dai from the ETH mainnet to the Gnosis chain using [The xDai Bridge](https://bridge.xdaichain.com/). When you bridge Dai to xDai, you will then already have the xDai in your wallet that is needed to pay the gas on transactions of the Gnosis network (which only cost fractions of a cent!).

 {{< figure src="inkedbridge_li.jpg" >}}

Then once you have xDai in the account you wish to use to make your validator deposit, you can use [Honeyswap](https://honeyswap.org/) or [CowSwap](https://cowswap.exchange/#/swap) or to swap xDai for GNO. Remember that for each validator you plan to run on the Gnosis Beacon Chain, you will need exactly 1 GNO. It is highly recommended that you start with 1 validator so that you can become familair with this process before you try to run more.

 {{< figure src="inkedhoneyswap_li.jpg" >}}

 {{< figure src="cowswap.png" >}}

You can import the GNO token to Metamask by visiting https://blockscout.com/xdai/mainnet/token/0x9C58BAcC331c9aa871AFD802DB6379a98e80CEdb/token-transfers
and then clikcing on the fox to import the token to Metamask.

 {{< figure src="import_gno_token.jpg" >}}

 {{< figure src="mm_gno_token.jpg" >}}

## Step 1 : Install Gnosis Beacon Chain (GBC), Gnosis Chain Validator and Gnosis GBC Key Generator and from the DappStore

 {{< figure src="dappstore.jpg" >}}

The beacon chain may take a few hours to sync the first time you install, depending on the size of the Beacon Chain at the time you are installing.

{{< hint type=important >}}
It is highly recommended that before you proceed to the next steps that you ensure that your Gnosis Beacon chain is synced. To do this, simply open the Gnosis beacon chain package and scroll down to inspect the logs. An example of what your logs will look like when the chain is in sync is shown below.

{{< /hint >}}

 {{< figure src="gbc_logs.jpg" >}}

{{< hint type=important >}}
Please note that the Gnosis beacon chain needs a "PoW" chain to point to, just like the ETH2 beacon chain points to the ETH1 mainnet. In this case the proxy for the "PoW" chain is the xDai chain. The Prysm Gnosis Beacon Chain supports two xDai clients at this time, Nethermind and Open Etheruem. In the current Avado package, the default is to use the public xDai rpc https://rpc.xdaichain.com/. Please understand that this is a public rpc run by a third party so this is not a fully decentralized solution at this time but it works fine and limits the resource consumption on your Avado. In order to support full decentralization, Avado will be adding an xDai client (or two) as nodes that you can run on your own. Keep in mind that this will significantly increase the resource load on your Avado with both the CPU and RAM consumption. Using the public rpc, this package will run on an i5 now, but if you run your own xDai node when that becomes available, you will need an i7. **Also when the merge happens in mid 2022, it is unlikley that using an i3/i5 will continue to work with the full package that contains the execution layer and concensus layer in one. Plan your upgrde path accordingy or consider not running it if you are using an i3/i5 and have no plans to upgrade.**

{{< /hint >}}



## Step 2: Open the Gnosis GBC Key Generator to create your keys

{{< hint type=danger >}}
Have a pen and paper ready to write things down. This is important before you proceed. You will be writing down passwords and a 24 word mnemonic phrase which are your responsibility to keep safe throughout your staking journey. If you lose the 24 word mnemonic phrase, no one will be able to help you and you will not be able to withdraw your funds when withdrawls are enabled.

{{< /hint >}}


Open the Key Generator and let Leslie the Launchpad Rhino (yes really) help create validator keys. You will not need to do any command line work to complete this step. Write down the exact password you use in this step and double check it. Then check it again. You will need it later when you start your validator. Enter your your staking key password, the number of keys you wish to generate and your mnemonic language. **Use a strong password that contains 8-10 characters, 1 capital letter, 1 number and 1 special charcater and does not contain too many repeating charcaters or common words.** **Seriously, don't include any common words in your password.** Using a random passowrd generator is a great way to help ensure that your keystore password meets the backend requirements of the validator web ui when you import the keystore as dicussed in Step 4. 
Then click `Generate Keys` 

 {{< figure src="key_gen1.jpg" >}}


{{< hint type=info >}}
Note that if you wish to create more keys later on using the key generator, if you use the same keystore password for all future keys that you create and stake with on the Avado, it will make your life easier if you ever have to re-import all your keys to the validator client. Just take care to manage your passwords and mnenonic phrases carefully when creating future validator keys.

{{< /hint >}}

{{< hint type=important >}}
Note that if you wish to run more than 1 validator, the EASIEST way to do this is to create a new keystore, deposit data and a new mnemonic phrase for each individual validator and then make individual deposits of 1 GNO each. You can create multiple keys in a batch using the exisiting key generator, and that will generate multiple keys with ONE deposit data file. Only do this if you have enough funds to make the deposit for the number of keys you generate or you will have a bad time when you get to Step #5. Whatever you do, keep careful track of whatever keys you make and keep them and the other files together and consider some type of naming scheme so you don't get confused later on. **You have been warned!**

{{< /hint >}}



## Step 3: Download zip file with your generated keys

Click on `Download ZIP file with your generated keys`

 {{< figure src="key_gen2.jpg" >}}

After you have downloaded the file, locate it on your device and extract the tar.gz file to as folder. If you are using a Windows 10 device, you may need to download WinZip or 7-Zip to extract the file if you don't aready have something that can extract a tar file. You can download WinZip here: https://www.winzip.com/win/en/tar-gz-file.html or 7-Zip here: https://www.7-zip.org/

Once you have extracted the zip file, open it and view the contents. You will find two json files titled deposit_data-### and keystore-m_###, and two plain text files titled mnemonic and password.

 {{< figure src="key_gen3.jpg" >}}

{{< hint type=danger >}}
It is very important that you backup the textfiles containing your mnemonic and password for the keystore file. The mnemonic is the ONLY way that you will be able to withdraw your stake from the contract down the road when withdrawals are functional so treat it very carefully! How you store this information is your responsibility and it is strongly recommended that you store it offline in cold storage. Remember, paper backups are your friend. **WRITE DOWN YOUR MNEMONIC PHRASE AND KEYSTORE PASSWORD!** If you lose it, no none will be able to help you and you will lose access to your funds.

{{< /hint >}}

You can view a transcript of the logs from the key generator as Leslie the Rhino helped to generate your keys by clicking on `show a transcript of key generation`

Once you have verified that you have downloaded your keys to your device and you have safely backed up your mnemomic phrase and keystore password, you can safely remove the Gnosis GBC Key Generator package from your Avado. The keys are now in your sole possesion and you can proceed with making the deposit and importing the keys to the validator client in the next steps. 

## Step 4 : Import Your Key to the Validator Wallet on the Avado

It is recommended that you import the keystore file to the validator wallet before you make the deposit to ensure that the validator will accept your keystore file before you lock your funds into the deposot contract. 

Open the Validator package on the Avado.

 {{< figure src="validator1.jpg" >}}

You will then be propmted to create a wallet on the Avado to hold your validator keys. Select Imported Wallet.

Next, you will be prompted to import the keystore file that you created using the key generator. Simply drag the keystore file into the window where indicated and click continue. **Do not drag the whole folder into the window, open the validator_keys folder and drag in only the keystore file.** Enter the keystore password that you used to create the key in Step 3. The click on Submit Keystores. That's it!

 {{< figure src="validator2.jpg" >}}


 {{< figure src="facepalm.jpg" >}}



After you hit continue, if you have done everything correctly, you will be taken to the web UI and you should see this in the upper right hand corner:

 {{< figure src="gbc_status.jpg" >}}



## Step 5 : Visit the Gnosis Beacon Chain deposit website to make your deposit to the staking contract

{{< hint type=danger >}}
Warning! Visiting the official Gnosis Beacon Chain Deposit website is the **ONLY** way you should make the desposit. **Do not attempt to manually send funds to the deposit contract or your will lose your funds.**

{{< /hint >}}

Make sure your Metamask is set on the Gnosis network (or xDai) as we discussed in Step 0.

Vist the [Gnosis Beacon Chain Deposit website](https://deposit.gnosischain.com/) and verify that the URL is https://deposit.gnosischain.com/ and then connect your Metamask wallet. Make sure your wallet is set to the Gnosis/xDai network.

 {{< figure src="deposit_1.jpg" >}}


{{< hint type=tip title=success >}}
**Now, it is time to make the deposit.**

{{< /hint >}}

Open the validator_keys folder that was created in Step 3. Drag the deposit data file (**and only the deposit_data file**) into the window that is showing on the Deposit page. Wait for it to confirm the deposit data. Note that this screenshot was taken from an older version of the deposit site and it is no longer required to swap to mGNO prior to making the deposit. As long as you have at least 1 GNO in your wallet when you import the deposit data file, the wizard will do the swap for you behind the curtain. 

 {{< figure src="inkeddeposit_5_li.jpg" >}}



Then you may click on `Deposit`.

You will be asked to check three boxes to acknowledge that you have a pulse.

 {{< figure src="deposit_6.jpg" >}}

Let the deposit complete.

 {{< figure src="inkeddeposit_7_li.jpg" >}}

That is it for the deposit. Give it time to process, it takes about 2-4 hours for the deposit to be recongized by the GBC. You can check on the status of your desposit by going to https://beacon.gnosischain.com/ and searching for your public key number. **Your public key number can be found by opening the keystore json file with a text editor and looking for "pubkey": "[*yourpublickeynumber*]".** Copy it from there and input into the search field on https://beacon.gnosischain.com/. You should see something like this:

 {{< figure src="inkeddeposit_8_li.jpg" >}}

{{< hint type=important >}}
Please note that it is NOT an ETH1 deposit as shown on beacon.gnosischain.com this is just a consequence of how the software was developed and not every bug has been fixed yet. Same thing when you see your validator in the validator web UI. The total balance is NOT in ETH. It is actually in mGNO.

{{< /hint >}}





At this point, your validator should start making attestations automatically when it becomes active as long as you leave the Gnosis Beacon Chain and Validator packages running 24/7. You can log out of the Prysm Web UI but simply leave your Avado on with the required packages (Gnosis Beacon Chain and Gnosis Vaildator) running. You can monitor the status of your validator at https://beacon.gnosischain.com/ 


{{< hint type=tip title=success >}}
**If you have followed all the steps up to this point, congratulations you will be validating very soon!!!**

{{< /hint >}}

{{< hint type=tip title=success >}}
Once the GBC recognizes your deposit your validator will be assigned a Validator Index number. It is strongly recommended that you use https://beacon.gnosischain.com/ to monitor your validator, rather than relying on the prysm web UI. You can and should search your validator public key number on https://beacon.gnosischain.com/ soon after you have completed the deposit. To get your validator public key number, open the keystore json file with a text editor and you will see it. Copy it to your clipboard and then search it on beaconcha.in and **bookmark this page** as you will likely want to end up coming back to it daily to monitor your validator performance. Owl in a days work!

{{< /hint >}}


## AVADO support channel
Telegram: [AVADO - Gnosis Staking](https://t.me/AvadoXDAI)






