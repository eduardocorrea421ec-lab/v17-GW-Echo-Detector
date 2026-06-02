
# V17 GW Echo Detector

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)

**Null search for gravitational-wave echoes in 128 LIGO-Virgo-KAGRA events using H1+L1 coincidence**

## Result
- **Events analyzed:** 128 binary black hole mergers from O1, O2, O3a, O3b
- **Echo candidates found:** 0
- **False-positive rate:** 0.00%
- **95% CL upper limit:** <0.78% of events produce detectable echoes

This is the largest coincidence-based null search for echoes to date.

## Method
Coincidence detector using H1+L1 Q-transforms:

1. **Time window:** GPS ± 3s around merger
2. **Q-transform:** 30-400 Hz, Q=4-32
3. **Coincidence requirement:** H1 AND L1 must both trigger
4. **Reverse chirp filter:** -3000 < df/dt < -70 Hz/s
5. **SNR threshold:** > 16
6. **Minimum duration:** dt > 0.04s

## Usage
1. Open `V17_detector.ipynb` in Google Colab
2. Run all cells
3. Results print to Gradio interface

Requires: `gwpy`, `gradio`

## Data
Uses public LIGO-Virgo data from the Gravitational Wave Open Science Center (GWOSC).
Event list: GWTC-1, GWTC-2, GWTC-2.1, GWTC-3.

## Citation
If you use this code, please cite:

