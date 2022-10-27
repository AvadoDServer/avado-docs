---
title: Teku
description: "Setting up Teku: ETH2.0 beacon chain and validator"
tags: [eth, ethereum, geth, tutorial]
---

# Teku

Teku is an open-source Ethereum consensus client (sometimes called an Ethereum 2.0 client) written in Java. Teku contains a full beacon node implementation and a validator client for participating in consensus.

* https://docs.teku.consensys.net/en/latest/
* https://github.com/ConsenSys/teku
* https://github.com/AvadoDServer/AVADO-DNP-Teku

Teku is a good alternative for the overused [Prysm client](/en/tutorials/prysmvalidator)

## Prepare for "The Merge"

> Ethereum will transition from Proof of Work to Proof of Stake soon, around September 15. This section summarizes how you should prepare your Avado box
{.is-info}

What should I do to prepare for the Merge?
1. Check your Geth package:
    * Is your Geth package up to date? (Avado version `>10.0.45` based on Geth version `v1.10.23`)
    * Are you running a **full** node? (Prysm needs a full client after the merge, light clients will no longer work)
    * Is Geth fully synced? If you sync from scratch, sync now, because syncing takes a while. If your Geth installation has been running for a long time and has grown large in size, consider removing Geth and installing a new, clean copy from the Dappstore to create a fresh database and minimize disk consumption. 
    
	* The steps listed here:
    https://wiki.ava.do/en/tutorials/geth#pruning-your-geth-node
for setting a fallback provider like Infura will still work until the merge so you can keep validating while you perform Geth maintenance. After the merge happens, Geth maintenance will require some downtime for your validator. 

2. Check your Teku package: Avado version `>0.016` based on Teku `v22.8.1`
3. Configure the “Fee recipient address”:
   * Open the **Teku** package
   * Click the red banner to navigate to the settings page
   * Enter the fee recipient address (this is the address where you will receive the priority fees of transactions in the blocks you propose)
   * Click **Apply changes** button

## Prerequisites

Before running the Teku beacon chain it is recommend to run the [geth execution client]({{< relref "geth" >}}).

For now this is not required, but it will be after the merge!


## Settings

Setting up Teku is really easy and the defaults are probably OK for you.

![teku-settings.png](teku-settings.png)

If you messed up, you can use the "Reset defaults" to reset to the default Avado settings

## Fast initial sync

Teku enables you to be up and running in only a few minutes by downloading a recent finalized checkpoint state rather than syncing from genesis.

Avado runs a server that offers recent snapshots. This is configured by default.
If you do not want to use this, clear the `initial-state` setting on the settings page.

You can find the details at https://docs.teku.consensys.net/en/latest/HowTo/Get-Started/Checkpoint-Start/

## Add validators

1. To add a validator click the "Add validator" field to expand it:
  ![add_validator.png](add_validator.png)
  ![add_validator_exp.png](add_validator_exp.png)
1. Next, click "Choose keystore file..." and browse to the keystore file (json) you downloaded from the [Key generator package](/en/tutorials/prysmvalidator#step-3-download-zip-file-with-your-generated-keys)
1. Enter the keystore password
1. (Optional) If you have a slashing protection file, upload the file here.
1. Finally click "Add validator" to add the validator to Teku

## Memory

If you run many validators, it is recommend to increase Teku's memory limit. Open <http://my.ava.do/#/Packages/teku.avado.dnp.dappnode.eth/detail> and look for the **JAVA_OPTS** environment variable. Next  increase the default `-Xmx3g` (i.e. maximum 3 gigabytes of 'heap space') to `-Xmx5g` (i.e. maximum 5 gigabytes of 'heap space')