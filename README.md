<p align="center">
  <img src="assets/isologo_white.png" alt="Cyberwheel Logo" height="100"/>
</p>

## Purpose
Make electric unicycles that are reliable for everyday use: waterproof, impact-resistant, durable over time, and easy to repair.

For this, create an open-source community to design both the Hardware and Firmware, so they can be repaired and modified, free of proprietary restrictions.

[Video Pitch: https://youtu.be/mN5FoosNMC0](https://youtu.be/mN5FoosNMC0)

## Current state
![](README/20250424212907.png)
TODO: Video. Waiting for laser-cut chassis to do new version and tune the PID.

## Why EUCs?
EUCs have a significantly bigger wheel than scooters (16 ~ 18"), which makes them more stable (yeah, It's hard to believe, but trust me), specially in rough terrain. They can go up curbs, down stairs, and sometimes even UP stairs. They're very pleasant to ride. Hands free, it feels like you're floating.

They're way easier to carry around, like a little suitcase, so you can use them to park your car in the outskirts of the city and ride the couple km left to your destination, skipping traffic and parking fees. For short trips, it might even replace your car. Current ones get easily to 90 km/h, and exceed 100 km of range.

## Goals
I want to challenge the idea that, if your EUC cuts out, it's your fault. A well designed EUC should never cut power, even if you try. There must be margin for error.

And this margin includes undervoltage AND overvoltage. Ideas to consider are resistor or motor coil short-circuit braking, instead of dumping to the battery when it's already full.

More on [requirements](./requirements.md).

## What's the problem with current EUCs?
Even though current EUCs are very cool and powerful, they're generally not resistant to crashes, the hardware and software is propietary, they can often be damaged by simple rain, can overheat easily with no sensors to prevent it, and have battery fires.

I want to design an EUC that you can trust and repair yourself.

I plan to use a sealed enclosure for the electronics and batteries, increase the redundancy when possible, increase the margins for error, and design the EUC so it's impossible to conceive a cutout as anything but a fatal error.

## Features
- Sealed electronics and battery compartment
    > You can throw it in the sea and won't have to worry about it.
- Use the chassis as a heatsink. Probably an aluminum chassis, or an embedded heat sink.
- The handle will serve as a kickstand, and will unfold to serve as a metal arm that can be used to lock the EUC to a pole. It will also serve as a seat.
- It will have the charger built-in
- Consider self-leveling light that calculate the slope of the road based on the motor current draw and adjust the angle with a simple servo.
- Battery pack with fireproof cover
- Easy to assemble and disassemble

## Target parameters for now
About 50kmh, 80kg rider, hill climbing, 18" or 16", 20s 84V, no suspension, hollow bore motor preferrably
> I think C38 or C30 motors match. Best is C38 high torque

## References
- Euc compare:
    - https://freshlycharged.com/euc-comparison-tool/
    - [EUC COMPARISON SPREADSHEET](https://onedrive.live.com/view.aspx?resid=5C7F7C96B9CB240D!453580&ithint=file%2Cxlsx&authkey=!AH72KLYXambSLHc&fbclid=IwAR0THVUZS6h6SZOj39XxWlnTjURvUr4NtPwmEg5kYFh51V8Ruyizmrrgx64)
- Buy EUC:
    - https://myewheel.com/
    - https://www.electricunicycles.eu/product_catalog
    - https://ewheels.com/pages/parts#products_categories_row_180
- https://forum.electricunicycle.org/topic/18154-i-made-a-custom-gotway-monster/
- To improve on nickel current collectors: https://cellsaviors.com/blog/copper-nickel-sandwich
- Check how his airplane is built, could take some ideas: https://www.youtube.com/@wairworthy/shorts
- VESC
    - https://vesc-project.com/
    - https://vesc-project.com/documentation
    - https://github.com/vedderb/bldc
    - [Balance App Info - VESC](https://vesc-project.com/node/2689)
        - https://t.me/joinchat/JP0KNxbguWM5KhHrT5_CYA
        - [VESC Balance Tutorial Playlist](https://youtube.com/playlist?list=PLHu3LpOcWhxyn11v0Hx8pvxD1ymyQL4SX&si=PjZiLmkFITcXCBZ9)
    - VESC Tool setup tutorial https://youtu.be/lDuV8cnPRmI
    - Understand how ESC works [https://youtu.be/YV-ee8wA5lI](https://youtu.be/YV-ee8wA5lI)
- Add safety: https://github.com/thankthemaker/rESCue
- https://www.instagram.com/eucyou?
- Fault code list: https://vesc-project.com/node/3941
- [Little FOCer V3.1 ESC 84V 20S](https://customwheel.shop/high-voltage-vesc-motor-speed-controllers/little-focer-v31-vesc-84v-20s-chassispanel-mount)

- Battery
    - [Build massive diy battery, high power, good construction](https://youtu.be/QMQYfk2RKtU)
    - [A very, very detailed video on how I built my battery pack for electric skateboard.](https://youtu.be/7QjO90LG67g)
    - https://secondlifestorage.com/index.php
    - https://inventuspower.com/custom-battery-packs/
    - https://medium.com/tianyechen-portfolio/formula-sae-electric-battery-management-system-df12e000f457
    - [FS NOTTINGHAM 2020 ACCUMULATOR](https://youtu.be/4xOo8Uv2nHw?si=mMkoztjvpohZPZ4r)
- https://www.thecotillion.theater/the-blerg-archive/2020/3/22/the-guide-to-electric-unicycle-maintenance-2020-edition

- https://www.instructables.com/DIY-Self-Balancing-One-Wheel-Vehicle/
- https://ieeexplore.ieee.org/document/7860971
- https://ieeexplore.ieee.org/document/7861046?section=abstract
- https://clarkpads.com/