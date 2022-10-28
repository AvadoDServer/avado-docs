---
title:  Claiming your free Gnosis validator(s)
aliases: [/en/tutorials/gnosis-claim-perk]
---

{{< hint type=note >}}
This page is only for people that have participated in the Gnosis validator airdrop.
{{< /hint >}}

Congratulations - you are eligible for free validators, so how do you get your free validator up and running ?

## Step 1 : Set up your software and your NFT

### Software

You need to install these packages from the dappstore

- Gnosis Beacon chain
- Gnosis chain validator
- Gnosis GBC key generator

Please have a look [here](/tutorials/gnosis_beacon_chain) (step 1) for instructions on how to set it up. 

### NFT

You will also need your AVADO NFT in your wallet. If you haven't done so already go and mint your AVADO NFT. 
Instructions on how to mint your AVADO NFT are [here](/tutorials/avado-nft).

## Step 2 : Generate your validator keys

Use the key generator package and generate your keys. Depending on the instructions in the e-mail you received you should create 1, 4 or 6 validator keys.

Make sure to fill out the correct number of validators in the **Amount of keys to generate** field
![screenshot_2022-02-01_at_18.39.45.png](screenshot_2022-02-01_at_18.39.45.png)

After generating your keys, use the button "Download ZIP file" to download the key archive to your computer. Extract the archive on your computer. 


![screenshot_2022-02-01_at_18.40.27.png](screenshot_2022-02-01_at_18.40.27.png)

You will find a couple of files in the archive that you will need later:
- keystore-m_xxxxx_xxxx_0_0_0-xxxxxxxxxx.json : the validator key(s)
- deposit_data-xxxxxxxxxx.json : the deposit file

You might have multiple validator key files here if you generated more than one validator.

{{< hint type=important >}}
Make sure you create a backup of this whole archive file in a secure place (USB stick or other backup method). If you lose these keys, you will lose access to the validator and the funds!
{{< /hint >}}

## Step 3 : Import the keys in your Gnosis validator

Open your Gnosis Chain Validator package and open the UI (Click the "I Agree" button)

![screenshot_2022-02-01_at_18.41.03.png](screenshot_2022-02-01_at_18.41.03.png)

In the dashboard, go to Wallet & accounts --> account list. Press the **import keystores** button and upload all the validator file(s) you have created in step 2

![screenshot_2022-02-01_at_18.46.12.png](screenshot_2022-02-01_at_18.46.12.png)

Type in the password you used to create these keys - and press the "Submit Keystores" button.

When this is done you should see your new validator(s) in the list with a red **n/a** next to it. This means that the validator hasn't been funded yet.

![screenshot_2022-02-01_at_18.46.33.png](screenshot_2022-02-01_at_18.46.33.png)
(Note that on the screenshot above I have 5 active validators already, and I'm adding a 6th)

Congratulations - your AVADO has now been fully configured to start vaildating.

## Step 4: Claim your deposit

go to https://portal.nft.ava.do/ and connect your wallet. You need to connect your wallet to the gnosis chain and select the account that holds your AVADO NFT.

Once you are connected to the wallet - your AVADO will pop up and you'll be able to press the **Claim** button

![screenshot_2022-02-02_at_00.14.47.png](screenshot_2022-02-02_at_00.14.47.png)

Select (or drag and drop) the deposit file (deposit_data-xxxxxxxxxx.json) in the upload box and provide your e-mail address to verify you were subscribed to the campaign.

![screenshot_2022-02-02_at_00.34.44.png](screenshot_2022-02-02_at_00.34.44.png)

Then click the "upload file" button. 
You will receive a request so sign a message from metamask. This is to prove that you are actually the owner of the NFT.



{{< hint type=important >}}
Note that signing using a ledger or other hardware wallet does not seem to work at the moment. We are aware and are working on a solution. ( feb 4th )
{{< /hint >}}

![screenshot_2022-02-04_at_10.49.14.png](screenshot_2022-02-04_at_10.49.14.png)

You will get a confirmation if the upload succeeded.

![screenshot_2022-02-04_at_10.57.05.png](screenshot_2022-02-04_at_10.57.05.png)



You will get a follow up e-mail once the deposit has been done. Please allow 24 hours for us to fund the validator.



## Step 5: Wait until your validator becomes active

Approximately 1.5 hour after the deposit your validator will become active.

Happy validatting !!!

## What happens next ?

The deposited validator and all the profits are yours. the AVADO team nor the Gnosis team will have access to your funds.

Thank you for being a validator on Gnosis! We hope you enjoy the ride !