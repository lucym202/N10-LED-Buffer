# N10 LED Buffer

A small LED buffer add‑on for the Stormforge N10 (Chinese mATX NAS chassis) SAS backplane. It buffers the ACT (activity) signals so higher-current LEDs can be used while keeping the board's activity indicators functional.

## Images
See repository images for an example installation.

## Quick summary
- Cut the trace from the activity LED cathode to P11.
- Route the ACT pad(s) to the buffer board P11 connection.
- Route the buffer board LED pad(s) to the original LED cathode.
- Solder and secure; test before final mounting.

## Required tools & parts
- Fine soldering iron (0.2–0.4 mm tip), 0.3 mm solder wire
- Flux, solder wick, fine tweezers (ESD safe)
- Thin insulated wire (30–34 AWG enamelled)
- Hobby knife or micro rotary tool for cutting PCB traces
- Magnification (stereo microscope or microscope — I used 100×)
- Isopropyl alcohol and brush for cleaning

## Installation (short)
1. Power down and remove the backplane for access.
2. Locate and cut the copper trace between the LED cathode and P11; verify isolation with a multimeter.
3. Solder a thin wire from the backplane P11 pad to the buffer board ACT pad.
4. Solder a thin wire from the buffer board LED pad to the isolated LED cathode pad.
5. Check continuity, verify no shorts, reinstall and test LED activity.
6. Secure wiring with Kapton tape or hot glue for strain relief.

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
- To confirm a channel responds, briefly touch the ACT pad with the multimeter + probe while the meter is set to measure current; the corresponding LED should light. Take care when using the multimeter in current mode and avoid creating a sustained short.

Notes:
- These checks verify the buffer's idle voltages and the small leakage/source currents seen on the ACT inputs. If values are significantly outside the ranges above, re-check soldering, component orientation, and that there are no accidental shorts.

## Hand-soldering 0603 SMD (brief)
- Use strong magnification (100× if available), plenty of flux, and a fine-tip iron.
- Tack one pad first: add a tiny solder bead, place the component with tweezers and reflow to hold it.
- Solder the opposite pad with a minimal amount of solder, then reflow the tacked pad if needed.
- Clean flux with isopropyl alcohol. Use solder wick to remove bridges.

## Testing & troubleshooting
- If LED is off: check polarity, continuity, and solder joints.
- If channel behaves incorrectly: ensure the original trace was fully cut and the ACT wiring is solid.

## Safety & notes
- This mod changes the backplane; proceed at your own risk. Use ESD precautions.
- Builder note: 100× microscope made assembly far easier for 0603 parts.

## License
Licensed under the CERN Open Hardware Licence v2 - Strongly Reciprocal (CERN-OHL-S-2.0). See the LICENSE file for details.

SPDX-License-Identifier: CERN-OHL-S-2.0
