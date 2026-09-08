---
layout: research
title: Pseudospin-Locked Chiral Edge States in a Gyromagnetic Photonic Crystal
description: Microwave realization of an edge state that is simultaneously nonreciprocal and pseudospin-selective (manuscript in preparation)
img: assets/img/projects/gyromagnetic_phc/hero_experiment.jpeg
importance: 1
category: research
short_title: "Pseudospin-locked chiral edge states"
platform: "Microwave photonic crystals"
role: "Full-wave modeling & sample design"
status: "Manuscript in preparation"
summary: "Combining one-way edge transport with pseudospin-selective excitation, with microwave experiments and photonic routing devices."
---

**Context:** Undergraduate research assistant, Topological Physics Research Group (Prof. Zhen Gao), Department of EEE, SUSTech. A manuscript based on this work is in preparation.

Photonic quantum spin Hall (QSH) systems support pseudospin-locked *helical* edge states, but their reciprocal nature allows backscattering through pseudospin flipping at generic defects. Photonic quantum anomalous Hall (QAH) systems support nonreciprocal *chiral* edge states, but a conventional chiral channel does not carry an independently addressable pseudospin degree of freedom. This project realizes an edge state that is **simultaneously nonreciprocal and pseudospin-selective**.

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gyromagnetic_phc/concept.jpeg" title="concept" alt="Comparison of helical, chiral, and pseudospin-locked chiral edge transport" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Helical, chiral, and pseudospin-locked chiral edge states: real-space transport sketches (top) and schematic edge dispersions (bottom).
</div>

## Platform and topological phase engineering

The platform is a Wu–Hu-type gyromagnetic photonic crystal. Unit-cell deformation controls the ordering of dipole-like (p) and quadrupole-like (d) modes near the Γ point, producing the p–d band inversion underlying the QSH and conventional insulating (CI) phases. Introducing magneto-optic YIG rods under an external magnetic bias breaks physical time-reversal symmetry through the gyrotropic permeability tensor and lifts the balance between the two pseudospin sectors, so that QSH, QAH, and CI phases coexist within one design framework.

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/gyromagnetic_phc/phase_design.jpeg" title="phase engineering" alt="Unit-cell geometries, bulk bands, and pseudospin eigenfields across the topological phase transition" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Photonic-crystal design and phase diagram: bulk bands and pseudospin-resolved eigenfields track the transition between TR-broken QSH, QAH, and conventional insulating phases.
</div>

## My role

I led the full-wave modeling and sample design: bulk-band and projected-band COMSOL models for the different phases; identification of topological phase transitions through p–d mode ordering, E<sub>z</sub> field profiles, phase vortices, and spin Chern numbers; and the measurement configurations for QAH–CI and QSH–CI interfaces. I also participated in the VNA-based microwave transmission and near-field mapping experiments, processed the measured field data, and reconstructed edge-state dispersions by Fourier analysis.

## Key results

<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/gyromagnetic_phc/hero_experiment.jpeg" title="experiment" alt="Microwave sample, edge dispersions, transmission spectra, and pseudospin-selective near-field measurements" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Experimental observation of a single pseudospin-locked chiral edge state at the QAH–CI interface: sample and setup (a), simulated and FFT-reconstructed edge dispersion (b, e, f), bulk and one-way transmission spectra (c, d), and measured near-field maps under pseudospin-selective excitation (g–i).
</div>

At the QAH–CI interface, the spin Chern number difference C<sub>±</sub> = (0, −1) predicts a single pseudospin-down chiral edge state. Experimentally, rightward transmission inside the bandgap is approximately **20 dB stronger** than leftward transmission, confirming strong nonreciprocity; chiral-source near-field measurements show that the pseudospin-down source excites the guided right-propagating edge mode while the opposite pseudospin does not couple into the edge channel. The edge state also routes robustly around defects introduced on the interface.

## Device-level extension

Based on the coexistence of QSH, QAH, and CI phases in the same platform, I further designed topological devices that use pseudospin as a routing resource: a photonic **pseudospin multiplexer/demultiplexer** and a low-crosstalk **pseudospin-locked waveguide crossing**, validated in both simulation and measurement.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/gyromagnetic_phc/mux_demux.jpeg" title="mux demux" alt="Simulated and measured field distributions of the pseudospin multiplexer and demultiplexer" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/gyromagnetic_phc/waveguide_crossing.jpeg" title="waveguide crossing" alt="Simulated and measured transport through a pseudospin-locked waveguide crossing" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: pseudospin multiplexer/demultiplexer — pseudospin-up and pseudospin-down inputs are routed to different output ports. Right: pseudospin-locked waveguide crossing with low crosstalk, in simulation and experiment.
</div>
