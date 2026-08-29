# pinn-gravitational-wave-reconstruction

Gravitational Waves are the ripples in the curvature of spacetime, produced by the relative motion of gravitating masses, and are detected by highly sensitive detectors such as LIGO (Hanford and Livingston), VIRGO (Italy) and KAGRA (Japan), allowing multimessenger astronomy.

With the construction of LIGO India uunderway in Maharashtra, the precision of gravitational wave localisation will increase by an order of magnitude. While these detectors are highly successful in isolating the gravitational waves, source parameter extraction remains tedious.

To combat this, investigations have been done on the use of Physics Informed Neural Networks (PINNs) which apply physical constraint on the differential equations Governing these events (particularly compact binary systems). However, an explicit comparison using the same dataset has not been done between soft constraint PINNs (physics equation entered as the penalty loss term) and hard constrained PINNs (physics equation embedded directly in the output layer via a physically-parameterized ansatz ).

This study plans to generate synthetic PyCBC BBH (binary black hole) waveforms injected into simulated Advanced LIGO noise across an SNR ∈ {8 ,15, 15, 40}, with merger-aligned segments. We use the leading-order (Newtonian-quadrupole) post-Newtonian frequency evolution equation to compare the two PINNs on : 

1. Waveform match/overlap against ground truth. 
2. Relative chirp mass error vs SNR. 
3. Training convergence behaviour.

This study is limited to the early-to-mid inspiral, non-spinning quasi-circular systems where the PN approximation is valid as it breaks down near merger.