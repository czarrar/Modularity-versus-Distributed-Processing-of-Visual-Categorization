# Results

## Correlation-Based Analyses

We measured the similarity in patterns of brain responses to seeing different categories of stimuli (faces, letters, etc). Patterns of responses were examined in each anatomical region of the Harvard-Oxford cortical atlas and the activity in each region was compared between pairs of categories from different runs (odd or even) using the Pearson correlation.

- We first examined the amount of information present in each category. 
    - As can be seen in the thresh figure:
    - we found X regions that had significant within ...
    - Highest correlation for each category was ...
    - Regions that had at least 4 categories with unique information in each category were found in 7 regions: list (make figure of regions found in each category). Also generate the detailed matrix plot of those regions to show. Might make all the plots but only for supplementary materials.

Can have a table that shows each region with:
    - Number of significant same category
    - Number of significant off diagonal
    - Values for each of the same category
    - Maximum value for the off-diagonal

I'm also debating about making a plot showing a simple classification with the diagonal versus the off-diagonal.

Taken together, I should be showing that faces are both spread throughout the brain and also especially localized in certain areas. Strong representation of information for the other categories isn't seen for the other categories.

It might be useful looking at the distance matrix and finding the appropriate (and reproducible) clusters. We might expect that for vehicles, the clustering splits the data into some additional categories. Actually, I could even figure this out with MDMR, by grouping the stimuli in some useful way.

### Plot All Data

1. We plot all the data. What is it that we observe? It appears that there is often confusion between xyz and across the brain faces have the most reproducible pattern. Furthermore, only certain brain regions in ventral visual cortex observe widespread detection of various categories.

As for plots for point 1, we have 48 plots, one for each region. I would keep these all in supplementary. Then, I'm going to look at the most consistently significant relationships in one summary plot (collapsing across regions) and then another one showing across regions which ones have the most relationships.

If we take just the diagonal, then it would be useful to plot that stuff as a 4D image into a file. So this is the last thing that is left... Oh and I should put into 3D the summary across categories.


### Other stuff

In supplementary materials, we can focus on the raw correlations or the contrast of each category versus everything else.

We found correlations between brain regions for the raw activity of each category suggests widespread similarity in the patterns. Since activity could be similar due to the fact that individuals were engaged in a task, we also used a general contrast of each category activity versus the activity of all other categories. And finally as a more rigorous alternative, we used partial correlations to examine the unique information shared between pairs of categories.

--

## Multivariate Correlation-Based Analyses

Now I want to replicate to some extent the analyses above using a more multivariate approach. In this case, I want to take into account all the trials. The question is if the pattern of activity across trials for each category can be discriminated. So this is like an MDMR style analysis although instead I need to fit a multinomial response. I'm now a bit unsure if this will really work.

C = M

The other idea of the distance-based approach was to reduce the computational demands. Also it would sort-of put all the regions in the same space. I could then apply the sparse group lasso. 
  
  
  
  
  
  