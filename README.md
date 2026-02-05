# Argo-derived Variance and Non-Gaussian Temperature Misfit Modelling

## Overview

This repository documents the methodology used to **quantify and model temperature misfits**
between a physical ocean reanalysis and independent observations, with a specific focus on
applications to **biologging tag geolocation**.

The core objective is to characterize **depth-dependent uncertainty** in ocean temperature fields
using Argo float observations, and to assess whether **Gaussian error assumptions** are appropriate
when comparing model outputs to biologging tag measurements.

Two complementary notebooks are provided:
- `variance_medit.ipynb`: estimation of depth-dependent variance from Argo–model comparisons,
- `test_of_kde.ipynb`: evaluation of normalized tag–model errors and non-Gaussian misfit modelling.

Together, these notebooks support the development of a **physically grounded and statistically
robust likelihood formulation** for temperature-based geolocation.

---

## Scientific motivation

Ocean general circulation models, even when constrained by data assimilation, remain imperfect
representations of the true ocean state. Temperature fields produced by such models may exhibit:

- Systematic biases relative to in situ observations,
- Depth-dependent variability and uncertainty,
- Non-Gaussian error structures arising from unresolved processes.

When these model fields are used in inverse problems—such as reconstructing fish trajectories from
biologging data—ignoring these characteristics can lead to **overconfident likelihoods** and
**unrealistic reconstructed tracks**.

This project addresses two key questions:

1. *How does the variance of model–observation temperature misfits depend on depth?*
2. *Are normalized temperature errors consistent with a Gaussian distribution, or do they exhibit
   systematic departures requiring a more flexible likelihood model?*

---

## Data sources

### Ocean model

The reference temperature fields are extracted from the **Copernicus Marine Service**
physical ocean reanalysis, providing daily three-dimensional temperature fields on a fixed
latitude–longitude grid.

The model captures large-scale and mesoscale ocean variability but does not fully resolve
fine-scale processes, motivating an explicit characterization of uncertainty.

### Argo float observations

Argo float temperature profiles are used as an **independent observational reference**.
These profiles provide vertically resolved, in situ measurements spanning a wide range of
depths and oceanic conditions.

Argo data are not used to correct the model state itself, but rather to **diagnose the statistical
properties of model–observation misfits**.

### Biologging tag data

Temperature and pressure records from biologging tags are used to:
- Validate the Argo-derived uncertainty estimates,
- Test whether tag–model errors behave consistently with expected variance,
- Diagnose departures from Gaussian error assumptions.

---

## Repository structure

```text
.
├── README.md
├── variance_medit.ipynb
└── test_of_kde.ipynb