# Buck Converter Hardware Build

Physical breadboard build using the LM2596-ADJ. Power-up and
measurements pending lab visit.

## Components
- LM2596T-ADJ (3A adjustable buck IC, TO-220-5)
- Bourns 2100HT-181 — 180µH toroidal inductor
- 1N5822 Schottky diode (3A, 40V)
- Electrolytic capacitors — 220µF input, 220µF output
- Feedback divider: R1 = 1.0 kΩ, R2 = 3.3 kΩ (Vout ≈ 5.3 V)

## Planned measurements
- [ ] Steady-state Vout vs theoretical
- [ ] Output ripple (scope capture)
- [ ] Switch node waveform
- [ ] Efficiency vs load (η = Pout / Pin at multiple Iout points)
- [ ] Photos of the breadboard prototype
- [ ] Optional: soldered perfboard version

Build progression and measurement data will be added after lab visit.
