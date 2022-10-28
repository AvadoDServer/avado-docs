---
title: Manually opening network ports on the AVADO
description: Manually  opening ports on your router to your AVADO
aliases: ["/en/troubleshooting/manually-opening-ports"]
---

Certain packages - like blockchain nodes - usually need to open a couple of ports on your router to work well. 

The AVADO OS is be able to open specific ports on your router - so this should happen automatically, but not always: if your router is not set to accept these configurations through uPNP - then you need to open ports manually, and that is what we'll explain here.

## Prerequisite : find out the internal IP address of your AVADO

Go to the AVADO admin UI - and click on the avatar image (the green circle in this picture) you'll get a popup. Take note of the "Internal IP" - we will need it later.

![portforwarding-step0.png](portforwarding-step0.png)

## Open your router's web UI

Find out how to open the web-UI of your router by looking in your router's manual, by looking the website of your ISP or by contacting your ISP's  support. Here we will explain  how to do  this on a Fritzbox 7530. Your brand may vary - and there is a generic tutorial on port forwarding here: https://www.purevpn.com/blog/how-to-forward-ports-on-your-router/#How_to_setup_Port_Forwarding_on_your_router 

## Add device for sharing
Go to internet -> permit access
click on "add device for sharing"
![portforwarding-step1.png](portforwarding-step1.png)

## Select your AVADO box and add sharing

Then select your AVADO from the dropdown list (verify if the IP address displayed corresponds to your internal IP address you looked up in the first step) and click "New sharing"

![portforwarding-step2.png](portforwarding-step2.png)

## Add port forwardings

Fill in the ports that you  want to forward. In this case we're trying to open ports 30303/TCP and 30303/UDP which are the ports for your Ethereum node (Geth)

![portforwarding-step3a.png](portforwarding-step3a.png)

and for the second port

![portforwarding-step3b.png](portforwarding-step3b.png)

## confirm port forwarding settings

You'll arrive back at the oveerview screen - press "OK" to confirm these settings

![portforwarding-step4.png](portforwarding-step4.png)

## Verify settings

And an overview to you can see that all is done correctly.

![portforwarding-step5.png](portforwarding-step5.png)

Congratulations ! Ports are now forwarded to your AVADO!