---
layout: research
title: Gauge-Field-Induced Duality and Self-Dual Photonic Crystals
description: Translating hopping-sign patterns and gauge flux into dual and self-dual photonic-crystal Hamiltonians, from tight-binding models to full-wave verification
img: assets/img/projects/gauge_duality/duality_schematic.png
importance: 2
category: research
short_title: "Gauge-field-induced duality"
platform: "Synthetic gauge fields"
role: "Tight-binding & full-wave modeling"
status: "Numerical research"
summary: "Engineering coupling signs and gauge flux to realize dual and self-dual photonic lattices, and exploring Hofstadter-type spectra."
---
**Context:** Undergraduate research assistant, Topological Physics Research Group (Prof. Zhen Gao), Department of EEE, SUSTech.

Unlike ordinary spatial symmetry, **duality** connects different Hamiltonian configurations in parameter space: lattices with different hopping-sign patterns can share the same spectrum under a duality transformation, while a *self-dual* configuration maps onto itself and hosts characteristic degeneracy features. The central challenge of this project was not only to construct dual tight-binding models, but to **implement their coupling signs and gauge fluxes in realistic electromagnetic structures**.

<!-- Original schematic confirmed by the author; exported from PPT_Research_experience_Chengle_Fan.pdf, p. 11. The citation below is theoretical background, not an image credit. -->
<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gauge_duality/symmetry_duality_concept.png" title="Symmetry and duality" alt="Comparison of conventional symmetry, projective symmetry, and duality transformations, with positive and negative hopping amplitudes and zero or pi gauge flux" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Conventional symmetry, projective symmetry, and duality transformations. Solid and dashed bonds denote hopping amplitudes t and −t; plaquette labels indicate the gauge flux. For the Hamiltonian-family formulation of duality, see <a href="https://doi.org/10.1103/PhysRevResearch.5.023099">Fruchart, Yao, and Vitelli, Physical Review Research 5, 023099 (2023)</a>.
</div>

## Photonic-crystal implementation

<!-- Figure source: Chengle Fan, PPT_Research_experience_Chengle_Fan.pdf, p. 17; corresponding content in Duality+Butterfly.pptx, slide 3. Cropped to remove slide chrome only. -->
<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/gauge_duality/cmr_photonic_design.png" title="CMR photonic-crystal design" alt="CMR photonic-crystal design with dielectric elements, PEC boundaries, mode phases, and three coupling-sign configurations" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    CMR photonic-crystal design with dielectric elements and perfect-electric-conductor (PEC) boundaries. The mode-phase sketches illustrate how element orientation controls the coupling-sign patterns for the dual and self-dual configurations.
</div>

## My contributions

- Constructed square-lattice tight-binding Hamiltonians with different hopping-sign and gauge-flux configurations, including dual pairs and the self-dual configuration, and analyzed their Bloch spectra and eigenmode properties.
- Implemented the corresponding photonic-crystal unit cells in COMSOL and verified that the full-wave bulk bands reproduce the tight-binding duality relation.
- Built supercell models and projected-band calculations to identify interface and boundary modes of different dimerization/gauge-flux configurations, and analyzed finite-size field distributions to distinguish bulk, edge, and corner-localized modes.
- Used FFT-based spectral reconstruction to compare finite-sample field simulations with momentum-space band predictions.
- Explored field-gradient-driven wave-packet dynamics related to non-Abelian Bloch oscillations in the self-dual platform, identifying practical limitations from small gaps, imperfect degeneracy, and possible Zener tunneling.

<!-- Figure source: Chengle Fan, PPT_Research_experience_Chengle_Fan.pdf, p. 18; corresponding content in Duality+Butterfly.pptx, slide 4. Cropped to remove slide chrome only. -->
<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/gauge_duality/photonic_duality_simulations.png" title="Photonic duality simulations" alt="Comparison of dual lattices A and B and a self-dual lattice, showing tight-binding patterns, photonic-crystal geometries, COMSOL bands in GHz, and FFT spectra" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Numerical comparison of dual lattice A, dual lattice B, and the self-dual lattice (top to bottom). Columns show the tight-binding coupling patterns, photonic-crystal designs, full-wave bands in GHz, and FFT-reconstructed spectra. The two 0-flux configurations have similar band dispersions, while the π-flux configuration shows approximately paired bands.
</div>

## Hofstadter-type spectral engineering

As an extension, I engineered rotation-dependent effective couplings of higher-order photonic modes to implement spatially modulated hopping amplitudes, and investigated Hofstadter-butterfly-like fractal spectra in finite photonic arrays using MATLAB-based spectral reconstruction.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/gauge_duality/hofstadter_spectrum.png" title="hofstadter" alt="Hofstadter-type spectrum of a photonic lattice with modulated coupling" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hofstadter-butterfly-like spectrum of a coupling-modulated photonic lattice as a function of the modulation (Harper/AAH) frequency.
</div>

This project trained me to connect Hamiltonian-level design with realistic photonic implementation — how abstract concepts such as gauge flux, coupling sign, duality, and dimerization appear as measurable photonic signatures, including band degeneracies, edge modes, and corner modes.
