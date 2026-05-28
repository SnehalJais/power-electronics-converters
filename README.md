# Power Electronics Converters

Simulation and analysis of three fundamental DC-DC converter topologies,
with hardware validation of a buck converter. Built as a self-directed
study to deepen practical understanding of switching converter design,
magnetic components, and real-world non-idealities.

## Topologies covered

| Converter | Type | Key concept demonstrated |
|---|---|---|
| Buck | Non-isolated step-down | CCM vs DCM operation |
| Flyback | Isolated, energy-storage | Leakage inductance spike (K=1 vs K=0.99) |
| Forward | Isolated, direct-transfer | Three-winding reset and core demagnetization |

## Tools

- LTspice (schematic capture and transient simulation)
- Multimeter, oscilloscope, bench supply (hardware buck)
- LM2596-ADJ, Bourns 180µH toroidal inductor, 1N5822 Schottky (hardware buck)

## What's in this repo

Each converter has its own folder with:
- `simulations/` — LTspice schematic files (`.asc`)
- `waveforms/` — captured PNG plots of simulation results
- `analysis/` — design specs, theory, observations, and what I learned

The buck converter also has a `hardware/` folder for the physical
breadboard build, scope captures, and efficiency measurements.

## Highlights

### Buck converter
Same circuit operated in both CCM and DCM by varying load conditions.
Demonstrates how operating mode affects inductor current waveform and
output regulation.

### Flyback converter
Captured at both K=1 (ideal coupling) and K=0.99 (1% leakage) to show
how real-world transformer leakage produces voltage spikes on the
switching device — explaining why flyback designs require RCD snubbers
and switches rated well above Vin.

### Forward converter
Three-winding design with tertiary reset. Theoretical output of 4.8V
(Vin × D × Ns/Np = 12 × 0.4 × 1); simulated output of ~3.6V due to
diode forward drops, winding resistance, and coupling losses.

## Status

- [x] Buck converter simulation (CCM + DCM)
- [x] Flyback converter simulation (K=1 + K=0.99)
- [x] Forward converter simulation
- [ ] Buck converter hardware build (in progress)
- [ ] Efficiency characterization vs load

## About

Built by [Snehal Jaiswal](https://linkedin.com/in/sjaiswal7), Computer
Engineering and Computer Science at UW–Madison. Interested in embedded
systems, power electronics, and hardware-software integration.
