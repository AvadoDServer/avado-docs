---
title: Move ETH2 validators to a new location
description: Move ETH2
---

## READ AND UNDERSTAND BEFORE ATTEMPTING

1. This is the process I used and it worked perfectly for me but you must understand what you are doing and the risks involved if you don’t follow the steps correctly. You can get slashed and loose ETH if you are not careful.
2. YOU MUST WAIT AT LEAST 5 FINILIZED EPOCHS (currently about 30 minutes) BEFORE IMPORTING YOUR KEYS TO THE NEW LOCATION AFTER YOU SHUTDOWN THE VALIDATOR PACKAGE IN THE ORIGINAL LOCATION OR RISK BEING SLASHED!!! (I waited 10 FINILIZED EPOCHS just to be extra safe)
3. You must be certain to fully remove the validator & Beacon chain packages from the original location BEFORE you import your keys into the new location. If you do not and the same keys end up on two different live validators, you will be slashed and loose ETH
4. These steps will work to move validators from one Avado to another Avado or to a DAppNode. I have tried both. These steps are ONLY for these 2 scenarios.

## Moving ETH2 Validators to a new location

Step 1 – The NEW location where you want to move your validators to must be fully setup and ready to import your keys. GETH and Beacon chain must be fully synced in the new location and the validator package installed.

Step 2 – Shutdown the validator & Beacon chain packages where your ETH2 validators are currently running.

Step 3 – Uninstall the validator & Beacon chain packages. BE SURE TO ALSO REMOVE ALL DATA VOLUMES.

Step 4 - Now you MUST wait a minimum of 5 FINALIZED epochs before moving and importing your Keystore files to the new location

Step 5 – Once you have waited at least 5 FINALIZED epochs it’s the same process as when you originally setup your ETH2 validator, just in the NEW location.

Step 6 – From here you can follow the same instructions from the Avado wiki setting up ETH2 staking, start at Step 5.1

Reach out on [Telegram](/support/telegram/#staking-support) if you have questions.