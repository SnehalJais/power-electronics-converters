# Forward Converter Analysis

## Design specification
- Input voltage: 12 V
- Output voltage target: 5 V
- Switching frequency: 100 kHz
- Duty cycle: 0.4
- Turns ratio Np:Ns:Nreset = 1:1:1
- Topology: forward converter with three-winding (tertiary) reset

## Theory
Unlike a flyback, a forward converter transfers energy directly through
the transformer during the switch on-time. The secondary uses a
buck-style output filter (output inductor + capacitor). The ideal output
relationship is:

  Vout = Vin × D × ( Ns / Np )

For Vin = 12 V, D = 0.4, Ns/Np = 1:
  Vout = 12 × 0.4 × 1 = 4.8 V (theoretical)

## Core reset
The transformer's magnetizing flux must be reset each cycle or the core
saturates. This design uses a third (tertiary) winding with a reset
diode (D3) that returns magnetizing energy during the off-time. Duty
cycle is kept below 0.5 to ensure the core fully demagnetizes before the
next switching event.

## Simulation notes
Coupling was set to K = 0.99 with 0.1 Ω series resistance per winding.
K = 1 with three identical coupled inductors creates a singular matrix
that prevents the solver from converging — K = 0.99 is both more
physically realistic and numerically stable.

## Simulation results
- `waveforms/forward_Vout_steady.png` — startup transient followed by
  damped settling to steady state

## Observations
- Theoretical Vout: 4.8 V
- Simulated steady-state Vout: ~3.6 V
- The gap is explained by modeled losses: default silicon diode forward
  drops on D1 and D2 (~0.7 V each), 0.1 Ω winding resistance, and 1%
  coupling leakage.
- The output shows a classic underdamped second-order response: rise to
  a ~5.7 V peak, then damped settling to steady state — consistent with
  the L-C output filter (L = 100 µH, C = 100 µF, R = 10 Ω).

## Key takeaway
The forward converter delivers a regulated DC output through direct
energy transfer, with output voltage set by duty cycle and turns ratio.
The discrepancy between theoretical and simulated Vout illustrates the
real-world impact of diode and resistive losses on switching converter
performance.
