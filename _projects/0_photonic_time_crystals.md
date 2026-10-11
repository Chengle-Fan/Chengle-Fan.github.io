---
layout: research
title: Numerical Modeling of Photonic Time Crystals
description: Research training in time-varying photonics through Floquet band calculations and time-domain simulations
img: assets/img/projects/photonic_time_crystal/ptc_fdtd_fields.png
importance: 4
category: research
short_title: "Photonic time crystals"
platform: "Time-varying photonics"
role: "Numerical modeling"
status: "Ongoing research training"
summary: "Connecting Floquet band calculations with time-domain simulations using plane-wave expansion, temporal transfer matrices, and FDTD."
---

**Context:** Ongoing research training in time-varying and spatiotemporal photonics.

## Research focus

I am studying how temporal modulation changes electromagnetic wave propagation. This training connects frequency-domain descriptions of periodic media with direct time-domain simulations.

## Numerical approach

- Plane-wave expansion for band calculations in time-varying and spatiotemporal media.
- Temporal transfer matrices for independent checks of band calculations.
- MATLAB FDTD simulations, field reconstruction, and comparisons with published reference problems.

My current emphasis is on understanding the assumptions of each method and checking agreement between complementary numerical approaches.

## Numerical training examples

{% include figure.liquid path="assets/img/projects/photonic_time_crystal/ptc_fdtd_fields.png" title="Photonic time-crystal reference reproduction" alt="FDTD training simulations comparing pulse dynamics in a pass band and a momentum gap" class="img-fluid rounded" %}
<div class="caption">My FDTD reproduction using parameters from <a href="https://doi.org/10.1364/OPTICA.5.001390">Lustig, Sharabi, and Segev, Optica 5, 1390–1395 (2018)</a>. The panels compare pulses in a pass band and a momentum gap. These are numerical training results based on a published reference problem; the two panels use different color scales.</div>

{% include figure.liquid path="assets/img/projects/photonic_time_crystal/ptc_tmm_bands.png" title="Temporal transfer-matrix calculation" alt="Calculated Floquet bands and momentum gaps for a two-step temporal modulation" class="img-fluid rounded" %}
<div class="caption">My temporal transfer-matrix calculation for a two-step modulation model, showing real-quasifrequency pass bands and momentum gaps. This is a numerical method check within the training project.</div>

{% include figure.liquid path="assets/img/projects/photonic_time_crystal/ptc_fdtd_fft_bands.png" title="FDTD spectral reconstruction" alt="Probe-based spectral reconstruction from finite wave-packet simulations" class="img-fluid rounded" %}
<div class="caption">My FFT-based reconstruction from finite wave-packet simulations and fixed probes. The horizontal coordinate is the source center wavevector, so this plot is a probe-based numerical response rather than an exact infinite-medium eigenvalue spectrum.</div>

## Selected background reading

1. E. Lustig, Y. Sharabi, and M. Segev, “Topological aspects of photonic time crystals,” *Optica* **5**, 1390–1395 (2018). [doi:10.1364/OPTICA.5.001390](https://doi.org/10.1364/OPTICA.5.001390)
2. J. Park and B. Min, “Spatiotemporal plane wave expansion method for arbitrary space-time periodic photonic media,” *Optics Letters* **46**, 484–487 (2021). [doi:10.1364/OL.411622](https://doi.org/10.1364/OL.411622)
3. D. Ramaccia, A. Alù, A. Toscano, and F. Bilotti, “Temporal multilayer structures for designing higher-order transfer functions using time-varying metamaterials,” *Applied Physics Letters* **118**, 101901 (2021). [doi:10.1063/5.0042567](https://doi.org/10.1063/5.0042567)
