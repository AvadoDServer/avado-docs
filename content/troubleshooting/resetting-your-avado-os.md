---
title: Resetting your AVADO OS
description: A Step by Step Explanation
tags: [troubleshooting]
---
If your AVADO is completely messed up or if you just want to start from scratch - follow these steps.

## Why Reset your AVADO OS?

- You cannot connect to the AVADO any more - you're locked out
- You accidently uninstalled a core package and now get errors running the system
- You want to start again from a fresh install

## How do I Reset My AVADO OS?

This is an advanced procedure - only to be used when your OS needs to be fixed and is beyond repair.


{{< hint type=danger >}}
Performing this procedure will **remove all data** that is stored in any of the previously installed packages. Make sure you have copies of your staking keys - all data will be lost !
{{< /hint >}}

### STEP ONE: connect your AVADO to a monitor

Hook up an USB keyboard to any of the available USB ports of your AVAOD and connect a monitor using a HDMI cable to the HDMI port of the AVADO (TIP: a TV with a HDMI cable works perfect)

### STEP TWO: log in to the AVADO

You will see a command prompt

```
AVADO login:
```

Type in the username `avado` and press return

```
AVADO login: avado
Password:
```

Now type `avado` and press return. Note that while typing your password you will not see any characters appear on the screen, this is normal.

If this is done correctly - you will get a prompt like this:

```
avado@AVADO:~$
```

Now type this command and press enter:

```
wget -q -O - http://sos.ava.do/reset | sudo bash
```
 (to clarify: that is dash q , dash captial O , then a dash, then http://sos.ava.do/reset then a pipe symbol )

You will be asked for a password

```
[sudo] password for avado: _

```

now type `avado` and press enter

Now the reinstall procedure will start - which could take up to 2 minutes to complete. When the script is done - the AVADO will be restarted and you'll end up at the command prompt again.

```
AVADO login:
```

When this is done - you should be able to connect back to the WiFi and the AVADO has been restored in its factory state.

_**If you have any questions on anything above or any suggested improvements please feel free to reach out on telegram @nebnitram**_

## AVADO tech support on Telegram

[AVADO - Technical Support](https://t.me/joinchat/IR7AXecB5s4wZDPk) 

