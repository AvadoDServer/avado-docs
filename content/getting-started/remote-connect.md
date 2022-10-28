---
title: Remote Connection 
description: How to set up an easy remote connection to your AVADO
weight: 0
aliases: ["/en/tutorials/remote-connect"]
---

{{< toc >}}

# What is Remote Connect
Remote connect is a package that allows remote connections to your AVADO.

The Remote Connect solution is super easy and works in nearly every environment. No need to open any ports on your router or fiddle with config files etc.
It works from both your home WiFi and from anywhere in the world with just one configuration. 

So let's get it set up !

 {{< figure src="overview.png" >}}


## Step 0 : Update your AVADO

This tutorial assumes that your AVADO is up to date with all latest package versions. 
Go to [https://ava.do/start](https://ava.do/start) to check if your AVADO is up to date, or install available updates.

## Step 1 : Install package

You can find the "Remote Connect" package in the [DappStore](http://my.ava.do/#/installer).
- In the DappStore, the name is "Remote Access".
- Once installed the system name is "remoteconnect.avado.dnp.dappnode.eth".

Press the install button and let it finish.

## Step 2 : download a client for connecting

Meanwhile - you can download the remote connect client for your device and install it

- [Windows](https://download.zerotier.com/RELEASES/1.6.6/dist/ZeroTier%20One.msi)
- [MacOS](https://download.zerotier.com/RELEASES/1.6.6/dist/ZeroTier%20One.pkg)
- [Android](https://play.google.com/store/apps/details?id=com.zerotier.one)
- [iOS](https://itunes.apple.com/us/app/zerotier-one/id1084101492?mt=8)

## Step 3 : go to the configuration wizard

Go to [http://my.ava.do/#/Packages/remoteconnect.avado.dnp.dappnode.eth](http://my.ava.do/#/Packages/remoteconnect.avado.dnp.dappnode.eth)

You will see your unique network ID - and a default network name.
(Tip: You can click the network name to change it - so you can organize if you have multiple AVADO's)

 {{< figure src="id.png" >}}

Use the icon next to the AVADO network ID to copy it to your clipboard

## Step 4 : join your personal AVADO network with your client

Next step is to paste this network ID into your client.

### MacOS instructions

You will find an icon in the top bar of your desktop - Click on the icon to open the configuration menu

 {{< figure src="macos-join1.png" >}}

enter the networkID of your AVADO and press **Join**

 {{< figure src="macos-join2.png" >}}

{{< hint type=important >}}
Make sure to check the **Allow Global** and **Allow DNS** checkboxes or things will not work.

{{< /hint >}}

### Windows instructions

Click the orange icon to get the pop-up menu and select **Join Network**

 {{< figure src="win-join1.png" >}}

Enter the networkID of your AVADO and press **Join**

 {{< figure src="win-join2.png" >}}

{{< hint type=important >}}
Make sure to check the **Allow Global** and **Allow DNS** checkboxes or things will not work.
{{< /hint >}}

### Android instructions

Install the ZeroTier One app from the Google Play Store. Once opened, click on the + to join a network. Input your Avado network ID at the top and select Network DNS. Then click at the bottom to add network. Make sure you enable the connection in the remote connection package on the Avado as described in Step 5. Then just click on the slider in the app to connect to your Avado and use your browser to confirm that you can access tha Avado dashboard at my.ava.do.

{{< figure src="screenshot_20220103-172121_zerotier_one.jpg" height=500 >}}
{{< figure src="screenshot_20220103-180020_zerotier_one.jpg" height=500 >}}



### iOS instructions

See Android instructions above it works the exact same way!

TODO : if you want to add instructions and screenshots click the edit button above.


## Step 5 : enable client access on the AVADO

Go back to your AVADO. After a few seconds you will see the new client automatically appear in the network member list.

 {{< figure src="device-shows-up.png" >}}

The only thing you need to do now is check the box to enable access to this client.

 {{< figure src="enable-and-rename.png" >}}
{{< hint type=tip >}}
 You can click the **description** to rename your device to a name that you can easily remember the device that you gave access to. 
{{< /hint >}}


## Step 6 : Switch back to your home WiFi

Before trying it out : 
- if you are connected through the AVADO VPN: **disconnect from the VPN**
- if you are connected through the AVADO WiFi: **switch back to your home WiFi**.


## Step 7 : Connect through the Remote Connect client

After you disconnected from the AVADO VPN and/or switched back to your home Wifi - now it's time to connect your device to the AVADO network.

Click on the connection so that it has a checkmark in front of it. If you click on **Network Details** you should see "OK" next to the status.

 {{< figure src="screenshot_2021-12-14_at_14.25.25.png" >}}

{{< hint type=important >}}
If you see **REQUESTING_CONFIGURATION** please give it a minute or 2 to switch to "OK".

{{< /hint >}}

{{< hint type=important >}}
If you are using the Remote Connect method - please use the url **http://my.ava.do** instead of the old http://my.avado/ since the old URL will not work on this connection.

{{< /hint >}}


## Step 7 : disconnect and reconnect

From the client - you can turn off the active connection by clicking the selected network , the checkmark will disappear and you are disconnected.
To reconnect later - just click the network again. When the checkmark is present you are connected again !

 {{< figure src="disconnect.png" >}}

You can use this connection from within your own network, or from anywhere in the world. All traffic over this connection is peer-to-peer and is fully encrypted.

## Troubleshooting


In case of trouble - reach out on [Telegram technical support channel](https://t.me/joinchat/IR7AXecB5s4wZDPk) 





