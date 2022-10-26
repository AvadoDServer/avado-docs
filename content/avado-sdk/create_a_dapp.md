---
title: reate your DApp for the AVADO DAppstore
aliases:
  - /en/developers/building-an-avado-package
---

# Create your DApp for the AVADO DAppstore

## Convenience is most important
Let's start with some context.
AVADO devices are used in more than 60 countries on all continents. Even though this means a very diverse culture of our users, we do find that our users all share the same motivation why they bought the AVADO. They are looking for **privacy** and **convenience**!
Privacy is given by running their own device, but convenience really comes from how easy the DApp is to be used.

Therefore we have certain requirements that have to be met in order to become a DApp in our Store.
* No Command Line Interface - any CLI has to be integrated into the UI
* All info the user has to provide (for example a public address) needs to be part of the onboarding wizard (see section onboarding wizard for more info)
Note that the AVADO device can run other DApps like Nodes, so if your package needs a certain application to run, create this requirement as a dependency. 
* Information from other packages like a Node ID should be automagically inserted without action needed from the user

## AVADO SDK
The AVADO SDK makes life easier for developers that want to build a package on AVADO.
You can install the SDK from npm using this command

`npm i -g git+https://github.com/AvadoDServer/AVADOSDK.git`


## Wizard
We expect each package to have a web-UI embedded in the docker container whenever user interaction is required to configure or maintain the software. 
Users should never be exposed to a command  line interface or SSH into the box etc…

A wizard should be used for interactions such as :
- onboarding of a user - a form that the user needs to fill in to  configure the software
- backup and restore of keys / wallets / configuration files
- status of the package (node in sync , relevant statistics or status)

We  roughly divide wizards in 3 categories:
### Wizards that communicate with the node’s API directly
These have a web-app embedded (a React app preferably) and contain  the necessary libraries client side to talk to the node itself. Using  CORS or a CORS proxy  on the package you can seamlessly talk to the API.
An example React  App that talks to the API can be found in the Avalanche package
https://github.com/AvadoDServer/AVADO-DNP-AvalancheGo/tree/master/build/wizard 
https://github.com/AvadoDServer/AVADO-DNP-AvalancheGo/blob/master/build/wizard/src/pages/home/components/AvalancheInfo.js

### Wizards that need interaction with the file system. 
These can use the package’s file system through calls over a websocket to read and write files on the container. Using a (nodejs) rest API in the container - you can do more advanced things like running executables on the container etc.
An example of interacting with the file system van be found in the Swarm package: https://github.com/AvadoDServer/AVADO-DNP-Bee/blob/main/build/wizard/src/pages/home/components/DownloadBackup.js


###  Wizards that need interactive sessions with a command line tool embedded in the container. 
Here we use the linux tool “expect” to  automate this session, and feed it with input from the wizard.
An example of this can be found in the ETH2 key generation wizard. It takes user input from a webform, and feeds it  to this script which is executed by a REST api call in the package:

Some examples from existing packages:
- Rest API: https://github.com/AvadoDServer/AVADO-DNP-eth2-keygen/blob/main/build/monitor/server.js 
- Expect script: https://github.com/AvadoDServer/AVADO-DNP-eth2-keygen/blob/main/build/files/mkkeys.sh 

 
## Maintenance
Our users expect that the package in our DAppstore is always the latest version of your Application available. Therefore we ask you to update the AVADO version of your DApp within 24 hours of the publication of a new version of your application.
The AVADO box has an auto update function integrated by default, which will update the DApp within one hour on each box. If the default is turned off, the user will be prompted that an update is available through an update button in the dappstore but he has to update it manually.

## Quality check
Once you created the DApp or updated the DApp we will test it and go through all functions. We have a dedicated testing group where we will publish the IPFS Hash. Once the test shows the DApp working properly from a technical and UX point of view, we will publish it (see 5. Publishing for more details) 

## Publishing
You can build the package yourself using the AVADO SDK and each time you want to publish - you issue a PR in your repo - containing the IPFS hash of your package. We will pick this up in the next update of the dappstore.

## Support
AVADO is using Telegram to give support to the community. We will set up a support channel for your DApp. This will be a special group and we expect to see at least one of your support team participating in the group. 
In general our community is very supportive and we even incentivize giving support. This will also be activated in this channel, but we will exclude your support team from receiving the incentive we pay out each month. (see more info on our support concept here: How to scale support

## Activation
Your DApp will be accessible for each of our Users as soon as it is published in the DAppstore. This could mean that several hundred users will use your services immediately. Please ensure that your system scales well with this sudden amount of user increase.
We also encourage projects to have a special marketing strategy in place to inform and activate users. AVADO has created a NFT which can be found on the xDAI chain Blockchain and you can use this information to incentivize AVADO users by dropping some of your tokens or for any other kind of activation marketing.

## Privacy
AVADO will not share any private information of our users. The NFT is the only way to identify an AVADO User, through his Ethereum address. AVADO does not collect any user or usage data from the boxes that are running, therefore we cannot provide any info on how many users are using your DApp on the AVADO. 

## Contact
If you need more information on how to build the DApp, please contact Stefaan@avado.ag

