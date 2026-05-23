[⬅ Back : Calibration](../DOCS/Calibration_&_Tuning.md) | [Main Repository](../README.md)

# Testing & Troubleshooting

Even after successful assembly and configuration, real-world testing often reveals hidden issues that are difficult to notice during bench testing.

Because of this, troubleshooting should always be approached systematically instead of changing random settings blindly.

The goal during troubleshooting is:

- Identifying symptoms correctly
- Isolating the actual cause
- Verifying changes one step at a time

---

## Drone Flips Immediately During Takeoff

### Typical Symptoms

- Drone flips instantly after throttle increase
- One side lifts aggressively
- Violent roll movement during takeoff

### Most Common Causes

- Incorrect motor direction
- Wrong propeller orientation
- Incorrect motor order mapping
- Wrong flight controller orientation

### How To Verify

Inside Betaflight:

1. Open the **Motors** tab
2. Remove all propellers
3. Spin each motor individually
4. Verify motor numbering matches Betaflight visualization
5. Check motor rotation direction manually

Then verify:

- Propeller direction matches motor direction
- Flight controller orientation matches actual mounting direction

### Fix

- Reverse incorrect motors using ESC Configurator
- Correct motor mapping if necessary
- Reinstall propellers correctly
- Adjust FC orientation inside Betaflight if mounted rotated

### Expected Result

- Drone should lift vertically without sudden flipping
- Hover should feel stable and predictable

---

## Drone Drifts During Hover

### Typical Symptoms

- Slow movement in one direction during hover
- Drone unable to remain level
- Constant correction required from pilot

### Most Common Causes

- Improper accelerometer calibration
- Uneven initialization surface
- Slight frame imbalance
- Transmitter stick offsets

### How To Verify

Inside Betaflight:

1. Open the **Setup** tab
2. Verify artificial horizon remains level
3. Check receiver tab for centered stick values
4. Recalibrate accelerometer on a flat surface

### Fix

- Recalibrate accelerometer
- Enable calibration-on-arm if required
- Adjust transmitter trims carefully
- Recheck frame balance

### Expected Result

- Drone should hover with minimal correction
- Drift should reduce significantly

---

## Motors Become Excessively Hot

### Typical Symptoms

- Motors too hot to touch after short flight
- Reduced flight efficiency
- Burning smell or excessive heat

### Most Common Causes

- Overloaded propellers
- Excessive vibration
- Aggressive PID tuning
- Poor motor quality
- Excessive weight

### How To Verify

Check for:

- Frame vibration
- Bent propellers
- Loose motor mounting
- Aggressive oscillation during hover

Compare motor temperatures after short hover tests.

### Fix

- Reduce excessive PID aggressiveness
- Replace damaged propellers
- Improve vibration isolation
- Reduce unnecessary weight
- Upgrade motors if required

### Expected Result

- Motors should remain warm but not dangerously hot
- Flight behavior should feel smoother

---

## Flight Controller Not Detected by Computer

### Typical Symptoms

- FC not appearing in Betaflight
- USB device not detected
- DFU mode unavailable

### Most Common Causes

- Missing STM32 drivers
- Incorrect DFU drivers
- USB cable issues
- Driver conflicts

### How To Verify

- Try different USB cable
- Check Device Manager
- Attempt DFU mode manually
- Verify Betaflight COM port detection

### Fix

Install:

- STM32 drivers
- CP210x drivers
- Zadig DFU drivers

If detection still fails:

- Re-enter DFU mode manually
- Reflash firmware carefully

### Useful Tools

- Zadig
- STM32 Driver Package
- RCImpulse Driver Fixer

### Expected Result

- Flight controller should reconnect normally
- Firmware flashing should work correctly

---

## ESCs Not Responding Correctly

### Typical Symptoms

- Motors not spinning smoothly
- Random twitching
- Desync behavior
- Uneven throttle response

### Most Common Causes

- Incorrect ESC protocol
- Poor ESC firmware
- Weak ESC hardware
- Signal instability

### How To Verify

Inside ESC Configurator:

- Verify all ESCs are detected
- Test motor response individually
- Check protocol settings inside Betaflight

### Fix

- Use compatible DShot protocol
- Reflash ESC firmware if required
- Replace unstable ESCs
- Verify wiring integrity

### Expected Result

- Motors should respond smoothly
- Throttle behavior should feel synchronized

---

## Crash Inspection Checklist

After every crash, inspect:

- Propellers
- Motor shafts
- Frame arms
- Wiring
- Flight controller mounting
- Battery condition

Even small crashes can create hidden vibration or alignment issues that affect flight stability later.

---

## Excessive Frame Vibration

### Typical Symptoms

- Unstable hover
- Noisy motors
- Oscillation during throttle increase
- Poor PID behavior
- Random flight instability

### Most Common Causes

- Loose frame arms
- Cracked carbon/plastic structure
- Weak frame rigidity
- Improper stack mounting
- Bent propellers

### How To Verify

Check for:

- Arm flex during throttle
- Loose screws
- Visible vibration during hover
- Cracks near motor mounts
- Flight controller movement inside frame

### Fix

- Tighten frame hardware
- Replace cracked parts
- Improve FC soft mounting
- Replace damaged propellers

### Expected Result

- Smoother hover
- Reduced oscillation
- Cleaner stabilization response

---

## Drone Feels Different After Crash

### Typical Symptoms

- Previously stable drone now drifts
- Sudden vibration appears
- Uneven motor sound
- Reduced stability

### Most Common Causes

- Bent motor shaft
- Cracked frame
- Shifted flight controller
- Damaged propeller
- Loose stack screws

### How To Verify

Inspect:

- Motor alignment
- FC mounting
- Arm straightness
- Propeller balance
- Stack rigidity

### Fix

- Replace damaged components
- Re-tighten stack
- Recalibrate sensors
- Replace bent props

---

## Random Power Cut During Flight

### Typical Symptoms

- Drone suddenly falls from air
- FC reboots randomly
- ESC resets during throttle punch
- Temporary shutdowns

### Most Common Causes

- Weak XT60 connection
- Poor solder joints
- Loose battery connector
- Voltage drop
- Power distribution failure

### How To Verify

Check:

- XT60 solder quality
- Battery wire movement
- ESC power joints
- Voltage sag during throttle

Gently move wires while powered OFF to inspect looseness.

### Fix

- Reflow solder joints
- Replace damaged connectors
- Improve wire strain relief
- Secure battery properly

### Expected Result

- Stable power delivery
- No random shutdowns

---

## Drone Randomly Twitches During Hover

### Typical Symptoms

- Sudden small jerks
- Random twitching
- Inconsistent stabilization
- Brief motor surges

### Most Common Causes

- Loose signal wires
- ESC signal noise
- Vibration interference
- Poor grounding
- Damaged motor wire

### How To Verify

Inspect:

- ESC signal wires
- Motor wire insulation
- FC connector stability
- Loose solder joints

Check for twitching during low throttle bench testing.

### Fix

- Secure loose wiring
- Re-solder weak joints
- Improve wire routing
- Reduce vibration sources

---

## Very Short Flight Time

### Typical Symptoms

- Battery drains quickly
- Voltage drops rapidly
- Weak throttle response
- Battery becomes hot

### Most Common Causes

- Overweight drone
- Inefficient propellers
- Damaged battery
- Excessive current draw
- Aggressive tuning

### How To Verify

Check:

- Battery voltage before/after flight
- Motor temperatures
- Hover throttle percentage
- Battery puffing/swelling

### Fix

- Reduce unnecessary weight
- Replace weak battery
- Use efficient propellers
- Improve tuning stability

### Expected Result

- More stable voltage
- Longer usable flight time

---

## Battery Voltage Sag

### Typical Symptoms

- Sudden power drop during throttle punch
- Drone feels weak at high throttle
- FC brownouts
- Battery warning appears too early

### Most Common Causes

- Weak battery C-rating
- Old battery
- Excessive current draw
- Poor connector resistance

### How To Verify

Monitor:

- Voltage during throttle increase
- Battery temperature
- Connector heating

### Fix

- Use higher discharge battery
- Replace aged batteries
- Improve power connections

---

## ESC Desync

### Typical Symptoms

- Sudden motor stutter
- One motor stopping briefly
- Violent shaking during throttle
- Mid-air instability

### Most Common Causes

- Weak ESC firmware
- Incorrect protocol
- Excessive motor load
- Poor motor timing

### How To Verify

- Test motors individually
- Reduce throttle aggressively during hover
- Listen for motor stutter sounds

### Fix

- Use DShot protocols
- Reflash ESC firmware
- Reduce propeller load
- Replace unstable ESCs

---

## Flight Controller Noise Problems

### Typical Symptoms

- Random unstable behavior
- Inconsistent gyro response
- Oscillation despite tuning

### Most Common Causes

- Excessive electrical noise
- Poor power filtering
- Vibration coupling
- Poor stack isolation

### How To Verify

Check:

- FC mounting softness
- Capacitor condition
- Power wiring cleanliness

### Fix

- Add low-ESR capacitor
- Improve soft mounting
- Separate noisy wires

---

## Receiver Randomly Disconnects

### Typical Symptoms

- Sudden failsafe
- Controls freeze temporarily
- Intermittent signal loss

### Most Common Causes

- Loose receiver wire
- Weak transmitter signal
- Damaged antenna
- Power instability

### How To Verify

- Check receiver LEDs
- Inspect antenna orientation
- Move transmitter farther gradually

### Fix

- Secure receiver wiring
- Replace damaged antenna
- Improve receiver mounting

---

## Drone Behaves Unstable Outdoors But Fine Indoors

### Typical Symptoms

- Hover instability outdoors
- Unexpected drifting
- Wind sensitivity

### Most Common Causes

- Wind disturbance
- GPS interference
- Weak tuning margins
- Lightweight frame

### How To Verify

Compare:

- Indoor hover
- Outdoor hover

under calm conditions.

### Fix

- Increase tuning stability
- Reduce weight imbalance
- Avoid testing in strong wind initially

---