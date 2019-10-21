# Perceptual variability and executive function (archival copy)

This is a Ma lab copy of the original GitHub repository and code base, kept here for archival purposes. Please go to https://github.com/lianaan/Perc_Var for possible updates.

 The code in this repository accompanies the following publication: 
 
 [Mihali, A, Young, AG, Adler, L, Halassa, MM, Ma, WJ. A low-level perceptual correlate of behavioral and clinical deficits in ADHD. 2018, Computational Psychiatry](https://www.mitpressjournals.org/doi/abs/10.1162/cpsy_a_00018)
## Experiment : Visuo-motor decision-making with task-switching

## Data format

The experiment code yields '.mat' files containing 'data', 'settings' and the  [Psybayes](https://github.com/lacerbi/psybayes) output 'post' and 'outputs', which are processed with the script `analysis_raw.m` and combined into `alldata.mat`.
  
 The last fields represent structs with all the trials in each of the 4 possible conditions (each itself a struct):
 
 - cond_Ori
 - cond_OriS
 - cond_Col
 - cond_ColS
 

 

##  Scripts

* `analysis_all_plots.m` takes in `alldata.mat` and the psychometric curve parameters `params_all.mat`, calls the plotting functions from `data_analysis_and_plots` and return the figures in the manuscript. 
* The psychometric curve parameters in `params_all.mat` are the output of `psych_curves_pars_fit.m`, `loglike.m` and `function_psi.m` from `model_fitting`. `psych_curves_pars_fit.m` uses a grid search to find the parameters that maximize the loglikelihood, which is computationally intensive, so it was run on the NYU HPC cluster. While Psybayes also estimated the psychometric curve parameters for each condition individually, this offline fitting was necessary since our main model assumed shared parameters across conditions.
