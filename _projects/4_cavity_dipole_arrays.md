---
layout: research
title: Cavity-Mediated Topological Transport in Metallic Dipole Arrays
description: Experimental characterization and data processing for cavity-tunable metallic dipole arrays (ongoing collaboration)
img: assets/img/projects/cavity_dipole/samples.jpeg
importance: 4
category: research
short_title: "Cavity-tunable topological dipole arrays"
platform: "Microwave metamaterials"
role: "Experimental characterization & data processing"
status: "Ongoing collaboration"
summary: "Measuring transmission and near fields in metallic dipole arrays to connect cavity-controlled transport with reconstructed dispersion."
---

**Context:** Ongoing collaboration between Prof. Zhen Gao's group (SUSTech) and Prof. Mengyao Li's group (Tsinghua Shenzhen International Graduate School).

This ongoing project investigates **cavity-tunable metallic dipole arrays** in the microwave regime. A two-dimensional array of metallic resonant elements is enclosed between metallic plates. Changing the plate separation (cavity height) modifies the electromagnetic environment and the effective interactions between dipolar modes. The project examines how this affects band structure and interface-mode confinement while keeping the in-plane lattice arrangement fixed.

<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/cavity_dipole/samples_configs.jpeg" title="Cavity configurations" alt="Structural illustrations of metallic dipole arrays enclosed by plates at different separations" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Structural illustrations of metallic dipole arrays with different separations between the confining metal plates. The cavity height is a control parameter for the electromagnetic environment and effective dipole interactions.
</div>

## My role

My main contribution is **experimental characterization and data processing**: vector network analyzer (VNA) transmission measurements, near-field scanning, extraction of field amplitude and phase, and FFT-based reconstruction of measured dispersion spectra. I also compare these measurements with simulated projected bands and finite-structure field distributions to assess mode confinement and transport.

## Representative measurements and simulations

<!-- Asset provenance: exp_fft.png is ppt/media/image211.png on slide 66 (Lz=0.3a); field_sim.png is ppt/media/image218.png on slide 67 (Lz=0.333a) of Research_experience_Chengle_Fan.pptx. These are different settings, not a matched experiment/simulation pair. -->
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/cavity_dipole/exp_fft.png" title="experimental FFT dispersion" alt="Dispersion spectrum reconstructed by spatial Fourier transform of measured near fields" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Experimental dispersion reconstructed from measured near fields, for the setting labeled L<sub>z</sub> = 0.3a in the research presentation.</div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/cavity_dipole/field_sim.png" title="simulated field distribution" alt="Simulated electromagnetic field distribution of a cavity-controlled dipole-array mode" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Simulated field distribution for the setting labeled L<sub>z</sub> = 0.333a in the research presentation. This is a different cavity-height setting from the experimental spectrum shown alongside it.</div>
    </div>
</div>
This collaboration develops my experience in microwave measurements and dispersion reconstruction for systems whose response depends on both the resonator array and its surrounding cavity.

## Related background

Cavity control of topological phases has been demonstrated in a one-dimensional resonator chain: Zhao et al., <a href="https://doi.org/10.1038/s41467-025-61121-5">Observation of cavity-tunable topological phases of polaritons</a>, Nature Communications 16, 5914 (2025). This provides background for the ongoing study of two-dimensional dipole arrays described here.
