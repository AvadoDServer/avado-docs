---
title:  Ethereum staking withdrawals (2023)
---

Exciting news: Ethereum staking withdrawals are coming soon. The official Ethereum update is called the [**Shapella = Shanghai + Capella upgrade**](https://ethereum.org/en/staking/withdrawals/). This update enables staking withdrawals on Ethereum, allowing people to unlock ETH staking rewards. Reward payments will automatically and regularly be sent to a provided **withdrawal address** linked to each validator (aka *'partial withdrawals'*). Users can also exit staking entirely, unlocking their full validator balance (aka *'full withdrawals'*).

[The update is scheduled for April 12, 2023](https://blog.ethereum.org/2023/03/28/shapella-mainnet-announcement)
<!-- {{< tweet user="TimBeiko" id="1640722906744487936" >}} -->

Your Execution client (Geth or Nethermind) and Beacon Chain client (Teku or Prysm) need to be updated. We recommend to check that automatic updates are enabled, so you get the required updates automatically.

## TLDR;

{{< mermaid class="text-center" >}}
flowchart TD

X{RocketPool?} -->|Yes| R[Ready]
X --> |No| A
A{Withdrawal <br/>credentials?} -->|Starts with `0x01`| R[Ready]
A -->|Starts with `0x00`| C
C[Wait]
{{< /mermaid >}}

## Staking rewards

After the Shapella update, if your validator has a balance of more than 32 ETH, the excess amount is automatically paid out to your withdrawal address. There are no transaction (gas) fees associated with receiving these rewards.

More details: <https://ethereum.org/en/staking/withdrawals>

{{< figure 
    src="withdrawals.png"
    width=500px
    title="This is what withdrawals will look like on beaconcha.in"
    link="https://zhejiang.beaconcha.in/validator/62474#withdrawals"
>}}

## How to prepare

### RocketPool staker?

If you are staking with RocketPool you don’t have to do anything. All rewards will be added to your minipool automatically.

That said, the upcoming RocketPool upgrade, Atlas, will require some actions, but this is out of scope of this article.

### Solo staker?

If you are a solo staker (32ETH), there are two scenarios: Your validators either have a withdrawal credential that starts with 
`0x01` (new stakers) or `0x00` (og stakers). The withdrawal credentials have to be set to `0x01` for the automatic payout of the rewards. If you have a `0x00` address, **you can set your withdrawal address with a tool Avado will release on April 12**. *🤞We promise, no command line interface will be required🤞*

Once the Shapella fork happens (April 12), we expect a huge queue to set withdrawal addresses. Only 16 addresses can be configured per block (12s), so it will take a while before your change will get through. **We recommend to wait a few days before setting your withdrawal address**, let the queue settle first. **You will not loose any rewards if you wait**, it will just take a bit longer before you can use them.

{{< hint type=warning title="Heads up warning" >}}
⚠️ Be extra careful when setting the withdrawal address. This must be an address you control, and cannot be changed once set. If you make a mistake, you will never be able to access your deposit nor rewards in the future ⚠️
{{< /hint >}}


{{< hint type=danger >}}
If you know or fear that your validator seed phrase is ☠️**compromised**☠️, it is important to beat potential scammers in the race to configure your withdrawal address. Your best option is the CLWP project:
* https://clwp.xyz
* <https://www.reddit.com/r/ethstaker/comments/10mahzn/set_your_ethereum_validator_withdrawal_address/>
{{< /hint >}}

