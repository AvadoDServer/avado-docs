---
title: Reinstall the IPFS package
description: IPFS package
date: 2022-09-15T10:45:25.387Z
tags: [ipfs]
dateCreated: 2022-09-14T17:23:42.925Z
---

# I removed my IPFS package, what now ?

The IPFS package is an essential package.  Without it, packages can't be updated NOR can you load the dappstore/install new packages.



This guide will help you reinstall the ipfs package.

Connect your Avado using an ssh connection or attach a screen & keyboard.Once a console is presented, enter the system with login/passwd: avado/avado

Then navigate towards te folowing path, using command:

```bash
cd /usr/src/dappnode/DNCORE/
```

Once there we will unpack the stock/default ipfs package, load it and start it. Type in: 

```
docker load -i ipfs.dnp.dappnode.eth_0.2.3.tar.xz && docker-compose -f docker-compose-ipfs.yml up -d
```

...output shows you something like this:

`>>IMAGE HERE<<`

Go back to the dappstore and update this stock version to the recent one.

`>>IMAGE HERE<<`







fyi: software versions could differ 