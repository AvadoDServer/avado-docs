---
title: FAQ
description: Frequently Asked Questions
weight: 40
aliases: ["/en/faq"]
---

{{< toc >}}

## LAN

### My AVADO box is not connected to the internet. What can I do ?

Please check your cables. Make sure the network lights (green + yellow) are on on the AVADO side of the network plug. If not, please try inserting the network cable in another port on your router. If that does not help - try again with another network cable. Make sure your internet connection is working on other devices. 

Try restarting your router by unplugging it and waiting 15 seconds and then plugging it back in. You can also restart your Avado by pressing and holding the button on the front for 5 seconds until it powers off. Wait for a few seconds and then press the button again to power it back up. Checking your cables and restarting your system will often solve connection problems. 

### Internet Speed and Bandwidth

It is recommended to have 20MBps Up- and Download Speed. In addition you should have unmetered traffic. Blockchain applications consume a lot of data. Depending on how many packages you run simultaniously - you should expect your AVADO to consume at between 3 to 5 TB of traffic per month. If you have an unmetered broadband connection - this should however not impact your internet experience overall. 

## WiFi

### How do I change the WiFi password ?
{{< hint type=warning >}}
It is **HIGHLY recommended** that you **FIRST CONFIGURE YOUR REMOTE CONNECTION CLIENT!** before attempting to change your WiFi password.
If you don't configure your remote connection first and anything goes wrong while you change the password, you will have to take the walk of shame and reach out to Sponnet on telegram to unlock your Avado.
{{< /hint >}}

Steps:
1. Make sure [Remote Connection]({{< relref "/getting-started/remote-connect" >}}) is configured correctly
2. Go to the `System` menu
3. Click the `AVADP Wifi access point` package
4. On this page you will see the SSID (The name of the WiFi network) and the WPA_PASSPHRASE. (The password). You can change both here.
{{< hint type=warning >}}
Make sure you select **at least 8 characters** for the password - otherwise it will not be accepted and your WiFi access point will not be reachable any more.
{{< /hint >}}
5. Click the **Update Environment variables** button to save and restart the package.
6. After about 30 seconds you will be able to log on to your updated WiFi network.

### The WiFi does not show up after booting my AVADO node

Please make sure that your box has an internet connection from your router. Notably make sure that the network cable is inserted before booting the box. When your AVADO does not have an internet connection, the WiFi will not show up.

Try restarting your router by unplugging it and waiting 15 seconds and then plugging it back in. You can also restart your Avado by pressing and holding the button on the front for 5 seconds until it powers off. Wait for a few seconds and then press the button again to power it back up. Checking your cables and restarting your router will often solve the problem of the Avado WiFi not showing up. 

## Connecting to your Avado

### My VPN isn't working anymore. What should I do?

You have to use the remote connection solution now: [docs]({{< relref "/getting-started/remote-connect" >}})

### I cannot connect to my Avado?

Check the [Connection troubleshooting page]({{< relref "/troubleshooting/connection-troubleshooting" >}}) for help.

## Device

### My device gets very hot at times. Should I be worried? 🌡️

The device dissipates its heat through the metal casing and the grill on the top of the device - so it is normal that this area gets hot because of this.

However, during the initial sync of any of the blockchain networks (Bitcoin , Ethereum, and others) - your box needs to work at 100% CPU capacity for several hours (or days depending on your AVADO model) and as a consequence the device can get quite hot.

This is only a temporary situation until the chain is fully synced, and then it will return to a normal CPU load - and temperature.

If this worries you, you can:
- put a fan on top of the device to cool it down. Any small breeze of air will already cool it down to room temperature. 
- point a desktop fan to the device
- putting a PC fan on top of it - you can power these using one of the unused USB ports.

## Avado Storage

## Can I upgrade my AVADO disk size
It is not currently possible to upgrade the drive storage. You can try the clean up option.
If your device seems to use a lot of the available storage, try to re-install some packages, this might help reduce the disk space needed as some packages bloat over time.
- go to my dapps
- then look at the right side and click on the "manage" option
- now you can choose between "Pause", "Restart", "Reset" or "Remove" the package
- choose "Remove"
- do this with all clients packages first (starting with Geth)
- once the package is removed go to the "System" Menue tab and select "Disk Cleanup" at the bottom of the page
- Now check the disk space available if its enough go ahead and re-install the package you removed
- If it is not enough, go through the steps above with the next package

## Packages/Dapps 

### How can I update my packages/Dapps to the newest version?

In AVADO devices the auto updates are always on unless you turn auto updates off.

### My Ethereum node synced very quickly - but is now stuck at 99%. Why? {#geth99}

The Ethereum node does its sync in 2 phases. First it downloads all block-headers (which is the 0-99% you see) and after that - geth downloads and processes all block bodies, which takes a long time. This can take up to 2 or 3 days to finalize.
So it is normal to see this 99% progress bar for a prolonged time. This only happens during the initial sync, once the chain is synced, it will remain at 100%.

According to Dr. Sebastian Burgel, there is a good technical explanation for why it takes so long to sync:

> "During the first days of syncing, your node is downloading the blocks which goes relatively fast. In the very end (where your node is at) you are actually building the state trie. It's a HUGE amount of storage in which you store things like "which address has how many ETH", "what is the token balance of each account" or "what are values in all smart contracts" - that is unfortunately a very computationally (and disk read/write) expensive and takes a long time while syncing the last blocks, IIRC it takes about 30% of the sync time.

Some more info on that here: <https://github.com/ethereum/go-ethereum/issues/20985#issuecomment-619851323>

### What if I am staking Ethereum and my node goes down? Will I get slashed?

No. Please read https://medium.com/prysmatic-labs/eth2-slashing-prevention-tips-f6faa5025f50

Slashing occurs when a validator has provably acted against the Ethereum network. Slashing doesn’t need to have malicious intent necessarily for example, it could happen from misconfiguration. The validator acted in a way the can confuse or disrupt the integrity of the system It removes, or ‘slashes’, a portion of the offending validators existing stake, causing a gradual loss of ETH over time until the validator is forcefully ejected and marked as SLASHED. This is irreversible. 

Slashing is not to be confused with inactivity penalties, which are normal loss of funds incurred over time the longer your validator is offline and unable to perform its duties. Inactivity penalties are roughly equal to the rewards that would be earned over the same amount of time. If you are online and your validator is performing it's duties **most of the time**, you will still be profitable.

The only exception is in the event that you are offline if the total network particpation drops to less than 66% at which point offline validators start getting penalized heavily. In the event of a network failure when participation drops below 66%, you should do everything you can to keep you validator online at any cost until the network participation goes back above 66%. Given what is at stake, it is unlikely that partcipation will drop below 66% barring a catastrphic failure of the network, but it's good to know the risks. 

### Can I use my AVADO with MetaMask ?

Yes! And this is actually the best way to reclaim your privacy and there are two ways to do this:
1. In MetaMask go to `Settings` > `Networks` 
2. Scroll to the bottom and click the `Add Network` button.
3. Fill in thse values:
   * Network Name: `AVADO`
   * RPC URL : `http://ethchain-geth.my.ava.do:8545` or (https://): `https://ethchain-geth.my.ava.do`
   * Chain ID : `1` Please note that entering a chain ID for your ETH node is now required by Metamask. The default value for ETH is 1.
   * Click `Save`

You can now use this connection to send all MetaMask chain queries & transactions through your own ETH node!

<!-- Alternatively, it is possible to connect to the RYO CLOUD RPC which is also a decentralized alternative to INFURA and others. This option is convenient for users who have issues VPN'ing into the AVADO or who are using another device without VPN setup. Procedure is similar to the one listed above with the following parameters:
Network Name: `RYO CLOUD`
RPC URL (https://): `https://mainnet.eth.cloud.ava.do`
Chain ID : `1` Please note that entering a chain ID for your ETH node is now required by Metamask. The default value for ETH is 1. -->

Video: Connecting Metamask to your own ETH node on AVADO: 
{{< youtube IKEpxMVa2Kw >}}

## Advanced Usage

### Connect via SSH

To connect to the node via SSH, use it's internal IP on your LAN and connect with user `avado` and password `avado`.

## Mining

### I'm just wondering if it's possible to mine ARRR with an AVADO?

➡ Nope. AVADO is not a mining rig. The AVADO is designed to run nodes, not mine. It can not mine any coin.
