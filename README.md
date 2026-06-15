# Biolek Charge-Controlled Memcapacitor in Xyce

This repository contains a Xyce implementation of the Biolek charge-controlled memcapacitor model from:

Biolek, D., Biolek, Z., & Biolková, V. (2010).
"SPICE Model of Memcapacitor."
Electronics Letters.

The model was adapted to run in Xyce and validated through hysteresis and crossbar experiments.

## Features

- Charge-controlled memcapacitor
- Biolek/Joglekar window function
- Bounded state variable (0 ≤ x ≤ 1)
- Frequency-dependent hysteresis
- Xyce compatible
- Crossbar array examples (1×1 and 4×4)

## Governing Equations

State equation:

dx/dt = k q(t) w(x)

Window function:

w(x) = 1 - (2x - 1)^(2p)

Memcapacitance:

C(x) = 1 / (1/Cmax + (1/Cmin - 1/Cmax)x)

Constitutive relation:

V = q / C(x)

## Validation

The implementation was validated through:

- Pinched Q-V hysteresis loops
- Frequency collapse tests
- State boundedness tests
- Stability tests
- Crossbar matrix-vector multiplication

Observed behavior:

- Hysteresis decreases with frequency
- State variable remains within [0,1]
- Crossbar outputs match theoretical weighted sums

## Example

Xcap in out memcapacitor PARAMS:
+ Cinit=100n

.TRAN 1m 5 UIC

.PRINT TRAN V(in) V(Xcap:q)
