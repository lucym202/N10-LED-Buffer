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
