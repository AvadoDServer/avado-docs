---
title: Setting up an account for Tornado Cash v2
description: Getting started from scratch (fresh setup)
---

{{< hint type=warning >}}
Update January 16, 2022. Before you embark on setting up a TC relayer, please be aware that transactions processed by the Odanrot relayer have been very slim and there is a good chance that you will not see any rewards for running a relayer at this time. Proceed at your own risk.
{{< /hint >}}

Getting started from scratch (fresh setup)

**The Avado tornado.cash relayer pool is intended to be a premium, decentralized, privacy service consisting of individuals in the pool running private ETH1 nodes. This maximizes privacy for the end user and for the relayer. As such, there are a set of conditions that must be met to preserve the integrity of the pool as a premium, decentralized service. Running a tornado.cash relayer is performed at your own risk. You are responsible for understanding what you are doing and you must accept any and all risks associated with running a relayer.**

> It is required that you run Geth alongside your TC v2 package. No other Web3 providers will work. Not running Geth and using it as your ETH endpoint in the TC Relayer settings? Then your relayer will not be allowed to participate in the pool.

If you have been running a relayer and were not aware of these rules previously, now is the time to familiarize yourself with them. With the release of tornado.cash v2, comes a new day and new rules. This is necessary and has been voted on by the governing body of the relayer club. Complaints should be directed to the manager. :) Sorry, not sorry. If you are already running a clean account from Tornado Cash V1 and the account can be verified as clean (e.g. does not contain any transactions that link to external transaction/balance history), you may continue to use that relayer account so long as the minimum balance of 1 ETH is maintained at all times. 

You should be prepared to leave a fresh relayer account alone and let the rewards accumulate over time until such time as participation in the relayer pool is ceased. Relayer accounts in the pool will be audited on a regular basis and if a relayer account shared in the pool does not meet the funding requirements and minimum balance described in this guide, or if it contains linkable transactions to an account with a balance history, it will be removed from the pool until it is fixed with a clean relayer account that meets the requirements.

The relayer account should  **not have any other transactions coming in and out**  that are linkable to a balance history or identity. The only transactions one should see in the wallet when exploring on Etherscan should be the initial funding done through tornado.cash and subsequent Tornado.Cash: Proxy transactions. There should be no extra deposits or withdrawals to or from accounts that compromise the anonymity of the relayer. Using a decentralized Web3 exchange within the relayer account itself (such as Uniswap) is acceptable if you wish to convert stable coins earned during stable coin transactions back into ETH, since this does not compromise the anonymity of the relayer account and only represents a smart contract interaction that is self-contained.

**The terms and instructions are explained further in the steps below so read on if still interested, or stop reading if you cannot or will not follow the rules for participation in the relayer pool.**

_**Why:**_ Just like users want to be anonymous after using tornado.cash -  a relayer should also be anonymous. Just funding a relayer account with your own wallet will link your relayer to your identity and your transaction history - which is bad practice and is not good for your own privacy as a relayer, and compromises the integrity of the relayer pool as a premium, decentralized relayer service. 

**Therefore, the procedure below and running your own Geth node and using it as your ETH endpoint is required for participation in the pool.**

Step 1 : Use Metamask to Create a New Account
---------------------------------------------

In Metamask - click on the top right icon. This will be the account used as a Tornado Cash relayer. 

**It is important that this be a new account that is funded anonymously and does not link to other transaction history coming in our out. The following guide will explain the steps to accomplish this important concept.**

![](tc1.png)

Select create account and then name the relayer account whatever you like.

![](tc2.png)

![](tc3.png)

Step 2 : Fund This Account Through tornado.cash by Making two 1 ETH Deposits
----------------------------------------------------------------------------

Go to https://tornado.cash/ and select launch app. By using tornado.cash, the account used to make the deposit with will not be linkable to the relayer account when following the instructions in this guide.

![](tornadodotcash.png)

tornado.cash

Once you launch the app, first open the Metamask extension in the web browser and select the account you wish to make the funding deposit with. This can be any account you own which contains enough ETH to make a two separate 1 ETH deposits plus the gas fee which is currently a little more than 0.1 ETH so make sure you have at least 2.35 ETH in the account used make the deposits. 

Hit Connect on the tornado.cash page to link to Metamask and confirm in Metamask that the account used to make the deposit is connected via Web3 which you will see as a green dot which says “Connected” in Metamask. The tornado.cash site will then be connected to the account that will be used to make the deposit. Please note that due to the tornado cash requirement of maintaining a minimum balance of 1 ETH in your relayer wallet, the easiest (and least expensive) way of doing this is to make two seperate desposits to tornado.cash consisting of 1 ETH each. Therefore simply follow the instructions for making a 1 ETH deposit to tornado.cash and then repeat to make a second deposit.

![](tc_deposit_2.png)

![](wallet_connect.png)

![](rainy_day_2.png)

Connected to tornado.cash

Once you have confirmed that you are connected to the Metamask account and are ready to make the deposit, click _**Deposit**_ on the tornado.cash page and the browser will download a text file containing the deposit note. **Please backup the note.** If you lose it, you won't get your deposit back. Treat your note as a private key - never share it with anyone, including tornado.cash developers. Check the box to confirm that you have backed up your note and then click _**Send Deposit**_.

![](note_bkup.png)

After you send the deposit, the TC wheel will spin and you will be asked to confirm the transaction in Metamask. Suck it up and hit _**Confirm**_. No whining.

![](confirm_tx.png)

![](no_whining.png)

Remember that these funds will be used to fund a clean relayer account and privacy as a relayer is worth it. It is essential to the concept of a decentralized, premium relayer service. The balance of the relayer account will only increase unless it relays a stable coin transaction, which is not common but can occur. Please also note that **depositing 0.1 ETH is not enough** and will not meet the minimum requirements for the relayer pool. 

**Relayer accounts must be funded by using tornado.cash and it is required for participation in the relayer pool. If the relayer account is found to be funded by an account with a linkable balance history, it will be removed from the pool. That is the rule.** 

**No exceptions.**

![](deposit_complete_2.png)

**After you make the deposit, your note will be shown on the main tornado.cash page**

Step 3 : Fund the Relayer Account by Making a Withdrawal Using the Note
-----------------------------------------------------------------------

After waiting for a while (**24 hours at the very least**, 72 hours recommended) and confirming that there have been subsequent deposits between the time of the deposit and the time of withdrawal, prepare to withdraw the funds to the account created in **Step 1**. 

1.  Start by clicking on the _**Withdraw**_ tab on the main tornado.cash page.
2.  Copy and paste the note into ‘Note’ and fill out the ETH address of the tornado cash relayer as ‘recipient address’.
3.  Afterwards, please click _**Withdrawal Settings,**_ which is shown in the screenshot below as two slider bars beneath the Withdraw tab_._ 

> Please note that not enough time has passed for the note used in this example and there are no subsequent deposits yet. This is being used as an example to create the guide only.

![](withdraw.png)

When selecting settings, you will see a window with a dropdown menu where you can choose the relayer service to process the withdrawal. 

If you would like to use **v2.odanrot.eth** as a relayer service, that is smart because someone in our RYO pool will process the transaction and earn the reward. Hit save to confirm your relayer selection.

![](settings.png)

When you are taken back to the main page, select _**Withdraw**_ and the transaction will start processing and be mined. 

2 steps before taken back to the main page:

1.  Confirm your withdrawal: “Save”
2.  Relayer is now sending your transaction. It will respond with a transaction hash soon...  
     

![](withdrawing_1-eth_tc.jpg)

Screen refreshes to the main screen showing:

![](withdrawingnote_1-eth_tc.jpg)

After completion - you should have a little under 2 ETH in the fresh relayer account that was created in **Step 1**. This can be verified by looking at the account address in Metamask or on Etherscan.

Step 4 : Install and Configure the Relayer
------------------------------------------

First install the Tornado Cash Relayer v2 package from the Dappstore.

After installation is complete, click the “configure package” button and you’ll see the screen shown hereafter.

The URL of the Ethereum node to use assumes that, in support of decentralization, you have set up your own ETH1 node on AVADO (Geth). 

**If you have not yet installed Geth, do that now!** 

Click on _**Change settings**_. 

![](settings_1.png)

![](settings_2.png)

Make sure to set the fee to **0.05% (screenshots OUTDATED!)**

We also need to grab the private key from Metamask for the previously created relayer account created in Step 1, and funded in **Steps 2** and **3**.

Open Metamask and select the relayer account that was created in **Step 1**.

Click on the 3 dots and select “account details”.

![](tc9.png)

In that screen click on “_**Export Private Key**_”.

![](tc10.png)

Enter your Metamask password and press “_**Confirm**_”.

![](tc11.png)

Copy this private key, close the Metamask window and go back to the Tornado cash settings page.

Paste the private key in the “Signing Key” field and click _**Save and start package**_.

![](private_key.png)

**Follow ALL of the steps above to fund this account through tornado.cash with a 1 ETH transaction** 

Step 5: Share the Relayer in the RYO Cloud
------------------------------------------

Install the RYO client from the Dappstore.

![](ryo.png)

Open the package and click on _**Edit settings**_. Toggle the switch to share the Tornadocash relayer v2 and any other packages you wish to share in the cloud. Enter the name of your relayer node and the ETH address for RYO rewards. **Please note that this is NOT the TC relayer account address.** Please enter a different ETH address here. The RYO is not monetized at this time but it may be in the future so it's good to have an address in for when that time comes but **do not make the mistake of pasting the relayer address here**.

![](ryo_settings.png)

Then click on _**Save and start package**_. 

Step 5 :  Apply to get whitelisted
----------------------------------

There is no automated way (yet)  to verify all requirements to be added, therefore we are using a whitelist mechanism.

Everybody who implemented all steps as described above is eligible to join. Please reach out on the [Tornado cash relayer](https://t.me/joinchat/TJQHB7roveDqmuHC)  Telegram channel and ask to be added, you will be helped by your future-fellow-relayers !!

Step 6 : Happy Fishing!
-----------------------

You are now all set and ready to go! You should now see the relayer node ID on [https://status.cloud.ava.do/](https://status.cloud.ava.do/)

If you do not see the relayer name show up on the status page, please restart the RYO package and check again. Sometimes it takes a few restarts for the RYO client for the relayer to show up on the status page. Once you see the node ID on the status The relayer is now online and ready to process those Tx. You can monitor the progress of the relayer by watching the relayer address on Etherscan and relayer address on the RYO status page are clickable links so there you go. 

Don't forget to promote the tornado.cash relayer service **v2.odanrot.eth** on social media as a decentralized service where a group of individuals are each running their own private Ethereum nodes. This sets us apart from the crowd and is desirable for those who know what they are looking for in a premium service with a pool of relayers who take privacy very seriously and have taken the necessary steps to ensure the integrity of the pool.

**Happy fishing!**

![](squids.jpg)

Jigging for squid

Step 7 : Extra info
-------------------

It seems that the latest update from TC relayer requires you to have a balance >= 1 ETH

Please all who have < 1 ETH in their accounts - top it up using a second TC transaction

When you're above 1 ETH you will be automatically added again to the pool - but please use TC to top up your wallet not to lose your anonymity.

AVADO support channel
---------------------

Telegram: [AVADO - Tornado Cash Club](https://t.me/joinchat/TJQHB5xaNyGKD004)