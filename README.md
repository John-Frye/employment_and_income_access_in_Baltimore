# Neighborhood Groupings by Job Access in Baltimore 
## Background
One of the central questions that city planners grapple with is how to ensure that a city's infrastructure accomodates an equitable distribution of job opportunities to all of its residents. Prominent city planning philosophies, like New Urbanism, assert that [the density and accessibility of available jobs](https://www.thoughtco.com/new-urbanism-urban-planning-design-movement-1435790) in a community are key factors in that community's economic wellbeing. However, the past few decades of sub-urban to urban transportation by car have cast doubt on this understanding. [Donald Trump typified this criticism](https://www.huffpost.com/entry/trump-suburbs-bothered-low-income-housing_n_5f21a65bc5b66a5dd638387e) by drawing a comparison between prepurtedly wealthy "suburbs" and urban poverty. In this project, I would like to analyze how different neighborhoods in Baltimore are grouped based on job accessibility metrics, and how this relates to indicators of economic vitality, like income and employment rates. By doing so, I hope to provide city-planners with a pertinent strategy to extend economic opportunities to Baltimore's less privileged communities.
## Question
How are Baltimore's neighborhoods grouped based on the variables of household income, employment rate, job density, and the ease of commute to work?
## Data Sources and Definitions
All of my data came from the Opportunity Atlas. The data is categorized as follows: 
- [Average Household Income](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/income_data.xlsx):the average household income in a population tract.
- [Employment Rate](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/employment_data.xlsx): the fraction of individuals in a population tract that have a positive source of income. 
- [Job Density](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/job_density.xlsx): the number of jobs per square mile in a population tract.
- [Fraction of Short Work Commutes](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/commuter_data.xlsx): the fraction of individuals in a population tract that can commute in less than 15 minutes to work. 
## Data Analytics
I organized the Opportunity Atlas' data on the aforementioned variables using VLOOKUP. I then calculated the mean and standard deviation for the data on the variables. The mean is the average of the data for each variable, while the standard deviation is the measurement of deviation in the dataset relative to the mean. 

I used the mean and standard deviation to calculate the z-scores for each variable. The z-score is the value of the variable in one neighborhood minus the average of all of that variables' values in other neighborhoods, divided by the standard deviation. This tells us how many standard deviations away from the mean a given value is. The z-score helps us normalize--or standardize--our data, which is important because the variables are expressed using different values, like dollars and percents. A positive z-score indicates that a value is higher than the variable's average, while a negative z-score indicates that the value is lower than average. 

Next, I selected four "anchor points" for the data. An anchor point is essentially a point of refence from which we can calculate how far away other data points are. Based on the datapoints' proximity to one anchor over another, we can determine if there is a data cluster. For example, neighborhoods with data points that share similar values for income, employment, job density, and commute time could be classified as one data cluster. 

I calculated the squared distance between the selected anchors and the variables for each neighborhood. For each neighborhood, I then calculated the minimum distance squared of the variables to those of the anchor point. This helped me determine which anchor point the neighborhood in question was closest too in terms of the similarity of its data points. 

Lastly, I added the minimum distances squared, which gives us a value that we can use to most accurately judge what our data clusters are. With this value, I used the Solver function to compute the final anchor points I would be using to determine different clusters. 
### Clusters
Each of Baltimore's neighborhoods can be categorized in the following data clusters:
- Cluster 1: this cluster contains neighborhoods characterized by low average household income, low rates of employment, low job density, and a high fraction of short commutes. As noted in the chart above, the z score of this cluster's income, employment, and job density was negative, while its fraction of short work commutes was positive. Hence, its income, employment, and job density was lower than average, while its work commute times were higher than average. This cluster represents about 31% of all Baltimore neighborhoods included in this project.
- Cluster 2: this cluster features neighborhoods with low income, high employment rates, low job density, and a low fraction of short work commutes. It represents around 48% of all Baltimore neighborhoods included in this project. 
- Cluster 3: this cluster has neighbors with high income, high employment rates, low job density, and a high fraction of short commutes. It represents around 19% percent of all Baltimore neighborhoods.
- Cluster 4: this cluster is characterized by high income, high employment rates, high job density, and a high fraction of short commutes. It represents around 2% percent of all Baltimore neighborhoods.
## Data Interpretation 
The majority of Baltimore's neighborhoods are characterized by low average household income. 

The neighborhoods with high income, employment rates, job density, and short commutes are located in downtown Baltimore. As downtown is the business and financial hub of Baltimore, it is unsurprising that its residents are more likely to have short commute times and higher paying jobs. 

The neighborhoods with the highest household incomes all fell within cluster 3. Given cluster 3's characteristic of low job density, it could imply that these wealthier areas are residential suburbs of Baltimore. Interestingly, cluster 3 still features a short average commute time. More data is necessary to determine a reason for this factor. However, I hypothesize that cluster 3's higher incomes might support car ownership, which would allow for fast commute times despite a comparative absence of jobs in cluster 3's neighborhoods. 

Baltimore's lowest income neighborhoods tended to fall within clusters 1 and 2. Both clusters are characterized by low job density. In cluster 1's case, there are low employment rates but short commute times. 

## Additional Data
## Step-by-Step Instructions
