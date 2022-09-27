# ptb-xl

This repository explores 12-lead ECG data and its usage for modelling diagnoses of 'abnormal' signals.

It uses the large [PTB-XL dataset](https://physionet.org/content/ptb-xl/1.0.2/), described in our Jupyter notebook and in the corresponding paper, source 1 (Wagner et al, 2020).

We proceed as follows:
1. We perform a-priori data checks and exploration, visualizing the 12-lead signal in interactive figures.
2. We perform a review of basic ECG theory and some modelling literature with respect to diagnostic classification. Some a-priori data useage ideas get listed.
3. We extract wave-peak features: R-peaks and related heart-rate estimates, the QRS-complex and P and T peaks. These get visualized these on figures.
4. We explore the use of the data for (multi-label) diagnostic modelling. To this purpose, we use a benchmarking codebase based on the PTB-XL data.

The end-goal would be to put these in an interactive dashboard with an interpretations of why a model suggests a certain diagnostic class, for a given importance trade-off of different labels, e.g. as in (Perez Alday et al, 2020).

### Usage

The jupyter notebook is intended to be run from google colab. It's recommended to add your google drive to store and load the data and modelling results. Other than that, the notebook should be self-contained but for changing a few paths potentially.

**Note:** To see the interactive figures, the notebook needs to be run in an active python instance.

A better step for the future would be to run these from Docker environments. Fitting the models at the end of the file is not practical from a colab environment intended for interactive use.

### Lessons learned

The dataset has an enormous amount of directions that can be explored for better diagnostic support and treatment. We've described some of those in the jupyter notebook, and any are listed in reference 1. It is large, has rich label annotations in a hierarchy and has repeat measurements on patients.

#### Approach

In this short project we've approached things fairly linearly: get to know the data and basic theory. Then we explored what has been done, trying some of those ways out to get a better feel for the data and the current state-of-the-art. It showcases how I'd start approaching this problem on a longer timeframe. I didn't shoot for new creative idea exploration on a short timeframe (e.g. comparing metadata and signals of repeat patient measurements, or comparing label-free clustering/structuring to diagnostic labels). 

#### Wave features

Visualizing is fairly straightforward. There are many diagnostic classes however, imbalanced and with their distribution not representative of future use-case data. There were many out-of-the-box algorithms to extract wave-features from 1D signals. A much more robust method would be to use all signals at the same time - or to apply a concensus algorithm on top of the 1D outputs - ignoring peaks that don't occur in at least 4 other signals for example. Finding such algorithm is a future step.

The interactive figures nicely display the estimated peaks on all the 1D signals however - together with estimated heart rates.

##### Multi-label classification

Predicting diagnoses in an automated way could make a tremendous impact in medicine. It could save a lot of time, improve diagnostic accuracy in first instance. In second instance, the actual diagnostic criteria can be explored. Automated methods can perhaps validate the current structure or propose subdivions/similaties etc.

To this end, we started using an existing codebase for multi-label classification of diagnostic superclasses (the simplest multilabel problem to start out with), created by (Strodthoff et al, 2021). There are an extensive amount of whole-signal based methods in there. Getting the codebase to work has been relatively straightforward. We put an emphasis on understanding the code and checking how the steps are performed, so that we can expand on it in a later step. 

Fitting times are fairly long. In the current timescope and computational framework, we didn't have time to perform a lot of evaluations and comparisons. In first instance, the validation metrics didn't seem to score as well as I'd hope for. More extensive evaluation by logging predictions, confusion matrices, evaluation metrics and correlation of predictors with misdiagnoses to Weights and Biases would be one of my next steps.

The codebase didn't explore the useage of certain pre-processing steps it seems (though some filters have been implemented). Comparing current the state-of-the-art with smoothing and baseline correction would be a next step. They did explore a few wavelet extracted features. Another step would be to compare with baseline models based on the peak features of the previous step, and to then potentially augment the deep learning models with these and static features such as sex, device and potentially age.

Finally, predictions need to be interpretable and put in an interactive framework to be of practical use. We've listed two sources that look at interpretability: (Strodthoff et al, 2021) and (Dongdong et al, 2021). 

There are many references on ECG modelling out there, including several physionet challenges. There's a lot of potential for ECG data both in terms of improving the diagnostic and treatment process as well as studying the cactual structure of the data.


### References

1. PTB-XL data:
  - Wagner, P., Strodthoff, N., Bousseljot, R.-D., Kreiseler, D., Lunze, F.I., Samek, W., Schaeffter, T. (2020), PTB-XL: A Large Publicly Available ECG Dataset. Scientific Data. https://doi.org/10.1038/s41597-020-0495-6
2. Validation metric and wave feature references:
  - Perez Alday EA, Gu A, Shah AJ, Robichaux C, Wong AI, Liu C, Liu F, Rad AB, Elola A, Seyedi S, Li Q, Sharma A, Clifford GD, Reyna MA (2020). "Classification of 12-lead ECGs: the PhysioNet/Computing in Cardiology Challenge 2020". Physiol Meas. http://doi.org/10.1088/1361-6579/abc960.
3. Modelling of PTB-XL for different use-cases:
  - Strodthoff, N., Wagner, P., Schaeffter, T., Samek, W. (2021). "Deep Learning for ECG Analysis: Benchmarks and Insights from PTB-XL". IEEE Journal of Biomedical and Health Informatics 25, no. 5, 1519-1528.
4. Wave-feature references:
5. Interpretable multi-label classification:
  - Dongdong Zhang, Samuel Yang, Xiaohui Yuan, Ping Zhang (2021). "Interpretable deep learning for automatic diagnosis of 12-lead electrocardiogram". iScience 24, Issue 4, 2589-0042. https://doi.org/10.1016/j.isci.2021.102373.

Codebases: TODO

See the Jupyter notebook for further references (TODO: input here)
