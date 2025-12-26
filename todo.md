user vs model parameters, difference? why they get added as user

check dimensions

Hacer el diseño en fusion 360
Diseñar y fabricar la tapa superior
Diseñar soporte para la batería y la electrónica

base datos con contactos, excel o algo. y de donde ha salido.
power ui? excel vale

validar coste y precios, prototipo y encuesta, contactos proveedores

create an about page in cyberwheel docs

configure pid with balance app (refloat doesn't work)
create video about the project

save vesc config in the release, or in stuff, at least

put the euc in fusion and add 3d printed designs to hold batteries and electronics in place.

comprar: aislante mosfet electronica

note all required connectors and stuff to buy


- buy Shrink wrap (transparent? inspect all cells, visible from sides)
    - perimeter (2170 cells): 4*21.7 + 4 * 70 = 366.8mm
    - width of flat roll before contraction > 183.4mm to fit

# Issues
- Can the chassis be done as a single laser-cut bent piece? What about rivetting several ones?
    - Airplane wings use sealants that cure along with rivets. Consider it
- Insurance?
    - Personal liability insurance for PMV should be enough.


# Questions
- Should I ground the chassis for signals? Or isolate it from everything? (It will not be connected to any battery terminal)
- Is it possible to calculate the slope based on the inclination and motor current draw?
    - Assuming static wind relative to ground, high current draw at low speed must be high slope, high speed 0 draw is no inclination or slightly negative etc. Might allow leveling lights that compensate acceleration and don't blind. Also raise more than usual when accelerating.
- Why not the battery on top? Electronics Top-Front and Battery Top-Behind. Test adding weight on top.
- REGEN Efficiency?
- Connect - of battery with chassis or isolate it?
- How does Mitch calculate the PID parameters in the code? float, int with precision, interrupts and global variables...
- Battery at the top makes it unstable or ok? If ok electronics at bottom and battery at top. If battery at bottom, experiment with parallel batteries to conform to the non-rectangular shape
- Weight at the bottom for stability and low center of mass? I'm not sure if it matters. (Similar to trailer oscillations? Top heavy wheel could oscillate, but bottom heavy just has inertia in the wheel, and can roll easily). With weight at the top of the wheel I might have more leverage to prevent a fall. Experiment.
- **Why does death wobble happen? Truly understand the mechanics.**
- Can the slope of the path be inferred from the motor behavior? f(acceleration, speed, current)
- Is there a way to provide active thermal management to the battery and electronics, for such a vehicle? Peltier?
- Use the same mosfets of the EUC for charging the battery, so we skip most of the charging circuitry? (When doing regen the motor generates high voltage AC power, which is rectified to the battery. That's basically the same as charging from the wall). Must be safe.

# Tests
- Try battery on top and electronics at the sides. It's waaay simpler that way. See if it's problematic the high center of mass.
- Measure and graph wobble speed vs center of mass. Ask mechanics techaers.
