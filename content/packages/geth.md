---
title: Setting up Ethereum Node (Geth)
aliases: ["/en/tutorials/geth"]
---

{{< toc >}}

This guide describes the steps of installing and configuring Geth, the recommended Ethereum client.

{{< hint type=important >}}
Read all instructions in their entirety before proceeding for the best setup experience. 
{{< /hint >}}

## Step 0 : Install Geth from the DappStore
> Navigate to the DappStore and locate the dapp named `Ethereum Node (Geth)`.
{.is-info}

![geth-dappstore-install.png](geth-dappstore-install.png)

> Click `Install`
{.is-info}

## Step 1 : Wait
> It will likely take you several days to sync a full node even on a fast internet connection. Be patient, it will happen.
{.is-info}

> It is normal for the node to appear to become stuck at 99% synchronization.
This is because of how the synchronization is performed and is not indicative of a problem.
No further action should be required on your part just wait until your Chain Status shows synced.
{.is-warning}

> Once you start synchronization, it is strongly recommended that you not restart the Geth dapp or your Avado until synchronization finishes.
{.is-danger}

![geth-synced.png](geth-synced.png)

## (Optional) Configuration and Tuning
> The following steps are not required for your node to work correctly.
You do not need to do any of the following if you do not want to.
{.is-warning}

### Open the Management Page for Geth

> All of these configuration changes will be made on the management  page for Geth.
{.is-info}

![geth-mgmt-1.png](geth-mgmt-1.png)

> Each change is made by appending to or editing the value of the `EXTRA_OPTS` environment variable.
{.is-info}

![geth-mgmt-2.png](geth-mgmt-2.png)

> When appending new options to the field make sure that there is a space between your option and any other options otherwise Geth may fail to start correctly after the change is applied.
{.is-danger}

### Increase Cache Size
> Geth can be slowed down by frequent requests to the SSD for data and this can sometimes slow down other Dapps on your box as well.
This can sometimes be mitigated by allocating more RAM to Geth's cache.
{.is-info}

Append this option `--cache 4096` to specify the amount of RAM  allocated to Geth for cache and click `Update environment variables`.

> By default it is 1024MB; We've found that it can safely be increased as high as 4096MB.
You can adjust the value up to your own preference.
{.is-warning}

### Limit Peer Count
> Geth can consume large amounts of bandwidth communicating with its peers.
This can sometimes be mitigated by reducing the number of peers.
{.is-info}

Append this option `--maxpeers 20` to specify the maximum number of peers Geth will connect to and click `Update environment variables`.
> By default it is 50; We've found that it can safely be decreased as low as 20.
Below that your node may take longer than is acceptable to receive new blocks.
{.is-warning}

### Snap Synchronization (Beta)
> **BETA FEATURE - USE AT YOUR OWN RISK**
{.is-danger}

> [Snap Synchronization was released in Geth v1.10.0 in Beta and is not currently enabled by default.](https://blog.ethereum.org/2021/03/03/geth-v1-10-0/)
{.is-warning}

> It offers significant improvements both in time and the bandwith required to synchronize a new node.
{.is-info}

![snap-sync-times.png](snap-sync-times.png)

> This option will not change anything about your node if it is already synchronized, **DO NOT ADD IT**.
{.is-warning}

> It is highly recommended that you reset the Geth dapp to remove all previous data after applying this option to minimize the chance of database corruption.
**This will reset any synchronization progress that you have.**
If you've been synchronizing for less than 24hrs for most people this will still let you finish synchronizing faster.
{.is-danger}

Append this option `--syncmode=snap` to use snap sync instead of fast sync and click `Update environment variables`.

After the change has applied, reset the dapp.

![geth-reset.png](geth-reset.png)

## Running a light-client

Are you low on free disk space ? Then running a light client might be something for you. You won't have a full copy of the whole Ethereum state - but will query other full nodes for missing state information. So it will behave as a normal node, only takes much less disk space. (note that you're now not contributing to decentralization of the network so much anymore since you don't have a copy of the full state)

> Please note that after the merge, light clients will no longer be supported! If you are running a light client still, you should follow the steps for running a full execution client ASAP.
{.is-danger}

> The recent Avado Ethereum node (Geth + mainnet) version 10.0.32 (includes version v1.10.13 of the software), released on Dec. 4, 2021 may have resolved the problem with finding light client peers so this is still likely a very good solution if you have an i5 with 1TB disk size.
Please note that once you have tried a light client if it does not find peers (you can see that by ckecking the Geth logs) then you can resync a full node from scratch by simply removing the --syncmode "light" command and then updating the variables and restarting the package. A freshly installed full node will take up less than 1TB and will buy you some time until you you need to prune it and plan an upgrade path.
{.is-success}



How to configure your Geth client as light client ?

go to the admin screen of the package ( http://my.avado/#/Packages/ethchain-geth.public.dappnode.eth/detail )

Edit the field EXTRA_OPTS to read `--rpcapi eth,net,web3,txpool --syncmode "light"
`
and press the `update environment variables` button.

Then press the `RESET` button for the GETH package and over the next couple of minutes disk usage will drop by a LOT. Just wait for a few minutes and check the home page of your AVADO again.

Here is an example of what to look for when inspecting the Geth logs to see if peers are connecting. In this case the light client has found 2 peers which is good! It will work.

![light_peers.jpg](light_peers.jpg)


## Pruning Your Geth Node

> **Beta Feature - Use at your own risk** Please note that in most cases, the easiest way to perform maintenance on your execuiton client is to fully remove it from your Avado and install a new copy from the Dappstore.
{.is-danger}


Another option for people who are low on disk space that are staking ETH2 with Prysm and running a Geth full node is pruning. Pruning will gain you some disk space and buy you some more time before you’ll need to upgrade at some stage. This option allows you to continue running a full Geth node, which may be preferable for some, rather than the light client solution discussed above. The choice is ultimately yours. For now, your validator should perform the same with either solution.

First, you should set a web3 fallback provider for your beacon node. This will point your beacon node to an ETH1 client hosted on the cloud while your Geth package is being pruned in the later steps, so that you can keep validating while the procedure is being done. 

> Please note, using a third party web3 client is not a decentralized solution but it is one that has been found to work for the purpose of providing a fallback endpoint that is needed in order to halt your local instance of Geth while you prune the state.
{.is-warning}

### Setting up a Fallback Endpoint (will not work after the merge)

> Please note the step of setting up a fallback endpoint will not work after the merge and execution client maintenance will likely mean downtime for your validator going forward.
{.is-danger}

To set up a fallback endpoint on Infura, go to Infura.io and sign up for an account. Then, open a new project for “ETHEREUM” not “ETH 2”. Once you have initiated your project, copy the https: line for the mainnet as shown

![infura_endpoint.png](infura_endpoint.png)

Go to My DApps and then click on `Manage` for the ETH2.0 Prysm beacon chain package.

In the Environment variables field, you will see the EXTRA_OPTS line.

![ev_field0.png](ev_field0.png)

Under where it says value, the complete default line of text says this:
`--http-web3provider=http://my.ethchain-geth.public.dappnode.eth:8545 --grpc-gateway-corsdomain=http://prysm-beacon-chain-mainnet.avadopackage.com,http://eth2validator.avadopackage.com`

Select everything on that line and replace it with the following text to add the flag for the fallback web3 provider:
> Note that the url https://mainnet.infura.io/v3/yourprojectid should contain the project ID that you copied from Infura so you will need to replace that in text below or it will not work.
{.is-info}


`--http-web3provider=http://my.ethchain-geth.public.dappnode.eth:8545 --fallback-web3provider=https://mainnet.infura.io/v3/yourprojectid --grpc-gateway-corsdomain=http://prysm-beacon-chain-mainnet.avadopackage.com,http://eth2validator.avadopackage.com`

Your EXTRA_OPTS line should now look like this:

![fallback_opts2.png](fallback_opts2.png)

Then click on the `Update environment variables` button and then `Restart` the Prysm Beacon package. Now you have set a fallback ETH1 client that is hosted by a web3 provider (like Infura or Alchemy) so that when you stop your local Geth client, the Beacon node will fallback to the alternative endpoint. You can test this yourself by pausing your local Geth package and inspecting the Beacon logs to verify that the package continues to run with the alternative ETH1 endpoint.

![alt_endpoint3.png](alt_endpoint3.png)

### Pruning Geth

Now, go to My DApps and then click on `Manage` for the Geth package.

The default line of text for the EXTRA_OPTS line says this: 
`--http.api eth,net,web3,txpool`

Make a note of this line and copy it onto a notepad or come back to this guide so you can replace this information later once you have completed the pruning steps.

Now, replace what is on that line with this text:
`snapshot prune-state`

Then click on the `Update environment variables` button and then `Restart` the Geth package.

Geth will start the process of Pruning your Geth package. You can check in the Geth logs on your progress. You must wait for the process to complete which could take overnight or up to 24 hours. Be patient and wait until the logs indicate it has completed.

![prune_logs.jpeg](prune_logs.jpeg)

Once the process is completed, go back into the Geth package and paste back in the EXTRA_OPTS line you removed earlier:
`--http.api eth,net,web3,txpool`

Then click on the `Update environment variables` button and then `Restart` the Geth package.

Once it syncs back up you should see a nice reduction in the disk usage since you have succesfully pruned the Geth package. The Beacon node will resume using your local client when it's ready. Hopefully this will buy you some time while you plan your upgrade path and allow you to do so while still continuing to run a full Geth client on your own machine. You can leave in the web3 data you put into Prysm Beacon Chain EXTRA_OPTS. It will be your future fallback in the event that for some reason your Geth client goes down or you decide to prune again later. But please note, using a third party web3 client is not decentralized so you will want to get your local node back up and running as soon as you can to preserve your decentralized ideals.




## AVADO support channel
Telegram: [AVADO - Ethereum Club](https://t.me/joinchat/IdBKSAiIvw-q1-1p)






