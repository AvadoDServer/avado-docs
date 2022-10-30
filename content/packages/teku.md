---
title: Teku
description: "Setting up Teku: ETH2.0 beacon chain and validator"
tags: [eth, ethereum, geth, tutorial]
aliases: ["/en/tutorials/teku"]
---

# Teku

Teku is an open-source Ethereum consensus client (sometimes called an Ethereum 2.0 client) written in Java. Teku contains a full beacon node implementation and a validator client for participating in consensus.

* https://docs.teku.consensys.net/en/latest/
* https://github.com/ConsenSys/teku
* https://github.com/AvadoDServer/AVADO-DNP-Teku

Teku is a good alternative for the overused [Prysm client](/en/tutorials/prysmvalidator)

## Prerequisites

Before running the Teku consensus client, you need to install and run the [geth execution client]({{< relref "geth" >}}).

## Settings

Setting up Teku is really easy and the defaults are probably OK for you.

{{< figure src="teku-settings.png" >}}

If you messed up, you can use the "Reset defaults" to reset to the default Avado settings

## Fast initial sync

Teku enables you to be up and running in only a few minutes by downloading a recent finalized checkpoint state rather than syncing from genesis.

Avado runs a server that offers recent snapshots. This is configured by default.
If you do not want to use this, clear the `initial-state` setting on the settings page.

You can find the details at https://docs.teku.consensys.net/en/latest/HowTo/Get-Started/Checkpoint-Start/

## Add validators

1. To add a validator click the "Add validator" field to expand it:
   {{< figure src="add_validator.png" >}}
   {{< figure src="add_validator_exp.png" >}}
1. Next, click "Choose keystore file..." and browse to the keystore file (json) you downloaded from the [Key generator package](/en/tutorials/prysmvalidator#step-3-download-zip-file-with-your-generated-keys)
1. Enter the keystore password
1. (Optional) If you have a slashing protection file, upload the file here.
1. Finally click "Add validator" to add the validator to Teku

## Memory

If you run many validators, it is recommend to increase Teku's memory limit. Open <http://my.ava.do/#/Packages/teku.avado.dnp.dappnode.eth/detail> and look for the **JAVA_OPTS** environment variable. Next  increase the default `-Xmx3g` (i.e. maximum 3 gigabytes of 'heap space') to `-Xmx5g` (i.e. maximum 5 gigabytes of 'heap space')