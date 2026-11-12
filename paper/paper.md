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

The software implements template-based echo search using combs of repeating damped sinusoids with parameters for echo time delay, relative amplitude decay, and phase inversion. It allows users to systematically test GWTC-2 and GWTC-3 events for post-merger echoes, generating SNR time series and background distributions essential for astrophysical interpretation.

# Statement of Need
