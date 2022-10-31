---
title: Teku
description: "Setting up Teku: ETH2.0 beacon chain and validator"
tags: [eth, ethereum, geth, tutorial]
aliases: ["/en/tutorials/teku"]
---

Teku is an open-source Ethereum consensus client (sometimes called an Ethereum 2.0 client) written in Java. Teku contains a full beacon node implementation and a validator client for participating in consensus.

* https://docs.teku.consensys.net/en/latest/
* https://github.com/ConsenSys/teku
* https://github.com/AvadoDServer/AVADO-DNP-Teku

Teku is a good alternative for the overused [Prysm client](/en/tutorials/prysmvalidator)

## Installation

Before running the Teku consensus client, you need to install and run the [geth execution client]({{< relref "geth" >}}).

Installing Teku is as simple as navigating to the [DappStore](http://my.ava.do/#/installer), clicking the Teku **Install** button.

As soon as Teku is installed, it automatically synchronizes with the Ethereum beacon chain network. The only setting you have to configure is the **Default recipient address**:

* Click red warning message to open the **Settings** page
* Enter your Ethereum address and click **Apply Settings**

{{< figure src="fee_recipient_address.png" >}}

{{< hint type=info >}}
You can also set a different fee recipient address for each validator. This is required if you mix full validators with [Rocket Pool validators]({{< relref "rocketpool" >}})
{{< /hint >}}


## Add validators

1. To add a validator click the **Add validator** field to expand it:
   {{< figure src="add_validator.png" >}}
   {{< figure src="add_validator_exp.png" >}}
2. Next, click **Choose keystore file...** and browse to the keystore file (json) you downloaded from the [Key generator package]({{< relref "packages/eth2keygen#download" >}})
3. Enter the keystore password
4. (Optional) If you have a slashing protection file, upload the file here.
5. Finally click **Add validator** to add the validator to Teku


## Next steps

{{< figure src="ui_overview.png" >}}

1. Check the _sync status_ in the top right
2. Check that you have enough peers. If you only see outbound peers: check your firewall. _UPnP_ should have opened port `9000` automatically. If not, open port `9000` manually on your router/firewall.
3. Check the status of your validators via  the <https://beaconcha.in> website. Clicking the green banner on the main page will open this website with your validators automatically.
4. Check the logs on <http://my.ava.do/#/Packages/teku.avado.dnp.dappnode.eth/detail> (White, Blue and Green text are good, Red text needs extra attention)

## Settings

Setting up Teku is really easy and the defaults are probably OK for you.

{{< figure src="teku-settings.png" >}}

If you messed up, you can use the "Reset defaults" to reset to the default Avado settings

## Checkpoint sync

Teku enables you to be up and running in only a few minutes by downloading a recent finalized checkpoint state rather than syncing from genesis.

Avado runs a server that offers recent snapshots. This is configured by default.
If you do not want to use this, clear the `initial-state` setting on the settings page. You can also select a different source.

You can verify the checkpoint sync by opening the check page. 
Check the state root of the displayed trused sources make sure the state root matches. If all state roots match, all is good. You can find more trusted sources on <https://eth-clients.github.io/checkpoint-sync-endpoints/>

{{< figure src="check_checkpoint.png" >}}



## Memory

If you run many validators, it is recommend to increase Teku's memory limit. Open <http://my.ava.do/#/Packages/teku.avado.dnp.dappnode.eth/detail> and look for the **JAVA_OPTS** environment variable. Next  increase the default `-Xmx3g` (i.e. maximum 3 gigabytes of 'heap space') to `-Xmx5g` (i.e. maximum 5 gigabytes of 'heap space')