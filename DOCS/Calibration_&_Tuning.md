[⬅ Back : Software](../DOCS/Software_&_Configuration.md) | [Main Repository](../README.md) | [ Next : Troubleshooting ➡ ](../DOCS/Troubleshooting.md)

# Calibration & Tuning

Even after proper assembly and configuration, a drone usually does not fly perfectly on the first attempt. Small vibrations, sensor offsets, weight imbalance, or incorrect tuning can completely change how the drone behaves in air.

Calibration and tuning are what transform a drone from:

- Barely flyable

to

- Smooth and predictable

<br>

Every drone behaves slightly differently, even when using similar hardware. Things like:

- Frame rigidity
- Propeller balance
- Motor quality
- Weight distribution
- Battery weight
- Wiring layout

all affect flight behavior in some way.

Because of this, tuning is less about copying settings from the internet and more about understanding how the drone responds during actual flight.

---

## Sensor Calibration

The flight controller depends heavily on accurate sensor data for stabilization.

Important calibrations include:

- Gyroscope calibration
- Accelerometer calibration
- Level calibration

Improper calibration can create:

- Drifting
- Unstable hover
- Tilted flight
- Incorrect stabilization behavior

Calibration should always be performed on a flat and stable surface.

During testing, recalibration became especially important after:

- Crashes
- Frame modifications
- Component repositioning
- Firmware resets

because even small physical changes sometimes affected the sensor behavior noticeably.

Features like:

- Calibration on arm
- In-flight calibration

also helped significantly in reducing:

- Drift
- Small leveling errors
- Transmitter offset issues

especially during hovering and slow maneuvering.

---

## ESC Calibration

ESC calibration helps synchronize throttle response between all motors.

If ESCs are not calibrated properly, motors may:

- Start at different throttle levels
- Respond unevenly
- Feel inconsistent during hover

This can make the drone feel unstable even if the hardware itself is completely fine.

Modern digital ESC protocols reduce many of these issues automatically, but proper ESC setup and firmware configuration still make a noticeable difference in:

- Smoothness
- Synchronization
- Throttle consistency

## PID Tuning

PID tuning is one of the most important parts of drone stabilization.

PID values control how aggressively and smoothly the drone reacts to movement and external disturbances.

In simple terms:

- **P (Proportional)** controls how strongly the drone reacts to movement errors.
- **I (Integral)** helps the drone maintain stability over time and resist drifting.
- **D (Derivative)** smooths corrections and reduces sudden oscillations.

Improper PID tuning can cause:

- Shaking
- Oscillation
- Sluggish response
- Bounce-back movement
- Overheating motors

Fortunately, modern Betaflight default PID values are already surprisingly good for beginner platforms, so the drone was initially flyable without major tuning changes.

Most tuning improvements during testing were focused more on:

- Smoothness
- Stability
- Reducing vibrations
- Improving handling feel

rather than extreme aggressive tuning.

---

## Vibration & Stability Issues

One thing quickly noticed during testing was how heavily vibrations affect flight behavior.

Even small vibration sources can create:

- Noisy gyro readings
- Unstable hover
- Poor PID response
- Inconsistent motor corrections

Common vibration sources included:

- Unbalanced propellers
- Loose frame arms
- Poor motor mounting
- Loose wiring
- Weak flight controller mounting

Larger frames are naturally more stable, but they can also amplify vibrations if the structure is not rigid enough.

After switching from generic motors to DJI motors, the drone immediately felt:

- Smoother
- More stable
- Less noisy during hover

mainly because of:

- Better balancing
- Stronger motor construction
- Improved thermal stability

This showed that flight feel is not only software dependent. Mechanical quality also heavily affects tuning behavior.

---

## Hover Testing

Most tuning observations were made during low-altitude hover testing.

Instead of immediately flying aggressively, small controlled hover tests made it easier to observe:

- Drift
- Oscillation
- Throttle behavior
- Vibration response
- Stabilization quality

Hover testing also helped identify:

- Loose components
- Incorrect motor directions
- Excessive heating
- Calibration problems

before the drone was pushed into more demanding flight conditions.

This slow testing approach prevented multiple crashes during development and made troubleshooting much easier.

---

## Practical Tuning Observations

One important thing learned during tuning was that smooth and predictable flight behavior is far more useful than overly aggressive response.

Many online setups prioritize:

- Extreme responsiveness
- Sharp movement
- Racing-style tuning

But for regular drone platforms used for:

- Learning
- Experimentation
- Testing
- Stable maneuvering

a smoother setup feels significantly better and easier to control.

Another important observation was that hardware upgrades often improved tuning behavior more effectively than software changes alone.

For example:

- Better ESCs improved synchronization noticeably
- Better motors reduced vibration
- Balanced propellers improved hover stability
- Cleaner wiring reduced random instability issues

Over time, tuning became less about chasing perfect numbers and more about understanding how the drone actually behaves during real flight conditions.

---
