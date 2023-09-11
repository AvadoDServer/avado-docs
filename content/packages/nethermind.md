---
title: Nethermind
---

{{< toc >}}

This guide describes the steps of installing and configuring Nethermind, the recommended Ethereum Execution client.

Since "The Merge" on September 15 2022, Nethermind needs a beacon chain, consensus client to function. Make sure you install either [Nimbus]({{< relref nimbus >}}), [Teku]({{< relref teku >}}) or [Prsym]({{< relref prysm >}}). This is required to run a full Ethereum node.

## Installation instructions

1. Navigate to the DappStore and locate the dapp named **Nethermind** and Click **Install**
2. After Nethermind is successfully installed it automatically generates a JWT token. This allows the consensus client (Teku/Prysm/Nimbus) to make a connection.  
  **Double check** that your consensus client is running. Note that it might take several days to sync the entire Ethereum state.

{{< hint type=tip >}}
It will likely take you several days to sync a full node even on a fast internet connection. Be patient, it will happen.
Refrain from restarting Nethermind, this will make this process take longer.
{{< /hint >}}

## AVADO support channel
Discord: https://discord.gg/Vp6Ggsy56P
