---
title: ETH Withdrawal address tool
---

{{< figure
    src="dappstore.jpg"
    width=300px
>}}

{{< toc >}}


Since the [**Shapella = Shanghai + Capella upgrade**](https://ethereum.org/en/staking/withdrawals/) update, Ethereum now supports staking withdrawals.  This allowes stakers to unlock their ETH staking rewards. Reward payments are automatically and regularly sent to their **withdrawal address** (aka *'partial withdrawals'*). Users can also exit staking entirely, unlocking their full validator balance (aka *'full withdrawals'*).
[Read more]({{< ref "/specials/withdrawals" >}})

For withdrawals to work, you validators need a withdrawal credential that starts with `0x01`. You can use this package to check and, if necesary, set your withdrawal address.

## ⏳ Timing recommendations ⏳

The Ethereum protocol allows for only 16 addresses configurations per block (12s), so in the wake of April 12, it will take a while before your change gets through.

**We recommend to wait a few days before setting your withdrawal address**, let the queue settle first. **You will not loose any rewards if you wait**, it will just take a bit longer before you can use them.

## Check your keys

If you have validators that need their withdrawal address set, they will show up in a table.
{{< figure
    src="check.png"
>}}

If all your validators are configured, you have nothing left to do.

{{< figure
    src="allset.png"
>}}

At the bottom of the page, the wizard lists all your validators. You can click them to see more info on your validator on the <https://beaconcha.in> website.


## Set withdrawal credentials

Setting the withdrawal address consists of 3 easy steps:

### 1. Enter your mnemonic

{{< hint type=note title="🥷 Security warning 🥷" >}}
**Is it safe to enter your mnemonic here?** You always have to be careful when entering a mnemonic! The mnemonic is a full access key to your validator, so you have to handle with a lot of care. Avado uses a secure connection (Zerotier) between your browser and your Avado device, but make sure nobody is looking over your shoulder. We also recommend to disable browser extensions or to use your browse's *incognito mode*.
{{< /hint >}}

Enter your mnemonic and the tool will automatically check if it corresponds with your validator.

### 2. Select the withdrawal address

The best way to select your withdrawal address is to connect your wallet. Avado recommends to use a hardware wallet, but any Ethereum wallet works.

**Please think carefully which address you use!** You can only set this address once. You can not change it later. If you lose the private key of this address, your validator's deposit and rewards are lost forever.

{{< figure
    src="withdrawaladdress.png"
>}}

You can also toggle the **manual input** button to enter a manual address. This field supports ENS names, but please make sure you make no typos! Check and double check the address.

{{< figure
    src="manual.png"
>}}

### 3. Confirm

Review the information and review the information again.

If you are 100% sure, click the **confirm** button.

