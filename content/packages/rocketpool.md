---
title: Rocket Pool
description: Setting up a ETH beacon chain validator with Rocket Pool on Avado
tags: [eth, ethereum, rocketpool, tutorial]
aliases: ["/en/tutorials/rocketpool"]
---

{{< toc >}}

{{< figure src="rocketpool.png" >}}

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
* **Ethereum Consensus client (Prysm or Teku)**: Make sure the Ethereum Consensus client package is <b>installed</b> and <b>synced</b>
* **MEV-Boost**: Make sure the MEV-Boost package is <b>installed</b> and <b>enabled</b> in the settings of your Consensus client
* **Ether**: Make sure you have enough Ether
    * 16 ETH for your half of the validator deposit
    * 1.6 ETH worth of RPL (158 RPL), you can get RPL via https://app.uniswap.org/
    * some extra ETH to pay for gas, lets say 16,4 ETH in your wallet


## Demo video 

Youtube tutorial on how to create your minipool. Note that video is slightly outdated. The process has some extra steps now, but the video still gives a good overview of the process in general.

{{< youtube 9YKdzP5TZDo >}}

## Step 0 : Install packages

1. **Ethereum Execution client**: Follow this [guide]({{< relref "geth" >}}) to setup Geth if you haven't already done so.
2. **Ethereum Consensu client**: Both [Teku]({{< relref "teku" >}}) (recommended) and [Prysm]({{ relref "prsym" }}) are supported.
3. **MEV-Boost**: Follow this [guide]({{< relref "mev-boost" >}}) if you haven't done so yet.
4. **Rocket Pool**: Select the **Rocketpoool node** package in the [DappStore](http://my.ava.do/#/installer) and click **install**


## Step 1: Configure Rocket Pool

Check the settings on the [RocketPool manage page](http://my.ava.do/#/packages/rocketpool.avado.dnp.dappnode.eth/detail):
* **NETWORK**: `mainnet`
* **EXECUTIONCLIENT**: `geth`
* **CONSENSUSCLIENT**: 
    * For Teku use `teku`
    * For Prsym use `prysm`

If you changed any of the settings, click **Update environment variables**

{{< figure src="environment_variables.png" >}}

## Step 2: Initialize, fund and register Rocketpool Node

{{< hint type=tip title="Wait" >}}
Make sure the Execution and Consensus client are fully synced before you proceed.  
You can check the progress at the top right of the [RocketPool configure page](http://my.ava.do/#/Packages/rocketpool.avado.dnp.dappnode.eth)
{{< figure src="sync_status.png" >}}
{{< /hint >}}

After you verified the information on the Welcome page, click **Start setup** to setup your Rocketpool Node and first minipool. 

### Initialize wallet

Enter a **secure** password (twice) and click **Init wallet**.

Next download a backup of your wallet.

### Fund wallet

{{< hint type=tip >}}
You may want to wait for a quiet period with lower gas fees on the Ethereum network for the following steps. It will greatly reduce the total gas cost of calling smart contracts in the following steps.  
You can check the current gas price in the top right or on e.g. the [ultrasound money](https://ultrasound.money/) website. 
{{< /hint >}}

Send `16.4 ETH` to your wallet (16 ETH + 0.4 ETH gas money). `0.4` is a safe margin to create everything, including the expensive minipool contract deploy. 
The remaining gas can be withdrawn from this wallet later.

Next, send at least the minimum required amount of RPL to your wallet. This is required as collateral and you will also get rewards for running minipools in RPL tokens. The more RPL you stake, the more you will earn. All RPL sent to this wallet will be used as your stake later - so please send exactly the desired stake amount.

* https://coinmarketcap.com/nl/currencies/ethereum/
* https://coinmarketcap.com/nl/currencies/rocket-pool/

Hit "Refresh balances" to update your balance of crypto sent to your address.

You will advance to the next step once the necessary funds have arrived in your wallet.

### Register node

To register your node on the Rocketpool smart contracts, click **Register Node**,  confirm and wait for the transaction to finish.

The *Transaction details on Etherscan* link will show more details about the transactions on the Etherscan website.


### Withdrawal address

{{< hint type=caution >}}
Check your withdrawal address at least twice. If you make a mistake here, you can not change the address later if you don't have the private keys of this address.
{{< /hint >}}


Next, you need to set a withdrawal address for your node. This must be an address you control (preferably a cold wallet, but Metamask wallet also works). All of your RPL checkpoint rewards, your staked RPL, and your Beacon Chain ETH will be sent there when you claim your checkpoint rewards or exit your validator.

Enter your (cold) wallet address and, after you validated the address twice (**important!**), click **Register Node** and confirm.

### Join smoothing pool and initialize Fee distributor

The Smoothing Pool is a way to reduce the randomness associated with block proposals on the Beacon Chain. If you've ever had a streak of bad luck and gone months without a proposal, you may find the Smoothing Pool quite exciting.

The Smoothing Pool is a collective pool for block rewards. The rewards in the smoothing pool are distributed fairly to every member of the pool every month.

[Minipools that were created before the "Redstone release"  need to initialize the fee distributor before they can extra minipools]


## Step 3: Create minipool

1. Approve RPL
   * Click button
   * Yes (to confirm)
   * Wait for transaction to finish
2. Stake RPL
   * Click "Stake"-button
   * Yes (to confirm)
   * Wait for transaction to finish
3. Deposit 16 ETH and create MiniPool
   * Click "Deposit 16 ETH and create MiniPool"-button
   * Yes (to confirm)
   * Wait for transaction to finish


## Step 4: Download and store your backup

Open to the **Setup** page and click **Download Rocket Pool Data Backup**

Check the contents of the backup file (3 validators in this example):
   {{< figure src="backup-contents.png" >}}

{{< hint type=caution title="Security risk" >}}
🔑 This backup contains the private keys to your hot wallet and also the private key of your validator(s). Make sure to handle the backup with care, so that it does not get stolen! 🔑
{{< /hint >}}

## Step 5: Configure your validator

Once you created your minipool, you need to:
1. Import the keys into the validator package (i.e. Teku or Prysm).
2. Make sure your validators use the Rocket Pool smoothing pool (`0xd4E96eF8eee8678dBFf4d535E033Ed1a4F7605b7`) as **fee recipient address**
3. Make sure **[MEV-Boost]({{< relref "mev-boost" >}})** is enabled.


### Configure validators

{{< hint type=caution title="Slashing risk" >}}
☢️ As always, make sure you run the validator only once! Never run your keys on multiple validators or machines at once. You will get slashed if you do this! ☢️
{{< /hint >}}

{{< tabs "configure_validator" >}}
{{< tab "Automatic method" >}}

If you have created a minipool and it is not imported into your validator yet you will see an error banner on top of the Rocket Pool wizard:
{{< figure src="add_validator.png" >}}

Click the **Add validators to Prysm/Teku** to add the validator automatically.
{{< /tab >}}

{{< tab "Manual method: Teku" >}}
1. Switch to the Teku settings page and click the "Add validator" field to expand it:
   {{< figure src="../teku/add_validator.png" >}}
   {{< figure src="../teku/add_validator_exp.png" >}}
2. In your file explorer, locate the content of your backup file, and navigate into the `teku/keys` (yes Teku) folder. Next, drag and drop the `json` key files into the "Browse Files" field.
4. For each keyfile, enter the password (these are stored in the `Teku/passwords` folder)
4.  Finally click "Add validator" to add the validator to Teku
5.  Repeat if you have multiple keys
{{< /tab >}}
{{< tab "Manual method: Prysm" >}}

1. Open the Prysm validator Dapp. If you don't run other validators yet, you will see this screen. Select "Import Keystores" and click the "Select wallet" button (If you already have validators running, click "Wallet & Accounts > Account list > Import Keystores" instead)
   {{< figure src="onboarding.png" >}}
2. In your file explorer, locate the content of your backup file, and navigate into the `teku/keys` (yes Teku) folder. Next, drag and drop the `json` key files into the "Browse Files" field.
3. Select "Keystores have different passwords"
4. For each keyfile, enter the password (these are stored in the `Teku/passwords` folder)
5.  Click "No" on the slashing protection data
6.  Click continue
   {{< figure src="keys.png" >}}
{{< /tab >}}
{{< /tabs >}}

### Configure the Fee Recipient address

Because the Avado Rocket Pool package uses the Smoothing Pool, the validators need to use the smoothing pool address as the fee recipient address.

The smoothing pool address is [`0xd4E96eF8eee8678dBFf4d535E033Ed1a4F7605b7`](https://etherscan.io/address/0xd4E96eF8eee8678dBFf4d535E033Ed1a4F7605b7)

If you used the automatic method above, this address is configured automatically.
If you change this address, an error banner will appear on top of the Rocket Pool wizard:

{{< figure src="fee_recipient_address.png" >}}

Click the **Correct the fee recipient address** button to correct the fee recipient address.

For Teku, you can edit the fee recipient address on the settings if plan to only run minipool validators. If you mixed solo staking nodes and rocket pool nodes, you can set the fee recipient address per validator in the validator list.

## Step 6: Wait and monitor

It will take a while for Rocket Pool to deposit the second 16 ETH to the deposit contract and for your validator to get to the front of the queue.
You can track the status by clicking the 🚀 logo of the validator on the status page. This takes you to the <https://rocketscan.io> website and shows you the complete history of your minipool.

## Step 7: Claim rewards

On a monthly basis, rewards can be claimed via the **Rewards** page. Note that claiming rewards involves a smart contract call and will need gas money from your hot wallet. For most users it is smarter to wait multiple months before withdrawing rewards.

{{< figure src="rewards.png" >}}

The **Claim rewards** button withdraws all rewards to your withdrawal address.

The **Clain and restake RPL rewards** button, withdraws the ETH rewards, and restakes the RPL rewards to your Rocket Pool node.

## Adding more minipools

It is possible to add multiple minipools. On the setup page, click **Add another minipool** to add an extra minipool.

## More information
* Node operator commision details:
https://docs.rocketpool.net/overview/faq/#how-does-the-protocol-protect-the-value-of-reth
* Token value (rETH)
https://coinmarketcap.com/currencies/rocket-pool-eth/
* Token value (RPL)
https://coinmarketcap.com/nl/currencies/rocket-pool/

## AVADO support channel
Need community help?
Telegram: [AVADO - Rocketpool staking](https://t.me/+82CX5K76Fd4xN2M8)