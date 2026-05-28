# Buck Converter Analysis

## Design specification
- Input voltage: 12 V
- Output voltage: 5 V (target)
- Switching frequency: 100 kHz
- Topology: non-isolated buck (step-down)

## Theory
A buck converter steps voltage down by chopping the input with a switch
and filtering with an L-C output stage. The ideal relationship is:

  Vout = Vin × D

where D is the duty cycle. For Vout = 5 V from Vin = 12 V:
  D = 5 / 12 ≈ 0.42

## CCM vs DCM
The same circuit operates in two modes depending on load and inductor
value:

- **Continuous Conduction Mode (CCM):** inductor current never reaches
  zero. Occurs at higher load current. Output is well-regulated and the
  Vout = Vin × D relationship holds.
- **Discontinuous Conduction Mode (DCM):** inductor current falls to
  zero for part of each cycle. Occurs at light load or small inductance.
  Output voltage rises above the CCM prediction and depends on load.

Both modes were captured from the same schematic by varying load
resistance.

## Simulation results
- `waveforms/buck_CCM.png` — inductor current stays positive (CCM)
- `waveforms/buck_DCM.png` — inductor current hits zero each cycle (DCM)

## Hardware (in progress)
A physical buck converter is being built using the LM2596-ADJ adjustable
regulator with a Bourns 2100HT-181 (180µH) toroidal inductor, a 1N5822
Schottky freewheel diode, and electrolytic input/output capacitors.
Output voltage will be set to ~5.3 V via a 1kΩ / 3.3kΩ feedback divider.
Scope captures, efficiency measurements, and assembly photos to follow.
