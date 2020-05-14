---
layout: post
title: PackUBIEST - a GPS tracker for my backpack
date: 2017-11-02 00:00:00 +0300
description: My first PackCTRL project was stolen and I had to make sure I'd be prepared if it happened again. # Add post description (optional)
img: packubiest.jpg # Add image post (optional)
tags: [GPS, Arduino, PackCTRL] # add tag
---
This project is part of the [PackCTRL project]({{site.baseurl}}/_posts\2017-11-01-packctrl-not-your-regular-backpack.markdown), and reading it first is a good idea.

If you read it, you know why I wanted to add some security to my backpack. Short version: the first one was robbed.

So I started the PackCTRL 2.0 project with the strong desire of adding some secruty features. After thinking about built-in tasers and siren alarms, I decided to develop a GPS tracker. Modest and safe.

## PackUBIEST
The GPS tracker was named PackUBIEST based on _ubi est?_, which translates from latin to "where is it?"
In it's final version, it had 2 main features:
- SMS based communication system;
- GPRS _real-time_ communication system;

### Hardware
To build the tracking device, I needed a programmable device with SMS, GPRS, GPS and battery management capabilities. After some research, I discovered Linkit One, by Seeed Studio, an Arduino-like board with everything I needed in it.

The power for PackUBIEST was separated from the rest of the backpack power storage, but still shared its charger. I was composed by 2x 18650 cells a 5V charger. At first, it had also an induction charger, which was removed due to safety issues - it was getting too hot!

Everything was enclosed in a small 3D printed box, which I'd hide inside the internal modular panel of the PackCTRL.

With this configuration, I could get up to 3 days of GPS tracking before recharging the module again, and I could still use other PowerBANKs to boost the PackUBIEST duration.

### SMS Communication
So the foundation of the communication system was based on SMS messages, as a _reliable_ method. PackUBIEST would react to commands from a single authorized master number.

To become its master, one should send it the command `Auth`. The module would react, asking for the password. If it receives the correct password in the next minute, the new master is registered.

Being its master, there are a few commands available:
| Command | Response |
|---+---|
| Juice? | Battery left, in percentage. |
| Check | Tests connection to sattelites and answers the amount found |
| Where? | Returns a link to Google Maps with a pin on the current location |
| Activate | Enters real-time mode |
| Deactivate | Exits real-time mode |


### Real-Time Communication
Coming soon.