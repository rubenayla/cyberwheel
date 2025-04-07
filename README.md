<p align="center">
  <img src="assets/isologo_white.png" alt="Cyberwheel Logo" height="100"/>
</p>

## Purpose
Develop an Electric Unicycle that is truly practical for everyday use: reliable, rain- and impact-resistant, and durable over time.

For this, create an open-source community to design both the Hardware and Firmware, so they can be repaired and modified, free of proprietary restrictions.

## Goals
I want to challenge the idea that, if your EUC cuts out, it's your fault. A well designed EUC should never cut power, even if you try. There must be margin for error.

And this margin includes undervoltage AND overvoltage. Ideas to consider are resistor or motor coil short-circuit braking, instead of dumping to the battery when it's already full.

More on [requirements](./requirements.md).

## Why EUCs?
EUCs have a significantly bigger wheel than scooters (16 ~ 18"), which makes them more stable (yeah, It's hard to believe, but trust me), specially in rough terrain. They can go up curbs, down stairs, and sometimes even UP stairs. They're very pleasant to ride. Hands free, it feels like you're floating.

They're way easier to carry around, like a little suitcase, so you can use them to park your car in the outskirts of the city and ride the couple km left to your destination, skipping traffic and parking fees. If you're not going to do large trips, it might even replace your car. Current ones get easily to 90 km/h, and exceed 100 km of range.

## What's the problem with current EUCs?
Even though current EUCs are very cool and powerful, they're generally not resistant to crashes, the hardware and software is propietary, they can often be damaged by simple rain, can overheat easily with no sensors to prevent it, and have battery fires.

I plan to use a sealed enclosure for the electronics and batteries, increase the redundancy when possible, increase the margins for error, and design the EUC so it's impossible to conceive a cutout as anything but a fatal error.







## Features
- Sealed electronics and battery compartment
    - You can throw it in the sea and won't have to worry about it.
    - Probably an aluminum conducting chassis, or embedded heat sink.



## References
- 
- [EUC COMPARISON SPREADSHEET](https://onedrive.live.com/view.aspx?resid=5C7F7C96B9CB240D!453580&ithint=file%2Cxlsx&authkey=!AH72KLYXambSLHc&fbclid=IwAR0THVUZS6h6SZOj39XxWlnTjURvUr4NtPwmEg5kYFh51V8Ruyizmrrgx64)
- To improve on nickel current collectors: https://cellsaviors.com/blog/copper-nickel-sandwich
- Check how his airplane is built, could take some ideas: https://www.youtube.com/@wairworthy/shorts
- [Balance App Info - VESC](https://vesc-project.com/node/2689)
    - https://t.me/joinchat/JP0KNxbguWM5KhHrT5_CYA
    - [Video Tutorial Series](https://www.youtube.com/playlist?list=PLHu3LpOcWhxyn11v0Hx8pvxD1ymyQL4SX)
- Euc compare:
    - https://freshlycharged.com/euc-comparison-tool/
    - https://onedrive.live.com/view.aspx?resid=5C7F7C96B9CB240D%21453580&authkey=!AH72KLYXambSLHc
- Buy EUC:
    - https://myewheel.com/
    - https://www.electricunicycles.eu/product_catalog
    - https://ewheels.com/pages/parts#products_categories_row_180
    - 
- Add safety: https://github.com/thankthemaker/rESCue
- https://www.instagram.com/eucyou?
- Fault code list: https://vesc-project.com/node/3941
