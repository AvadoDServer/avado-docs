---
title: Setting up a Goerli node
description: Setting up a Goerli node
tags: [tutorial, goerli]
aliases: ["/en/tutorials/goerli"]
---

## What is Görli (aka Goerli)?

The **Görli** testnet is the first cross-client proof-of-authority (POA) network for Ethereum.

### Why?

Ethereum is moving towards Ethereum 2.0 (aka ETH2) - the main reason behind this is that the network needs to be upgraded to keep the things running smoothly and scale beyond its ~15/transactions per second limit, Ethereum is going to move from Proof Of Work (POW) to Proof Of Stake (POS) so that the network will become easier to run on basic computers.

## Setting up “Goerli Testnet (Ethereum)” node

How to install and run it:

1.  Go to: “DAppsstore”
2.  Select: “Goerli Testnet (Ethereum)”
3.  Click the “INSTALL”-button
4.  Wait … (a bit)  
    Let the installer do the work
5.  Synchronisation of the Beacon Chain will start immediately
6.  You're all set!

### Double check

Check the logs of this package to check if everything is working.

1.  Click on “show node logs”.

Scroll down. You should see no errors.

## Verify the synchronisation status on your AVADO
-----------------------------------------------

1.  Verify current block via: [https://goerli.etherscan.io/](https://goerli.etherscan.io/)
2.  Check the logs of this package

If the most recent slot in your log is near to the current slot (e.g.: 556,423 on 16th of Feb 2021)…you're almost done! ;-)

## After the installation and synchronisation

Next possible steps:

1.  Connect your Metamask Wallet  
    See video: [https://www.youtube.com/watch?v=IKEpxMVa2Kw](https://www.youtube.com/watch?v=IKEpxMVa2Kw )   
    This video is for connection Metamask wallet to the ETH Nethermind node on your AVADO.

## More information

Explorer: [https://goerli.etherscan.io/](https://goerli.etherscan.io/)