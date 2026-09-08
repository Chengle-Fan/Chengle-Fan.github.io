---
layout: page
title: Gauge-Field-Induced Duality and Self-Dual Photonic Crystals
description: Translating hopping-sign patterns and gauge flux into dual and self-dual photonic-crystal Hamiltonians, from tight-binding models to full-wave verification
img: assets/img/projects/gauge_duality/self_duality_lattices.png
importance: 2
category: research
---

**Context:** Undergraduate research assistant, Topological Physics Research Group (Prof. Zhen Gao), Department of EEE, SUSTech.

Unlike ordinary spatial symmetry, **duality** connects different Hamiltonian configurations in parameter space: lattices with different hopping-sign patterns can share the same spectrum under a duality transformation, while a *self-dual* configuration maps onto itself and hosts characteristic degeneracy features. The central challenge of this project was not only to construct dual tight-binding models, but to **implement their coupling signs and gauge fluxes in realistic electromagnetic structures**.

<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gauge_duality/self_duality_lattices.png" title="self-duality" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Photonic-crystal realizations of dual lattice pairs and the self-dual configuration. The duality operation exchanges intra- and inter-cell couplings; insets show the corresponding tight-binding hopping patterns and gauge flux per plaquette.
</div>

## My contributions

- Constructed square-lattice tight-binding Hamiltonians with different hopping-sign and gauge-flux configurations, including dual pairs and the self-dual configuration, and analyzed their Bloch spectra and eigenmode properties.
- Implemented the corresponding photonic-crystal unit cells in COMSOL and verified that the full-wave bulk bands reproduce the tight-binding duality relation.
- Built supercell models and projected-band calculations to identify interface and boundary modes of different dimerization/gauge-flux configurations, and analyzed finite-size field distributions to distinguish bulk, edge, and corner-localized modes.
- Used FFT-based spectral reconstruction to compare finite-sample field simulations with momentum-space band predictions.
- Explored field-gradient-driven wave-packet dynamics related to non-Abelian Bloch oscillations in the self-dual platform, identifying practical limitations from small gaps, imperfect degeneracy, and possible Zener tunneling.

<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/gauge_duality/duality_bands.png" title="duality bands" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fourier-reconstructed spectra of finite samples overlaid with tight-binding bands: the two 0-flux dual structures (d, f) share the same spectrum, while the self-dual π-flux structure (e) exhibits the expected degeneracy at the M point.
</div>

## Hofstadter-type spectral engineering

As an extension, I engineered rotation-dependent effective couplings of higher-order photonic modes to implement spatially modulated hopping amplitudes, and investigated Hofstadter-butterfly-like fractal spectra in finite photonic arrays using MATLAB-based spectral reconstruction.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/gauge_duality/hofstadter_spectrum.png" title="hofstadter" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hofstadter-butterfly-like spectrum of a coupling-modulated photonic lattice as a function of the modulation (Harper/AAH) frequency.
</div>

This project trained me to connect Hamiltonian-level design with realistic photonic implementation — how abstract concepts such as gauge flux, coupling sign, duality, and dimerization appear as measurable photonic signatures, including band degeneracies, edge modes, and corner modes.
