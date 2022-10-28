---
title: Setting up an ETH2.0 validator
description: Setting up an ETH2.0 validator
tags: [eth, ethereum, prysm, tutorial]
aliases: [/en/tutorials/prysmvalidator]
---

# Set up a Validator for the Ethereum 2.0 Mainnet

Getting started from scratch (fresh install)



{{< hint type=tip title=success >}}
 This guide describes the steps of generating keys using the Key Generator package and then accessing the Ethereum 2.0 Validator Launchpad to complete the deposit to the Ethereum Mainnet contract 0x00000000219ab540356cbb839cbe05303d7705fa. 

{{< /hint >}}

{{< hint type=important >}}
Proceed at your own risk. You are solely responsible for your stake.

{{< /hint >}}

{{< hint type=danger >}}
Visiting the official Ethereum 2.0 Lanuchpad is the ONLY way you can make the desposit. Do not attempt to manually send funds to the deposit contract or your will lose your funds.

{{< /hint >}}

## Prepare for "The Merge"

{{< hint type=info >}}
Ethereum will transition from Proof of Work to Proof of Stake soon, around September 15. This section summarizes how you should prepare your Avado box

{{< /hint >}}

What should I do to prepare for the Merge?
1. Check your Geth package:
    * Is your Geth package up to date? (Avado version `>10.0.45` based on Geth version `v1.10.23`)
    * Are you running a **full** node? (Prysm needs a full client after the merge, light clients will no longer work)
    * Is Geth fully synced? If you sync from scratch, sync now, because syncing takes a while. If your Geth installation has been running for a long time and has grown large in size, consider removing Geth and installing a new, clean copy from the Dappstore to create a fresh database and minimize disk consumption. 
    
	* The steps listed here:
    https://wiki.ava.do/en/tutorials/geth#pruning-your-geth-node
for setting a fallback provider like Infura will still work until the merge so you can keep validating while you perform Geth maintenance. After the merge happens, Geth maintenance will require some downtime for your validator. 

2. Check your Prysm packages:
   * Beacon chain: Avado version `>10.0.46` based on Prysm version `v3.0.0`)
   * Validator: Avado version `>10.0.44` based on Prysm version `v3.0.0`)
3. Configure the “Fee recipient address”:
   * Open the *Beacon Chain* package
   * Click the red banner to navigate to the settings page
   * Enter the fee recipient address (this is the address where you will receive the priority fees of transactions in the blocks you propose)
   * Click **Apply changes**
   (This will restart Prysm, so Prysm might get out of sync for a minute)
![prysm_fee_recipient.png](../prysm/prysm_fee_recipient.png){.align-center}

## Step 0 : Install Geth as your ETH1 endpoint and let it sync
Follow this [guide](/tutorials/geth) to setup Geth if you haven't already done so.

Continue to Step 1 after it has completely synchronized.

## Step 1 : Install Prysm ETH2.0 validator and ETH2.0 Key Generator and from the DappStore

For those of you who are visual learners and like to watch videos showing you step by step, you can watch this video and learn how to create your keys and make the staking deposit by watching this video below. Additional details are provided in the text below. 

https://youtu.be/pFnQSopANr0

Once you start the installation of the validator, the beacon chain will also install and start to sync automatically. The beacon chain may take a few hours to sync the first time you install, depending on the size of the Beacon Chain at the time you are installing.

## Step 2: Open the ETH2.0 Key Generator to create your keys and deposit your stake of 32 ETH

{{< hint type=danger >}}
There is a bug in the ETH2.0 Key Generator that results in a **wrong network** error when uploading the keystore to the official launchpad.

{{< /hint >}}

{{< hint type=info >}}
Use the **WAGYU Key Generator** until the ETH2.0 Key Generator receives an update.
Create your keys here: https://www.wagyu.gg
More information about WAGYU: https://medium.com/@shawynot/staking-ethereum-without-the-command-line-83c18dd4ffe8

{{< /hint >}}

{{< hint type=danger >}}
RETURN TO THIS GUIDE AFTER CREATING YOUR KEYS

{{< /hint >}}

{{< hint type=danger >}}
Have a pen and paper ready to write things down. This is important before you proceed. You are writing down passwords and a 24 word mnemonic phrase which are your responsibility to keep safe throughout your staking journey. If you lose the 24 word mnemonic phrase, no one will be able to help you.

{{< /hint >}}

![rhino.243747b9.png](../keygen/rhino.243747b9.png)

Open the Key Generator and let Leslie the Launchpad Rhino help create validator keys. Write down the exact password you use in this step and double check it. Then check it again. You will need it later when you start your validator. Enter your your staking key password, the number of keys you wish to generate and your mnemonic language. Use a strong password that contains at least 1 capital letter, 1 number and 1 special charcater and does not contain too many repeating charcaters or common words. Then click `Generate Keys` 

{{< hint type=danger >}}
There is a known issue with the key generator password criteria. **Please do not use $ in your password** or it will not work.

{{< /hint >}}


{{< hint type=info >}}
Note that if you wish to create more keys later on using the key generator, you MUST use the same keystore password for all future keys that you create and stake with on the Avado.

{{< /hint >}}


## Step 3: Download zip file with your generated keys

Click on `Download ZIP file with your generated keys`

![download_keys.png](../keygen/download_keys.png)

After you have downloaded the file, locate it on your device and extract the tar.gz file to as folder. If you are using a Windows 10 device, you may need to download WinZip or 7-Zip to extract the file if you don't aready have something that can extract a tar file. You can download WinZip here: https://www.winzip.com/win/en/tar-gz-file.html or 7-Zip here: https://www.7-zip.org/

Once you have extracted the zip file, open it and view the contents. You will find two json files titled deposit_data-### and keystore-m_###, and two plain text files titled mnemonic and password.

{{< hint type=danger >}}
It is very important that you backup the textfiles containing your mnemonic and password for the keystore file. The mnemonic is the ONLY way that you will be able to withdraw your stake from the contract down the raod when withdrawals are functional in Phase 2 so treat it very carefully! How you store this information is your responsibility and it is strongly recommended that you store it offline in cold storage. Remember, paper backups are your friend. **WRITE DOWN YOUR MNEMONIC PHRASE AND KEYSTORE PASSWORD!** If you lose it, no none will be able to help you and you will lose access to your funds.

{{< /hint >}}

You can view a transcript of the logs from the key generator as Leslie the Rhino helped to generate your keys by clicking on `show a transcript of key generation`

Once you have verified that you have downloaded your keys to your device and you have safely backed up your mnemomic phrase and keystore password, you can safely remove the ETH2 Key Generator package from your Avado. The keys are now in your sole possesion and you can proceed with making the deposit and importing the keys to the validator client in the next steps. 


## Step 4 : Visit the Ethereum Launchpad to make your deposit to the mainnet contract

{{< hint type=danger >}}
Warning! You are about to make the desposit on the official Ethereum 2.0 Launchpad for the mainnet. This is a serious commitment and cannot be reversed once you complete the desposit. Visiting the official Ethereum 2.0 Lanuchpad is the **ONLY** way you can make the desposit. **Do not attempt to manually send funds to the deposit contract or your will lose your funds.**

{{< /hint >}}

Click on the link in the second bullet item of the key generator where it says Done! `Ethereum Launchpad`.

https://launchpad.ethereum.org/

Since you have already created your keys (without using a command line interface) on the Avado, you will be skipping the first steps of the launchpad. However, you should read through each of the steps because they are loaded with good information on the level of commitment that is required to be a validator on the Ethereum 2.0 network. Start by clicking on `Get Started`. Click continue to read through and accept each of the 10 important "commandments".

![agree.png](../keygen/agree.png)

Choose your Eth 1 client. For most of you, this will be Geth or Nethermind. You can disregard the instructions to install the ETH 1 client because if you followed Step 0 of this guide, the Avado has already done this for you. Click `Continue`

Then select Prysm as your ETH 2 client. Click `Continue`

On the next page, you do not need to fill out any number of validators, you can leave this as 0. You also do not need to select an operating system. We are skipping this step so continue to scroll all the way to the bottom of the page and confirm that you are keeping your keys safe and you **HAVE WRITTEN DOWN YOUR MNEMONIC PHRASE.** Then click `Continue`

![gen_keys_zero.png](../keygen/gen_keys_zero.png)

![safe.png](../keygen/safe.png)


{{< hint type=tip title=success >}}
**Now this is where we get serious. It is time to make the deposit.**

{{< /hint >}}

{.is-warning}

Open the validator_keys folder that was created in Step 3. Drag the deposit data file (**and only the deposit_data file**) into the window that is showing in the Lanchpad page.

![deposit.png](../keygen/deposit.png)

![deposit_data.png](../keygen/deposit_data.png)

Once you have dragged the deposit_data file into the window, you will see a blue check mark which indicates a valid deposit data file and you may Click `Continue`.

Now you will connect your wallet. It is recommended to use Metamask, but you may choose whatever option is most comfortable for you. Ensure that your wallet is connected to the Ethereum Mainnet and that the Launchpad is able to connect to the wallet account with which you wish to make the deposit. In this example, I am showing you an account which does not contain any Ether. Make sure you have at least 32 ETH plus enough Ether for the gas fees of making the transaction.

![wallet_connect.png](../keygen/wallet_connect.png)

![link_wallet.png](../keygen/link_wallet.png)

Take a deep breath and then click `Continue`. Review all of the terms on the next page and check all of the boxes to continue with the desposit. You will be asked to confirm the transaction in your wallet account.

![agree.png](../keygen/agree.png)

That is it for the deposit. Give it time to process. You can check on the status of your desposit by going to beaconcha.in and searching for your public key number. Your public key number can be found by opening the keystore json file. Copy it from there and input into the search field on beaconcha.in. When your deposit goes through, when you look you will see something like this:

![deposit_search.png](../keygen/deposit_search.png)


## Step 5 : Import Your Key to the Validator Wallet on the Avado

It is suggested that you follow the video tutorial to complete this step of importing your key and configuring the validator interface. If you are following this guide, you have just created your keystore file using the Avado key generator and made a deposit by visiting the Ethereum 2.0 Lanchpad. You are now ready to import them to the Avado by following the steps in the video below. The steps 5.1 through 5.5 provide additional detail and a troubleshooting section is provided at the bottom of the page.

### open**5.0** https://www.youtube.com/watch?v=-FEttfq0sq8

**5.1** Open the Validator package on the Avado.
![open_val.png](../keygen/open_val.png)

**5.2.1** After agreeing and opening the Prysm web dashboard, you will then be propmted to create a wallet on the Avado to hold your validator keys. Select Imported Wallet.

{{< hint type=danger >}}
It is strongly recommended that you have a pen and paper ready to write down the passwords that you create in the next steps so that you can recreate them in the future when needed.

{{< /hint >}}


![imported_wallet.png](../keygen/imported_wallet.png)

**5.2.2** Next, you will be prompted to import the keystore file that you created using the key generator. Simply drag the keystore file into the window where indicated and click continue. **Do not drag the whole folder into the window, open the extracted folder and drag in only the keystore file or files if doing more than 1.
**
![import_keystore.png](../keygen/import_keystore.png)

**5.2.3** Then you will be prompted to enter your keystore password. This is the same password that you used when you created the key with the key generator.

![keystore_unlock.png](../keygen/keystore_unlock.png)

{{< hint type=info >}}
Note that there used to be an extra step here: "create a Prysm Web UI Password". Since Prysm v2.0.3 this password was replaced with an automatic JSON Web Token. 

{{< /hint >}}

**5.4** Lastly, you will be prompted to enter a wallet password. This password is used by the Avado to encrypt your validator wallet and should be a secure password but does not carry the same stringent requirements as the password in the previous step.

![wallet_password.png](../keygen/wallet_password.png)

**5.5** After you hit continue, if you have done everything correctly, you will be taken to the web UI and you should see this in the upper right hand corner:

![beacon_status.png](../keygen/beacon_status.png)

At this point, your validator should start making attestations automatically when it becomes active as long as you leave the Beacon Chain and Validator packages running 24/7. You can log out of the Prysm Web UI but simply leave your Avado on with the required packages (ETH1, Beacon Chain and Vaildator) running. You can monitor the status of your validator at beaconcha.in or beaconscan.com

{{< hint type=tip title=success >}}
**If you have followed all the steps up to this point, congratulations you will be validating very soon!!!**

{{< /hint >}}

{{< hint type=tip title=success >}}
It is strongly recommended that you use beaconcha.in to monitor your validator, rather than relying on the prysm web UI. You can and should search your validator public key number on beaconcha.in soon after you have completed the deposit. To get your validator public key number, open the keystore json file with a text editor and you will see it. Copy it to your clipboard and then search it on beaconcha.in and bookmark this page as you will likely want to end up coming back to it daily to monitor your validator performance.

{{< /hint >}}





## 6.0 Troubleshooting

There is a known issue with the prysm web UI and the Brave browser. If you are using Brave, please make sure you turn the shields off for this page or it will not read correctly.

![switch2.jpg](../keygen/switch2.jpg)

Here is the list of common errors you may see in red at the bottom of the screen after creating the validator through the Web UI:

**500 is wrong password on your keystore file.** The keystore password you entered when importing your key to the Avado through the Prysm Web UI does not match the password you used when you created your keystore file. You can double check the keystore password by looking in the folder generated by the key generator and there is a text file called password that you can check on.

**400 is password not meeting requirements for the web UI.** This is the second prompt for a password that you come to when setting up the Prysm Web UI. This is the most common error BY FAR and it is due to the stringent password requirments of the Prysm Web UI. If you are getting this error, start over with the validator setup and pay careful attention to the password you choose for the Prysm Web UI. A recommended password format is 8-10 characters. Here is a sample of a valid password, you will use a different one. Fs<6@tx8

**0 beacon chain not ready.** Check that the Beacon Chain is installed and running and is synced. If it is not, you should either wait until it is synced or you should reinstall the Beacon Chain package from scratch by clicking on remove volume and then let the Beacon Chain reinstall with the default settings.
![beacon_sync.png](../keygen/beacon_sync.png)

![remove_vol.png](../keygen/remove_vol.png)

If after importing your validator key to the Prysm Web UI, you see this error in the upper right hand corner but the Beacon Chain and Validator logs look okay, please try using another browser to access the Prysm Web UI. There have been several instances of people having problems accessing the Prysm Web UI with the Brave browser and at this time, Avado is not able to fix this as it is related to the Prysm Web UI backend which is not under the control of Avado.

![beacon_unknown.jpg](../keygen/beacon_unknown.jpg)

Sometimes it may be necessary to restart the Beacon Chain and Validator packages if you start missing attestations and can't figure out why. Simply press restart for the Beacon Chain and Validator and let them reload, then monitor your Validator status on beaconcha.in or beaconscan.com to see if your validator resumes it's duties.
![restart_client.png](../keygen/restart_client.png)

If you are unable to resolve any other errors you are having, please reach out on the telegram channel and we will add reseolved issues to this guide as the solutions become known.


## AVADO support channel
Telegram: [AVADO - Ethereum Club](https://t.me/joinchat/IdBKSAiIvw-q1-1p)






