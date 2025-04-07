# Cyberwheel Design Requirements
## Concept
> WE SHOULD NOT BLAME THE RIDER FOR A SUDDEN UNPREDICTABLE CUTOFF OF THE EUC.
- Foolproof, weatherproof
- Impossible to fry electronics by riding hard
- Impossible to damage battery by riding too cold (leanback and emergency before)
- Leanback angle calculation is central point, function of:
    - Temperatures
    - Voltages
    - Currents
    - As a consequence:
        - Speed
    > To maintain a given guaranteed minimum torque
- Make it perform strict self-tests
- Error states:
    - **Warning**: Just so you know
    - **Alert**: Gradual limits that affect the performance when balancing. Affects leanback
        - Battery overheating, overvoltage, or undervoltage. All will limit the speed. Overheating may limit it to 0.
    - **Emergency**: STOP. Hard leanback. Safety measures
    > For molicel p42a pack: <8.4A, <4.2V, >0ºC, <45ºC. Gradual transfer curve when getting close to these limits, that results in gradual predictable leanback


## Hardware
- The charger will be built into the EUC, with a small vacuum cleaner style cable.
- Crimped connectors?
    > Not just soldered when there’s so much vibration.
- Bolts: Positive locking mechanism
    - > cotter pin, safety wiring, [nylon, prevailing torque, jet, K] lock nuts, tab washers or locking plates.
- Several wires in parallel for redundancy (motor and battery wiring), while being able to detect a single one disconnecting?
    > Maybe unnecessarily complex
- Battery disconnect loop key? (actionable from the outside.)

## Firmware
- Include emergency modes that get triggered for many reasons
- Dynamic calculation of max speed based on battery level, temperature, and other factors.
- Gradual tiltback that asympotically grows in intensity as the max speed is reached.
- 

- State machine?
    - OFF (Not balancing, when put sideways)
    - Balancing (Normal, affected by alerts)
    - Charging
    - Emergency (Balancing but with hard leanback, to speed 0)

