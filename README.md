# ptb-xl

This repository explores 12-lead ECG data visually and its usage for modelling diagnoses of 'abnormal' signals.

It uses the large [PTB-XL dataset](https://physionet.org/content/ptb-xl/1.0.2/), described in our Jupyter notebook and in the corresponding paper, source 1 (Wagner et al, 2020).

We proceed as follows:
1. We perform a-priori data checks and exploration, visualizing the 12-lead signal in interactive figures.
2. We extract wave-related features: r-peaks and related heart-rate, the QRS-complex and visualize these on the figures. (TODO)
3. We perform a review of basic ECG theory and some modelling literature with respect to diagnostic classification. Furthermore, we outline multiple objectives to aid (future) ECG diagnostic classification that the current data can be explored for. 
4. We explore a benchmarking codebase for multilabel diagnostic superclass classification, and outline how we would proceed to build on this codebase.

The end-goal would be to put these in an interactive dashboard with an interpretations of why a model suggests a certain diagnostic class, for a given importance trade-off of different labels, e.g. as in source 2 (Perez Alday et al, 2020).

### Usage

The jupyter notebook is intended to be run from google colab. It's recommended to add your google drive to store and load the data and modelling results. Other than that, the notebook should be self-contained but for changing a few paths potentially.

A better step for the future would be to run these from Docker environments. Fitting the models at the end of the file are not practical from a colab environment intended for interactive use.

### Lessons learned

The dataset has an enormous amount of directions that can be explored for better diagnostic support and treatment. We've described some of those in the jupyter notebook, and any are listed in reference 1. It is large, has rich label annotations in a hierarchy and has repeat measurements on patients.

#### Approach

In this short project we've approached things fairly linearly: get to know the data and basic theory. Then we explored what has been done, trying some of those ways out to get a better feel for the data and the current state-of-the-art. It showcases how I'd start approaching this problem on a longer timeframe. I didn't shoot for new creative idea exploration (e.g. comparing metadata and signals of repeat patient measurements, or comparing label-free clustering/structuring to diagnostic labels). 

#### Wave features

Visualizing is fairly straightforward. There are many diagnostic classes however, imbalanced and with their distribution not representative of future use-case data. Extracting r-peaks and QRS-complexes in a robust manner relies on a concensus algorithm between the 12 signals (TODO). We did not test it deeply on our data, which is technically possible with the physician-provided labels of r-peaks, plus comparing how accurate they are for particular labelled wave abnormalities.

##### Multi-label classification

We then started exploring the use of an existing codebase for multi-label classification of diagnostic superclasses (the simplest multilabel problem to start out with), created by (Strodthoff et al, 2021). There are an extensive amount of methods in there, with some supposedly providing interpretations. Getting the codebase to work has been relatively straightforward. We put an emphasis on understanding the code and checking how the steps are performed, so that we can expand on it in a later step. Fitting times are fairly long and don't fit in the scope of our computational resources and timeframe. In that way, we weren't able to reproduce the results of the paper yet.

The first steps would be to include different pre-processing steps for denoising and correcting for baseline drift. Then to change to diagnostic classes as opposed to superclasses and changing the validation metric to the one of (Perez Alday et al, 2020). Ideally adding logging steps to Weights and Biases to compare example predictions, validation metrics and a break-down of which labels more often get labeled (in)correctly. Then comparing to wave-feature derived classifiers. Then trying to combine the former two methods, including static information like sex, device, age. Finally providing interpretations of why the labels have been provided. (Then there are many directions, accounting for uncertainty etc., using cut-offs, ...)

The 12-lead ECG can have many different types of noise and bias (baseline_drift). I'm curious to account for these in the modelling framework.


### References

1. PTB-XL data:
  - Wagner, P., Strodthoff, N., Bousseljot, R.-D., Kreiseler, D., Lunze, F.I., Samek, W., Schaeffter, T. (2020), PTB-XL: A Large Publicly Available ECG Dataset. Scientific Data. https://doi.org/10.1038/s41597-020-0495-6
2. Validation metric and wave feature references:
  - Perez Alday EA, Gu A, Shah AJ, Robichaux C, Wong AI, Liu C, Liu F, Rad AB, Elola A, Seyedi S, Li Q, Sharma A, Clifford GD, Reyna MA. Classification of 12-lead ECGs: the PhysioNet/Computing in Cardiology Challenge 2020. Physiol Meas. 2020 Nov 11. http://doi.org/10.1088/1361-6579/abc960.
3. Modelling of PTB-XL for different use-cases:
  - Strodthoff, N., Wagner, P., Schaeffter, T., Samek, W. (2021). "Deep Learning for ECG Analysis: Benchmarks and Insights from PTB-XL". IEEE Journal of Biomedical and Health Informatics 25, no. 5, 1519-1528.
4. Wave-feature references:
5. Interpretable multi-label classification:

See the Jupyter notebook for further references (TODO: input here)
