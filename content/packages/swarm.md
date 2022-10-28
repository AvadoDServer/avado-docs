---
title: Swarm (Mainnet)
description: Set up a Swarm mainnet node on AVADO
aliases: ["/en/tutorials/swarm"]
---

This is the BEE client - configured for mainnet

## Setting up your software
- install Swarm Node (BEE) from the DappStore (http://my.ava.do/#/installer)

## Setting up your metamask to interact with your node 

- Switch to the gnosis chain
- add the BZZ token to metamask (token address is 0xdBF3Ea6F5beE45c02255B2c26a16F300502F68da)


## Funding your node 
- get some xDAI (5 should be enough to get started)
- purchase 1 BZZ from honeyswap (https://app.honeyswap.org/#/swap)
- get your public key address from your node. This can be found on http://bee.my.ava.do/#/ under "Bee Node" -> "Public key"
- send 1 BZZ to this address
- send 0.1 xDAI to this address


## Working with your node

You can use the integrated Swarm Dashboard to access your node


## Backing up your keys

Go to http://my.ava.do/#/Packages/bee.avado.dnp.dappnode.eth/detail
go to "Download from DNP"
1. type `/home/bee/.bee/keys` and press "Download"
2. type `/home/bee/.password` and press "Download"

Keep these two archives on a backup medium - like an USB stick 

## Restore your keys

Go to http://my.ava.do/#/Packages/bee.avado.dnp.dappnode.eth/detail
go to "Upload to DNP"

1. Select the `keys.tgz` file and type 
`/home/bee/.bee/keys` in the location field and press "Upload"

2. Select the file `password.tgz` type `/home/bee/.password` and press "Upload"

Your files are now restored. Press the "Restart" button on the screen to restart your Bee node with the new setup.
