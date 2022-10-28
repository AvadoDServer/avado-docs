---
title: Connection troubleshooting
aliases: ["/en/troubleshooting/connection-troubleshooting"]
---

# Help - I cannot connect to my AVADO!

## Checklist for the AVADO / Router connection

### Network lights are blinking ?

Make sure that the network lights are ON and blinking on the AVADO.
The network lights are the orange and green LED's next to the network plug on the AVADO device. Usually one of the two blinks while the other is on permanently.

### Change router port

If any reconfiguration on the router has been done, it sometimes helps to plug in the network cable into a different free network port on your router. This will trigger the router and the AVADO to re-negotiate their network connection and might solve connectivity issues.

### Swap the network cable

Swapping out the network cable for another one also has been reported to help in the rare case that you have a faulty cable.


## Checklist for MAC

### Disable VPN software

Disable VPN software you might have running on your computer like
- NordVPN

### Check your network settings

On your MAC go to `system preferences` -> `network`

You should see the Wi-Fi connection to the AVADO network (in this screenshot it is renamed to AVADO-i5 - yours will be called AVADO by default)
 {{< figure src="2022-06-02_11.34.34.jpg" >}}

Then click on the `Advanced` button and verify if you have an `IPv4 Address` that is in the rance `172.22.12.xxx`

 {{< figure src="2022-06-02_11.34.43.jpg" >}}

Then go to the `DNS` tab and verify if you have exactly this setting. there should be only one DNS server and it should be `172.33.1.2`

 {{< figure src="2022-06-02_11.34.51.jpg" >}}

If all that is the case you should be able to access the http://my.ava.do/ URL that leads you to the AVADO admin page.
