---
title: Rocket Pool
description: Setting up a ETH beacon chain validator with Rocket Pool on Avado
tags: [eth, ethereum, rocketpool, tutorial]
aliases: ["/en/tutorials/rocketpool"]
---

# AVADO Rocket Pool ETH staking

![rocketpool.png](rocketpool.png)

This page will describe how to stake ETH with Rocket Pool on your Avado.

Although this Avado packages makes it very easy to run a Rocket Pool node on your Avado, make sure you are up for the task. Make sure you read <https://docs.rocketpool.net/guides/node/responsibilities.html> to know your risks and resposabilities.

## Rocket Pool
Rocket Pool is the first truly decentralised Ethereum staking pool.
A decentralised network of node operators earn rewards for rETH holders.

More information:
https://rocketpool.net/

Tutorial about Rocket Pool 
https://medium.com/rocket-pool/rocket-pool-staking-protocol-part-1-8be4859e5fbd

## Prerequisites

* **Ethereum execution client (Geth)**: Make sure the Ethereum exectution client package (Geth) is <b>installed</b> and <b>synced</b>
* **Ethereum beacon chain client (Prysm)**: Make sure the Ethereum beacon chain package (Prysm) is <b>installed</b> and <b>synced</b>
* **Ether**: Make sure you have enough Ether
    * 16 ETH for your half of the validator deposit
    * 1.6 ETH worth of RPL (158 RPL), you can get RPL via https://app.uniswap.org/
    * some extra ETH to pay for gas, lets say 16,4 ETH in your wallet

## Step 0 : Install Geth as your ETH1 endpoint and let it sync
Follow this [guide]({{< relref "geth" >}}) to setup Geth if you haven't already done so.

Continue to Step 1 after it has completely synchronized.

## Step 1 : Install Ethereum beacon chain client (Teku/Prysm)
In the Dapp store look for "Teku" (recommended) or "ETH2.0 Beacon chain monitor" and click on install (if you did not install it yet).

Continue to Step 2 after it has completely synchronized.

## Step 2: Install Rocket Pool
Watch this video:
Youtube tutorial on how to create your minipool
https://www.youtube.com/watch?v=9YKdzP5TZDo

Install the "Rocketpool node"-Dapp:
http://my.ava.do/#/installer

Very simple: follow the steps as mentioned on this page:
http://my.ava.do/#/Packages/rocketpool.avado.dnp.dappnode.eth
A preview of the screens can be found in the video link above.

### Step 3.1: Teku

If you selected "Teku" as beacon chain client and validator, open the [Rocket Pool package page](http://my.ava.do/#/Packages/rocketpool.avado.dnp.dappnode.eth/detail) and replace `prsym` with `teku` (all lower case)

![rocketpoolvariables.png](rocketpoolvariables.png)

## Step 3: 5 more steps ;-)
The following steps are:
1. Init wallet
2. Fund Node
3. Register node
4. Withdrawal address
5. Add minipool

### STEP 3.1: INIT WALLET
First screen contains the following information:

To complete the onboarding wizard you will need these things:
1. A fully synced Ethereum node. Install the Ethereum Node (Geth) from the DappStore
1. A fully synced Beacon chain. Install the Prysm ETH2.0 Beacon Chain from the DappStore
1. An Ethereum wallet with 16 ETH + some gas to deposit it in your minipool (0.4 ETH should be enough)
1. An Ethereum wallet with the neccesary amount of RPL to stake.
1. An Ethereum wallet to receive your staking rewards into. This can be an empty wallet, or a cold storage wallet - as you prefer.
Check the Avado Rocket Pool Wiki page to learn what it takes to run a Rocket Pool node - and info on how to obtain RPL.

Please wait until your ETH1 node is synced

Do not forget to backup your wallet

### STEP 3.2: FUND NODE

Fund wallet
Now you need to fund your Rocketpool hot wallet.

Send 16.4 ETH to 0x45bea5da5d62fb0c9e761f330e24************  (16 ETH + 0.4 ETH gas money)

(0.4 is a safe margin to create everything - including the expensive minipool contract deploy. The remaining gas can be withdrawn from this wallet later)
Send a minimum of 158 RPL to 0x45bea5da5d62fb0c9e761f330e24************ 
(maximum allowed stake is 2355 RPL - the more you stake, the more you will earn.
(All RPL sent to this wallet will be used as your stake later - so please send exactly the desired stake amount)
Current Wallet balances:

ETH: 0 ETH
RPL: 0 RPL

FYI: as of 2022 03 25 this amounts to :
16 Ethereum (ETH @ 3180 USD) is +/- 50880 US Dollar
Source: https://coinmarketcap.com/nl/currencies/ethereum/
158 Rocket Pool (RPL @ 31 USD) = 5528 US Dollar
Source: https://coinmarketcap.com/nl/currencies/rocket-pool/

Hit "Refresh balances" to update your balance of crypto sent to your address.

You will go to the next step once you have funded your wallet sufficiently.

### STEP 3.3: REGISTER NODE
If you do mupltiple transactions to fund your ETH and/or RPL, please reload screen with menu saying "Welcome Setup Status"

Add first the sufficient amoutns of ETH and RPL. See Status tab.
Be sure to have enough ETH!
Not adding enough ETH will 



### STEP 3.4: WITHDRAWEL ADDRESS
You need to set a withdrawal address for your node.
Very simple step = click the button "Register Node"
Click Yes to confirm

=> Warning massage:
Warning
This should be an address you control (ex a MetaMask address). All of your RPL checkpoint rewards, your staked RPL, and your Beacon Chain ETH will be sent there when you claim your checkpoint rewards or exit your validator.

Please read the info on the wiki carefully before setting your withdrawal address!

Copy paste your withdrawel address

=> message
Double check that this withdrawal address (0x497199231d4b60Cd9869E2995E7239D1c99*****) is correct and this is an address you have full control over. Are you sure you want to continue?
Yes I own and control this address
No

=> REMARKs
The withdrawal address you set is where everything is sent to when you collect your rewards, but also if you later want to exit your minipool and get the 16 ETH back.
The remark that they make is that IF you enter a wrong address there - you cannot change it afterwards, so if make a mistake there, you could lose your funds.
What we do to mitigate this is to validate the input to see if it's a correct ETH address - if you type in anything other than a valid ETH address, it will not continue
What would be better is (and that is what they suggest) is that you link it to your metamask - and have you sign somehting that proves that you have accees to that wallet
I agree that that's better - but if in any other dapp I type in a wrong ETH address - I will also lose my funds...


### STEP 3.5: ADD MINIPOOL

1. approve RPL
Click button
Yes (to confirm)


2. Stake RPL
Click "Stake *** RPL"-button
Yes (to confirm)

3. Deposit 16 ETH and create MiniPool
Click "Deposit 16 ETH and create MiniPool"-button
Yes (to confirm)

Your MiniPool has been successfully created! Click the button below to go to the status page.

Transaction details on Etherscan

Warning: 
If your funds go down the 16 ETH, the message is like a confirmation but there is a red error massage.

Recommended
Download the backup file that is proposed.


There are 6 Txn fees to be payed in ETH!
- Register Node (0.008566689547)
- Set Withdrawal Address (0.002167425665)
- Approve (0.001726074857)
- Stake RPL (0.00893108866)
- Deposit (0.110217334572)
- Stake (0.00871277676)


=> Message
The commission you will receive from other deposits is +/- 14.55%.

Check and double check...
https://beaconcha.in/validators/eth1deposits
Verify your deposit here by entering your address


Check when if other 16 ETH have been added...
https://eth2-validator-queue.web.app/ "Eth2 Validator Queue Stats"
It takes around 12 hours ....


When the other 16 ETH have been added...
Check when your validator will be added...
https://beaconcha.in/validators (and add your address)
OR
There is also a link in the interface (last line on this page: http://my.ava.do/#/Packages/rocketpool.avado.dnp.dappnode.eth)
"More validator info on the Ethereum 2.0 Beacon Chain Explorer"
https://beaconcha.in/validator/(your address)#deposits

> It is possible to add multiple minipools: click "Add another minipool" to add an extra minipol
{.is-info}

## Step 5: Import the validator key in your validator

Once you created your minipool, you need to import the keys into the validator package. If you don't have one yet. We recommend to run Teku, but Prysm is also a good option.  
The following instructions are for Teku, but are nearly identical for Prysm.

1. Download RocketPool backup (in the RocketPool Dapp)
  ![backup.png](backup.png)
2. Check the contents of the backup file:
  ![backup-contents.png](backup-contents.png)
  (3 validators in this example)
1. Switch to the Teku settings page and click the "Add validator" field to expand it:
  ![add_validator.png](../teku/add_validator.png)
  ![add_validator_exp.png](../teku/add_validator_exp.png)
1. Next, click "Choose keystore file..." and browse to the keystore file (json) you downloaded from the [Key generator package](/en/tutorials/prysmvalidator#step-3-download-zip-file-with-your-generated-keys)
1. Enter the keystore password
1. Finally click "Add validator" to add the validator to Teku
1. Repeat if you have multiple keys

If you did everything right, you will see a table with your validators at the top of the page. Click on the "BeaconChain" icons to get more details on the status and performance of your validator on the beaconcha.in website.

## 2022-04-06: Update 0.0.62

Since version 0.0.62 the Avado RocketPool package no longer includes its own validator. So you need to move your validators to a separate validator package when you update. To avoid any risk of slashing, we decided to make this a (one time) manual process.

We recommend moving your validator to *Teku* to support a client diversity - but we provide instructions to move to Prysm too if you want to keep validating through Prysm. Choose which validator you want to go for and follow either one of of the following instructions.


### Moving your validators to Teku

Teku is a validator for ETH2 - and you can run your minipool through Teku.

1. Update the RocketPool package on Avado to version 0.0.62
1. **Double check the version number!** It must be 0.0.62!
  If you run an older version, you risk running your validator twice which is a slashable offence.
1. Download RocketPool backup (in the RocketPool Dapp)
  ![backup.png](backup.png)
2.  Check the contents of the backup file:
  ![backup-contents.png](backup-contents.png)
  (3 validators in this example)
3. Wait 2 epochs (~30 minutes).
4. Install the Teku package (http://my.ava.do/#/installer - "Teku ETH2 beacon chain & validator"  
5. Open the Teku package
6. Click "Add Validator"



### Moving your validators to Prysm

If you prefer moving your validator to Prysm - follow these steps instead:

1. Update the RocketPool package on Avado to version 0.0.62
1. **Double check the version number!** It must be 0.0.62!
  If you run an older version, you risk running your validator twice which is a slashable offence.
1. Download RocketPool backup (in the RocketPool Dapp)
  ![backup.png](backup.png)
2.  Check the contents of the backup file:
  ![backup-contents.png](backup-contents.png)
  (3 validators in this example)
3. Wait 2 epochs (~30 minutes).
4. Install the Prysm validator package (http://my.ava.do/#/installer - "Prysm Validator" ) - if you are already staking ETH2 you will already have this and you can skip this step.
1. Open the Prysm validator Dapp. If you don't run other validators yet, you will see this screen. Select "Import Keystores" and click the "Select wallet" button (If you already have validators running, click "Wallet & Accounts > Account list > Import Keystores" instead)
  ![onboarding.png](onboarding.png)
1. In your file explorer, locate the content of your backup file, and navigate into the `teku/keys` (yes Teku) folder. Next, drag and drop the `json` key files into the "Browse Files" field.
1. Select "Keystores have different passwords"
1. For each keyfile, enter the password (these are stored in the `Teku/passwords` folder)
1. Click "No" on the slashing protection data
1. Click continue
  ![keys.png](keys.png)

Done ! Your validator will pick up the validation process and you will be validating.

## Redstone release (2022-08)

Rocket Pool deployed a major upgrade called “Redstone” with major changes to how Rocket Pool works. For Avado users this means:
* All users join a smoothing pool which collectively pools the priority fees of transactions post merge. This is a way to effectively reduce the randomness associated with block proposals on the Beacon Chain.
**This requires clicking the “Update” button in the new Avado package**
Note that this requires that the “fee recipient address” of your Rocket Pool validators must be set to the smoothing pool’s address. The Avado package configures this automatically for you. **If you manually change this address, you will get punished.**
* The rewards system has changed. The rewards are no longer claimed automatically. You can now claim at your own discretion when the gas fees are low

### Rocket Pool staking merge ready checklist

* Make your Execution Client (Geth) and Beacon Chain Client (Teku or Prysm) are up to date
* Update the Rocket Pool Avado package to version > 0.0.78
* Click the **update** button
* Check the node status: The Merge update should be deployed and the smoothing pool should be joined.
  ![screenshot_2022-08-26_at_15.25.56.png](screenshot_2022-08-26_at_15.25.56.png){.align-center}


## More information
* Node operator commision details:
https://docs.rocketpool.net/overview/faq/#how-does-the-protocol-protect-the-value-of-reth
* Token value (rETH)
https://coinmarketcap.com/currencies/rocket-pool-eth/
* Token value (RPL)
https://coinmarketcap.com/nl/currencies/rocket-pool/

## Major benefits of running a Rocket Pool node
Here are the major benefits of running a Rocket Pool node:
- You only need 16 ETH instead of 32 ETH to run a validator yourself
- You earn half of the validator's total ETH rewards, plus an extra commission (varies from an additional 5 to 20 percentage points)
- You earn interest on the RPL you stake as supplemental insurance
- You can participate in the DAO and get to vote on changes to Rocket Pool's protocol or settings"

## AVADO support channel
Need community help?
Telegram: [AVADO - Rocketpool staking](https://t.me/+82CX5K76Fd4xN2M8)
