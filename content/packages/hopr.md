---
title: HOPR Client
description: Setting up HOPR Client
tags: [hopr, tutorial]
aliases: ["/en/tutorials/hopr"]
---

{{< toc >}}

## What is HOPR?

HOPR keeps any exchange of data private. Standard end-to-end encryption does not provide sufficient privacy. It leaks important metadata, such as who is exchanging data, when, and how often. Securing network-level privacy with HOPR unlocks a range of opportunities.

**Disclaimer**: Check with HOPR using one of their official communication routes for the status and benefits of operating a node before committing any funds.

## Setting up “HOPR client”

How to install and run it:

1.  Go to: “DAppStore”
2.  Select: “HOPR client”
3.  Click the “INSTALL”-button
4.  Wait … (a bit)  
    Let the installer do the work
5.  You're all set!

### Double check

Check the logs of this package to check if everything is working.

1.  Go to: “My DApps”
2.  Click: on the icon in the “Manage" column for the “HOPR client”-app

Scroll down. You should see no (installation) errors in the logs.

## Verify the installation status on your AVADO

1.  Go to: “My DApps”
2.  Click: “HOPR client” > to see: “HOPR Logs \[TESTNET NODE\]”

OR (same destination)

1.  Go to: “DappStore”
2.  Click: “HOPR Client (DETAILS)”
3.  Click: “CONFIGURE PACKAGE” > to see: “HOPR Logs \[TESTNET NODE\]”

If the UI tells you to send xDai and wxHopr you are running the right version.

![](hopr_log-to-fund.jpg)

If not: restart HOPR Client in the DApps tab.

![](hopr_log-error.jpg)

## After the installation

Read this (updated 2021 03 02):

[https://medium.com/hoprnet/jungfrau-release-all-you-need-to-know-8740c8cb86c7](https://medium.com/hoprnet/jungfrau-release-all-you-need-to-know-8740c8cb86c7)

Next (possible) steps:

### How to fund your address?

(This is a summary from [the medium article](https://medium.com/hoprnet/jungfrau-release-all-you-need-to-know-8740c8cb86c7) also mentioned above)

**YOU NEED xDAI > Where do I get xDai?**

You can get xDai from some faucet.  (due to scams on the faucet this is not a stable solution)

*   [https://blockscout.com/xdai/mainnet/faucet](https://blockscout.com/xdai/mainnet/faucet) > if problems take the next one in this list

OR: change/swap Dai to xDai.  (watch out for (very) high gas prices)

*   [https://dai-bridge.poa.network](https://dai-bridge.poa.network)
*   Complete list of exchanges and swap possibilities: [https://coinmarketcap.com/currencies/xdai/](https://coinmarketcap.com/currencies/xdai/)

OR: buy xDai from exchange (recommended)

*   Buy xDai with Fiat: [https://www.xdaichain.com/for-users/get-xdai-tokens/buying-xdai-with-fiat](https://www.xdaichain.com/for-users/get-xdai-tokens/buying-xdai-with-fiat)  
    Exchange BitMax is an option to buy with Fiat
*   Complete list of exchanges and swap possibilities: [https://coinmarketcap.com/currencies/xdai/](https://coinmarketcap.com/currencies/xdai/)

OR: ask a friend who has xDAI

See steps below using MetaMask

{{< hint type=tip title="Pro tip" >}}
When using xdai chain. ALWAYS select 1 GWEI as gas. All tx's are 1 gwei, but the default is not set to 1.
{{< /hint >}}

**YOU NEED wxHopr > How to get wxHOPR (wrapped xHOPR) ?**

**Start with HOPR > xHOPR > wxHOPR**

3 steps to get wxHORP:

1.  The official way to get wxHopr is to first [buy Hopr from an exchange](https://coinmarketcap.com/currencies/hopr/) (list of exchanges down the page).
2.  Use [https://omni.xdaichain.com/](https://omni.xdaichain.com/) to change Hopr to xHopr
3.  Use [https://wrapper.hoprnet.org](https://wrapper.hoprnet.org)/ to change xHopr to wxHopr.

FYI: 1 HOPR = 1 xHOPR = 1 wxHOPR

You can use Metamask to do all this. Just change the Networks carefully.  See below.

OR

**Start with xDAI > HOPR (xHOPR) > wxHOPR**

2 steps starting from xDAI:

1.  Use [https://app.honeyswap.org/#/swap](https://app.honeyswap.org/#/swap)  to change xDAI to HOPR (i.e. xHOPR) : via xDAI chain
2.  Use [https://wrapper.hoprnet.org](https://wrapper.hoprnet.org)/ to change xHopr to wxHopr.

FYI: 1 HOPR = 1 xHOPR = 1 wxHOPR

You'll need some xDAI gas, which is cheaper to do the needed transactions to accoplish this task.

See steps below using MetaMask

### Using METAMASK to do the transactions (a step by step guide)

Please read the complete article first. There are several possibilities… (aka steps which can be interchanged)

This one was the easiest to accomplish: Fiat > xDAI > HOPR (xHOPR) > wxHOPR > to address on AVADO

#### **Step 1: Get xDAI from faucet**

1.  Copy your (xDAI) address from the logfile > address should start with “0x”…
2.  Go to the faucet: [https://blockscout.com/xdai/mainnet/faucet](https://blockscout.com/xdai/mainnet/faucet)  
    Paste your address and confirm you're not a robot.  
    Only 0,01 xDAI will be sent.. You need 0,025 xDAI > you need to use this faucet 3 times (= 0,03 xDAI) > you'll need 3 days…
3.  The page should show “Success”  
    The page will show “Error” when you try too much (even with other browsers) …
4.  Verify your transaction by clicking on the link  
    eg. [https://blockscout.com/xdai/mainnet/tx/0x550bc118644cf03426b7a4ae11220ec2afaf6d4758788347501a01ab533556af](https://blockscout.com/xdai/mainnet/tx/0x550bc118644cf03426b7a4ae11220ec2afaf6d4758788347501a01ab533556af)
5.  Verify your wallet address:  
    https://blockscout.com/poa/xdai/address/<your address goes here>)
6.  Verify our logs on Avado. Give it some time…
7.  Go to the next step > Step 2 (2 variants) > fund your account with wxHOPR

OR

Follow this manual… [https://www.xdaichain.com/for-users/get-xdai-tokens/xdai-faucet](https://www.xdaichain.com/for-users/get-xdai-tokens/xdai-faucet)

OR

#### **Step 1: Get xDAI from exchange**

You can acquire more xDai directly [using an exchange](https://coinmarketcap.com/currencies/xdaistable/) 

OR

#### **Step 1: Get xDAI from DEX** (dapp exchange)

Like HoneySwap :  [https://app.honeyswap.org/#/swap](https://app.honeyswap.org/#/swap)  eg. DAI > xDAI

Watch out for gas prices based on the disired swap.

OR

#### **Step 1:** Ask a friend for xDAI

You need to have friends! ;-)

Send your xDAI to the address specified in your logs on the HOPR DApp in AVADO.

#### **Step 2:**  HOPR  >  xHOPR  >  wxHOPR

##### **Buy HOPR**

[buy Hopr from an exchange](https://coinmarketcap.com/currencies/hopr/) (list of exchanges [down the page](https://coinmarketcap.com/currencies/hopr/markets/)).

##### **Change Hopr to xHopr**  (NEEDS review)

Use [https://omni.xdaichain.com/](https://omni.xdaichain.com/) to change Hopr to xHopr.

1.  Go to: [https://omni.xdaichain.com/](https://omni.xdaichain.com/)  
    Warning message.  
     

![](xdaichain-transaction-hopr_2_xhopr.jpg)

Click Continue (By hitting the "continue" button, you are representing that you’ve read our [Terms of Service](https://forum.poa.network/t/end-user-licensing-agreement-and-terms-of-service/2197) in full, and that you agree to be legally bound by them.)

*   Connect your wallet  
    WalletConnect or MetaMask

![](xdaichain_walletconnect_hopr_2_xhopr.jpg)

*   You should be connected to the "xDai Chain"  
     

![](xdaichain_metamask_connected_hopr_2_xhopr.jpg)

*   Select the wallet where you HOPR tokens are
*   At the left side select “HOPR Token on xDai”  
     
*   <NEEDS REVIEW>

You're set!

OR

#### **Step 2:**  Convert xDAI to HOPR (xHOPR) 

Now that you've got that xDAI…

1.  Go to: [https://app.honeyswap.org/#/swap](https://app.honeyswap.org/#/swap)
2.  Select the proper tokens to swap and fill out the amount to swap. In this example 8 xDAI will be converted to HOPR (xHOPR). You can also fill out 10 as the HOPR amount to swap to. You wil see there is a little gas fee (in xDAI ?). So be sure you have some xDAI left in your wallet.

![](transaction_xdai_to_hopr-xhopr_via-honyswap.jpg)

Get your MetaMask wallet connected to xDAI Chain.

![](transaction_xdai_to_hopr-xhopr.jpg)

Press “Confirm”

![](transaction_xdai_to_hopr-xhopr_confirmed.jpg)

FYI: if you convert xDAI to HOPR, the HOPR you see is actually xHOPR.

Check your balance.

#### **Step 3: Change xHopr to wxHopr**

Use [https://wrapper.hoprnet.org](https://wrapper.hoprnet.org)/ change xHopr to wxHopr.

Go to [https://wrapper.hoprnet.org](https://wrapper.hoprnet.org)/ > “Utility to wrap `(xHOPR -> wxHOPR)` (and unwrap `(wxHOPR -> xHOPR)` xHOPR tokens.)”

![](swap_xhopr_to_wxhopr.jpg)

Connect to your wallet and put the amout of 10 to wrap.

![](swap_xhopr_to_wxhopr_connected.jpg)

Click on “Swap to wxHOPR”.

Your set.

Go to Step 4.

#### Step 4: 

Send your wxHOPR to the address specified in you logs on the HOPR DApp in AVADO.

Connect your MetaMask.  
Don't forget to put the max amount of 10 wxHOPR before clicking “Next”.  
 

![](metamask-sent-10wxhorp_to_wxhopr-network_10.jpg)

Click "Next". You wil see there is a little gas fee (in xDAI ?). So be sure you have some xDAI left in your wallet.

![](metamask-sent-10wxhorp_to_wxhopr-network_confirm_10.jpg)

Click “Confirm”

![](metamask-sent-10wxhorp_to_wxhopr-network_pending_10.jpg)

You'll see the transaction is pending. Wait a little, message will go to status “Send wxHOPR".

![](metamask-sent-10wxhorp_to_wxhopr-network_sent_10.jpg)

#### Step 5: You're all set

Your log file should NOT be mentioning to fund your node anymore. There is no need to restart the HOPR DApp.

![](hopr_log_after-wxhopr-fund.jpg)

Happy HOPR-ing!

## AVADO support channel

Telegram: [AVADO - HOPR Box Club](https://t.me/joinchat/GuD65j2xgWyIy6Ro)

## FAQ

Is there an option to backup the private key?  
\>No you should backup the db.

Do we have to fully fund HOPR on the Avado or just install the package without funding to receive the HOPR rewards?  
\>Avado is a device to earn crypto by running DApps. If you use the HOPR tokens to stake them in the DApp (once it is fully live) you will earn more tokens for running the application. That’s how you and HOPR benefit most.  
 

## More information

* [https://hoprnet.org/](https://hoprnet.org/)
* Documentation: [https://docs.hoprnet.org/](https://docs.hoprnet.org/)
* Hopr on telegram: [https://t.me/hoprnet](https://t.me/hoprnet)