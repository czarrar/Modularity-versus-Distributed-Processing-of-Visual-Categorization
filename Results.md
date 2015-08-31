# Results

## Correlation-Based Analyses

We measured the similarity in patterns of brain responses to seeing different categories of stimuli (faces, letters, etc). Patterns of responses were examined in each anatomical region of the Harvard-Oxford cortical atlas and the activity in each region was compared between pairs of categories from different runs (odd or even) using the Pearson correlation.

We found correlations between brain regions for the raw activity of each category suggests widespread similarity in the patterns. Since activity could be similar due to the fact that individuals were engaged in a task, we also used a general contrast of each category activity versus the activity of all other categories. And finally as a more rigorous alternative, we used partial correlations to examine the unique information shared between pairs of categories.

--

**Simple Classifiers**. We first wanted to see how well we could classify each visual category based on data from one set of the data. We applied this approach to the pearson correlations and then to the sparse inverse correlations using the adaptive lasso for the regularization (i.e., semi-partial correlation).

**Amount of unique information**. For the semi-partial correlation, we can quantify how many of the elements are significantly non-zero across our 20 subjects and in particular focusing on the diagonal. We can also plot the diagonal information into one 4D file (and or plot it and save it to a file). Our goal would be to see if for any region there is a significant amount of unique information for a given category.

**Relation of semi-partial correlations across regions**. Here, we want to show that the pattern of relationships between the categories is not unique across the cortex. Instead there appear to be X clusters.

- Calculate the correlation
- Calculate the partial correlation
- Plot the diagonal of the partial correlation
- Cluster the partial correlations? Or maybe just do some type of correlation between matrices.
  



  
  
  