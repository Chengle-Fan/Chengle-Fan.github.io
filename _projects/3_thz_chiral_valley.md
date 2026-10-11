---
layout: research
title: Terahertz Chiral Valley Edge States
description: Numerical modeling and optimization of terahertz photonic structures during a visiting research stay at NTU
img: assets/img/projects/thz_valley/3D.png
importance: 2
category: research
short_title: "Terahertz chiral valley edge states"
platform: "Terahertz photonic crystals"
role: "Numerical modeling & design optimization · NTU"
status: "Simulation and design study"
summary: "Modeling terahertz Chern–valley interfaces and assessing how magnetic bias, fabrication tolerances, and air layers affect the design."
---

**Context:** Visiting Research Student (Non-Graduating), Nanyang Technological University, Singapore, with Prof. Baile Zhang, January 12–April 27, 2026.

## Research focus

This project investigates topological wave transport in terahertz photonic structures. My work focused on numerical modeling and the practical constraints that arise when adapting a photonic design to a different frequency range.

## My contribution

- Developed 2D and 3D COMSOL models of Chern–valley interfaces to evaluate overlapping bulk bandgaps and interface-localized modes.
- Optimized a magneto-optic slab geometry while assessing magnetic bias, fabrication tolerances, and finite air-layer effects.

This experience strengthened my ability to compare simplified models with three-dimensional electromagnetic simulations and to incorporate fabrication constraints into numerical design.

## Numerical modeling and optimization

The following figures show my numerical modeling and design-optimization work during the NTU visit.

{% include figure.liquid path="assets/img/projects/thz_valley/3D.png" title="Three-dimensional bulk-band calculations" alt="Calculated Chern and valley photonic-crystal bulk bands and representative eigenfields with a 10 micrometre air layer" class="img-fluid rounded" %}
<div class="caption">Calculated bulk bands and representative eigenfields of the Chern photonic crystal (left) and valley photonic crystal (right), using three-dimensional models with a 10 μm air layer. These simulations examine the influence of the finite air layer on the photonic bands.</div>

### Comparing two-dimensional and three-dimensional models

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/projects/thz_valley/supercell_bands_2d.png" title="Two-dimensional interface supercell bands" alt="Calculated projected bands of a two-dimensional Chern–valley interface supercell" class="img-fluid rounded" %}
  </div>
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/projects/thz_valley/supercell_bands_3d.png" title="Three-dimensional interface supercell bands" alt="Calculated projected bands of a three-dimensional YIG–PEC Chern–valley interface supercell" class="img-fluid rounded" %}
  </div>
</div>
<div class="caption">Calculated projected band structures of the Chern–valley interface from a two-dimensional eigenfrequency model (left) and a three-dimensional YIG–PEC model (right). The comparison evaluates how the three-dimensional geometry affects the interface supercell spectrum.</div>

### Earlier design iteration

{% include figure.liquid path="assets/img/projects/thz_valley/early_design_bands_modes.png" title="Earlier-design bands and eigenmode profiles" alt="Projected bands, an enlarged spectral region, and three eigenmode field profiles from an earlier Chern–valley interface design" class="img-fluid rounded" %}
<div class="caption">Calculated projected bands and selected eigenmode field profiles for an earlier Chern–valley interface design. The marked states in the enlarged spectral region correspond to the three field profiles on the right, illustrating their different spatial localization. This figure documents an earlier design iteration; its geometry and frequencies differ from those of the later optimized design.</div>

### Fabrication-tolerance study

{% include figure.liquid path="assets/img/projects/thz_valley/fabrication_tolerance.png" title="Numerical fabrication-tolerance analysis" alt="Calculated band-edge frequencies and bandgap overlap as functions of hole-diameter error" class="img-fluid rounded" %}
<div class="caption">Numerical fabrication-tolerance analysis: calculated band-edge frequencies of the Chern and valley photonic crystals as functions of hole-diameter error. The shaded intervals show that their bandgap overlap is retained across the scanned error range.</div>
