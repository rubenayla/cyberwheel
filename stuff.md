# Reasoning for main location of components -- General configuration
The **inside chassis** of the EUC must hold its own weight, and it won't be subject to crashes or sudden crashes, since the rubber and rim separates it from the ground, and the internal components from crashes around it.

Therefore, a strong and heat conductive material is ideal, not necessarily tough. The sides will be flat, probably with velcro to put pads in any way.

For prototypes with pedal hangers, it will go over them. Like this the geometry is much simpler, the weatherproofing is better, and the motor can be dissassembled much more easily. For large bearing motors, the chassis will be the pedal hanger.

To gain maximum crash resistance, squishy stuff on the outside + rigid stuff inside is ideal, since nothing will penetrate the EUC and the acceleration will be softened. The pads will act as bumpers.

The **outside shell** of the EUC must be optimized for crash resistance, not strength. This highly suggests using GFRP or similar (Fire resistant epoxy?). It should be thermally reflective outside, and insulating, so the battery doesn't get cooked by the sun.

The **Front** will have lights. Since it needs a transparent material with power inside, it's ideal for the antennas too.

At **Top-front** there will be a handle. The handle could be the hinge for a bigger lever that also serves as kickstand and lock. You open it and click it closed around a lamp post or something. Could be two stacked frames like _, that can rotate to form /\, a triangular truss. Rigid grabbing point and good lock to leave it in the street.

The top should be seat-shaped so this could create a conflict.

**Back-down** needs a mudguard. A place for license plate, other info like phone number, and lights.

**Back-up** is the best place for charging ports, since it's the most protected from rain, and unoccupied by other components.

Large in x direction, since we'd need mudguards anyway.

# Observations
- Vents to relieve pressure during fire, while preventing oxygen and water from entering.
- If 60 4Ah Li-Ion cells release all their energy to an 8kg aluminum chassis, it would heat to ~464ºC without melting (Al melts at 660ºC)
    - $\Delta T = \frac{E_{bat}}{m_{Al}*cp_{Al}} = \frac{60*3.7V*4Ah}{8000g*0.9J/gK} = \frac{888 Wh * 3600J/Wh}{7200J/K} = 444K$
- Cascading PIDs
    - use 2 pid loops. One controls the vehicle rotation speed (rate), the other vehicle attitude (angle). This is how many multirotoros (copters) fly, and this is probably the mode that will bring the most stability. It may feel very different in onewheel configuration, not sure if many people like it or not, but this mode can make unicycle pedals feel very hard. 
    - the main (rate loop) does not depend on IMU. It reads RAW gyro data. So less susceptible to IMU tuning, numerical errors, accelerometer noise and jitter.
    - Angle loop depends on IMU, but has much less input.

# Other preferences
- Big inclined pedals inspired by nylonove
- The lighting must be uniform (more light at horizontal angle, to cover more area with uniform brightness), with a servo that takes the angle from the IMU and keeps the lights pointing forwards. https://youtu.be/UxABxSADZ6U
- Wheel easy to remove, downwards, with part of the arm screwed. Disconnect the cables in an accessible place and pull them down.
- Handle + Locker + Kickstand + Mudguard all at once
- Don't screw into plastic.
- Field Oriented Control (FOC) instead of BrushLess DC. No noise more efficiency.
- Connectors
    - XT90S
    - Molex Pico-Clasp (small, locking, populate as many pins as you want)
    - JST-PH (or XH. PH has more reliable pin insertion)

# Consider in the future
- **If a resistor is added to dump energy instead of regen, the euc will work at temperatures of 60ºC instead of 45ºC (Look [MolicelP42A Datasheet](./datasheets/INR-21700-P42A_datasheet_detailed.PDF))**
- Company: Safe environment and create provoked cutoffs, learn to fall
- Built-in dashcam
- Utilizar la placa principal como cargador? No necesitar placa extra. Hay un coche eléctrico que lo hace.
- Imagine a wheel with an axial flux motor at each side, and a controller board for each motor, working in parallel. Redundancy. If one fails, the other continues working, and the wheel leans back to slow down to a safe speed.
- Recognize when there's no rider (EUC flying alone), and slow down until it stops, instead of just balancing.
- Reverse leanback for breaking
- Tiny wheels to prevent falls after cutoff of normal EUC?

For a redundant system, wheel with 2 hub motors in it, with 2 controllers and batteries, fully independent systems working in parallel. If one fails, the other continues. Even if it fails with short-circuit, motor fuse of the fail side blows (shortcircuit creates a lot of current), while the other compensates and continues.

- Redundant electrical system: computer and power supply, maybe even motor coils (two motor windings in one motor structure, temperature of one doesn't affect the other)
- Storage compartment with small door lock (key or software controlled), to store things in the EUC and leave it locked to a tree or streetlight.
- Hollow bearings?
- No-power mode: when there's no battery available (BMS failure, short, bad contact, etc), go into a mode where balance is done just braking. Power to resistors or the motor itself, no battery.
- Electrically isolated tab gallium nitride mosfet?
- Haptic notification through the pedals when overpower or overspeed.
- Design the shell as a side pad? I don't think so. Flat metal and add pads over it.
- Fingerprint on switch?
- Blinkers on the pedals with buttons over the wheel?
- IMPORTANT, LONG TERM: WHEEL WITH DUAL HUB MOTORS, COILS AT EACH SIDE, DUAL VESC WITH DUAL PROCESSOR, DUAL BATTERY. REDUNDANCY AND BETTER CUTOFF TOLERANCE. VERY RARELY EUC FAIL STUCK. THEY FAIL OFF.


---
# Appendix
- Acronyms
    - EUC: Electric UniCycle
    - SOC: State Of Charge
    - ESC: Electronic Speed Controller
    - VESC: Vedder Electronic Speed Controller
    - BMU: Battery Management Unit
    - BMS: Battery Management System, BMU + switch to disconnect battery
- Reference system: X forwards, Y left, Z up.
- Dimensions:
    - Small hexagon: 30x41(25)
    - Big hexagon: 520 width x 400 height x 300 upper side
    - 18mm of lip to screw and seal the lid is enough.
    - 13cm max width at knee height. (->120mm)
    - Normal 16S battery thickness (with bms and stock padding): ~24mm
    - 2 layers of 2170 cells hexagonally packed mesaure: $21mm*(1+\sqrt(3)) = 39.2mm$
    - Wheel space of 74mm -> comaptible with 2.75in tyres, about 70mm wide. I want ~60mm wide, between 2 and 2.5 inches.
    - EUC Width (Distance between legs): About 24cm with padding, 20cm the bare EUC.
        - ![https://content.invisioncic.com/r254450/monthly_2021_09/Extreme-Dimensions-Weight-Comparison-v1.2-1200x851.jpg.7cdc2a8b0f7762dcdecbe4cc21f60eb5.jpg](ueuc/20230712203853.png)
    - Pedal height: about 6.5in = 165mm

- Cell Resistance $>100m\Omega$ -> it's bad.
- LFP voltage range: 3.2V nominal, 2.5-3.65V, 2.6-3.6V, 3-3.2V, 
- At the knee, max 13cm distance.

- To have bidirectional USBC charging: **LTC4160*- but the battery is 100V. It's not worth it to be able to charge the unicycle through the bidirectional USB-C PD
- King-Song S22 mosfet package: TO-247
- 4AWG butt connector (crimped)

- Good batteries (high charge rate)
    - **molicel p42a**
    - **Samsung 40t**
    - litech
    - Samsung inr40t

# Protection gear
- [Wrong way full guide](https://youtu.be/KuLZsmgloxY)
- Wristguard
    - 	**[Decathlon](https://www.decathlon.co.uk/p/fit-adult-inline-skating-wrist-guards/_/R-p-6032?mc=8495083)**
    - 	[Ennui](https://www.skatepro.com.pl/116-11108.htm?stockcode=920017)
    - 	[Gloves with wristguards](https://www.gyroriderz.com/products/gants-gyroriderz-avec-proteges-poignets-integres-2-0?lang=en)
- 	Full face downhill helmet (more visibility and lighter than motorcycle). Goggles with 2 layers of glass to prevent fogging, and removable glass.
- 	Downhill kneepads
- 	Mountaineering shoes
- 	Hand mirror

# 
- Iterar, validar, ágil
- El software pensaba basarlo en el proyecto VESC, que está disponible en GitHub, de código abierto, y se podrían hacer mejoras sin empezar desde cero, teniendo electrónica compatible.
- Luego hay cuestiones de seguridad relacionadas con la batería. Si se prioriza la seguridad de la batería, puede haber cortes de potencia que hagan peligrar al piloto, y viceversa
- Use the chassis for cooling. 8kg of aluminum with heatsink in wheel hub and giant wheel moving air. Tape the heatsink in winter if the temperature gets too low.
- use this fuse? Fuse (135A max peak, allow it for 60 seconds, 270A for 1S)
    - UL Class T fuse 300VAC 200A (High-current, fast acting)
- Tienda hacen baterias: https://es.wallapop.com/user/hgomezh-426221412

#
Batería mide 30x9x11, con una caja de esas dimensiones internas me cabe. Algo de margen y poco espumita.
Caja de vino de madera, milwaukee de plastico adaptada, tubo cuadrado pvc 120mm