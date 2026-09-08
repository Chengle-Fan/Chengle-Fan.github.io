---
layout: page
title: Terahertz Chiral Valley Edge States via Dirac Mass Engineering
description: Transferring a chiral valley edge-state mechanism from microwave to a fabrication-compatible THz platform (visiting research at NTU)
img: assets/img/projects/thz_valley/supercell_bands_3d.png
importance: 3
category: research
---

**Context:** Visiting research student, School of Physical and Mathematical Sciences, Nanyang Technological University (NTU), Singapore, with Prof. Baile Zhang (Jan–Apr 2026).

During my visit to NTU, I worked on transferring a chiral valley edge-state mechanism from the microwave regime to a **fabrication-compatible THz platform**, with the long-term goal of moving topological wave transport toward compact, chip-compatible implementations. The concept relies on Dirac mass engineering at a hybrid Chern photonic crystal (CPC) – valley photonic crystal (VPC) interface, where valley-dependent and chiral transport can coexist.

**Design challenge.** A direct geometric scaling of the microwave structure is insufficient: the original YIG-pillar concept had to be redesigned into a **laser-drilled YIG-slab geometry** compatible with the available fabrication route, and the useful bandgap window is sensitive to realistic factors — magnetic-bias orientation, hole-diameter tolerance, domain alignment, and the air layer between the YIG slab and the PEC boundaries.

## Workflow

- Scaled the original microwave design to the THz regime and evaluated whether the gyromagnetic response of YIG remains sufficient for the target topological mechanism.
- Redesigned the structure from a YIG-pillar lattice to a laser-drilled YIG-slab configuration.
- Used 2D COMSOL eigenfrequency calculations for rapid geometry screening and 3D COMSOL simulations for realistic YIG–PEC verification.
- Calculated CPC and VPC bulk bands to identify overlapping spectral windows, and built CPC–VPC supercell models to verify interface-localized modes.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/thz_valley/supercell_bands_2d.png" title="2d supercell bands" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/thz_valley/supercell_bands_3d.png" title="3d supercell bands" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Projected band structures of the CPC–VPC interface: 2D eigenfrequency approximation (left) versus full 3D YIG–PEC model (right). The overlapping topological gap supports interface-localized chiral valley edge states near 138–141 GHz.
</div>

## Fabrication-aware optimization

I swept hole-diameter errors to evaluate fabrication tolerance, included a finite air layer between the YIG slab and PEC in the 3D model, and re-optimized the structure after observing the associated frequency shift.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/thz_valley/fabrication_tolerance.png" title="fabrication tolerance" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fabrication-tolerance analysis: the CPC/VPC band edges at the K and K′ valleys as functions of the hole-diameter error. The bandgap overlap — and hence the interface state window — survives realistic micrometre-scale fabrication errors.
</div>

**Key results.** The redesigned THz platform supports a projected interface window with localized edge-state behavior after fabrication-aware optimization. The main conclusion is that this type of THz topological photonic design must be treated as a **full design loop** rather than a simple scaling problem — especially when moving toward compact, fabrication-compatible implementations. The optimized parameters were delivered to NTU collaborators for subsequent fabrication and experiments.
