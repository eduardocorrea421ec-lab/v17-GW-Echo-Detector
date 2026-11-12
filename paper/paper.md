---
title: 'v17 GW Echo Detector: A Python Pipeline for Gravitational Wave Echo Detection'
tags:
- Python
- gravitational waves
- LIGO
- echo detection
- black holes
- astrophysics
- GWOSC
authors:
- name: Eduardo Custodio Correa
orcid: 0009-0004-5493-5386
affiliation: 1
affiliations:
- name: Independent Researcher, EC-Lab, Sao Caetano do Sul, Brazil
index: 1
date: 12 November 2026
bibliography: paper.bib
---

# Summary

The v17 GW Echo Detector is an open-source Python pipeline designed to search for gravitational wave echoes following binary black hole mergers. Echoes are faint, repeating signals predicted by exotic compact object (ECO) models, wormholes, and quantum gravity corrections to classical black hole horizons, where the horizon is replaced by a reflective membrane at Planck scale. This package provides a complete, reproducible workflow from LIGO/Virgo/KAGRA strain data ingestion via the Gravitational Wave Open Science Center (GWOSC) to matched-filtering and statistical significance estimation of echo signals.

# Statement of Need

The detection of gravitational waves by LIGO and Virgo has opened a new observational window into strong gravity. While standard General Relativity predicts that black holes have absorbing horizons and produce no echoes, several beyond-GR theories predict echoes appearing 0.1 to 1 second after the main merger with amplitude 10-30 percent of the primary signal. Existing tools like PyCBC, GWpy, and Bilby focus on primary compact binary coalescence signals, lacking dedicated, lightweight echo-search pipelines with statistical validation. The v17 GW Echo Detector fills this gap.

# State of the field

Previous work on echo detection includes Abedi et al. [@Abedi2017], Conklin et al. [@Conklin2018], and Westerweck et al. [@Westerweck2018]. This work builds on those theoretical foundations providing an accessible implementation.

# Software design and Architecture

The pipeline is structured in four modular Python modules totaling around 1200 lines of documented code:

- **Data Module**: Fetches and conditions strain data from GWOSC using GWpy
- **Template Module**: Generates echo templates with configurable time delay, damping factor, and phase inversion
- **Search Module**: Performs matched-filtering using PyCBC-inspired algorithms
- **Statistics Module**: Calculates p-values, false alarm rates, and Bayesian evidence for echo candidates

The code is tested on GWTC-3 events and includes Jupyter notebooks for reproduction of results.

# Acknowledgements

We acknowledge use of LIGO Open Science Center data and the open-source community.

# References
