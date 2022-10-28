---
title: VPN Access
description: How to setup remote access to your AVADO using VPN
---

{{< hint type=warning title="OpenVPN access has been replaced by remote connect package">}}
Please continue to the [remote-connect](/tutorials/remote-connect) page to read the correct instructions how to connect to your AVADO.
{{< /hint >}}

# OBSOLETE: Setting up VPN (virtual private network) Access
This tutorial will help show you how to connect to your Avado using VPN through your local area network (LAN), or from a remote location when you are away from home! Being able to securely access your Avado dashboard through a VPN from anywhere you have an internet connection is an exciting and useful feature that comes built in to the Avado. It is recommended for all users of the Avado to set it up. Once you have your VPN configured, you can be proud that you are maximizing your privacy and using your Avado to take control of your information. Setting up your VPN is considered a best practice.

This tutorial will explain the basic setup for Windows 10, MacOS, or when using a mobile device running Andriod or iOS. 

## Step 0: Connect to your Avado WiFi network  
Once connected, navigate to http://my.avado/#/dashboard in your browser. If you are having trouble connecting to your Avado WiFi network for the first time, try reading the FAQ on connecting your WiFi here:
https://wiki.ava.do/faq#my-avado-box-is-not-connected-to-the-internet-what-can-i-do
https://wiki.ava.do/faq#wifi


## Step 1: Open the `Connect (VPN)` item in the left menu bar of your Avado Home Screen
After you have connected to the Avado WiFi and can access the Avado dashboard through the web interface, you can set up a VPN connection on whatever device you are connected with. You can set up VPN connections for all your devices if you like, such as your desktop/laptop and mobile device(s). Steps for setting up your VPN on various devices and operating systems are discussed below.

 {{< figure src="vpn_menu.png" >}}

When the Users menu opens, you will see a pre-configured user named `dappnode_admin`. Admin rights for this user should be set to on by default. It is recommended to add additional users for your desktop/laptop and mobile device(s). You can remove Admin privleges or delete access for individual users if needed for unfortunate events such as losing your device. :( 

 {{< figure src="users.png" >}}

To add additional users simply name the `user login` whatever you like and click `Add user`. **Be sure to turn on Admin privileges** for the new user so you can access your Avado through the web interface once you are connected to the VPN. 




## Step 2: Share the profile you wish to configure.
After clicking on `Share`, you will see three icons come up. Click on the download icon to access the page for the OpenVPN configuration files.

 {{< figure src="share_config.png" >}}



## Step 3: Download the configuration files for remote use and local (LAN) use.
After clicking on the download icon, a new page will load and there are buttons at the top of the page for downloading each of the configuration files. Go ahead and download both for local and remote use. Save them somewhere handy on your device and note the location of the files on your device.

 {{< figure src="download_config_2.png" >}}

## Step 4: **DISCONNECT FROM YOUR AVADO WiFi**
Once you have downloaded the Local (LAN) and remote configuration files, you should disconnect from the Avado WiFi network and re-connect to your home network. **This step is important and easy to overlook.** If you forget to disconnect from the Avado WiFi network and re-connect to your home network, when you try to connect with your VPN client in the next steps it won't work. :(

{{< hint type=important >}}
Make sure you disconnect from the Avado Wifi and re-connect to your home network or it won't work when you try to connect through VPN in the following steps.
{{< /hint >}}

## Step 5: Install your VPN client on the machine you would like to use. 

The following example is for the OpenVPN client for Windows 10. For instructions on installing OpenVPN for Android, see **Step 8**. For instructions on installing Tunnelblick on MacOS see **Step 9**. For iOS, see step **10**.

Navigate to https://openvpn.net/download-open-vpn/ in your browser and download the OpenVPN Connect client.

Once the installer has downloaded, run it and follow the prompts to install the OpenVPN client. You will most likely want to use all of the default settings during installation.

## Step 6: Connect your VPN using your Local LAN.

{{< hint type=tip >}}
**EASY VERSION:** Double click on the profile you downloaded and OpenVPN should be able to automatically import it. If not, proceed as below.
{{< /hint >}}

Open the OpenVPN application and click on the 3 bar menu icon in the upper left corner and then select `Import Profile`.

 {{< figure src="import_file_menu.png" >}}

Start by importing the Local (LAN) profile. Select `File` and then follow the prompt and drag the Local (LAN) file (*AVADO-VPN_local.ovpn*) into the window to import it.

 {{< figure src="import_file.png" >}}

Once you have imported the file, you will see a screen telling you that the file has been imported. Select the check box for `Connect after import` and then click on `Add.`

 {{< figure src="import_file_2.png" >}}

If you have followed the steps correctly and you are connected to your home network (not Avado WiFi), you should see the following screen indicating you are connected to your VPN. 

 {{< figure src="import_file_connect.png" >}}

You can now access http://my.avado/#/dashboard from your web browser while connected to your home network! :)

## Step 7: Connect your VPN using the remote profile.

Follow the instructions in **Step 6** above but this time, import the remote profile (AVADO-VPN.ovpn).

{{< hint type=tip >}}
**EASY VERSION:** Double click on the profile you downloaded and OpenVPN should be able to automatically import it. If not, proceed as below.
{{< /hint >}}

One way of simulating a remote connection scenario would be to connect your WiFi on your PC to your phone's mobile hotspot to access the internet away from your home network. Depending on the configuration of your router, you still may not be able to connect to the VPN using the remote profile. Don't despair. If the remote profile will not connect, you may need to set a port fowarding rule on your router for port 1194 UDP.

If you have never set up a port forwarding rule on your router it can be a little intimidating at first. It's not as hard as it seems. You can do it.

Instructions for setting a port forwarding rule on your router depend on the make and model of your router. Google the make and model of your router and you can find instructions on how to set a port forwarding rule for your specific router. This is example demonstrates how to set a port forwarding rule for a Motorolla router. Most routers operate in a similar way so hopefully you will find this example helpful. 

Begin by typing the address of your router into the address bar of your browser. In this example, the Motorolla router address is http://192.168.0.1/

Look for the `Advanced` tab and then the `Advanced Router` and `Forwarding` tab. Then select the `Add_IPv4` button.

 {{< figure src="port_forward_1.png" >}}

You will need to get your Avado Internal IP address to complete the port forwarding rule. To do this, open a new browser tab and navigate to your Avado dashboard (using your Local LAN VPN :)). Click on the computer avatar icon in the upper right corner. Copy the Internal IP.

 {{< figure src="avado_ip.png" >}}

Now go back to the tab with your router admin page. Paste your Internal IP in the Local IP box with a start and end port of 1194. Leave the External IP as 0.0.0.0 and the start port blank. Set the protocol to UDP and select `Enable`. Don't forget to hit `Save` to save the rule to your router. Then you can logout of your router.

 {{< figure src="forwarding_rule_1.png" >}}

Now you can go back to the OpenVPN client and attempt to connect the remote profile while using your phone's mobile hotspot and your PC to simulate a remote connection. If you have made it this far, congratulations!!

 {{< figure src="remote_connect.png" >}}

If after follwong the steps above, the remote profile will still not connect, you can open a command prompt on your PC and type `ping %externalhostname%` where %externalhostname% is whatever is there when you click on the computer Avatar in the upper right corner of your Avado Dashboard. For example: `ping 741...d66be5.dyndns.dappnode.io`, where 741...d66be5 is whatever is there. Hit enter and it should resolve to the External IP of your Avado. If it does not, please reach out for additional support on the Avado telegram page. If it does resolve to the External IP of your Avado, go back and ensure that you have followed all of the steps exactly. Make sure you have correctly set the port forwarding rule with the correct internal IP which is usually 192.###.#.# If you still can't connect through the remote profile, please reach out for support on the Avado telegram channel.


## Step 8: Using OpenVPN for Android
Hey, you are in luck. The recommended client for Andriod devices is OpenVPN and the setup is almost exactly the same as in **Steps 5 - 7** above. You can download OpenVPN for Andriod in the Play Store here:
https://play.google.com/store/apps/details?id=net.openvpn.openvpn


{{< hint type=tip >}}
**EASY VERSION:** Double click on the profile you downloaded and OpenVPN should be able to automatically import it. If not, proceed as below.
{{< /hint >}}


Once installed, open the app and add the profiles you downloaded in **Steps 2 & 3** by clicking on the `+` button in the lower right corner.

 {{< figure src="openvpn_droid_1.png" >}}

Then, select `File` to import the VPN configuration files that you downloaded. Browse to the location where the VPN configuration files were downloaded using the file explorer and then click on `IMPORT`. Do this for both the local and remote configuration files.

 {{< figure src="import_file_droid.png" >}}

Once you have imported both configurations, simply click on the local profile and it will connect and you can access your Avado in your browser.

 {{< figure src="connect_local.png" >}}

Repeat to connect your remote profile. Follow the instructions in **Step 7** to simulate a remote connection using your phone's mobile hotspot and to set a port forwarding rule on your router, if needed.

## Step 9: Using Tunnelblick for MacOS

Tunnelblick is the recommended VPN client for MacOS. You can download the latest stable release here:
https://tunnelblick.net/index.html

 {{< figure src="tunnelblick_dl.png" >}}

**EASY VERSION:** Double click on the profile you downloaded and Tunnelblick should be able to automatically import it. If not, proceed as below.

Open the Tunnelblick application and you will see a configuration screen. Select `I have configuration files`.

 {{< figure src="config_screen.png" >}}

Drag the configuration files you downloaded in **Steps 2 & 3** into the configurations window.

 {{< figure src="add_config.png" >}}

When you drag each file into the configurations window, it will ask you if you would like to install for all users or only me. That is your choice.

 {{< figure src="add_config_2.png" >}}

Then simply select the profile you would like to connect, starting with the local configuration. **Make sure you are connected to your home network and not the Avado WiFi**. Then click `Connect` in the lower right corner and a small window will pop up showing your successful connection.

 {{< figure src="connect_1.png" >}}

After you have successfully connected to the local configuration, follow the instructions in **Step 7** to connect your remote profile using your phone's mobile hotspot to stimulate a remote connection to your Mac and set a port forwarding rule on your router, if needed. 



## Step 10: Using OpenVPN for iOS

The VPN client for iOS is OpenVPN. Download it from the App Store and go back to **Step 8** because it works the same way!

# FAQ
Is it possible to operate AVADO with wireless only, or must it use ethernet?
=> Avado must be operated through network cable connection.

How do it test if my remote AVADO VPN connections is working?
=> You can test it with your phone, just disable wifi on your phone and see if you can connect to the remote VPN while using your mobile data

Anything specific that needs to be configured to get the remote VPN running? Haven‘t been able to set it up, it just won‘t connect.
=> The solution is (on some modems) to forward the UDP port 1194 on the modem that is connected to the router too. Than the VPN finally works remote.





