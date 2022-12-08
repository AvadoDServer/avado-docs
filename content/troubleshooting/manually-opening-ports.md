---
title: Manually opening network ports on the AVADO
description: Manually  opening ports on your router to your AVADO
aliases: ["/en/troubleshooting/manually-opening-ports"]
---

{{<toc>}}

Certain packages - like blockchain nodes - usually need to open a couple of ports on your router to work well. 

Adrian Sutton from the Teku team wrote a great blog post about this: <https://www.symphonious.net/2021/08/14/exploring-eth2-why-open-ports-matter>

The AVADO OS is able to automatically open specific ports on your router via [UPnP](https://en.wikipedia.org/wiki/Universal_Plug_and_Play).
If UPnP is not enabled on your router, you need to open ports manually. The process is explained on this page.

## Avado Ports

| Dapp                   | Port     | Protocols |
|------------------------|----------|-----------|
| Geth (mainnet)         | 30303    | TCP/UDP   |
| Nethermind (mainnet)   | 40303    | TCP/UDP   |
| Nethermind (Gnosis)    | 30305    | TCP/UDP   |
| Prysm Beacon chain (mainnet)        | 12000    | UDP       |
|                        | 13000    | TCP       |
| Teku (mainnet)         | 9000     | TCP/UDP   |
| Teku (Gnosis)          | 9006     | TCP/UDP   |
| Qtum                   | 3888     | TCP       |


## Find out the internal IP address of your AVADO

Go to the AVADO admin UI - and click on the avatar image (the green circle in this picture) you'll get a popup. Take note of the "Internal IP" - we will need it later.

 {{< figure src="portforwarding-step0.png" >}}

## Open your router's web UI

Find out how to open the web-UI of your router by looking in your router's manual, by looking the website of your ISP or by contacting your ISP's  support. Here we will explain  how to do  this on a Fritzbox 7530. Your brand may vary - and there is a generic tutorial on port forwarding here: https://www.purevpn.com/blog/how-to-forward-ports-on-your-router/#How_to_setup_Port_Forwarding_on_your_router 

## Add device for sharing
Go to internet -> permit access
click on "add device for sharing"
 {{< figure src="portforwarding-step1.png" >}}

## Select your AVADO box and add sharing

Then select your AVADO from the dropdown list (verify if the IP address displayed corresponds to your internal IP address you looked up in the first step) and click "New sharing"

 {{< figure src="portforwarding-step2.png" >}}

## Add port forwardings

Fill in the ports that you  want to forward. In this case we're trying to open ports 30303/TCP and 30303/UDP which are the ports for your Ethereum node (Geth)

 {{< figure src="portforwarding-step3a.png" >}}

and for the second port

 {{< figure src="portforwarding-step3b.png" >}}

## confirm port forwarding settings

You'll arrive back at the oveerview screen - press "OK" to confirm these settings

 {{< figure src="portforwarding-step4.png" >}}

## Verify settings

And an overview to you can see that all is done correctly.

 {{< figure src="portforwarding-step5.png" >}}

Congratulations ! Ports are now forwarded to your AVADO!