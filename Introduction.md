# Introduction

In the present work, we ask if the brain represents visual categories (e.g., faces or letters) in localized regions or across a distributed set of regions *or along a continuum between the localized and distributed perspectives*.  

To test this question, we applied three analytic methods.
First, we measured univariate brain activity for each category and compared the spatial overlap in activity across categories. Less overlap would suggest localized or modular function while more overlap would suggest a distributed design.
Second, we examined category information in (multivariate) patterns of brain activity within anatomical regions-of-interest. We focused on the unique information shared by pairs of the same or different categories (e.g., face-face or face-letters) by controlling for patterns of activity found in other categories. Unique information for a category would suggest that additional processing independent of other categories is occurring for that category in this region. Although several studies have examined information shared between two patterns of brain activity (cite), few have examined the unique information …. 
Finally, our third approach combined information across the brain into one model allowing comparison of information not only within each region but also between regions. That is, we can measure if any category information in a region is redundant due to it’s presence in other brain areas. That is, we test if category information is unique not only relative to other categories but also relative to other brain regions. We use a multinomial sparse group lasso model that selects the anatomical regions and voxels within those anatomical regions that best predict each trial’s category membership. Only those regions and voxels are kept in the model that have unique information in predicting category membership.
Our analyses then test if if indeed a region has localized representations for visual categories, then that information must be unique for each category within and across brain regions.

To test this question, we used two fMRI datasets in which participant’s viewed several categories of photos in study 1, a slow-event related design (faces, letters, fruits, objects, and vehicles) and in study 2, a previously published block-design (cite; faces, houses, cats, bottles, scissors, shoes, chairs, scrambled).  

We initially applied our analyses to study 1 and then sought to replicate our effects to the broader range of categories found in study 2. Since study 2 was a block-design, we were not extract trial-level brain activity and thus couldn’t apply our classification analyses to this dataset.

during a slow event-related design [odd-ball detection task looking for circles]. apply three analytic techniques 

face parts versus configural processing. thinking re-activation vs regular activation.