## Evaluation: Soft- vs. Hard-Constrained PINN Comparison

Both trained models were evaluated on the held-out test split (250
samples per SNR bucket), across three metrics tied to the physics
comparison: waveform match (time-shift-maximized normalized correlation),
L2 relative reconstruction error, and chirp mass relative error (the one
mass parameter the leading-order PN constraint actually governs).

**Table: Physics-comparison metrics by SNR bucket**

| Target SNR | Model | Match | L2 relative error | Chirp mass error |
|---|---|---|---|---|
| 8 | soft | 0.000 +/- 0.000 | 1.075 +/- 0.099 | 6.38% +/- 10.80% |
| 8 | hard | 0.000 +/- 0.000 | 50.838 +/- 10.139 | 6.12% +/- 6.49% |
| 15 | soft | 0.000 +/- 0.000 | 1.019 +/- 0.009 | 3.15% +/- 3.15% |
| 15 | hard | 0.000 +/- 0.000 | 25.403 +/- 3.514 | 2.87% +/- 3.13% |
| 25 | soft | 0.000 +/- 0.000 | 1.007 +/- 0.003 | 2.37% +/- 2.01% |
| 25 | hard | 0.000 +/- 0.000 | 15.387 +/- 2.181 | 2.44% +/- 2.06% |
| 40 | soft | 0.000 +/- 0.000 | 1.003 +/- 0.001 | 1.97% +/- 1.65% |
| 40 | hard | 0.000 +/- 0.000 | 9.415 +/- 1.033 | 2.22% +/- 2.05% |

*Figures: fig_match_vs_snr.png, fig_l2_vs_snr.png, fig_chirp_mass_err_vs_snr.png*
-- soft vs. hard model performance across the SNR grid, with standard
deviation error bars.

### Auxiliary mass parameters (Option B heads)

Total mass, symmetric mass ratio (eta), and the derived component masses
$m_1$, $m_2$ are also reported, from the ordinary supervised regression
heads described in ARCHITECTURE_SPEC.md Section 4. These are **not** tied
to the PN constraint in either model and should not be read as part of the
soft-vs-hard physics comparison -- they characterize the auxiliary heads'
own accuracy only. $m_1$, $m_2$ are recovered algebraically from predicted
total mass and eta (never learned directly).

**Table: Auxiliary parameter mean error (%) by SNR bucket**

| Target SNR | Model | Total mass | Eta | $m_1$ | $m_2$ |
|---|---|---|---|---|---|
| 8 | soft | 5.08% | 8.37% | 13.63% | 18.34% |
| 8 | hard | 4.97% | 8.86% | 14.20% | 18.45% |
| 15 | soft | 2.15% | 6.61% | 11.18% | 14.15% |
| 15 | hard | 2.19% | 7.04% | 12.65% | 14.60% |
| 25 | soft | 1.89% | 6.21% | 10.01% | 12.89% |
| 25 | hard | 1.95% | 7.07% | 12.03% | 14.39% |
| 40 | soft | 1.62% | 5.71% | 9.71% | 12.41% |
| 40 | hard | 1.86% | 7.56% | 12.70% | 15.17% |

*Figures: fig_total_mass_eta_err_vs_snr.png, fig_component_mass_err_vs_snr.png*

### Reconstructed strain

*Figure: fig_strain_reconstruction_examples.png* -- one example test sample
per SNR bucket, true clean strain vs. soft- and hard-reconstructed strain,
zoomed to the pre-merger/merger region where the chirp structure is
visible. This is the direct visual check of whether each architecture's
reconstruction is physically sensible, complementing the aggregate
match/L2 numbers above.

*Figure: fig_convergence.png* -- training/validation loss curves (log scale)
and validation chirp mass error vs. epoch, both models overlaid, showing
relative convergence speed.

Full per-sample results (including m1/m2/total_mass/eta errors) are
available in `eval_results.csv` for any additional analysis (e.g.
stratifying by chirp mass or total mass rather than only SNR).
