[⬅ Back : Regular Quadcopter](../DOCS/Regular_Quadcopter.md) | [Main Repository](../README.md) | [ Next : Hardware ➡ ](../DOCS/Hardware_Overview.md)

# Design Philosophy

Before selecting components or assembling anything, it is important to first understand the design of the drone itself. The frame and overall structure decide how the drone behaves in air, how stable it feels, how much payload it can carry, and even how difficult it becomes to tune and control.

**Drones can have different configurations based on the number of motors:**

- Unicopter  (One main motor & One control motor)
- Bicopter   (Two main motors & Two control motors)
- Tricopter  (Three main motors & One control motor)
- Quadcopter (Four main motors)
- Hexacopter (Six main motors)
- Octacopter (Eight main motors)
<br>

**As the number of motors increases, the drone generally becomes more stable because thrust gets distributed across multiple motors.** <br>
*(Example : A Two-Wheeler is less stable than A Four-Wheeler.)*
<br>

**More motors also allow the drone to carry additional payloads such as larger batteries, cameras, sensors, or extra electronics.** <br>
*(More motors = More horsepower of drone.)*
<br>

**Some larger configurations like hexacopters and octacopters can even remain partially controllable after a motor failure, which is useful in professional applications.** <br>
*(Hexcopters are lke trucks with 6 motors. If any tire goes off, it doesn't affect it drastically.)*
<br>

However, increasing the number of motors also increases:

- Overall cost
- Wiring complexity
- Tuning difficulty
- Weight
- Power consumption
- Maintenance requirements

Because of this, larger configurations are usually used only when the application actually requires them. More motors may improve lifting capability and stability, but they also make the entire system more difficult to assemble, tune, troubleshoot, and maintain, especially for beginners.

**For most regular drone builds, quadcopters provide one of the best balances between:**

- Simplicity
- Stability
- Affordability
- Control
- Repairability

That is why this platform uses a quadcopter design.

Another major factor is frame size.

---

### Larger Frames Generally:

- Fly slower and smoother
- Feel more stable during flight
- Provide more internal working space
- Carry more payload
- Handle upgrades more easily

The additional space inside larger frames makes assembly, wiring, troubleshooting, and modifications much easier, especially for beginners. Larger drones are also usually better for learning because their movement feels more controlled and less aggressive.

Larger frames also usually have more distance between motors and propellers. Because of this, movement changes happen more gradually, giving the flight controller more time to stabilize the drone. This is one of the main reasons larger drones often feel smoother and easier to control.

---

### Smaller Frames Generally:

- Respond much faster
- Feel more aggressive
- Become more compact and lightweight
- Allow higher agility
- Require more precise tuning

But smaller drones can also become unstable more easily if the setup or tuning is poor. Since everything is compact, repairs and modifications can also become difficult.

Smaller drones have lower weight and shorter distances between motors, so even small motor speed changes affect the drone very quickly. This makes them feel highly responsive and agile, but also less forgiving during mistakes or unstable tuning.

Neither design is universally better. The correct design always depends on the purpose of the drone.

**Before building, it is important to ask:**

- Is the drone meant for learning?
- Is it meant for speed?
- Is it meant for carrying payloads?
- Is it meant for experimentation?
- Is it meant for stable flight practice?

In this case, the goal is to build a practical and stable drone platform that helps in both learning and experimentation.

Regular quadcopter platforms like the Q450 are extremely useful because:

- They are relatively cheap to build
- Replacement parts are easily available
- The frame is durable and repair-friendly
- They can survive beginner mistakes better than smaller aggressive drones
- They provide enough space for understanding wiring and hardware integration properly

> ***What is a Q450 frame ?***
>
>The Q450 is a popular beginner quadcopter frame with a motor-to-motor diagonal size of around 450mm.
>

---

<br>
For learning and experimentation, quadcopters provide one of the best balances between simplicity, stability, affordability, and repairability. They are complex enough to teach real drone engineering concepts while still remaining manageable for beginners.

<br>
Since everything is assembled from scratch, this type of build teaches much more than simply buying a ready-made drone. While building and flying it, a lot of practical concepts naturally become easier to understand, including:

- Power distribution
- Motor behavior
- Flight stability
- Tuning
- Vibration issues
- Battery limitations
- Flight controller configuration
- Troubleshooting techniques

So instead of treating this platform as just a drone build, it should be treated as a practical learning and experimentation system.

---
