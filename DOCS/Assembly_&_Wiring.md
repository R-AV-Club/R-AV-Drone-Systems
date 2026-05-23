[⬅ Back : Selection](../DOCS/Component_Selection_Logic.md) | [Main Repository](../README.md) | [ Next : Software ➡ ](../DOCS/Software_&_Configuration.md)

# Assembly & Wiring

Once all the components are selected, the next step is assembling the drone properly. A large number of drone problems actually begin during assembly itself due to:

- Poor wiring
- Loose mounting
- Weak solder joints
- Vibrations
- Incorrect component placement
- Loose screws

So while building, the focus should not only be making the drone work, but also making it:

- Clean
- Reliable
- Repairable
- Safe to troubleshoot later

<br>

```
Helpful tools during assembly usually include:

- Soldering iron        (Higher power rating, more quickly it heats !)
- Heat shrink           (To protect wire joints or solder points)
- Zip ties              (Universal & Reliable as always for attaching things to frame without messy adhesives)
- Multimeter            (Absolute necessary, true companion for electronics)
- Hex drivers           (Allen Keys)
- Wire cutters
```

---

## Before Starting Assembly

Before connecting anything, it is important to:

- Verify component compatibility 
- Check voltage ratings *(IMPORTANT! If unchecked, you will smoke valuable electronics)*
- Organize screws and hardware
- Plan wire routing *(Route wires such that it avoids propellers, motors and hot electronics like ESC)*
- Inspect components for damage *(If you feel it is damaged, try to isolate it from the rest of the build and check it individually)*

One very important safety rule during setup and testing is:

- Always remove propellers while configuring the drone *(Props act like sharp blades when spinning at high speeds and cause serious cuts or injuries)*

>Many beginners skip this and accidentally arm the motors during setup, which can become dangerous very quickly.

---

## Frame Assembly

The frame should be assembled tightly and evenly because loose structures introduce vibrations and instability during flight.

While assembling the frame:

- Arms should be tightened properly
- Frame alignment should be checked
- Loose joints should be avoided

Even small vibrations from loose frame parts can affect:

- Sensor readings
- Flight stability
- PID tuning
- can even lead to disassembled arm during flight

---

## Motor Mounting

Motor installation looks simple, but incorrect mounting can damage motors very easily.

One important thing while mounting motors is screw length.

If screws are too long, they can touch the internal motor windings and permanently damage the motor.

Motors should also be mounted securely because loose motors create:

- Vibrations
- Unstable flight behavior
- Inconsistent thrust

```
Motor direction is extremely important because each propeller is designed to spin in a specific direction for proper stabilization.

Incorrect motor direction can cause:

- Immediate flipping during takeoff
- Unstable behavior
- Loss of control
```

Motor directions are usually verified later during software configuration and initial testing.

Motor wire routing should be planned carefully to avoid:

- Propeller contact
- Excessive bending
- Wire stress during crashes

---

## Soldering Basics

>Strong solder joints are extremely important in drone systems because high current continuously flows through power connections. <br>
>If a solder joint is weak, it creates a resistance in path causing it to heat and melt that tiny contact.

Good solder joints should:

- Look shiny and smooth
- Fully cover the pad or wire
- Remain mechanically strong

Poor solder joints may:

- Overheat
- Create voltage drops
- Disconnect during flight
- Cause unstable behavior

Using proper soldering temperature, flux, and clean wire preparation makes assembly significantly more reliable.

### Soldering Temperature

>Temperature of solder has to be set within limits or it may cause burns on PCB *(printed circuit board)* of electronics component or can damage PCB traces. <br>
>Excessive heat also burns the outer insulation rubber or silicone wire causing it to soften and expose wires underneath it.

### Flux

>Flux is a chemical cleaning agent used during soldering that helps molten solder stick properly to metal surfaces. <br>
>Flux helps clean these surfaces temporarily while soldering, allowing the solder to flow smoothly and create stronger electrical contact.

During soldering, metal surfaces naturally contain:

- Oxidation
- Dust
- Contaminants

Without proper flux:

- Solder may not stick correctly
- Joints may look dull or rough
- Connections may become weak or unreliable

Flux can be available as:

- Flux core inside solder wire
- Liquid flux
- Solder paste flux

### Solder Wire

>Solder wire is a low melting-point metal wire used to electrically and mechanically join wires, pads, and electronic components together.
>
>When heated using a soldering iron, the solder wire melts and flows over metal surfaces, creating an electrical connection after cooling down.
>
>Most solder wires also contain a small flux core inside them which helps the solder flow properly during soldering.
>

Solder wires themselves contain different proportions of:

- Solder metal
- Flux core

Some solder wires contain very little flux, while others contain larger flux cores for easier soldering.

Better quality solder wires usually:

- Melt more smoothly
- Flow better on pads
- Create cleaner joints
- Require less additional flux

Cheap solder wires often create:

- Rough joints
- Poor flow
- Excessive smoke
- Difficult soldering experience

Because of this, solder wire quality heavily affects soldering reliability and ease of assembly.

### Solder Paste

>Similar to solder wire, this is in paste format.

Solder paste usually contains:

- Tiny solder particles
- Flux mixture

It is commonly used for:

- SMD components
- Rework
- Easier heat transfer during soldering

During manual drone assembly, solder paste can also help improve heat transfer and solder flow while working with larger pads or power connections.

---

## ESC Installation

>ESCs *(Electronic Speed Controllers)* act like electronic power regulators between the battery and motors. They continuously adjust motor speed based on commands received from the flight controller.

ESC placement affects:

- Cooling
- Wiring cleanliness
- Maintenance accessibility

During testing, cleaner ESC layouts made troubleshooting significantly easier later.

Older individual ESC setups required:

- Longer wiring
- More solder joints
- Additional space

Modern 4-in-1 ESCs simplified the build considerably by:

- Reducing wiring clutter
- Improving compactness
- Simplifying maintenance

ESC airflow is also important because overheating can reduce reliability during continuous hovering or aggressive maneuvering.

---

## Power Distribution & XT60 Connections

The power system is one of the most critical parts of the drone.

Poor soldering in high-current areas can create:

- Voltage drops
- Overheating
- Unstable behavior
- Sudden power loss

XT60 connectors and battery leads should always have:

- Strong solder joints
- Proper insulation
- Secure mounting

While soldering XT60 connectors, excessive heating can soften or deform the connector housing, so soldering should be done quickly and carefully.

Cold solder joints may sometimes work initially but fail later during high current loads or vibrations.

During assembly, keeping power wires short and clean also helps reduce:

- Wiring mess
- Resistance
- Unnecessary weight

---

## Flight Controller Mounting

The flight controller should be mounted carefully because it continuously reads vibration-sensitive sensor data.

Excessive vibration reaching the flight controller can create:

- Unstable flight
- Poor PID behavior
- Drifting
- Noisy sensor readings

Soft mounting helps reduce vibration transfer from the frame to the sensors. <br>
In our drone, we use **anti-vibration shock absorber platform** to remove most of the noise from other peripherals.

Most flight controllers have an **arrow marking** that should point toward the front of the drone unless configured differently in software.

Correct orientation is also extremely important. Even small mounting orientation mistakes can completely affect stabilization behavior.

---

## Wiring Management

Good wiring management makes a huge difference during troubleshooting and maintenance.

>For drone, we usually use silicone wires as they are capable of handling a lot of current and high voltages whilst providing flexibility to the wire. <br>
>Other wires like PVC wires are hard to bend and carry a lot of material weight with them therefore are not recommended. 

Messy wiring increases the chances of:

- Loose connections
- Propeller wire strikes
- Electrical noise
- Difficult repairs

Clean routing also improves airflow and overall reliability.

Simple things like:

- Zip ties
- Heat shrink
- Wire sleeves
- Proper wire length

make the drone much easier to maintain later.

---

## First Power-Up & Safety Checks

The first power-up should always be done carefully.

Before connecting the battery:

- Inspect all solder joints
- Check polarity
- Verify no wires are touching
- Confirm there are no loose screws

The drone should first be tested:

- Without propellers
- One component at a time
- With slow verification steps

>During initial testing:
>
>- Motors should spin smoothly
>- No component should heat rapidly
>- Flight controller LEDs should behave normally
>- Receiver should bind correctly
>- No burning smell or smoke should appear

If anything behaves abnormally, disconnect the battery immediately and inspect the system carefully before continuing.

Motor directions, receiver response, and flight controller behavior should all be checked carefully before attempting the first flight.

---
