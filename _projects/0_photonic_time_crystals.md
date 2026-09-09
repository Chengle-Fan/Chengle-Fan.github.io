---
layout: research
title: Numerical Modeling of Photonic Time Crystals
description: Numerical study of pulse propagation in photonic time crystals, connecting Floquet band calculations with time-domain simulations
img: assets/img/projects/photonic_time_crystal/ptc_fdtd_fields.png
importance: 3
category: research
short_title: "Photonic time crystals"
platform: "Time-varying photonics"
role: "Numerical modeling"
status: "Ongoing research training"
summary: "Modeling Floquet bands and pulse dynamics in photonic time crystals using plane-wave expansion, temporal transfer matrices, and FDTD simulations."
---

**Context:** Ongoing research training in time-varying photonics. I am studying pulse propagation in photonic time crystals through numerical modeling. This work connects Floquet band calculations with time-domain simulations of pulse splitting and amplification.

A photonic time crystal is spatially uniform but periodically modulated in time. Spatial momentum remains conserved, while the temporal periodicity produces a Floquet quasifrequency spectrum. Momentum gaps can contain complex-conjugate quasifrequency branches, so a finite pulse can be amplified or attenuated instead of simply propagating through an ordinary frequency band gap.

## Numerical approach

I use three numerical methods to connect Floquet band structure with pulse dynamics: plane-wave expansion, temporal transfer matrices, and FDTD simulations.

- plane-wave expansion (PWE) for the full Floquet spectrum;
- exact temporal transfer matrices (TMM) for two-step modulation and independent band checks; and
- a finite-sample D/B-Yee FDTD solver for field evolution through temporal interfaces.

With the FDTD solver I also run Gaussian wave-packet simulations with different central wavevectors, recording fields at fixed probes and folding the spectra by FFT into the first temporal Floquet zone. The code also includes a transmission-line analogue and reproductions of published results.

## Selected numerical results

<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/photonic_time_crystal/ptc_fdtd_fields.png" title="finite-pulse photonic time-crystal simulation" alt="Two simulated spacetime maps comparing a bounded band-state pulse with an amplified momentum-gap pulse in a photonic time crystal" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    FDTD simulations of pulse propagation in a photonic time crystal using the parameters of Lustig et al. (2018). The incident pulses correspond to a pass band (1.4 μm) and a momentum gap (0.93 μm). White brackets mark the modulation interval, 220–340 fs. Color shows ln(|D|/D0); the two panels use different color scales.
</div>

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/photonic_time_crystal/ptc_tmm_bands.png" title="photonic time-crystal Floquet bands" alt="Calculated quasifrequency bands of a square-wave photonic time crystal with gray momentum-gap regions" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Exact two-layer TMM result. Blue curves are real-quasifrequency pass bands; gray regions mark momentum gaps with nonzero imaginary quasifrequency.</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/photonic_time_crystal/ptc_fdtd_fft_bands.png" title="finite-sample FDTD FFT reconstruction" alt="Heat map of the first-zone quasifrequency response reconstructed from finite-sample Gaussian wave-packet simulations and fixed probes" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Probe-based reconstruction from 101 independent finite-space Gaussian wave-packet simulations, five fixed probes, and a 16-period analysis window. The horizontal coordinate is the source center $k_c$, not an exact infinite-medium eigenvalue.</div>
    </div>
</div>

## Results and ongoing work

Using the parameters of Lustig et al. (2018), I reproduced the contrasting dynamics of pulses in a pass band and a momentum gap. The pass-band pulse remains bounded and splits at temporal interfaces, while the momentum-gap pulse is amplified during modulation. I also compared spectra reconstructed from FDTD probe signals with the Floquet bands obtained from temporal transfer matrices. The reconstructed peaks follow the stable bands, and the pulse amplification is consistent with the transfer-matrix calculation.

This project is an ongoing numerical study. I am checking how the spatial and temporal resolution affect these results, and plan to investigate the topology of the Floquet bands and refine the transmission-line model using measured component parameters.

## References

1. E. Lustig, Y. Sharabi, and M. Segev, “Topological aspects of photonic time crystals,” *Optica* **5**, 1390–1395 (2018). [doi:10.1364/OPTICA.5.001390](https://doi.org/10.1364/OPTICA.5.001390)
2. J. Park and B. Min, “Spatiotemporal plane wave expansion method for arbitrary space-time periodic photonic media,” *Optics Letters* **46**, 484–487 (2021). [doi:10.1364/OL.411622](https://doi.org/10.1364/OL.411622)
3. D. Ramaccia, A. Alù, A. Toscano, and F. Bilotti, “Temporal multilayer structures for designing higher-order transfer functions using time-varying metamaterials,” *Applied Physics Letters* **118**, 101901 (2021). [doi:10.1063/5.0042567](https://doi.org/10.1063/5.0042567)
