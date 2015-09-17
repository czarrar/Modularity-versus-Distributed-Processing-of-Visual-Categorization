
# Methods

## Participants

Twenty right-handed, healthy adults (X females, age range Y-Z years, mean X years) participated in the study. All had normal or corrected-to-normal vision and no history of neurological or psychiatric illnesses. The protocol was approved by the Duke Human Investigation Committee, and informed consent was obtained for all participants. 

## Stimuli

336 stimuli were generated: circles, faces, fruits, letters, objects, and vehicles...

## Procedure

Participants viewed a series of color images that were randomly selected from one of five categories: Faces, Fruits, Letter Strings, Objects, and Vehicles (Fig. X). Interspersed between these stimuli were scrambled images, which were constructed by performing a two-dimensional (2D) Fourier transform of stimuli from one of the five categories, permuting the phase spectrum, and then performing an inverse transform. These “phase-scrambled” images thus had the same spatial frequencies and overall luminance as the non-scrambled stimuli but category membership was unrecognizable. Consequently, the scrambled images served as a baseline, controlling for any low-level brain response to visual stimuli. Participants were instructed to press the spacebar as quickly as possible when a target (circle) appeared. The target stimulus appeared on ∼12% of all trials or 36 times. Each image was displayed for 500 ms with a jittered interstimulus interval (ISI) that varied randomly between X and Y ms. Participants viewed a total of 60 exemplar images from each category. Images from each category were shown 5-7 times in each run with 10 runs in total.

## Image Acquisition and Preprocessing

[template...replace with own stuff] Data were acquired using a 3T Siemens TIM Trio scanner with a 32-channel head coil. Functional images were acquired using a multiband echo-planar pulse sequence (TR = 1000 ms, TE = 32 ms, flip angle = 62°, acceleration factor = 3, FOV = 210 × 210 mm, matrix = 84 × 84, slice thickness = 2.5 mm, 52 slices, voxel size = 2.5 mm3). A high-resolution structural image was acquired for registration using a 3D MP-RAGE sequence (TR = 2530 ms, TE = 2.77 ms, flip angle = 7°, FOV = 256 × 256 mm, matrix = 256 × 256, slice thickness = 1 mm, 176 slices).

Image preprocessing was performed using custom scripts (http://github.com/HumanNeuroscienceLab/repsim), which build on AFNI (v 2014-10-23 OpenMP, http://afni.nimh.nih.gov/afni) and FSL (v5.0.7, http://www.fmrib.ox.ac.uk/fsl). Structural images were skull-stripped with AFNI's 3dSkuppStrip (cite?). For the functional data, the first 6 volumes (6 s) were discarded to allow for MR equilibration. Functional images then underwent motion correction using AFNI’s 3dvolreg, skull stripping of the mean functional image using FSL’s BET (Smith 2002), spatial smoothing with a 4-mm FWHM Gaussian mask using FSL’s SUSAN (Smith and Brady 1997), high-pass filtering with a 0.01 Hz cut-off to remove low-frequency drift using FSL, and mean-based global intensity normalization. Finally, the functional images were registered to the high-resolution structural images with boundary-based registration using FSL’s Flirt. The structural images were in turn nonlinearly registered to the Montreal Neurological Institute’s MNI152 template (2 mm isotropic) using FSL’s FNIRT (Andersson et al. 2007) and this transform was then applied to the functional images in anatomical space.

## fMRI Data Analysis

### Univariate Brain Activity

Whole-brain voxel-wise regression analyses were performed at the subject-level using AFNI’s 3dDeconvolve and 3dREMLfit functions, which provide temporal pre-whitening via an autoregressive model. The linear model consisted of six explanatory variables for trials associated with faces, fruits, letter strings, objects, vehicles, or circles (the target). All variables were modeled as boxcar functions, where a value of 1 was assigned to time-points when a non-scrambled stimulus was on the screen (0.5-s per trial) and a value of 0 to time-points when the face was not on the screen, and then convolved with a double-gamma function (AFNI’s SPMG1). Regressors of no interest included baseline effects of each run and 6 head movement parameters. Contrasts were defined to identity brain regions that showed increased activity when viewing each stimuli versus the average activity for all other stimuli. Following individual analyses, whole-brain group analysis was performed using AFNI’s 3dMEMA (Chen et al. 2012), a program that incorporates individual beta precision estimates into group effects using a mixed-effects meta-analytic approach. Clusters were defined as contiguous sets of voxels with Z > 1.96 and then thresholded using Gaussian random field theory (cluster probability p < 0.05) to correct for multiple comparisons (Worsley et al. 1996). Finally, we computed the overlap in significant brain activity for each category versus the average to assess localized versus shared activity across categories. We conducted these analyses for activity across all the runs as well as the even runs and odd runs. 

### Correlation of Brain Activity Patterns

We measured category information based on patterns of brain activity in anatomical regions-of-interest (ROIs) taken from the Harvard-Oxford anatomical atlas (25% probability).  Specifically, we measured partial correlations using the adaptive lasso between pairs of activity patterns from the even versus odd runs. For each even-odd pair, we correlated activity from the same category or from different categories while controlling for any patterns of activity found in other categories not in the pair. Consequently, the correlation from the adaptive lasso reflected the amount of unique information between a pair of categories that could not be explained by activity in any other category. Furthermore by comparing activity between independent sets of even/odd runs, we were able to measure the stimulus-driven information in category-specific brain activity while ignoring any intrinsic fluctuations in brain signal related to particular runs \cite{Henriksson:Neuroimage:2015}.

We measured correlations for each subject. Group-level correlations were based on concatenating each subject’s pattern of brain activity for each category. Significance of the correlations was estimated by comparing the distribution of subject-level correlation values for each pair of activity patterns to zero using the non-parametric Mann-Whitney test (*p* < 0.05). 

We repeated the adaptive lasso correlations on functional parcellations of ventral visual areas. With these functional parcels, we aim to have more accurate ROIs that better respect boundaries between distinct brain regions. The parcels were generated using a prior region growing approach where we find representative seed time-courses of an area and grow those seed voxels into functionally homogenous regions (Blumensath et al., 2013).

### RV Coefficient

- Aim to measure the similarity of the spatial patterns in different brain regions for each of the categories.

- https://en.wikipedia.org/wiki/RV_coefficient
- https://www.researchgate.net/publication/252531898_RV-coefficient_and_its_significance_test_in_mapping_brain_functional_connectivity
- http://www.sciencedirect.com/science/article/pii/S105381190300507X
- http://www.sciencedirect.com/science/article/pii/S1053811906007105
- http://www.sciencedirect.com/science/article/pii/S1053811910013431

### Classification of Brain Activity Patterns

In our adaptive lasso (correlation) analyses, patterns of activity unique to a category could be redundant and repeat across brain areas. Here, we account for any redundant category information found across brain areas by using the multinomial sparse group lasso (cite). In one model, we identify the minimal number of regions (i.e., those anatomical regions with unique category information) that best predict the category of brain activation patterns. These classification analyses will be done for each subject and will use the pattern of activation for each individual trial or beta-series.

*Data Reduction.* For computational efficiency, we first reduce the dimensionality of each anatomical region’s voxelwise data to a subset of the top principal components. We determined those top components by comparing the eigenvalue of each component to a null distribution of eigenvalues generated from random uncorrelated data (cite). A total of 100 random sets of eigenvalues were generated. Principal components were kept if their eigenvalues were larger than 95% of the random eigenvalues (i.e., _p_ < 0.05). After obtaining the top components for each ROI, we combined those components together creating a matrix of T (trials) x P (components) where T = 300 trials and P = the total number of components across all ROIs.
[Do I need to state that the number of components will vary between regions?]

*Multinomial Sparse Group-Lasso.* Our classification approach uses patterns of brain activity to predict the category of visual stimuli in each trial for each subject. The goal is to identify the subset of anatomical regions that contain unique information in best predicting category membership. Each anatomical region is multivariate and contains the top principal components of the voxelwise brain activity in that region. Separate parameters of the data are estimated for each category in a multinomial logistic regression model, which generalizes the logistic regression to multi-class problems (cite). The model is fit using a sparse group lasso that removes redundant or unimportant groups (i.e., anatomical regions) and within important groups removes unimportant features (i.e., principal components of voxelwise data) (cite). Thus, in the sparse group lasso, the relevant components in an anatomical region are retained or discarded together. The best parameters and group/feature subset are selected by using a leave-one run out cross-validation. On each fold, data from 270 trials of each region’s top components are used to train the model and data from the remaining 30 trials are used for testing. The average classification accuracy for each trial and the average percent of anatomical regions retained by the model is calculated across all folds. We used the implementation of the multinomial sparse group lasso found in the R package msgl (cite).

Also should mention that use a permutation test to get the baseline levels of classification accuracy for each of the categories. Can also look at individual region beta-weights to see what the contribution is from each region.


As a baseline measure, we conduct classification analyses independently on each region.

- so this section, should be about running the lasso on each subject for each area separately and then using a permutation test to figure out if we should keep the region or not. this could be second…to see if those that were kept by the one model was more meaningful than running it separately. 
- then talk about running the model together. i’m not sure what actual details that I want to be giving here. I can explain the group part and goal to select regions. i probably should find imaging uses of it.

The problem that I’m facing with this stuff is that how do I do that final testing. I suppose the simplest way is to do the permutation testing but it takes forever. I could reduce the amount of time taken for the analysis by reducing the number of alphas and lambdas?


Drasgow, F. and Lissak, R. (1983) Modified parallel analysis: a procedure for examining the latent dimensionality of dichotomously scored item responses. Journal of Applied Psychology, 68(3), 363-373.
Hoyle, R. H. and Duvall, J. L. (2004). Determining the number of factors in exploratory and con- firmatory factor analysis. In D. Kaplan (Ed.): The Sage handbook of quantitative methodology for the social sciences. Thousand Oaks, CA: Sage.
Horn, J. L. (1965). A rationale and test of the number of factors in factor analysis. Psychometrika, 30, 179-185.

Mention that repeat our analyses using the functional parcellations in the ventral visual cortex.

## Notes

- Look at haxby dataset
- split our data in half and use half data that is most similar in each category (versus most dissimilar) and compare performance for those two halves.