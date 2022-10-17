# Analyzing Aggravated Burglaries in Davidson County

### Part 1 - Data Gathering using APIs

1. A dataset containing details about Metro Nashville Police Department reported incidents is available at https://data.nashville.gov/Police/Metro-Nashville-Police-Department-Incidents/2u6v-ujjs. Make use of the API to find all aggravated burglary incidents () that were reported during the nine month period from January 1, 2022 through September 30, 2021. (**Hint:** Check out the [API Docs](https://dev.socrata.com/foundry/data.nashville.gov/2u6v-ujjs) to see how to narrow down the response to just the desired results).

2. Using the [2020 American Community Survey API](https://www.census.gov/data/developers/data-sets/acs-5year.html), obtain, for each census tract, the population (B01001_001E in the detailed tables) and the median income (S1901_C01_012E in the subject tables). Hint: Tennessee's FIPS code is 47 and Davidson County's FIPS code is 37. 

### Part 2 - Spatial Joining and Data Merging

3. Download the 2020 census tract shapefiles for Tennessee from https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.2020.html. (The FIPS code for Tennessee is 47). Perform a spatial join to determine the census tract in which each burglary incident occurred. 

4. Aggregate the data by census tract. **Warning:** each incident can appear multiple times if there are multiple victims, so be sure that you aren't double-counting any incidents. Which census tract had the highest number of burglaries? Which census tract had the highest number of burglaries per 1000 residents? **Note:** Make sure that you keep all census tracts, not just those that have had a burglary.

5. Merge in the census data that you gathered in question 2. Remove any rows that have zero population or negative median income values.

### Part 3 - Statistical Modeling

6. Finally, we'll build some statistical models to see how well we can explain the number of aggravated burglaries using the median income of each census tract. Start with some EDA to look at the relationship between median income and number of aggravated burglaries.

7. Fit a Poisson regression model with target variable the rate of burglaries per census tract and with predictor the median income. Offset using the log of the population so that we are looking at the rate of burglaries per population instead of the number of burglaries. How can you interpret the meaning of the output?

8. **Bonus:** Try out a negative binomial model. To get started with a negative binomial model, you can check out [this tutorial](https://timeseriesreasoning.com/contents/negative-binomial-regression-model/). How does this model compare to the Poisson model?

Additional Resources for Generalized Linear Models:
* DataCamp - [Generalized Linear Models in Python](https://learn.datacamp.com/courses/generalized-linear-models-in-python)
* [Beyond Multiple Linear Regression, Chapter 4](https://bookdown.org/roback/bookdown-BeyondMLR/ch-poissonreg.html) Warning - the code in this book is all R, but the conceptual explanations are very clear.
* [This set of notes](https://apwheele.github.io/MathPosts/PoissonReg.html#negative-binomial-when-the-poisson-does-not-fit), which talks about the problem of overdispersion.