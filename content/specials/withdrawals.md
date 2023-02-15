---
title:  Ethereum staking withdrawals (2023)
---

Exciting news: Ethereum staking withdrawals are coming soon. The official Ethereum update name is called the [**Shanghai + Capella upgrade**](https://ethereum.org/en/staking/withdrawals/). This update enables staking withdrawals on Ethereum, allowing people to unlock ETH staking rewards. Reward payments will automatically and regularly be sent to a provided withdrawal address linked to each validator. Users can also exit staking entirely, unlocking their full validator balance.

The update is expected to happen early April 2023:
{{< tweet user="christine_dkim" id="1624069668460761091" >}}

{{< figure 
    src="withdrawals.png"
    width=500px
    title="This is what withdrawals will look like (Zhejiang test network)"
    link="https://zhejiang.beaconcha.in/validator/62474#withdrawals"
 >}}

## TLDR;

{{< mermaid class="text-center" >}}
flowchart TD

X{RocketPool?} -->|Yes| R[Ready]
X --> |No| A
A{Withdrawal <br/>credentials?} -->|Starts with `0x01`| R[Ready]
A -->|Starts with `0x00`| C
C{Validator keys <br/> compromised?} -->|NO| W[Wait]
C -->|Maybe or Yes| D[Use CLWP ASAP];
{{< /mermaid >}}

## Staking rewards

After the update, if your validator has a balance of more than 32 ETH, the excess amount is automatically paid out to your withdrawal address. There are no transaction (gas) fees associated with receiving these rewards.

More details: <https://ethereum.org/en/staking/withdrawals>

## How to prepare

If you are staking with RocketPool you don’t have to do anything.

If you are a solo staker (32ETH) , you have to check your withdrawal address. Recent stakers have already configured a correct (`0x01`) withdrawal address when making the 32 ETH deposit to the Staking contract. OG stakers, don’t have a withdrawal address yet, they have a BLS (`0x00`) address instead.

You can check what address you have by checking your validator on https://beaconcha.in and checking the “Deposits” tab. 

{{< 
    figure src="0x00_solo.png"
    title="The withdrawal credential starts with `0x00`, so this validator will need to set a withdrawal address"
    link="https://beaconcha.in/validator/42#deposits"
>}}

 {{< 
 figure src="0x01_rocketpool.png" 
  title="The withdrawal credentials start with `0x01`, so this (RocketPool) validator needs no further actions"
    link="https://beaconcha.in/validator/269178#deposits"
 >}}


If your “Withdrawal credentials” start with `0x01` *there is **nothing** you should*. The rewards will be automatically deposited to your withdrawal address.

If your “Withdrawal credentials” start with `0x00`, you will have to configure your withdrawal address after the update. Only 16 addresses can be configured per block, so there will be a huge queue at the beginning.

If your validator seed phrase is safely stored offline, there is no need to rush. **We currently recommend just waiting** for the tooling to be battle-tested and the dust to settle. If you are impatient, we recommend reading the documentation of the test network instead: https://zhejiang.launchpad.ethereum.org/en/withdrawals

If you know or fear that your validator seed phrase is ☠️**compromised**☠️, it is important to beat potential scammers in the race to configure your withdrawal address. Your best option is the CLWP project:
* https://clwp.xyz
* <https://www.reddit.com/r/ethstaker/comments/10mahzn/set_your_ethereum_validator_withdrawal_address/>


{{< hint type=warning title="Heads up warning" >}}
⚠️ Be extra careful when setting the withdrawal address. This must be an address you control, and cannot be changed once set. If you make a mistake, you will never be able to access your deposit nor rewards in the future ⚠️
{{< /hint >}}
