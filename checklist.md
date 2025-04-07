# Safety
- [ ] Dynamic forces have been simulated
- [ ] Dynamic forces have been tested
- [ ] Fatigue tests have been performed (riding x km in rough terrain should work)
- [ ] Waterproofing test
    - The chassis keeps positive and negative pressure inside. The lighting panel should break/melt in case of fire, so it won't be a bomb.
- [ ] Battery at 100%, go fast and try sudden braking
    - Does the battery suffer overvoltage?
    - What is the maximum deceleration achieved? (consider a minimum threshold to validate it)
    > Alternatives are controlled short of motor wires, without regen. An external resistor (probably better the first approach)
    > This affects braking power but also ability to ride in <0ºC, where the battery can't charge (the anode gets covered in metallic lithium layer that can cause a short circuit)
- [ ] Record at x speed and calculate the torque being applied. Must get over a minimum


# 
- [ ] The documentation fully explains the maintenance and safety procedures

> Could be cool to record these tests and let people propose and vote new tests to be performed.


## To consider
- [ ] Crazy test: Unplug the battery
    - It should enter emergency mode, spend all power available for leanback, and start braking with pwm control, dumping the energy slowly to the motor coils, in a stable deceleration with enough leeway to perform balancing.