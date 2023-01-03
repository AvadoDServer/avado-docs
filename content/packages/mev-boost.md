---
title: MEV-Boost
description: MEV-Boost is an open source middleware run by validators to access a competitive block-building market.
tags: 
  - ethereum
  - staking
aliases: ["/en/tutorials/mev-boost"]
---

`mev-boost` is an open source relayer to optimized block builders. By using `mev-boost` even home stakers get access to MEV (Maximal Extractable Value) rewards when they propose a block.

When you enable `mev-boost` in your validator, you can expect to get higher block rewards.

## Installation

Using `mev-boost` only makes sense if you run an Ethereum validator. So make sure you first install an execution client (e.g. Geth), a consensus layer client and a validator (e.g. Teku or Prysm).

You can find the **MEV-Boost** package in the Avada DappStore

{{< figure src="install.png" >}}

## Configure your Validator

You can enable MEV-Boost in your validator ([Teku](http://teku.my.ava.do/settings) or [Prysm](http://prysm-beacon-chain-mainnet.my.ava.do/settings)) by clicking the check box, and applying the changes.

 {{< figure src="teku.png" >}}

If you check the validator log, you should see entries like this from time to time:

{{< figure src="validatorlog.png" >}}

## Configure MEV-Boost

For most users the default configuration should be OK, but you can  configure MEV-Boost via the Avado UI on <http://my.ava.do/#/Packages/mevboost.avado.dnp.dappnode.eth>

The default configuration uses the **bloXroute** (ethical) and **Ultra Sound** relay endpoints:
```        https://0xad0a8bb54565c2211cee576363f3a347089d2f07cf72679d16911d740262694cadb62d7fd7483f27afd714ca0f1b9118@bloxroute.ethical.blxrbdn.com,https://0xa1559ace749633b997cb3fdacffb890aeebdb0f5a3b6aaa7eeeaf1a38af0a8fe88b9e4b1f61f236d2e64d95733327a62@relay.ultrasound.money
```

{{< figure src="config.png" >}}

You can find more relay endpoints at <https://github.com/eth-educators/ethstaker-guides/blob/main/MEV-relay-list.md>

## Check your Ultra Sound Relay registration

If you use the [Ultra Sound](https://relay.ultrasound.money/) relay (default), you check that your validator has registered correctly by going to https://relay.ultrasound.money/. Next paste your **validator address** in the **check registration** widget on the top right. Your validator address (aka public key) is the hexadecimal address you see in the list in Teku, Prysm or your [beaconcha.in dashboard](https://beaconcha.in/dashboard).

{{< figure src="ultra_sound_check.png" >}}

## Links
* https://github.com/flashbots/mev-boost
* https://boost.flashbots.net/
