# ptb-xl

This repository explores 12-lead ECG data vizually and how it can be modelled for the goal of predicting diagnoses of 'abnormal' signals.

It uses the large [PTB-XL dataset](https://physionet.org/content/ptb-xl/1.0.2/), described in our Jupyter notebook and in the corresponding paper:
Wagner, P., Strodthoff, N., Bousseljot, R.-D., Kreiseler, D., Lunze, F.I., Samek, W., Schaeffter, T. (2020), PTB-XL: A Large Publicly Available ECG Dataset. Scientific Data. https://doi.org/10.1038/s41597-020-0495-6

We proceed as follows:
1. We perform some a-priori data checks and exploration, vizualizing the 12-lead signal in interactive figures.
2. We extract wave-related features: r-peaks and related heart-rate, the QRS-complex and visualize these on the figures.
3. We perform a review of basic ECG theory and some modelling literature with respect to diagnostic classification. Furthermore, we outline multiple objectives to aid (future) ECG diagnostic classification that the current data can be explored for.
4. We explore a benchmarking codebase for multilabel dianostic superclass classification, and outline how we would proceed to build on this codebase.

Lessons learned:


### References

1. PTB-XL data:
  - Wagner, P., Strodthoff, N., Bousseljot, R.-D., Kreiseler, D., Lunze, F.I., Samek, W., Schaeffter, T. (2020), PTB-XL: A Large Publicly Available ECG Dataset. Scientific Data. https://doi.org/10.1038/s41597-020-0495-6
2. Modelling:
