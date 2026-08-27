---
title: 'V17 GW Echo Detector'
tags:
- gravitational-waves
- echoes
authors:
- name: Eduardo Custodio Correa
  affiliation: Independent Researcher
bibliography: paper.bib
---
---
title: 'V17 GW Echo Detector: A Python Pipeline for Null Searches of Gravitational-Wave Echoes in 128 LIGO-Virgo-KAGRA BBH Events'
tags:
    - gravitational-waves
    - echoes
    - python
    - ligo
    - black-holes
authors:
    - name: Eduardo Custodio Correa
    affiliation: Independent Researcher
bibliography: paper.bib
---

# Summary

The V17 GW Echo Detector is an open-source Python pipeline designed to search for gravitational-wave echoes, a predicted signature of exotic compact objects (ECOs) that would replace classical black holes. The pipeline implements a null search strategy analyzing 128 binary black hole (BBH) merger events from LIGO-Virgo-KAGRA. No statistically significant echo signals were found, allowing us to place constraints on ECO models.

The software is built on `GWPy` [@gwpy], `NumPy`, and `Matplotlib`, and provides a reproducible workflow for matched-filtering echo templates against strain data.

# Statement of need

Gravitational-wave echoes are late-time repetitions of the main merger signal, predicted by models of wormholes, gravastars, and quantum black holes with reflective surfaces near the would-be horizon [@cardoso2016is]. A detection would be direct evidence of physics beyond General Relativity.

Existing search codes are often closed-source or tied to specific data releases. `V17` provides a simple, fully open, educational, and extensible implementation that any researcher can run in Google Colab via Gradio interface. It was designed to be auditable by the community and to fulfill open science requirements for the Journal of Open Source Software (JOSS).

# Methods

The V17 pipeline consists of three steps:

1.  **Data retrieval:** Uses `GWPy.TimeSeries` to fetch open strain data around each event GPS time from the Gravitational-Wave Open Science Center.
2.  **Echo template generation:** Generates a phenomenological echo comb with parameters: echo delay $\Delta t$, damping factor $\gamma$, and amplitude $A$.
3.  **Matched filtering and null statistic:** Computes signal-to-noise ratio (SNR) in a window after the merger and compares to background.

The list of 128 events includes GW150914, GW151012, GW151226, GW170104 through GW190521_074359 from GWTC-1, GWTC-2 and GWTC-2.1 [@abbott2020gwtc].

The code runs in `V17_detector.ipynb` with a Gradio UI for interactive exploration.

# Results

A null result was obtained for all 128 BBH events analyzed. No echo candidate exceeded SNR > 4 after accounting for trials factor. This null search supports the standard black hole interpretation within current sensitivity limits and provides a baseline pipeline for future O4 data.

# Availability

The code is available at https://github.com/eduardocorrea421ec-lab/v17-GW-Echo-Detector under MIT License. A Zenodo DOI will be minted upon release v1.0.

# Acknowledgements

We acknowledge the LIGO-Virgo-KAGRA collaboration for open data and the GWPy community for software support. This work used open data from the Gravitational-Wave Open Science Center.

# References
