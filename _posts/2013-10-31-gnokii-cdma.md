---
layout: post
title: "Using Gnokii with a CDMA Modem"
description: ""
category: "Linux"
tags: [gnokii]
---
{% include JB/setup %}


Traditionally we used a GSM modem to send out nagios notifications, but since the GSM modem only supports China Mobile's GSM card, and for some reason we need to replace the card with a CDMA card from China Telecom, I decided to buy a CDMA modem for that. 

So I searched on taobao because in China that's the place to find gadgets like that. Unfortunately none of the retailers is sure if the CDMA modem they sell is compatible with Linux, and they have no idea what kind of chip is used in the modem. However, I had no choice but to buy one of the modems that looks like the GSM modem we were using, hoping that my Linux box would support it.

This afternoon the modem was delivered. So I plugged it in and ran `dmesg | tail` and `lsusb` to check if the device is supported. Luckily the chip was recognized at once.

<pre>[142658.680202] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
...
Bus 003 Device 004: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
</pre>


I tested it with minicom. It was smooth. `ATD<my_number>` rings the bell of my mobile phone. Here's my serial port setup:

        +-----------------------------------------------------------------------+
        | A -    Serial Device      : /dev/ttyUSB0                              |
        | B - Lockfile Location     : /var/lock                                 |
        | C -   Callin Program      :                                           |
        | D -  Callout Program      :                                           |
        | E -    Bps/Par/Bits       : 9600 8N1                                  |
        | F - Hardware Flow Control : No                                        |
        | G - Software Flow Control : No                                        |
        |                                                                       |
        |    Change which setting?                                              |
        +-----------------------------------------------------------------------+

And the gnokii configuration file in /etc/xdg/gnokii/config

    [global]
    # port = see below
    model = AT   # or AT-HW to use hardware handshake
    connection = serial
    port = /dev/ttyUSB0
    serial_baudrate = 9600
    use_locking = no

