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
     affiliation:1
affiliations:
    - name: Independent Researcher, EC-Lab, Sao Caetano do Sul, Brazil
    index: 1
date: 12 November 2026
bibliography: http://paper.bib
---

Summary

The v17 GW Echo Detector is an open-source Python pipeline designed to search for gravitational wave echoes following binary black hole mergers. Echoes are faint, repeating signals predicted by exotic compact object (ECO) models, wormholes, and quantum gravity corrections to classical black hole horizons, where the horizon is replaced by a reflective membrane at Planck scale. This package provides a complete, reproducible workflow from LIGO/Virgo/KAGRA strain data ingestion via the Gravitational Wave Open Science Center (GWOSC) to matched-filtering and statistical significance estimation of echo signals.

The software implements template-based echo search using combs of repeating damped sinusoids with parameters for echo time delay, relative amplitude decay, and phase inversion. It allows users to systematically test GWTC-2 and GWTC-3 events for post-merger echoes, generating SNR time series and background distributions essential for astrophysical interpretation.

Statement of Need

The detection of gravitational waves by LIGO and Virgo has opened a new observational window into strong gravity. While standard General Relativity predicts that black holes have absorbing horizons and produce no echoes, several beyond-GR theories predict echoes appearing 0.1 to 1 second after the main merger with amplitude 10-30 percent of the primary signal. Existing tools like PyCBC, GWpy, and Bilby focus on primary compact binary coalescence signals, lacking dedicated, lightweight echo-search pipelines with statistical validation.

Researchers need a lightweight, reproducible, pip-installable tool to systematically test echo hypotheses without building custom scripts for each event. Current analyses often rely on unpublished code, hindering reproducibility. v17 GW Echo Detector fills this gap, providing an MIT-licensed package with no proprietary dependencies, extensive documentation, and continuous integration tests.

State of the field

Previous work on echo detection includes the seminal work of Abedi et al. [@Abedi2017] who reported tentative evidence for echoes in LIGO O1 data at 2.9 sigma, and Conklin et al. [@Conklin2018] who extended the search to O2. Westerweck et al. [@Westerweck2018] provided a more conservative analysis arguing for lower significance using Bayesian model selection.

From a software perspective, general GW toolkits exist: PyCBC for matched filtering, GWpy for data access, and cWB for unmodeled searches. However, none provide an end-to-end echo pipeline.

Software design and Architecture

The pipeline is structured in four modular Python modules totaling around 1200 lines of documented code: Data Module, Template Module, Search Module, and Statistics Module. The design prioritizes reproducibility via Docker, testing via pytest, and usability via Jupyter notebooks demonstrating analysis of GW150914.

Acknowledgements

We acknowledge use of LIGO Open Science Center data. We thank the JOSS reviewers for constructive feedback.

References
