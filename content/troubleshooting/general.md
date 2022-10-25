---
title: Reset/Retrieve WiFi password
description: I messed up ! Please help me
published: true
date: 2022-09-14T16:45:02.892Z
tags: 
editor: markdown
dateCreated: 2021-06-17T00:16:39.986Z
---

# WiFi problems 

## I changed my WiFi password or disabled it & locked myself out of my AVADO

You need to attach a screen and a keyboard to your AVADO
Get a USB keyboard and attach it to any of the USB ports of your AVADO
Find a screen with a HDMI cable (tip: use your TV if you don't have a monitor) and attach the HDMI cable to your AVADO. Make sure your AVADO is connected to the internet before proceeding.

You will see a login prompt
`AVADO login: _`

Login with username `avado` and password `avado`

If you simply forgot your password, you can find it by reading out the config file of the WiFi package.
At the console you type:

**cat  /usr/src/dappnode/DNCORE/wifi.dnp.dappnode.eth.env**

![terminal output wifi](wifi-cat.png)



If you can't login with the credentials as shown above, you should restart the container by typing in the folowing command:

**docker-compose -f docker-compose-wifi.yml up -d**

![terminal output wifi](wifi-docker.png)

Still no luck ? 

Download and install a fresh copy of the package, by typing in:

```bash
sudo apt-get install curl
```

It will then ask for a password. Type `avado` and press enter. The curl tool will be installed so you will see some output on the screen. Wait a minute for that to finish.

When you get back at the commend prompt, type the following command:

```bash
curl -s http://sos.ava.do/wifi | bash
```

and press enter





It should show something like 
```txt
Starting WiFi reset procedure
...
(then some more log lines)
...
OK - Wifi container restarted. Please try to reconnect to SSID=AVADO, password=avado123

```

Now you should be able to reconnect using the default password.

To exit the shell on your AVADO device - type "exit" and disconnect the keyboard & screen.

