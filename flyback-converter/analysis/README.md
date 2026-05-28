# Flyback Converter Analysis

## Design specification
- Switching frequency: 100 kHz
- Topology: isolated single-switch flyback

## Theory
A flyback converter stores energy in a coupled inductor (transformer)
during the switch on-time, then releases it to the output during the
off-time. Unlike a forward converter, energy is stored in the magnetic
field rather than transferred directly. The ideal output relationship is:

  Vout = Vin × ( D / (1 − D) ) × ( Ns / Np )

## Coupling coefficient: K = 1 vs K = 0.99
The transformer coupling was simulated at two values to compare ideal
versus realistic behavior:

- **K = 1 (ideal):** perfect coupling, no leakage inductance. Clean
  output, no voltage spikes on the switch.
- **K = 0.99 (realistic):** 1% leakage inductance. When the switch
  opens, leakage-stored energy has no return path and produces a large
  voltage spike on the switch node — the classic flyback leakage spike.
  Real designs add an RCD snubber to clamp this.

## Simulation results
- `waveforms/flyback_Vout_steady.png` — steady-state output ripple (K=1)
- `waveforms/flyback_leakage_spike_K099.png` — leakage spike on switch
  node (K=0.99)

## Key takeaway
The K=0.99 case demonstrates why flyback designs must rate the switching
device for voltages well above Vin. The leakage spike can be several
times the input voltage and is a primary driver of switch voltage
selection and snubber design.
