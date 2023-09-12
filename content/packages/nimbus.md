---
title: Nimbus
description: "Setting up Nimbus"
tags: [eth, ethereum, geth, tutorial]
---

Nimbus is an open-source Ethereum beacon chain and validator client

* https://nimbus.guide/index.html
* https://github.com/status-im/nimbus-eth2
* https://github.com/AvadoDServer/AVADO-DNP-nimbus

Nimbus is a good alternative for the overused Prysm client.

## Installation

Before running Nimbus, you need to install and run an execution client ([Geth]({{< relref "geth" >}}) or [Nethermind]({{< relref "nethermind" >}})).

Installing Nimbus is as simple as navigating to the [DappStore](http://my.ava.do/#/installer), clicking the Nimbus **Install** button.

As soon as Nimbus is installed, it automatically synchronizes with the Ethereum beacon chain network. The only setting you have to configure is the **Default recipient address** and select the **Execution Client**.

* Open the **Settings** page
* Enter your Ethereum address
* Make sure the correct execution client is selected
* click **Apply Settings**

## Add validators

To run a validator, you need to [create Validator keys first]({{< relref eth2keygen >}})

1. To add a validator click the **Add validator** field to expand it:
   {{< figure src="../teku/add_validator.png" >}}
   {{< figure src="../teku/add_validator_exp.png" >}}
2. Next, click **Choose keystore file...** and browse to the keystore file (json) you downloaded from the [Key generator package]({{< relref "packages/eth2keygen#download" >}})
3. Enter the keystore password
4. (Optional) If you have a slashing protection file, upload the file here.
5. Finally click **Add validator** to add the validator

{{< hint type=info >}}
You can also set a different fee recipient address for each validator. This is required if you mix full validators with [Rocket Pool validators]({{< relref "rocketpool" >}})
{{< /hint >}}

## Next steps

1. Check the _sync status_ in the top right
2. Check that you have enough peers. If you only see outbound peers: check your firewall. _UPnP_ should have opened port `9000` automatically. If not, open port `9000` manually on your router/firewall.
3. Check the status of your validators via  the <https://beaconcha.in> website. Clicking the green banner on the main page will open this website with your validators automatically.
4. Check the logs on <http://my.ava.do/#/Packages/nimbus.avado.dnp.dappnode.eth/detail> (White, Blue and Green text are good, Red text needs extra attention)

## Settings

Setting up Nimbus is really easy and the defaults are probably OK for you.

If you messed up, you can use the "Reset defaults" to reset to the default Avado settings

## Checkpoint sync

Nimbus enables you to be up and running in only a few minutes by downloading a recent finalized checkpoint state rather than syncing from genesis.

Avado runs a server that offers recent snapshots. This is configured by default.
If you do not want to use this, clear the `initial-state` setting on the settings page. You can also select a different source.

You can verify the checkpoint sync by opening the check page. 
Check the state root of the displayed trusted sources make sure the state root matches. If all state roots match, all is good. You can find more trusted sources on <https://eth-clients.github.io/checkpoint-sync-endpoints/>

{{< figure src="../teku/check_checkpoint.png" >}}


## AVADO support channel
Discord: https://discord.gg/Vp6Ggsy56P
