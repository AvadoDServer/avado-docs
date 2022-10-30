---
title: Ethereum Staking
weight: -20
---

{{< toc >}}

[Ethereum Staking](https://ethereum.org/en/staking/solo) with Avado helps secure the Ehtereum network and [earns you ETH rewards](https://ava.do/#ethvalidator). 

To stake ETH on an Avado you need 32 ETH to run a [solo validator](#solo-staking) or 17.6 ETH to run a [Rocket Pool validator](#rocket-pool).

Avado make staking ETH really easy, but it is unfortunately not risk free.
Make sure you understand the risks by reading:
* <https://ethereum.org/en/staking/solo/#considerations-before-staking-solo>
* <https://docs.rocketpool.net/guides/node/responsibilities.html>

## Solo Staking

Solo staking is the **gold standard** of ETH staking. It is the purest and the least risky way of staking.

{{< tweet user="superphiz" id="1561737594421002249" >}}

To stake solo stake ETH you need to:
1.  Run an **Execution Client**: An execution client is software that ...  
    {{< button relref="/packages/geth" >}}Install Geth execution client {{< /button >}}
2. Run a **Consensus Client** _(a.k.a. Beacon Chain client)_: A Consensus client is ...  
    {{< button relref="/packages/teku" >}}Run a consensus client Teku{{< /button >}} or {{< button relref="/packages/teku" size="small" >}}Run a consensus client Prysm{{< /button >}}
3. **Generate keys** and **deposit 32 ETH to the Deposit Contract**  
   {{< button relref="/packages/eth2keygen" >}}Create your validator keys{{< /button >}}
4. (Optional) install MEV-Boost to earn extra rewards when it is your turn to propose blocks.  
   {{< button relref="/packages/mev-boost" >}}Install MEV-Boost{{< /button >}}

Next you need to **monitor** and **keep your node online**.

**Note**: If ever desired, you can exit as a validator which eliminates the requirement to be online, and stops any further rewards. Be aware that until the planned Shanghai upgrade withdrawing those funds will not be possible.

## Rocket Pool

{{< figure src="/packages/rocketpool/rocketpool.png" >}}
[Rocket Pool](https://rocketpool.net/) is a truly decentralised Ethereum staking pool. It allows you to stake with only 16 ETH from yourself plus 16 ETH from the Rocket Pool staking pool. As insurance you also need 1.6 worth of ETH in Rocket Pool's RPL token.

To run a Rocket Pool node you need to:
1. {{< button relref="/packages/geth" >}}Run an execution client (Geth){{< /button >}}
2. {{< button relref="/packages/teku" >}}Run a consensus client (Teku){{< /button >}}
3. {{< button relref="/packages/rocketpool" >}}Set up a Rocket Pol node{{< /button >}}
4. {{< button relref="/packages/mev-boost" >}}Set up MEV-boost{{< /button >}}

Next you need to **monitor** and **keep your node online**.
