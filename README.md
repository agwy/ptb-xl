# ptb-xl

This repository explores 12-lead ECG data vizually and how it can be modelled for the goal of predicting diagnoses of 'abnormal' signals.

It uses the large [PTB-XL dataset](https://physionet.org/content/ptb-xl/1.0.2/), described in our Jupyter notebook and in the corresponding paper:
Wagner, P., Strodthoff, N., Bousseljot, R.-D., Kreiseler, D., Lunze, F.I., Samek, W., Schaeffter, T. (2020), PTB-XL: A Large Publicly Available ECG Dataset. Scientific Data. https://doi.org/10.1038/s41597-020-0495-6

We proceed as follows:
1. We perform some a-priori data checks and exploration, vizualizing the 12-lead signal in interactive figures.
2. We extract wave-related features: r-peaks and related heart-rate, the QRS-complex and visualize these on the figures.
3. We perform a review of basic ECG theory and some modelling literature with respect to diagnostic classification. Furthermore, we outline multiple objectives to aid (future) ECG diagnostic classification that the current data can be explored for. 
4. We explore a benchmarking codebase for multilabel dianostic superclass classification, and outline how we would proceed to build on this codebase.

### Usage

The jupyter notebook is intended to be run from google colab. It's recommended to add your google drive to store and load the data and modelling results. Other than that, the notebook should be self-contained.

A better step for the future would be to run these from Docker environments, when enough computational resources are present. Fitting the models at the end of the file are not practical from a colab environment intended for interactive use.

### Lessons learned

The dataset has an enormous amount of directions that can be explored for better diagnostic support and treatment. We've described some of those in the jupyter notebook, and any are listed in reference 1. It is large, has rich label annotations in a hierarchy and has repeat measurements on patients.

In this short project we've approached things fairly linearly: get to know the data and basic theory, then explore what has been done, trying some of those things out to get a better feel for the data and the current state-of-the-art. It showcases how I'd start approaching this problem on a longer timeframe. I didn't shoot for new creative idea exploration (e.g. comparing metadata and signals of repeat patient measurements, or comparing label-free clustering/structuring to diagnostic labels).

The 12-lead ECG can have many different types of noise and bias (baseline_drift). I'm curious to account for these 


### References

1. PTB-XL data:
  - Wagner, P., Strodthoff, N., Bousseljot, R.-D., Kreiseler, D., Lunze, F.I., Samek, W., Schaeffter, T. (2020), PTB-XL: A Large Publicly Available ECG Dataset. Scientific Data. https://doi.org/10.1038/s41597-020-0495-6
2. Modelling:
