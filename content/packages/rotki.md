---
title: Rotki
description: How to install and use Rotki on Avado
tags: [avado, dapp, rotki]
---

## About Rotki

Rotki is an open source portfolio tracking, analytics, accounting and tax reporting tool that respects your privacy. The mission of rotki is to bring transparency into the crypto and financial sectors through the use of open source. Most importantly unlike virtually every other competing service which consists of closed source SaaS onto which you are forced to hand over all your financial data, with rotki your data is stored encrypted locally in your computer. It enables you to take ownership of your financial data!

Rotki is open source and the base features are free. You can fund the development by purchasing a Premium license whioch unlocks more features. More info on https://rotki.com/products/

Website: <https://rotki.com/>
GitHub: <https://github.comrotki>
Documentation: <https://rotki.readthedocs.io/en/latest/>

## Installation

Open Rotki on the DappStore page and click **Install**  
![install.png](install.png)

## Getting Started

![home_a.png](home_a.png)

There are thee ways to open Rotki:
1. The easiest method is to open Rotki in the Avado UI (over VPN): Click on the **Open** button of the Rotki package. This opens Rotki inside the Avado UI.
2. You can also open <http://my.rotki.avado.dnp.dappnode.eth/> to open outside of the Avado UI. Note that this still requires an active VPN connection.
3. Check your IP address in the Avado UI and open <http://your-ip-address:8084> to open Rotki on your local network without an active VPN. *Note that you need to trust your network to do this.*

### Create a user

Before you can use Rotki you need to create an account first. This will create a database that stores your configuration.

![create_rotki_account.png](create_rotki_account.png)

You can add as many accounts as you want.

### Add the accounts and balances you want to track

The next action is to add the [accounts and balances you want to track](https://rotki.readthedocs.io/en/latest/usage_guide.html#tracking-accounts-and-balances). 

For example, add you ethereum address, by clicking **Add blockchain address* and add your address (e.g. `rotki.eth`)

![add_account.png](add_account.png)

### Avado Ethereum Node

It is recommend to use your own **Ethereum node** to fetch Ethereum information:

* Click the **account icon** in the top right and select **Settings**.
* Scroll to **Local Nodes**
* Enter `http://my.ethchain-geth.public.dappnode.eth:8545`
  (If you are not running geth, you can use the pool from your Avado colleagues: `https://mainnet.eth.cloud.ava.do`)


### Export your data

![manage_a.png](manage_a.png)

To export your data:
* Open the **Manage** page of Rotki (** My Dapps > Rotki > Manage **)
* In the **Download from DNP** field, enter `/data/`
* Click **Download**