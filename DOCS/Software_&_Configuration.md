[⬅ Back : Assembly](../DOCS/Assembly_&_Wiring.md) | [Main Repository](../README.md) | [ Next : Calibration ➡ ](../DOCS/Calibration_&_Tuning.md)

# Software & Configuration

Once the hardware is assembled, the drone still cannot fly properly until the flight controller is configured correctly. This is the stage where the hardware finally starts behaving like an actual drone.
```
A large number of beginner problems usually happen during configuration rather than assembly. Even perfectly good hardware can behave unpredictably because of:

- Incorrect firmware settings
- Wrong motor direction
- Bad calibration
- Receiver mapping issues
- ESC protocol mismatch
- Incorrect flight controller orientation
```

So configuration should always be done slowly and carefully.

One very important safety rule during the entire setup process:

- Always remove propellers while configuring or testing the drone

Even small mistakes during setup can suddenly spin motors at full speed.

---

## Betaflight Ecosystem

For this platform, Betaflight was mainly used because it is:

- Widely supported
- Modern
- Actively maintained
- Fast
- Beginner friendly once understood properly

Betaflight is extremely popular in the FPV ecosystem and works very well even for regular drone platforms when stability and responsiveness are required.

Compared to older ecosystems, Betaflight also provides:

- Easier configuration
- Better UI
- Faster firmware updates
- Strong community support
- Easier troubleshooting

This makes experimentation and repeated testing much easier.

In practical usage, Betaflight becomes the main software used for:

- Flight controller setup
- Receiver configuration
- Motor testing
- Flight mode setup
- Sensor calibration
- PID tuning
- General troubleshooting

---

## Flashing Firmware & Driver Recovery

Before the drone can operate properly, the flight controller needs firmware.

Firmware is basically the operating system of the flight controller.

Without proper firmware:

- The FC may not boot correctly
- Sensors may not function properly
- Communication may fail
- The drone may become unstable

Firmware flashing is usually done through:

- Betaflight Configurator
- USB connection
- DFU mode when required

During early experimentation with Betaflight, the flight controller was accidentally factory reset after clicking the reset FC option inside Betaflight Configurator. After rebooting, the board became completely undetectable by the system.

At first it looked like the flight controller was permanently damaged, but the actual issue was:

- Missing STM32 drivers
- DFU communication problems
- Improper USB driver configuration

To recover the board:

1. **STM32 drivers** were reinstalled
2. **CP210x drivers** were installed
3. **Zadig** was used for DFU driver setup
4. The board was manually entered into DFU mode
5. Firmware was reflashed again

After this, the flight controller became functional again.

Later, similar detection problems appeared while configuring ESC firmware through ESC Configurator.

Since ESC Configurator uses the flight controller as a communication bridge, the FC would sometimes randomly stop getting detected by Windows during configuration sessions.

A tool called:

- **RCImpulse Driver Fixer**

turned out to be extremely useful because it could reliably detect and reconnect flight controllers that randomly failed to appear in the system.

In practical usage, it almost felt like the software could “wake up” the flight controller back into communication mode.

Experiences like this are very common while experimenting with drone firmware and are a reminder that many “dead” flight controllers are actually recoverable.

Firmware flashing should always be done carefully with:

- Stable USB connection
- Correct firmware target
- Proper drivers installed

because incorrect firmware or interrupted flashing can prevent the board from booting correctly.

---

## ESC Firmware & ESC Configurator

After the flight controller is detected properly, the next major step is verifying ESC communication.

**ESC Configurator** is a software tool used to communicate with ESCs through the flight controller for firmware flashing and configuration.

The two main firmware ecosystems tested on this platform were:

- *BLHeli*
- *Bluejay*

>BLHeli is one of the most widely used ESC firmware systems and works very well for most drone ESCs.

>Bluejay mainly becomes useful for:
>
>- Smoother operation
>- RPM filtering support
>- Custom startup sounds
>
>And honestly, custom startup sounds are just fun to experiment with during builds.

ESC firmware configuration also allows:

- Motor direction reversal
- Protocol configuration
- Startup tuning
- ESC behavior adjustments

This becomes very useful during tuning and troubleshooting because motor direction can be changed digitally without physically swapping motor wires.

Expected Result:

- All ESCs should be detected correctly inside ESC Configurator
- Motors should respond smoothly during testing
- ESC communication should remain stable during configuration

---

## Receiver Setup & UART Configuration

Once ESC communication works properly, the next major step is configuring receiver communication.

The FlySky i6 transmitter and receiver pair was used for this platform because it is:

- Affordable
- Reliable
- Beginner friendly
- Widely available

For receiver communication, this platform uses:

- IBUS serial protocol

One major advantage of IBUS is that it carries:

- All 4 stick channels
- Multiple AUX channels

through a single signal wire.

This keeps the setup:

- Cleaner
- Simpler
- Easier to manage

while still supporting around:

- 14 AUX channels

for switches and additional controls.

During setup, UART configuration inside Betaflight becomes extremely important because the receiver will not work unless the correct UART port is configured properly.

```
The receiver only communicates through the UART port where its signal wire is physically connected.

Inside Betaflight:

1. Open the “Ports” tab
2. Find the UART connected to the receiver
3. Enable “Serial RX” on that UART
4. Save and reboot the flight controller

After this:

1. Open the “Receiver” configuration section
2. Select the correct receiver protocol
3. Verify receiver communication
```

One very common beginner issue is:

- Receiver not responding even though wiring is correct

In many cases, the actual problem is simply:

- Incorrect UART selection
- Serial RX disabled
- Wrong receiver protocol selection

Inside Betaflight, stick movement should always be verified before flight because incorrect channel mapping can create:

- Reversed controls
- Incorrect throttle behavior
- Unstable flight response

Expected Result:

- Receiver bars inside Betaflight should move correctly with transmitter stick movement
- Roll, pitch, yaw, and throttle directions should respond properly
- AUX switches should also respond correctly

---

## ESC Protocols & Motor Communication

Once the receiver is working properly, the next major step is motor communication.

The flight controller communicates with ESCs using different signal protocols.

These protocols define how motor speed commands are sent from the flight controller to the ESCs.

In simple terms:

```txt
Flight Controller → ESC → Motor
```

The flight controller continuously calculates how fast each motor should spin for stabilization, movement, and corrections. Those speed commands are then transmitted to the ESCs using communication protocols.

Different protocols mainly affect:

- Communication speed
- Response time
- Accuracy
- Synchronization
- Signal reliability

<br>

### Older Analog Protocols

```
Older communication protocols include:

- PWM
- OneShot
- MultiShot
```
These protocols are often called “analog-style” protocols because they mainly work using pulse timing.

In these systems, the flight controller sends pulses to the ESC, and the pulse width represents motor speed.

A simple way to visualize this is:

```txt
Short pulse  → Lower motor speed
Long pulse   → Higher motor speed
```

So instead of sending exact digital data, the ESC estimates motor speed based on pulse timing.

Because of this approach, older protocols are generally:

- Slower
- Less precise
- More delay-prone
- More sensitive to signal noise

However, they still have some advantages:

- Simpler implementation
- Wider compatibility with older ESCs
- Lower processing requirements
- Stable enough for basic and slow platforms

This is one reason older ESCs like SimonK worked reasonably well with slower traditional systems such as Pixhawk-based platforms.

For normal hovering and slow movement, these protocols can still work properly.

But during aggressive corrections or fast stabilization updates, limitations become more visible.

<br>

### Digital DShot Protocols

```
Modern communication protocols include:

- DShot150
- DShot300
- DShot600
- DShot1200
```

Unlike analog protocols, DShot protocols transmit exact digital commands instead of pulse-length estimation.

A simplified visualization looks like:

```txt
Analog Protocol:
"Guess motor speed from pulse timing"

Digital DShot:
"Motor speed command = EXACT digital value"
```

Because of this, DShot protocols provide:

- Faster communication
- Better accuracy
- Lower signal errors
- Better synchronization
- More reliable motor response

This becomes extremely important during:

- Fast stabilization corrections
- Aggressive maneuvering
- High-speed flight
- Rapid throttle changes

The higher the DShot number:

- Faster the communication speed
- Lower the delay
- Faster the motor response

For example:

- DShot150 is slower
- DShot600 is much faster and more responsive

However, faster DShot protocols also require:

- Compatible ESCs
- Stable firmware
- Capable flight controllers

Otherwise communication instability can occur.

<br>

### Why DShot Feels Better in Flight

> **During testing, older SimonK ESCs struggled heavily with fast FPV-style signal updates.**

This caused:

- Lag
- Delayed corrections
- Unstable response
- Motor desync

>Motor desync happens when the ESC loses proper synchronization with motor timing, causing unstable spinning or sudden response failure.

Modern ESCs using DShot protocols handled these rapid updates much more smoothly and significantly improved:

- Stability
- Responsiveness
- Synchronization
- Overall flight confidence

This was one of the biggest practical differences observed during experimentation.

---

### Choosing the Right Protocol

For modern FPV-style flight controllers and newer ESCs:

- DShot protocols are usually the best option

because they provide:

- Better responsiveness
- More reliable communication
- Easier digital configuration
- Improved synchronization

However, older analog protocols are not “bad”.

They are still useful for:

- Older ESCs
- Slower drone platforms
- Basic hovering systems
- Simpler flight controllers
- Legacy compatibility

So the correct protocol always depends on:

- ESC capability
- Flight controller capability
- Firmware support
- Flight style
- Stability requirements

Expected Result:

- Motors should spin smoothly during testing
- Motor response should feel synchronized
- No random twitching or desync behavior should appear
- Throttle response should feel clean and predictable

---

## Sensor Calibration

After communication systems are working properly, the next major step is sensor calibration.

>**The flight controller depends heavily on proper sensor calibration for stable flight behavior.**

Important calibrations include:

- Accelerometer calibration
- Gyro calibration
- Level calibration

Improper calibration can cause:

- Drifting
- Unstable hover
- Tilted flight behavior
- Incorrect stabilization response

Calibration should always be performed on a flat and stable surface.

Inside Betaflight, calibration is usually performed through the **“Setup”** tab while the drone remains completely stationary on a level surface.

The flight controller continuously uses sensor data to understand:

- Drone angle
- Rotation
- Movement
- Orientation in space

So if the sensors are calibrated incorrectly, the FC starts assuming an incorrect orientation as “level”.

A simple way to visualize this is:

```txt
Actual Drone Position      FC Assumes

Perfectly Level      ≠     Slightly Tilted
```

In this situation, the drone may constantly try correcting itself unnecessarily, causing:

- Drift
- Slow movement in one direction
- Unstable hover
- Incorrect stabilization

This is why the drone should remain completely still during calibration.

Betaflight also provides some very useful calibration-related features that improve practical flight behavior significantly.

>One useful feature is:
>
>- Calibration on arm
>
>This allows the drone to recalibrate small sensor offsets during arming, helping improve stability before takeoff.

>Another very useful feature is:
>
>- In-flight calibration
>
>This becomes especially useful when:
>
>- The drone is powered on over uneven ground
>- Small drift offsets appear
>- Transmitter sticks are not perfectly centered

For example, if the drone is initialized while sitting slightly tilted on the ground, the flight controller may incorrectly assume that tilted position is level, causing drift during hover.

In-flight calibration helps re-optimize and re-center the drone during actual flight conditions, reducing:

- Drift
- Offset errors
- Incorrect leveling behavior

Similarly, if slight unintended transmitter stick input exists because of imperfect centering, Betaflight can compensate and smooth out those offsets during flight.

Features like these may seem minor initially, but during practical testing they make the drone feel significantly:

- Smoother
- More stable
- More predictable

especially during hovering and slow maneuvering.

Expected Result:

- Artificial horizon inside Betaflight should remain level
- Drone should not drift excessively during hover
- Stabilization should feel smooth and predictable

---
