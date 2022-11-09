---
title: Connection troubleshooting
aliases: ["/en/troubleshooting/connection-troubleshooting"]
---

{{<toc>}}

## Checklist for the AVADO / Router connection

### Check if the network lights are on and blinking

Make sure that the network lights are ON and blinking on the AVADO.
The network lights are the orange and green LED's next to the network plug on the AVADO device. Usually one of the two blinks while the other is on permanently.

If this is not the case either plug your AVADO into another port of your router or try with another network cable.

### Change router port

If any reconfiguration on the router has been done, it sometimes helps to plug in the network cable into a different free network port on your router. This will trigger the router and the AVADO to re-negotiate their network connection and might solve connectivity issues.

### Swap the network cable

Swapping out the network cable for another one also has been reported to help in the rare case that you have a faulty cable.


## Checklist for MacOS

### Disable VPN software

Disable VPN software you might have running on your computer (like NordVPN). Even if you don't have an active connection, the software might still interfere with your remote connection software to the AVADO. If everything else fails - uninstall your VPN software to rule this out.

### Check your WiFi network settings

On your MAC go to `system preferences` -> `network`

You should see the Wi-Fi connection to the AVADO network (in this screenshot it is renamed to AVADO-i5 - yours will be called AVADO by default)
 {{< figure src="2022-06-02_11.34.34.jpg" >}}

Then click on the `Advanced` button and verify if you have an `IPv4 Address` that is in the rance `172.22.12.xxx`

 {{< figure src="2022-06-02_11.34.43.jpg" >}}

Then go to the `DNS` tab and verify if you have exactly this setting. there should be only one DNS server and it should be `172.33.1.2`

 {{< figure src="2022-06-02_11.34.51.jpg" >}}

If all that is the case you should be able to access the http://my.ava.do/ URL that leads you to the AVADO admin page.

## AVADO tech support on Telegram

[AVADO - Technical Support](https://t.me/joinchat/IR7AXecB5s4wZDPk) - there are many people with an AVADO in this channel that can help you troubleshoot your AVADO connection.



