---
title: "A proper adapter removes noise from your (PicoPSU powered) console"
layout: post
tags:
- games
- retro
date: "2018-11-29 10:00:00"
apps: [denied]
---

I fitted my Japenese SEGA Saturn and Dreamcast with [a PicoPSU](https://tekeverything.com/what-is-a-pico-psu/). The [relatively simple operation](http://www.mmmonkey.co.uk/dreamcast-psu-using-picopsu/) replaces the 110V power supply with a much more flexible output that will take any third-party 12V 5A power supply with a 5.5mm/2.5mm barrel connector.

![A front-facing photo of a PicoPSU, courtesy of tekeverything.com](/assets/blog/pico-160xt-psu-1.jpg)

The alternatives are:

* A step-down converter.
* A PAL power supply in an NTSC console. 

I've used both options and they're not ideal. The step-down converter is noisey and it always bothered me that I could just stick a 220V wire into my 110V console if I wasn't careful. Frying it in the process.

Replacing the 110V power supply with a 220V board from a PAL console is much more convenient. The downside here is price though; you need a donor console that will sit idle, powerless so to speak...

The PicoPSU is the ideal solution then. It really can be, but it the outcome depends on the third-party power supply.

After I installed the PicoPSU in the Saturn, I was quite impressed with the result. It worked fine. The Dreamcast wasn't such a success. The screen was filled with a very odd type of noise: square blocks all over the screen. Nothing I tried could remedy it. Closer inspection of the Saturn showed the same effect, but much less pronounced.

It wasn't until I read on a forum that the power supply could have something to do with the interference, that I tried a different power supply. The adapter from my external Seagate hard drive had about the correct specifications. When I tried it with the Dreamcast, I was stunned. The picture was crystal clear. No disturbances anywhere.

The stories are true then: you **need** good quality power supply, or you won't get the most out of your PicoPSU.

I got two ['LEICKE Power Supply Charger 60W 12V 5A 5.5 * 2.5 mm'](http://www.leicke.eu/en/products/NT03012) and they're perfect. You can [get the LEICKE power supplies here](https://www.bol.com/nl/p/leicke-voeding-60w-12v-5a-5-5-2-5mm-voor-lcd-tft-scherm-led-strips-nas-ext-vaste-schijven-voor-pico-psu-tot-60w-hoog-rendement-stand-by-0-7w/9200000095019486/). 

![Leicke 60W 12V 5A product photo](/assets/blog/leicke-12v-60w.jpg)

### SEGA Mega Drive

The 16-bit console is a different story, sort of. There's no need to replace the internal power supply, but there's also an external power brick. My Japanese Mega Drive has an annoying humm when the screen is mostly dark. I blamed the SCART cable first, but even [the cable I got from retrogamingcables.co.uk](https://www.retrogamingcables.co.uk/sega/mega-drive-1/sega-mega-drive-1-sega-genesis-1-stereo-rgb-av-scart-cable-tv-lead) has the issue.

Could the power supply I'm using be at fault here as well? Well, I think it can.

The one I'm using now outputs 1 ampere, which is just shy of the required 1.3 ampere. From what I'm seeing online [this could result in a buzzing noise while playing](https://www.youtube.com/watch?v=vOUA8dESHsE).

~~Getting a replacement [9V 1.3A 'center negative' adapter with a 5.5mm/2.1mm barrel](http://www.sega-16.com/forum/showthread.php?24832-Genesis-model-1-32-X-Sega-CD-model-1-Correct-power-supplies-and-polarities&p=580173&viewfull=1#post580173) isn't as easy as getting a 12V 5A brick though, if you discard the modular variety. After some browsing around I discovered that many guitar effect pedals use the same type power supply. The [Rockpower 50 NT](https://www.bax-shop.nl/gitaareffect-voeding-adapter/rockpower-50-nt-eu-combo-pack-9v-adapter) seems to fit the bill perfectly.~~

*I forgot to check Retro Game Supply. They [sell a very nice Mega Drive/Genesis power supply](https://en.retrogamesupply.com/collections/sega/products/power-supply-for-sega-megadrive-genesis-1) for even less than the one I found earlier.*

~~I'll let you know if it resolves the buzzing when it arrives.~~
The buzzing has disappeared with the new power adapter. 🎉
