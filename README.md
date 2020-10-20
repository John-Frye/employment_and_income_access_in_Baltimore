# Neighborhood Groupings by Job Access in Baltimore 
## Background
One of the central questions that city planners grapple with is how to ensure that a city's infrastructure accomodates an equitable distribution of job opportunities to all of its residents. Prominent city planning philosophies, like New Urbanism, assert that [the density and accessibility of available jobs](https://www.thoughtco.com/new-urbanism-urban-planning-design-movement-1435790) in a community are key factors in that community's economic wellbeing. However, the past few decades of sub-urban to urban transportation by car have cast doubt on this understanding. [Donald Trump typified this criticism](https://www.huffpost.com/entry/trump-suburbs-bothered-low-income-housing_n_5f21a65bc5b66a5dd638387e) by drawing a comparison between purportedly wealthy "suburbs" and urban poverty. In this project, I would like to analyze how different neighborhoods in Baltimore are grouped based on job accessibility metrics, and how this relates to indicators of economic vitality, like household income. By doing so, I hope to provide city-planners with a pertinent strategy to extend economic opportunities to less-privileged areas of Baltimore.
## Question
What strategies can city-planners employ to promote economic vitality in Baltimore's low-income communities?
## Data Sources and Definitions
All of my data came from the Opportunity Atlas. The data is categorized as follows: 
- [Average Household Income](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/income_data.xlsx):the average household income in a population tract.
- [Employment Rate](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/employment_data.xlsx): the fraction of individuals in a population tract that have a positive source of income. 
- [Job Density](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/job_density.xlsx): the number of jobs per square mile in a population tract.
- [Fraction of Short Work Commutes](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/commuter_data.xlsx): the fraction of individuals in a population tract that can commute in less than 15 minutes to work. 
## Data Analytics
I organized the Opportunity Atlas' data on the aforementioned variables using VLOOKUP. I then calculated the mean and standard deviation for the data on the variables. The mean is the average of the data for each variable, while the standard deviation is the measurement of deviation in the dataset relative to the mean. 

![alt_text](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/mean_and_stdev.png)

I used the mean and standard deviation to calculate the z-scores for each variable. The z-score is the value of the variable in one neighborhood minus the average of all of that variables' values in other neighborhoods, divided by the standard deviation. This tells us how many standard deviations away from the mean a given value is. The z-score helps us normalize--or standardize--our data, which is important because the variables are expressed using different values, like dollars and percents. A positive z-score indicates that a value is higher than the variable's average, while a negative z-score indicates that the value is lower than average. 

https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/mean_and_stdev.png

Next, I selected four "anchor points" for the data. An anchor point is essentially a point of refence from which we can calculate how far away other data points are. Based on the datapoints' proximity to one anchor over another, we can determine if there is a data cluster. For example, neighborhoods with data points that share similar values for income, employment, job density, and commute time could be classified as one data cluster. 

![alt_text](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/anchors.png)

I calculated the squared distance between the selected anchors and the variables for each neighborhood. For each neighborhood, I then calculated the minimum distance squared of the variables to those of the anchor point. This helped me determine which anchor point the neighborhood in question was closest too in terms of the similarity of its data points. 

![alt_text](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/distance_squared.png)

Lastly, I added the minimum distances squared, which gives us a value that we can use to most accurately judge what our data clusters are. With this value, I used the Solver function to compute the final anchor points I would be using to determine different clusters. 
### Clusters
Each of Baltimore's neighborhoods can be categorized in the following data clusters based on these anchor points:

![alt_text](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/clusters_and_anchors.png)

__- Cluster 1:__ this cluster contains neighborhoods characterized by low average household income, low rates of employment, low job density, and a high fraction of short commutes. As noted in the chart above, the z score of this cluster's income, employment, and job density was negative, while its fraction of short work commutes was positive. Hence, its income, employment, and job density were lower than the mean, while its work commute times were higher than the mean. This cluster represents about 31% of all Baltimore neighborhoods included in this project.

__- Cluster 2:__ this cluster features neighborhoods with low income, high employment rates, low job density, and a low fraction of short work commutes. It represents around 48% of all Baltimore neighborhoods included in this project. 

__- Cluster 3:__ this cluster has neighbors with high income, high employment rates, low job density, and a high fraction of short commutes. It represents around 19% percent of all Baltimore neighborhoods.

__- Cluster 4:__ this cluster is characterized by high income, high employment rates, high job density, and a high fraction of short commutes. It represents around 2% percent of all Baltimore neighborhoods.
### Visual Analysis of Clustering
The following series of graphs illustrate how different neighborhoods are clustered based on the variables: 

![alt_text](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/Cluster_Chart.png)

Neighborhoods from clusters 1 and 2 tend to fall below the mean for household income and job density, although there are several cluster 1 neighborhoods that feature a higher-than-average job density. Cluster 3 neighborhoods also tend to exhibit a low job density, though their average household incomes are higher than neighborhoods from other cluster types. 

![alt_text](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/Unemployment_Visual.png)

Lower income neighborhoods from clusters 1 and 2 tend to have lower employment rates, though there are a number of cluster 2 neighborhoods with higher employment rates and higher incomes. Notably, there are many cluster 2 neighborhoods whose employment rates are above the mean, but their household incomes are still below the mean. The majority of cluster 3 neighborhoods have both high incomes and high employment rates.

![alt_text](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/Commute_Visual.png)

The majority of cluster 1 neighborhoods have short commute times, but low household incomes. The majority of cluster 2 neighborhoods have low incomes and long commute times, though there are a number of neighborhoods with higher-than-mean incomes in tandem with long commute times. The majority of cluster 3 neighborhoods have high incomes and short commute times

Given the limited number of datapoints for cluster 4, it is difficult to visualize where these neighborhoods fall in various clusters. However, two of the cluster's three neighborhoods fall below the mean for household income. This is interesting because cluster 4 is characterized by higher-than-mean income rates. A possible explanation for this discrepancy is that, when all of the variables' z scores are taken into consideration, the cluster's data is pulled in a direction that is difficult to communicate via a two-dimensional graph.

## Data Interpretation 
The majority of Baltimore's neighborhoods are characterized by low average household income. 

The neighborhoods with high income, employment rates, job density, and short commutes are located in downtown Baltimore. As downtown is the business and financial hub of Baltimore, it is unsurprising that its residents are more likely to have short commute times and higher paying jobs. 

The neighborhoods with the highest household incomes all fell within cluster 3. Given cluster 3's characteristic of low job density, it could imply that these wealthier areas are residential suburbs of Baltimore. Interestingly, cluster 3 still features a short average commute time. More data is necessary to determine a reason for this factor. However, I hypothesize that cluster 3's higher incomes might support car ownership, which could allow for fast commute times despite a comparative absence of jobs in cluster 3's neighborhoods. 

Baltimore's lowest income neighborhoods tended to fall within clusters 1 and 2. As shown in the graphs, both clusters are characterized by low job density. In cluster 1's case, there are low employment rates but short commute times. Cluster 2 featured high employment rates, a characteristic of the higher income clusters, but its average household income was interestingly low. Given its low job density, it is possible that residents of cluster 2 neighborhoods are employed elsewhere in Baltimore. It begs the question as to whether or not these residents' difficulty commuting negatively impacts their income from work. 

Notably, a number of hypothetical clusters are absent. There are no clusters in Baltimore with low income, employment rates, job density, and long commute times. There are also no clusters with high income and employment, but low job density and long commutes. The first absent cluster can be attributed to Baltimore's urbanity, as low values for all four variables [are associated with poor rural areas](https://www.ers.usda.gov/topics/rural-economy-population/employment-education/rural-employment-and-unemployment). The latter cluster's absence can be attributed to a trend [described by Bloomberg CityLab](https://www.bloomberg.com/news/articles/2019-09-03/when-bad-commutes-make-bad-transportation-policy), wherein prolonged urban sprawl tends to attract jobs to once-suburban areas, reducing commute time. 

### Policy Recommendation
Baltimore City should increase investment in neighborhoods that fall within clusters 1 and 2 with the goal of increasing job density. For example, small business subsidies and funding for start-up accelarators could be targeted at these neighborhoods. These initiatives could increases the number of businesses in these areas, which would, in turn, increase employment rates. Higher employment rates could possibly increase household incomes in cluster 1 neighborhoods, which already have the advantage of fast commute times. Though cluster 2 neighborhoods already feature high employment rates, the access to nearby jobs could decrease commute times for residents who, unlike cluster 3 residents, tend to not have the pre-existing incomes to afford cars.  

However, there needs to be more research done on whether or not long commute times have a negative impact on lower income workers versus higher income workers. For example, I would like to see if workers who rely on public transportation for longer distances face wage penalties due to increased absence, tardiness, higher turnover, or lower work productivity. I would also like to research car ownership among Baltimore's higher income residents versus lower income residents. This latter point would need additional research on the length of car commute times in order to determine if car ownership improves commute times for residents in more remote Baltimore communities. If such data could show that cluster 2 residents have few cars and that cars improve commute time for workers in these areas, I would then recommend that Baltimore invests more in speedier public transport for residents who cannot afford a car. 

## Step-by-Step Instructions
Step-by-step instructions for my data analysis [can be accessed here](https://github.com/John-Frye/employment_and_income_access_in_Baltimore/blob/main/Mini_Project_3_Step_by_Step.xlsx). 
