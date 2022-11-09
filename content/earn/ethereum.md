---
title: Ethereum Staking
weight: -20
---

On this page:

{{< toc >}}

[Ethereum Staking](https://ethereum.org/en/staking/solo) with AVADO helps secure the Ehtereum network. In exchange your will receive ETH rewards. 

To stake ETH on an AVADO you need 32 ETH to run a [solo validator](#solo-staking) or 17.6 ETH to run a [Rocket Pool validator](#rocket-pool).

AVADO makes staking ETH really easy, but it is unfortunately not risk free.
Make sure you understand the risks by reading:
* <https://ethereum.org/en/staking/solo/#considerations-before-staking-solo>
* <https://docs.rocketpool.net/guides/node/responsibilities.html>

## ETH Solo Staking

Solo staking is the **gold standard** of ETH staking. It is the purest and the least risky way of staking.

{{< tweet user="superphiz" id="1561737594421002249" >}}

To stake solo stake ETH you need to:
1.  Run an **Execution Client** _(a.k.a. Execution Engine or ETH1 client)_: An execution client is software that listens for Ethereum transactions, executes them and holds all necessary ETH information in its database.  
    {{< button relref="/packages/geth" >}}Install Geth execution client {{< /button >}}
2. Run a **Consensus Client** _(a.k.a. Beacon Chain client or ETH2 client)_: A Consensus client is software that runs the proof of stake consensus algorithm which enables the Ethereum network to agree on blocks from the execution clients. 
    {{< button relref="/packages/teku" >}}Install Consensus Client Teku{{< /button >}} or {{< button relref="/packages/teku" size="small" >}}Install Consensus Client Prysm{{< /button >}}
3. **Generate keys** and **deposit 32 ETH to the Deposit Contract**  
   {{< button relref="/packages/eth2keygen" >}}Create your validator keys{{< /button >}}
4. **Import keys** into your **Validator**: The validator package creates and validates new blocks in the chain. This is the work that get rewarded with ETH. In [Teku]({{< relref "/packages/teku" >}}) the validator is bundled with the Consensus Client. In [Prysm]({{< relref "/packages/prysm" >}}), this is a separate package that needs to be installed.
5. (Optional) install MEV-Boost to earn extra rewards when it is your turn to propose blocks.  
   {{< button relref="/packages/mev-boost" >}}Install MEV-Boost{{< /button >}}

Next you need to **monitor** and **keep your node online**.

**Note**: No withdrawing for now (until the planned Shanghai upgrade).

{{< hint type=danger >}}
**Always make sure you run your validators keys only once!** Do **NOT** run your validators on multiple clients or AVADO nodes. This would result in your stake getting slashed.  
Temporarily being offline is not a real issue. You'll will just miss out on some rewards.
{{< /hint >}}

## Staking ETH with Rocket Pool

{{< figure src="/packages/rocketpool/rocketpool.png" >}}
[Rocket Pool](https://rocketpool.net/) is a decentralised Ethereum staking pool. It allows you to stake with only 16 ETH from yourself plus 16 ETH from the Rocket Pool staking pool. As insurance you also need 1.6 worth of ETH in Rocket Pool's RPL token.

To run a Rocket Pool node you need to:
1. {{< button relref="/packages/geth" >}}Run an execution client (Geth){{< /button >}}
2. {{< button relref="/packages/teku" >}}Run a consensus client (Teku){{< /button >}}
3. {{< button relref="/packages/rocketpool" >}}Set up a Rocket Pool node{{< /button >}}
4. {{< button relref="/packages/mev-boost" >}}Set up MEV-boost{{< /button >}}

Next you need to **monitor** and **keep your node online**.

## Monitoring your validator(s)

The easiest and recommended way to monitor your validators is to create an account on [beachoncha.in](https://beachoncha.in) and register your validators' public keys in your account, you can then opt in to get e-mail alerts whenever you miss an attestation or when you propose a block
