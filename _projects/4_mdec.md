---
layout: research
title: Cavity-Tunable Dirac Phases in a Microwave Metasurface
description: Pseudospin measurements for the MDEC manuscript and ongoing exploration of cavity-controlled refraction
img: assets/img/projects/mdec/cavity_schematic.png
importance: 4
category: research
short_title: "Cavity-tunable Dirac phases (MDEC)"
platform: "Microwave metasurfaces"
role: "Pseudospin measurements & refraction modeling"
status: "Manuscript in preparation; refraction study ongoing"
summary: "Measuring pseudospin textures in a cavity-embedded honeycomb metasurface and exploring how cavity height controls refraction at fixed frequency."
---

**Context:** Undergraduate research assistant, Topological Physics Research Group (Prof. Zhen Gao), SUSTech. I am the **third-listed co-first author** of *Cavity-Tunable Dirac Phases in a Microwave Metasurface*, a manuscript in preparation.

This project studies how the electromagnetic environment controls **Dirac phases in a fixed honeycomb microwave metasurface**. Dipolar resonators are confined between two metallic plates. Changing the cavity height tunes the balance between short-range dipole interactions and long-range cavity-mediated interactions, reshaping the bands while leaving the resonators and in-plane lattice unchanged.

The manuscript reports energy-band measurements and reconstructed pseudospin textures that distinguish **type-I, type-II, and hybrid Dirac points** with different dispersion and winding numbers. Cavity height provides a way to move and merge Dirac points through environmental control.

<!-- Figure provenance: structural schematic panels (a-b) only of Fig. 2 in 2026_8_30_MDEC_v01.pdf. Unpublished band-structure and pseudospin-result panels are not displayed. -->
<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/mdec/cavity_schematic.png" title="Cavity-embedded metasurface schematic" alt="Schematic of capped-helix resonators enclosed by metallic plates and honeycomb metasurfaces at three cavity heights" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Structural schematic: capped-helix resonators enclosed by metallic plates, with the same honeycomb lattice at three cavity heights.
</div>

## My contribution: pseudospin measurements

I **participated in experimental pseudospin measurements**. These sublattice-resolved vector network analyzer (VNA) measurements record complex transmission from the honeycomb metasurface. The relative amplitude and phase on the two sublattices support reconstruction of the pseudospin textures and characterization of Dirac-point winding numbers.

## Ongoing work: cavity-controlled refraction

Building on the same platform, I am exploring **cavity-height-controlled refractive behavior**. I use MATLAB to analyze COMSOL-derived band structures, isofrequency contours, and phase matching at the air-metasurface interface, examining how the available refracted channels change with cavity height.

The current focus is a candidate for switching between **single and dual refracted channels at the same frequency and incidence angle**. Existing band-data analysis predicts one inward channel at a cavity height of 3.3a and two at 0.8846a. This provides a starting point for a reconfigurable beam splitter. Validation of the eigenmodes, excitation by the same input polarization, energy-flow directions, and channel power is still in progress.

<!-- Figure provenance: results/refraction/three_height_fixed/optimized_two_height_pair.png accompanying the application exploration report updated 2026-10-01. -->
<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/mdec/refraction_candidate.png" title="Candidate for cavity-controlled refraction" alt="Isofrequency contours and predicted single and dual refracted paths for two cavity heights at a common frequency and incidence angle" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Numerical candidate from the ongoing refraction study: two cavity heights share the same frequency and incidence angle. The contours and predicted paths come from band-data analysis; beam profiles and transmitted power remain to be validated.
</div>

<a class="text-link" href="{{ '/publications/' | relative_url }}">Manuscript and author details <span aria-hidden="true">↗</span></a>
