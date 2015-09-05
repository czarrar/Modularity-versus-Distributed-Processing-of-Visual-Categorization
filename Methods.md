
# Methods

These data were previously published in XYZ.

## Participants

Twenty right-handed, healthy adults (X females, age range Y-Z years, mean X years) participated in the study. All had normal or corrected-to-normal vision and no history of neurological or psychiatric illnesses. The protocol was approved by the Duke Human Investigation Committee, and informed consent was obtained for all participants. 

## Stimuli

360 stimuli were generated: circles, faces, fruits, letters, objects, and vehicles...

## Procedure

Participants viewed a series of color images that were randomly selected from one of five categories: Faces, Fruits, Letter Strings, Objects, and Vehicles (Fig. 1). Interspersed between these stimuli were scrambled images, which were constructed by performing a two-dimensional (2D) Fourier transform of stimuli from one of the five categories, permuting the phase spectrum, and then performing an inverse transform. These “phase-scrambled” images thus had the same spatial frequencies and overall luminance as the non-scrambled stimuli but category membership was unrecognizable. Consequently, the scrambled images served as a baseline, controlling for any low-level brain response to visual stimuli. Participants were instructed to press the spacebar as quickly as possible when a target (circle) appeared. The target stimulus appeared on ∼12% of all trials or 36 times. Each image was displayed for 500 ms with a jittered interstimulus interval (ISI) that varied randomly between X and Y ms. Participants viewed a total of 60 exemplar images from each category. Images from each category were shown 5-7 times in each run with 10 runs in total.

## Image Acquisition and Preprocessing

[template] Data were acquired using a 3T Siemens TIM Trio scanner with a 32-channel head coil. Functional images were acquired using a multiband echo-planar pulse sequence (TR = 1000 ms, TE = 32 ms, flip angle = 62°, acceleration factor = 3, FOV = 210 × 210 mm, matrix = 84 × 84, slice thickness = 2.5 mm, 52 slices, voxel size = 2.5 mm3). A high-resolution structural image was acquired for registration using a 3D MP-RAGE sequence (TR = 2530 ms, TE = 2.77 ms, flip angle = 7°, FOV = 256 × 256 mm, matrix = 256 × 256, slice thickness = 1 mm, 176 slices).

Image preprocessing was performed using custom scripts (http://github.com/HumanNeuroscienceLab/repsim), which build on AFNI (v 2014-10-23 OpenMP, http://afni.nimh.nih.gov/afni) and FSL (v5.0.7, http://www.fmrib.ox.ac.uk/fsl). Structural images were skull-stripped with AFNI's 3dSkuppStrip (cite?). For the functional data, the first 6 volumes (6 s) were discarded to allow for MR equilibration. Functional images then underwent motion correction using AFNI’s 3dvolreg, skull stripping of the mean functional image using FSL’s BET (Smith 2002), spatial smoothing with a 4-mm FWHM Gaussian mask using FSL’s SUSAN (Smith and Brady 1997), high-pass filtering with a 0.01 Hz cut-off to remove low-frequency drift using FSL, and mean-based global intensity normalization. Finally, the functional images were registered to the high-resolution structural images with boundary-based registration using FSL’s Flirt. The structural images were in turn nonlinearly registered to the Montreal Neurological Institute’s MNI152 template (2 mm isotropic) using FSL’s FNIRT (Andersson et al. 2007) and this transform was then applied to the functional images in anatomical space.

## fMRI Data Analysis

### Brain Activity

Univariate analyses provided ?. Whole-brain voxel-wise regression analyses were performed at the subject-level using AFNI’s 3dDeconvolve and 3dREMLfit functions, which provide temporal pre-whitening via an autoregressive model. The linear model consisted of six explanatory variables for trials associated with faces, fruits, letter strings, objects, vehicles, or circles (the target). All variables were modeled as boxcar functions, where a value of 1 was assigned to time-points when a non-scrambled stimulus was on the screen (0.5-s per trial) and a value of 0 to time-points when the face was not on the screen, and then convolved with a double-gamma function (AFNI’s SPMG1). Regressors of no interest included baseline effects of each run and 6 head movement parameters. Contrasts were defined to identity brain regions that showed increased activity when viewing each stimuli versus the average activity for all other stimuli. Following individual analyses, whole-brain group analysis was performed using AFNI’s 3dMEMA (Chen et al. 2012), a program that incorporates individual beta precision estimates into group effects using a mixed-effects meta-analytic approach. Clusters were defined as contiguous sets of voxels with Z > 1.96 and then thresholded using Gaussian random field theory (cluster probability p < 0.05) to correct for multiple comparisons (Worsley et al. 1996).

## Correlations

**Simple Classifiers**. We first wanted to see how well we could classify each visual category based on data from one set of the data. We applied this approach to the pearson correlations and then to the sparse inverse correlations using the adaptive lasso for the regularization (i.e., semi-partial correlation).

**Amount of unique information**. For the semi-partial correlation, we can quantify how many of the elements are significantly non-zero across our 20 subjects and in particular focusing on the diagonal. We can also plot the diagonal information into one 4D file (and or plot it and save it to a file). Our goal would be to see if for any region there is a significant amount of unique information for a given category.

**Relation of semi-partial correlations across regions**. Here, we want to show that the pattern of relationships between the categories is not unique across the cortex. Instead there appear to be X clusters.

- Calculate the correlation
- Calculate the partial correlation
- Plot the diagonal of the partial correlation
- Cluster the partial correlations? Or maybe just do some type of correlation between matrices.
  
  
  
  