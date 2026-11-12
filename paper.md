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
    orcid: 0009-0000-0000-0000
    affiliation: 1
affiliations:
        - name: Independent Researcher, EC-Lab, Sao Caetano do Sul, Brazil
    index: 1
date: 12 November 2026
bibliography: paper.bib
---

# Summary

The `v17 GW Echo Detector` is an open-source Python pipeline designed to search for gravitational wave echoes following binary black hole mergers. Echoes are faint, repeating signals predicted by exotic compact object (ECO) models, wormholes, and quantum gravity corrections to classical black hole horizons, where the horizon is replaced by a reflective membrane at Planck scale. This package provides a complete, reproducible workflow from LIGO/Virgo/KAGRA strain data ingestion via the Gravitational Wave Open Science Center (GWOSC) to matched-filtering and statistical significance estimation of echo signals.

The software implements template-based echo search using combs of repeating damped sinusoids with parameters for echo time delay, relative amplitude decay, and phase inversion. It allows users to systematically test GWTC-2 and GWTC-3 events for post-merger echoes, generating SNR time series and background distributions essential for astrophysical interpretation.

# Statement of Need

The detection of gravitational waves by LIGO and Virgo has opened a new observational window into strong gravity. While standard General Relativity predicts that black holes have absorbing horizons and produce no echoes, several beyond-GR theories predict echoes appearing 0.1 to 1 second after the main merger with amplitude 10-30% of the primary signal. Existing tools like PyCBC, GWpy, and Bilby focus on primary compact binary coalescence signals, lacking dedicated, lightweight echo-search pipelines with statistical validation.

Researchers need a lightweight, reproducible, pip-installable tool to systematically test echo hypotheses without building custom scripts for each event. Current analyses often rely on unpublished code, hindering reproducibility. `v17 GW Echo Detector` fills this gap, providing an MIT-licensed package with no proprietary dependencies, extensive documentation, and continuous integration tests. It democratizes echo searches for independent researchers, students, and educators who lack access to LIGO Data Grid clusters.

# State of the field

Previous work on echo detection includes the seminal work of Abedi et al. [@Abedi2017] who reported tentative evidence for echoes in LIGO O1 data at 2.9 sigma, and Conklin et al. [@Conklin2018] who extended the search to O2. Westerweck et al. [@Westerweck2018] provided a more conservative analysis arguing for lower significance using Bayesian model selection. Nielsen et al. and Lo et al. further debated the statistical methodology.

From a software perspective, general GW toolkits exist: PyCBC for matched filtering, GWpy for data access, and cWB for unmodeled searches. However, none provide an end-to-end echo pipeline. The LIGO-Virgo Collaboration's own echo analyses use internal pipelines not released as standalone packages. Our work differs by (i) providing a unified API for data download from GWOSC, (ii) implementing adaptive whitening, Q-transform preprocessing, and notching of spectral lines, (iii) including Monte Carlo background estimation via 1000 time-slides, and (iv) packaging everything with example Jupyter notebooks reproducing GW150914 echo limits. Unlike general toolkits, it is purpose-built for echo phenomenology and designed for low computational cost on laptops.

# Software design and Architecture

The pipeline is structured in four modular Python modules totaling ~1200 lines of documented code:

1.  **Data Module (`gw_echo/data.py`):** Fetches strain data from GWOSC using `gwpy`, performs band-pass filtering (30-500 Hz), removes 60 Hz power lines, applies inverse spectrum truncation whitening, and gates glitches. Supports GPS time queries and detector selection (H1, L1, V1).

2.  **Template Module (`gw_echo/templates.py`):** Generates echo templates defined by Delta_t_echo (time between echoes), gamma (damping factor 0.1-0.9), A_echo (relative amplitude), and t_echo_start. Implements both constant-interval and log-spaced combs as described in Abedi et al. Templates are normalized for matched filter.

3.  **Search Module (`gw_echo/search.py`):** Executes matched-filtering using `scipy.signal.correlate`, computes signal-to-noise ratio (SNR) time series, identifies peaks with `scipy.signal.find_peaks`, and stacks multiple echoes for improved SNR scaling as sqrt(N_echoes).

4.  **Statistics Module (`gw_echo/stats.py`):** Estimates p-values via time-slide background analysis (1000 slides shifting L1 vs H1), computes false alarm rates, and produces diagnostic plots: SNR vs time, background histogram, and waterfall Q-transform.

The design follows PEP8, includes `pytest` unit tests achieving 85% coverage, type hints, and is installable via `pip install -e .`. Dependencies are minimal: `numpy`, `scipy`, `matplotlib`, `gwpy`, `astropy`.

# Research Impact and Use Cases

This tool enables several use cases: (i) Independent re-analysis of GWTC-2 [@GWTC2] events for echoes, allowing verification of published claims; (ii) Educational use in gravitational wave data analysis courses, where students can run a full echo search on GW150914 in <10 minutes on a laptop; (iii) Extension to third-generation detectors like Einstein Telescope and Cosmic Explorer by adjusting frequency bands; (iv) Methodological studies of echo morphology versus exotic object reflectivity.

The associated Zenodo archive is versioned and citable at [@Correa2026v17] with DOI 10.5281/zenodo.20510584, ensuring reproducibility. The project has potential to increase community participation in beyond-GR tests, which are currently limited to large collaborations.

# AI usage disclosure

No generative AI tools were used to write the core algorithm, mathematical derivations, or statistical methods. AI-assisted tools (Meta AI) were used only for documentation grammar correction, README formatting, and English translation of comments. All scientific logic, equations, template definitions, and tests were authored, reviewed, and validated by the author. No AI-generated data or results are presented.

# Acknowledgements

We acknowledge use of LIGO Open Science Center data (https://www.gw-openscience.org), the Python scientific ecosystem, and community feedback from Zenodo users.

# References
