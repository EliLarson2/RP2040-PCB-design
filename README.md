# Custom RP2040 Embedded Controller PCB

A custom two-layer embedded controller designed in KiCad around the **bare RP2040 microcontroller** rather than a development-board module.

I completed the full hardware-development cycle: schematic capture, component selection, PCB layout and routing, fabrication, hand assembly, firmware programming, and hardware bring-up. The assembled board successfully booted and accepted firmware, and I validated its **I2C interfaces and external load-driver functionality**.

---

## Project Highlights

- Designed around a **bare RP2040**, implementing the support circuitry normally provided by a development board
- Integrated external QSPI flash, crystal and clock circuitry, 3.3 V regulation and decoupling, USB-C, I2C, load-driver circuitry, and programming/boot support
- Took the design from **schematic through fabricated hardware**
- Hand-assembled and incrementally brought up the completed PCB
- Successfully validated RP2040 programming and boot behavior
- Verified I2C communication and external load-driver operation
- Applied a structured measurement-driven approach to hardware debugging

---

## Hardware Overview

The controller integrates:

- RP2040 microcontroller
- External QSPI flash for nonvolatile program storage
- External crystal and clock circuitry
- 3.3 V power regulation and decoupling
- USB-C interface
- I2C interfaces for external peripherals
- External load-driver circuitry
- Programming and boot-support circuitry

Component selection and circuit implementation were based on manufacturer datasheets, reference designs, and the electrical requirements of the system.

---

## Schematic Design

The schematic was developed in KiCad around the standalone RP2040 rather than a Raspberry Pi Pico module. This required implementing the power, clocking, external flash, USB, decoupling, programming, and peripheral circuitry needed to support the microcontroller directly.

![KiCad schematic for the custom bare-RP2040 embedded controller](Images/RP2040_Schematic.jpeg)

*KiCad schematic showing the RP2040 support circuitry and external interfaces.*

---

## PCB Layout

The design was implemented as a two-layer PCB. I began by placing the major components and supporting circuitry, then routed and reviewed the complete board before fabrication.

![Initial PCB component placement before trace routing](Images/Trace_Firstrun.jpeg)

*Initial component-placement state before any traces were routed.*

Placement required balancing the physical relationships between the RP2040, external flash, clock circuitry, power components, USB-C interface, peripheral connections, and load-driver circuitry within a two-layer design.

---

## Fabrication and Assembly

After completing the schematic and PCB layout, I had the board fabricated and hand-assembled the components.

![Hand-assembled custom RP2040 embedded controller PCB](Images/Board_Assembled.jpeg)

*Fabricated and hand-assembled controller board used for hardware bring-up and interface validation.*

The assembled board was brought up incrementally rather than testing every function at once. This made it easier to isolate faults and verify each stage before moving deeper into firmware and peripheral testing.

---

## Board Bring-Up and Validation

My bring-up process followed a staged approach:

1. Visually inspect the assembled PCB for placement, orientation, and soldering issues.
2. Check power and ground connections before applying power.
3. Verify the regulated 3.3 V supply rail.
4. Confirm RP2040 programming and boot behavior.
5. Load firmware to validate basic processor operation.
6. Test the external interfaces and peripheral circuitry.
7. Troubleshoot and retest the board as a complete system.

Bring-up successfully verified:

- RP2040 programming and boot
- Firmware execution
- I2C interface functionality
- External load-driver functionality

This process reinforced the value of validating hardware from the power system outward instead of immediately treating a failure as a firmware problem.

---

## Engineering Takeaways

This project gave me practical experience with:

- Designing around a bare microcontroller
- Reading manufacturer datasheets and reference designs
- External QSPI flash integration
- Microcontroller clock circuitry
- Power regulation and decoupling
- USB-C implementation
- I2C hardware interfaces
- External load-driver circuitry
- Two-layer PCB placement and routing
- Hand assembly and soldering
- Firmware programming
- Hardware bring-up and fault isolation

More importantly, it taught me that completing a PCB layout is not the end of the design process. The board must also be manufacturable, understandable, testable, and practical to debug once physical hardware exists.

---

## Design-for-Test Improvements for Rev B

A second revision would preserve the working architecture while improving reviewability, test access, and maintainability:

- Organize the schematic into clearer functional or hierarchical blocks
- Improve schematic readability and design documentation
- Add dedicated test points for important power rails and interfaces
- Provide more intentional programming and debug access
- Improve silkscreen labeling and component identification
- Review power and thermal margins more formally
- Define a functional test procedure before fabrication
- Document bring-up results and validation steps more consistently

These improvements reflect one of the main lessons from the project: a successful PCB should not only function electrically—it should also be easy for another engineer to review, assemble, test, debug, and maintain.

---

## Why This Project Is in My Portfolio

This project demonstrates my ability to move beyond development boards and take ownership of a custom embedded-hardware design from the microcontroller level through physical validation.

It combines **schematic design, PCB layout, component selection, assembly, firmware programming, hardware bring-up, interface testing, and engineering reflection** in one complete project. That schematic-to-hardware workflow—and the debugging required to make the assembled system work—is the experience I want to continue building on professionally.
