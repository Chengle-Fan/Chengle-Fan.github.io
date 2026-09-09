---
layout: research
title: Numerical Modeling of Photonic Time Crystals
description: Ongoing research training in Floquet-band calculations, finite-sample time-domain simulation, and numerical cross-validation
img: assets/img/projects/photonic_time_crystal/ptc_fdtd_fields.png
importance: 0
category: research
short_title: "Photonic time crystals"
platform: "Time-varying photonics"
role: "Numerical modeling & scientific validation"
status: "Ongoing research training"
summary: "Developing a Base-MATLAB toolkit that connects Floquet band theory with finite-pulse simulations and probe-based spectral reconstruction."
---

**Context:** Ongoing research training in time-varying photonics. I am developing and auditing a one-dimensional numerical toolkit for photonic time crystals, with a focus on making results traceable across independent methods rather than relying on a single solver.

A photonic time crystal is spatially uniform but periodically modulated in time. Spatial momentum remains conserved, while the temporal periodicity produces a Floquet quasifrequency spectrum. Momentum gaps can contain complex-conjugate quasifrequency branches, so a finite pulse can be amplified or attenuated instead of simply propagating through an ordinary frequency band gap.

## What I am building

The current **V3.1 MATLAB package** connects four complementary views of the same system:

- plane-wave expansion (PWE) for the full Floquet spectrum;
- exact temporal transfer matrices (TMM) for two-step modulation and independent band checks;
- a finite-sample D/B-Yee FDTD solver for field evolution through temporal interfaces; and
- per-\(k\) Gaussian-wavepacket simulations with fixed probes and FFT folding into the first temporal Floquet zone.

The package also contains a transmission-line analogue and paper-reproduction layers. Shared numerical kernels are resolved and checked explicitly, so the reproduction scripts cannot silently call stale copies of the solvers.

## Selected numerical results

<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/photonic_time_crystal/ptc_fdtd_fields.png" title="finite-pulse photonic time-crystal simulation" alt="Two simulated spacetime maps comparing a bounded band-state pulse with an amplified momentum-gap pulse in a photonic time crystal" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Finite-pulse FDTD calculation using the parameters of Lustig, Sharabi, and Segev (2018). The 1.4 μm band-state pulse remains bounded and splits at the temporal interfaces, whereas the 0.93 μm momentum-gap pulse is strongly amplified while the modulation is active. The white bracket marks the 220–340 fs modulation window. Generated from the current V3.1 code in September 2026.
</div>

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/photonic_time_crystal/ptc_tmm_bands.png" title="photonic time-crystal Floquet bands" alt="Calculated quasifrequency bands of a square-wave photonic time crystal with gray momentum-gap regions" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Exact two-layer TMM result. Blue curves are real-quasifrequency pass bands; gray regions mark momentum gaps with nonzero imaginary quasifrequency.</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/photonic_time_crystal/ptc_fdtd_fft_bands.png" title="finite-sample FDTD FFT reconstruction" alt="Heat map of the first-zone quasifrequency response reconstructed from finite-sample Gaussian-wavepacket simulations and fixed probes" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Probe-based reconstruction from 101 independent finite-space Gaussian-wavepacket simulations, five fixed probes, and a 16-period analysis window. The horizontal coordinate is the source center \(k_c\), not an exact infinite-medium eigenvalue.</div>
    </div>
</div>

## Current validation snapshot

The full package was rerun in MATLAB R2024b Update 6 before this page was added. All **8/8 package checks** and **12/12 transmission-line checks** passed, including analytic limits, PWE–TMM comparisons, temporal-interface continuity, finite-chain energy accounting, FFT folding, paper-reproduction smoke tests, and a repository-wide code analysis.

For the full 101-point photonic-time-crystal reconstruction, 137 strong stable-band peaks were matched to the Yee-corrected TMM reference. The median and 90th-percentile quasifrequency differences were \(0.00565\,\Omega\) and \(0.03466\,\Omega\), respectively. For the 60-period momentum-gap pulse, FDTD gave \(\ln(\mathrm{gain})=29.793\), compared with \(29.873\) from the exact TMM calculation.

## Scope and next steps

These results are a **numerical reproduction and solver-validation study**, not yet a claim of experimental realization. The field plot uses explicit grid and boundary assumptions because the reference paper does not report every FDTD setting. The probe spectrum measures a finite-source, finite-sample, finite-window response; its linewidth is therefore not used to infer the bulk imaginary quasifrequency. Ongoing work includes convergence studies, stronger topology diagnostics, and calibration of the transmission-line model against measured component and scattering data.

## References

1. E. Lustig, Y. Sharabi, and M. Segev, “Topological aspects of photonic time crystals,” *Optica* **5**, 1390–1395 (2018). [doi:10.1364/OPTICA.5.001390](https://doi.org/10.1364/OPTICA.5.001390)
2. J. Park and B. Min, “Spatiotemporal plane wave expansion method for arbitrary space-time periodic photonic media,” *Optics Letters* **46**, 484–487 (2021). [doi:10.1364/OL.411622](https://doi.org/10.1364/OL.411622)
3. D. Ramaccia, A. Alù, A. Toscano, and F. Bilotti, “Temporal multilayer structures for designing higher-order transfer functions using time-varying metamaterials,” *Applied Physics Letters* **118**, 101901 (2021). [doi:10.1063/5.0042567](https://doi.org/10.1063/5.0042567)
