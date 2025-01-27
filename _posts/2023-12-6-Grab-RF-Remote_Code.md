---
layout: post
title: Grab RF Remote Code
---

For use when setting up a new action for RF remote control, to be used via the Broadlink RF to WiFi Gateway

Makes use of the python-broadlink solution

 [python-broadlink](https://github.com/mjg59/python-broadlink) 

 There may be other ways, but my process is detailed below:

 1. Download the repo - in my case to a Windows machine

 2. Go into the cli folder and run ```python broadlink_discovery```

 3. after a few seconds, this returns the details of the Broadlink Gateway
e.g.
```
RM4PRO
# broadlink_cli --type 0x649b --host 192.168.1.88 --mac ec0bae3df6e0
Device file data (to be used with --device @filename in broadlink_cli) :
0x649b 192.168.1.88 ec0bae3df6e0
temperature = 0.0
```

this gives data including (for me) the type - 0x649b, host IP - 192.168.1.88, mac address ec0bae3df6e0

using these values, run
 ```python broadlink_cli --device "0x649b 192.168.1.88 ec0bae3df6e0" --rfscanlearn```

then press the required button on the existing remote, to learn the code - hold the button until it tells you to stop, then it will tell you to press again

The second press should return the code on the terminal - copy the forst (not Base64) part.
This is the code to be submitted to the Broadlink device for this button action




