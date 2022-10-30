---
title: ETH Staking Key Generator and Deposit
---

{{< toc >}}

TODO:
* intro
* Alternative : Waygu

 {{< figure src="../eth2keygen/rhino.243747b9.png" width="200" >}}

## The Avado ETH Key generator

{{< hint type=danger >}}
There is a bug in the ETH2.0 Key Generator that results in a **wrong network** error when uploading the keystore to the official launchpad.
{{< /hint >}}

{{< hint type=info >}}
Use the **WAGYU Key Generator** until the ETH2.0 Key Generator receives an update.
Create your keys here: https://www.wagyu.gg
More information about WAGYU: https://medium.com/@shawynot/staking-ethereum-without-the-command-line-83c18dd4ffe8
{{< /hint >}}

{{< hint type=danger >}}
Have a pen and paper ready to write things down. This is important before you proceed. You are writing down passwords and a 24 word mnemonic phrase which are your responsibility to keep safe throughout your staking journey.  
☠️☣️😱 **If you lose the 24 word mnemonic phrase, no one will be able to help you.** 😱☣️☠️
{{< /hint >}}

### Video demo
{{< youtube pFnQSopANr0 >}}

### Installation

### Generate keys

Open the Key Generator and let Leslie the Launchpad Rhino help create validator keys. Write down the exact password you use in this step and double check it. Then check it again. You will need it later when you start your validator. Enter your your staking key password, the number of keys you wish to generate and your mnemonic language. Use a strong password that contains at least 1 capital letter, 1 number and 1 special charcater and does not contain too many repeating charcaters or common words. Then click `Generate Keys` 

{{< hint type=danger >}}
There is a known issue with the key generator password criteria. **Please do not use `$` in your password** or it will not work.
{{< /hint >}}


{{< hint type=info >}}
Note that if you wish to create more keys later on using the key generator, you MUST use the same keystore password for all future keys that you create and stake with on the Avado.
{{< /hint >}}


### Download zip file with your generated keys

1. Click on `Download ZIP file with your generated keys`
{{< figure src="../eth2keygen/download_keys.png" >}}

After you have downloaded the file, locate it on your device and extract the tar.gz file to as folder. If you are using a Windows 10 device, you may need to download WinZip or 7-Zip to extract the file if you don't aready have something that can extract a tar file. You can download WinZip here: https://www.winzip.com/win/en/tar-gz-file.html or 7-Zip here: https://www.7-zip.org/

Once you have extracted the zip file, open it and view the contents. You will find two json files titled deposit_data-### and keystore-m_###, and two plain text files titled mnemonic and password.

{{< hint type=danger >}}
It is very important that you backup the textfiles containing your mnemonic and password for the keystore file. The mnemonic is the ONLY way that you will be able to withdraw your stake from the contract down the raod when withdrawals are functional in Phase 2 so treat it very carefully! How you store this information is your responsibility and it is strongly recommended that you store it offline in cold storage. Remember, paper backups are your friend. **WRITE DOWN YOUR MNEMONIC PHRASE AND KEYSTORE PASSWORD!** If you lose it, no none will be able to help you and you will lose access to your funds.
{{< /hint >}}

You can view a transcript of the logs from the key generator as Leslie the Rhino helped to generate your keys by clicking on `show a transcript of key generation`

Once you have verified that you have downloaded your keys to your device and you have safely backed up your mnemomic phrase and keystore password, you can safely remove the ETH2 Key Generator package from your Avado. The keys are now in your sole possesion and you can proceed with making the deposit and importing the keys to the validator client in the next steps. 


## Visit the Ethereum Launchpad to make your deposit to the mainnet contract

{{< hint type=danger >}}
Warning! You are about to make the desposit on the official Ethereum Launchpad for the mainnet. This is a serious commitment and cannot be reversed once you complete the desposit. Visiting the official Ethereum Lanuchpad is the **ONLY** way you can make the desposit. **Do not attempt to manually send funds to the deposit contract or your will lose your funds.**
{{< /hint >}}

Click on the link in the second bullet item of the key generator where it says Done! `Ethereum Launchpad`.

https://launchpad.ethereum.org/

Since you have already created your keys (without using a command line interface) on the Avado, you will be skipping the first steps of the launchpad. However, you should read through each of the steps because they are loaded with good information on the level of commitment that is required to be a validator on the Ethereum 2.0 network. Start by clicking on **Get Started**. Click continue to read through and accept each of the 10 important "commandments".

 {{< figure src="../eth2keygen/agree.png" >}}

Choose your Execution Client. For most of you, this will be Geth or Nethermind. You can disregard the instructions to install the Execution client because if you followed Step 0 of this guide, the Avado has already done this for you. Click **Continue**

Then select your Consensus Client and click **Continue**

On the next page, you do not need to fill out any number of validators, you can leave this as 0. You also do not need to select an operating system. We are skipping this step so continue to scroll all the way to the bottom of the page and confirm that you are keeping your keys safe and you **HAVE WRITTEN DOWN YOUR MNEMONIC PHRASE.** Then click **Continue**

 {{< figure src="../eth2keygen/gen_keys_zero.png" >}}

 {{< figure src="../eth2keygen/safe.png" >}}


{{< hint type=tip title=success >}}
**Now this is where we get serious. It is time to make the deposit.**
{{< /hint >}}

Open the validator_keys folder that was created in Step 3. Drag the deposit data file (**and only the deposit_data file**) into the window that is showing in the Lanchpad page.

 {{< figure src="../eth2keygen/deposit.png" >}}

 {{< figure src="../eth2keygen/deposit_data.png" >}}

Once you have dragged the deposit_data file into the window, you will see a blue check mark which indicates a valid deposit data file and you may click **Continue**.

Now you will connect your wallet. It is recommended to use Metamask, but you may choose whatever option is most comfortable for you. Ensure that your wallet is connected to the Ethereum Mainnet and that the Launchpad is able to connect to the wallet account with which you wish to make the deposit. In this example, I am showing you an account which does not contain any Ether. Make sure you have at least 32 ETH plus enough Ether for the gas fees of making the transaction.

 {{< figure src="../eth2keygen/wallet_connect.png" >}}

 {{< figure src="../eth2keygen/link_wallet.png" >}}

Take a deep breath and then click **Continue**. Review all of the terms on the next page and check all of the boxes to continue with the desposit. You will be asked to confirm the transaction in your wallet account.

 {{< figure src="../eth2keygen/agree.png" >}}

That is it for the deposit. Give it time to process. You can check on the status of your desposit by going to <https://beaconcha.in> and searching for your public key number. Your public key number can be found by opening the keystore json file. Copy it from there and input into the search field on Beaconcha.in. When your deposit goes through, when you look you will see something like this:

{{< figure src="../eth2keygen/deposit_search.png" >}}

