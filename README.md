# Australian immigration and the economy

Project Overview

Built a model that predicted that the Australian GDP Growth would increase by 1.87% if the pandemic did not happen by using mean_absolute_error of Linear Regression and Random Forrest models.

Scraped Three tables from 
URL: https://www.homeaffairs.gov.au/research-and-stats/files/report-migration-program-2018-19.pdf,
URL: https://www.austrade.gov.au/Australian/Education/Education-data/Current-data/pivot-tables,
URL: https://www.macrotrends.net/countries/AUS/australia/gdp-growth-rate.
Where I used three different tools for scraping: BeautifulSoup, Pandas, Tabula.
Optimized Linear, Lasso and Random Forest Regression using GridsearchCV to reach the best model.
Code and Resources Used
Python Version: 3.7 Packages: BeautifulSoup,tabula,requests,pandas,numpy,sklearn,matplotlib,seaborn,csv, statsmodels.api.

# Web scraping
Used the webscraper modules BeautifulSoup, Pandas, Tabula to scrape three tables. We got the following:

Australia Immigration History - DF
columns: Year,Skill, Family, Child, Total, %Skill, %Family, Special Eligibility.

Volume of international studants in australia by year and sector - DF
Columns: Year, Higher Education, VET, Schools, ELICOS, Total;

Australian historical GDP - DF
Columns: Year, % GDP Growth, % Annual Change.

# Data Cleaning
After scraping the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

Joined all the three tables into one
created a % IMMI Growth Column
created a % Total Students Growth Column
created a Total of Students/IMMI Column
created a % Total IMMI Growth Column

# EDA
The analysis was based on three premises: Immigrants (Citizenships processed between Skill, Family, Special Eligibility, Child), Students(Higher Education, VET, Schools, ELICOS) and the  GPD Growth.

The Exploratory Data Analysis regarding GDP Growth showed a strong correlation with Special Eligibility immigrants of 0.64 and a positive one with Skill of 0.35. These two items pushed the % of Immigration Growth to a positive correlation of 0.29 despite the slightly negative correlation with Child. It was not registered a positive correlation between any of the students' items; therefore, the % Total Students Growth was negative 0,4.

# Model Building
First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.

I tried three different models:

Multiple Linear Regression – Baseline for the model Lasso Regression – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective. Random Forest – Again, with the sparsity associated with the data, I thought that this would be a good fit.

Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets.
Random Forest : MAE = 0.47 Linear Regression: MAE = 3.64 Lasso Regression: MAE = 0.71
