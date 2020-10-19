# Neighborhood Groupings by Job Access in Baltimore 
## Background
One of the central questions that city planners grapple with is how to ensure that a city's infrastructure accomodates an equitable distribution of job opportunities to all of its residents. Prominent city planning philosophies, like New Urbanism, assert that [the density and accessibility of available jobs](https://www.thoughtco.com/new-urbanism-urban-planning-design-movement-1435790) in a community are key factors in that community's economic wellbeing. However, the past few decades of sub-urban to urban transportation by car have cast doubt on this understanding. [Donald Trump typified this criticism](https://www.huffpost.com/entry/trump-suburbs-bothered-low-income-housing_n_5f21a65bc5b66a5dd638387e) by drawing a comparison between prepurtedly wealthy "suburbs" and urban poverty. In this project, I would like to analyze how different neighborhoods in Baltimore are grouped based on job accessibility metrics, and how this relates to indicators of economic vitality, like income and employment rates. By doing so, I hope to provide city-planners with a pertinent strategy to extend economic opportunities to Baltimore's less privileged communities.
## Question
How are Baltimore's neighborhoods grouped based on the metrics of household income, employment rate, job density, and the ease of commute to work?
## Data Sources and Definitions
All of my data came from the Opportunity Atlas. The data is categorized as follows: 
-[Average Household Income](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/income_data.xlsx):the average household income in a population tract.
-[Employment Rate](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/employment_data.xlsx): the fraction of individuals in a population tract that have a positive source of income. 
-[Job Density](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/job_density.xlsx): the number of jobs per square mile in a population tract.
-[Fraction of Short Work Commutes](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/commuter_data.xlsx): the fraction of individuals in a population tract that can commute in less than 15 minutes to work. 
## Data Analytics
I organized the Opportunity Atlas' data on the aforementioned metrics using VLOOKUP. I then calculated the mean and standard deviation for the data on the metrics. The mean is the average of the data for each metric, while the standard deviation is the measurement of deviation in the dataset relative to the mean. 
I used the mean and standard deviation to calculate the z-scores for each metric. The z-score 
### Clusters
## Key Takeaways
## Additional Data
## Step-by-Step Instructions
