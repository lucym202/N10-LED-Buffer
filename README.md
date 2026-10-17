# N10 LED Buffer

A small LED buffer add‑on for the Stormforge N10 (Chinese mATX NAS chassis) SAS backplane. It buffers the ACT (activity) signals so higher-current LEDs can be used while keeping the board's activity indicators functional.

## Images
See repository images for an example installation.

## Quick summary
- Cut the trace from the activity LED cathode to P11.
- Route the ACT pad(s) to the buffer board P11 connection.
- Route the buffer board LED pad(s) to the original LED cathode.
- Solder and secure; test before final mounting.
- You could redesign the board if you have trouble soldering 0603 components, but keep in mind the backplane uses 0603 resistors and LEDs

## Required tools & parts
- Fine soldering iron - 2mm chisel tip, 0.7 mm solder wire
- Flux, solder wick, fine tweezers (ESD safe)
- Thin insulated wire (30 SWG/28 AWG Kynar)
- Hobby knife or micro rotary tool for cutting PCB traces
- Magnification (I used a 100× microscope)
- Isopropyl alcohol and brush for cleaning
- 5x 2K Resistor SMD 0603
- 5x 12K Resistor SMD 0603
- 1x 470R Resistor SMD 0603
- 5x BC847B Transistor SMD SOT-23
- 1x 3.3v Zener Diode SMD 1206

## Bench testing the PCB (before attaching to backplane)
Perform a quick bench test to verify the buffer PCB is working before you solder it into the backplane.

1. For each channel, connect one LED with a 1.6 kΩ series resistor between the board 5V pad and the corresponding LED pad (one LED + resistor per channel). This provides a visible load for each output.
2. Attach the multimeter negative (COM) probe to GND on the board.
3. Apply +5V to the board by connecting +5V between the board 5V pad and GND.
4. All LEDs should be off with no ACT input asserted.

Measurements you should see (example values from the builder):
- D1 cathode voltage: should be < 3.3 V (builder saw ~2.2 V).
- ACT pad voltages (with no input): should be < 3.3 V (builder saw ~0.6 V).
- ACT pad currents (with no input): should be < 300 µA (builder saw ~220 µA).

Verification step (per-channel):
- To confirm a channel responds, briefly touch the ACT pad with the multimeter + probe while the meter is set to measure current; the corresponding LED should light.

Notes:
- These checks verify the buffer's idle voltages and the small leakage/source currents seen on the ACT inputs. If values are significantly outside the ranges above, re-check soldering, component orientation, and that there are no accidental shorts.

## Installation (short)
1. Power down and remove the backplane for access.
2. Locate and cut 5x copper traces between the LED cathode and P11; verify isolation with a multimeter.
3. For each channel, solder a thin wire from the backplane P11 pad to the buffer board ACT pad.
4. For each channel, solder a thin wire from the buffer board LED pad to the isolated LED cathode pad.
5. Connect the GND pad to any ground point on the backplane. This can be taken from the ground plane near the buffer board, scrape the solder mask off with a tool to create a solder pad
6. Connect the 5V pad to the 5V rail on the backplane. This can be taken from the positive side of any of the second row of electrolytic capacitors. Power up the backplane with a test power supply and verify with a multimeter.
7. Check continuity, verify no shorts, and bench test LED activity with a sacrificial hard drive on all ports.
8. Secure wiring with Kapton tape or super glue for strain relief, particularly on front side of PCB.
9. Reinstall and test


## Hand-soldering 0603 SMD (brief)
- Use strong magnification (100× if available), plenty of flux, and a fine-tip iron.
- Apply flux and tin one pad for each component on ACT side of the board.
- Start with the resistors, then the transistors, and finally the diode
- If you are right handed, turn board so the LED pads face left, hold the component with the tweezers in your left hand, and your soldering iron in your right
- Reflow the pad with the soldering iron, then move the component into place and allow the solder to cool
- Solder the opposite pad(s) with a minimal amount of solder, then reflow the tacked pad if needed.
- Clean flux with isopropyl alcohol. Use solder wick to remove bridges.

## Testing & troubleshooting
- If LED is off: check polarity, continuity, and solder joints.
- If LED is on when no drive is installed: Check transistor voltages, replace transistor if defective
- If channel behaves incorrectly: ensure the original trace was fully cut and the ACT wiring is solid.
- If LED is stuck on only when drive is installed verify your drive configuration, many SAS drives hold the indicator on from spin-up and blink off for activity

## Safety & notes
- This mod changes the backplane; proceed at your own risk. Use ESD precautions.
- Use a current limited power supply for testing, the entire board should draw <30mA
- Builder note: 100× microscope made assembly far easier for 0603 parts.

## License
Licensed under the CERN Open Hardware Licence v2 - Strongly Reciprocal (CERN-OHL-S-2.0). See the LICENSE file for details.

SPDX-License-Identifier: CERN-OHL-S-2.0
