---
title: Geth
aliases: ["/en/tutorials/geth"]
---

{{< toc >}}

This guide describes the steps of installing and configuring Geth, an Ethereum Execution client.

Since "The Merge" on September 15 2022, Geth needs a beacon chain, consensus client to function. Make sure you install either [Nimbus]({{< relref nimbus >}}), [Teku]({{< relref teku >}}) or [Prsym]({{< relref prysm >}}). This is required to run a full Ethereum node.

## Installation instructions

1. Navigate to the DappStore and locate the dapp named **Ethereum Node (Geth)** and Click **Install**
  {{< figure src="geth-dappstore-install.png" >}}
2. After Geth is successfull installed it automatically generates a JWT token. This allows the consensus client (Teku/Prysm) to make a connection.  
  **Double check** that your consensus client is running. Note that it might take several days to sync the entire Ethereum state.

{{< hint type=tip >}}
It will likely take you several days to sync a full node even on a fast internet connection. Be patient, it will happen.
Refrain from restarting Geth, this will make this process take longer.
{{< /hint >}}

{{< hint type=important >}}
It is normal for the node to appear stuck at 99% synchronization.
This is because of how the synchronization is performed and is not indicative of a problem.
No further action should be required on your part just wait until your Chain Status shows synced.

[More details]({{< relref "/faq/#geth99" >}})
{{< /hint >}}

{{< figure src="geth-synced.png" >}}


## Geth syncing process breakdown

⌛️ Syncing geth is a lengthy process, so you will need patience. This section gives a breakdown of the different phases and how you check geth's progress and can help you assess if your log looks normal. It also illustrates why geth seems stuck at 99%?

The metrics and statistics were gathered on an **Avado i7/2TB** with:
* 1 Gbps fibre line
* strong USB fan
* extra Geth options : `--cache 8192`, port 30303 open on router
* extra Teku options : `-Xmx5g`, port 9000 open on router

It took *~20.5 hrs* from start to the time when the validator came back online (started attesting). Your numbers will vary, depending on your network speed and Avado type. In particular, phase 1 is very network intensive, so if you have a slower network, this phase will take much longer. All phases are heavy on the ssd, so do use a fan to cool the Avado, so the ssd does not have to throttle.

The geth syncing process starts with some initialization and starts looking for peers. When it has found a few --opening port 30303 on the router helps a lot here--, it starts the actual syncing progress. The the main process may be divided into 5 major phases:

1. Import block headers / block receipts
   - this phase imports the main bulk of the blockchain data
   - dashboard initially shows Nan% then gradually runs up to 99%
   - network intensive (peak data rate `>250Mbps`)
   - log shows `imported new block headers` and `imported new block receipts`. At the end of these lines it shows the “age” of the block imported.  this will count down from many years/months/weeks (most ancient) to eventually weeks/days/hours (most recent)
   - this phase took about *~7 hrs*
2. State sync in progress
   - this phase builds the internal states
   - dashboard stays at 99% all of this time
   - cpu and disk i/o intensive (cpu `>50%`, ssd temperature `>70℃`)
   - log shows `state sync in progress` with an “eta” countdown - not very accurate but gives you a sense of its progress
   - this phase took about *~11 hrs*
3. State heal in progress
   - this phase catches up between the computed state and the newly arriving data
   - dashboard continues to be “stuck” at 99%
   - slightly less hectic (cpu `<20%`, ssd temperature `<70℃`)
   - log shows `state heal in progress`
   - there is a “pending” number but fluctuates and not obvious when it will end, but it will eventually get there
   - this phase took about *~2 hrs*
4. wait for sync to complete
   - at this point dashboard shows 100%, but geth may not be quite done yet
   - if you had already started your consensus client (Teku syncs almost instantly) it was just following the chain and logging `waiting for execution layer sync`.
   - once geth finished syncing, Teku will start attesting.
   - (if you’re using rocketpool, once geth finished syncing, you’ll be able to load/restore the validator keys via the rocketpool interface)
   - this phase took me ~0.5 hrs
5. State snapshot
   - this phase generates snapshots for other nodes to sync. This overlaps with the last part of phase 4. So you start to see `generating state snapshot`,  `aborting/resuming state snapshot generation`, etc. in the log even before syncing finished. These messages are expected. There is an “eta” to show when the process is expected to finish, which could take another few hours, and remains cpu intensive. All this happens in the background, and does not affect attestation.  


## Optional Configuration and Tuning

The following steps are not required for your node to work correctly. The following steps allow you to tweak Geth for your context by using non-default settings. You do not need to do any of the following if you do not want to.


Configuration changes can be made on the management  page for Geth. {{< figure src="geth-mgmt-1.png" >}}

Each change is made by appending to or editing the value of the `EXTRA_OPTS` environment variable. {{< figure src="geth-mgmt-2.png" >}}

{{< hint type=important >}}
When appending new options to the field make sure that there is a space between your option and any other options otherwise Geth may fail to start correctly after the change is applied.
{{< /hint >}}

### Increase Cache Size
Geth can be slowed down by frequent requests to the SSD for data and this can sometimes slow down other Dapps on your box as well.
This can sometimes be mitigated by allocating more RAM to Geth's cache.

Increasing the default cache size (4096 MB) will result in:
- less frequent writes to the on disk database
- slower increase of the database size (because some EVM states cancel out and never make it to the database)
- more impact from unexpected problems such as unclean power downs. It will take longer to resync.

If your Avado has plenty of RAM and you don't run too many other Dapps, you can increase the cache size to e.g. 8192 (8GB) by appending `--cache 8192` and clicking **Update environment variables**. Double check the logs to verify that Geth is running correctly.

Note: You can adjust the cache size to your own preference.

### Limit Peer Count

Geth works better when it has a lot of peers, but more peers also results in more bandwidth usage. 

To reduce bandwidth usage, you limit the maximum number of peers by appending `--maxpeers 20` and clicking `Update environment variables`.

The default value is `50`; But users have reported they could safely decrease it to as low as 20.


### Running a light-client
{{< hint type=warning >}}
Do **NOT** run a light client if you want stake Ethereum (i.e. run a validator). This will appear to run OK untill you are selected to propose a new Block. This will fail!
{{< /hint >}}

Are you low on free disk space but do you still want to run your own Ethereum node? Then running a light client might be something for you. You won't have a full copy of the whole Ethereum state - but will query other full nodes for missing state information. So it will behave as a normal node, but it will use way less disk space. A light client contributes less to the decentralization of the Ethereum network, but it is still better than using a centralized service.

How to configure your Geth client as light client ?
1. Go to the admin screen of the package: <http://my.ava.do/#/Packages/ethchain-geth.public.dappnode.eth/detail>
2. Edit the field EXTRA_OPTS and append ` --syncmode "light"` (make sure there is a leading space)
3. Press the **`**update environment variables**`** button

Here is an example of what to look for when inspecting the Geth logs to see if peers are connecting. In this case the light client has found 2 peers which is good! It will work.
{{< figure src="light_peers.jpg" >}}


### Pruning Your Geth Node

{{< hint type=warning title="Use at your own risk" >}}
For most users, the easiest way to perform maintenance on your execuiton client is to fully remove it from your Avado and install a new copy from the Dappstore.

Note that taking Geth offline results in an offline validator too.
{{< /hint >}}

Over time the Geth database accumulates redudant state information. Pruning this information is too intensive to run while Geth is performing its other tasks. So Geth needs to be restarted with different parameters to run this cleanup.

This is a lengthy process that takes multiple hours. But it can reduce the Geth database footprint significantly.

Process:
1. Go to the admin screen of the package: <http://my.ava.do/#/Packages/ethchain-geth.public.dappnode.eth/detail>
2. Edit the field EXTRA_OPTS and append ` snapshot prune-state` (make sure there is a leading space) 
3. Click on the **Update environment variables** button.
4. Wait while Geth runs the pruning process your Geth package. You can check in the Geth **logs** on your progress. You must wait for the process to complete which takes multiple hours. Be patient and wait until the logs indicate it has completed. {{< figure src="prune_logs.jpeg" >}}
5. Once the process is completed:
   1. Go back into the Geth package
   2. **Remove** ` snapshot prune-state` in the **0XTRA_OPTS** field
   3. Click the **Update environment variables** button

Once it syncs back up you should see a nice reduction in the disk usage since you have succesfully pruned the Geth package. The Beacon node will resume using your local client when it's ready.

## AVADO support channel
Discord: https://discord.gg/Vp6Ggsy56P
