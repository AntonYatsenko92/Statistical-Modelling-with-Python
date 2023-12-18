# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The purpose of the project was to create a statistical model that would predict the number of free bikes or empty slots available at a given bike station. This project focused on the Downtown Toronto region limiting the data to 500 bike stations (driven by the Yelp API's daily limit capacity). Once the data was pulled from the City Bikes, FourSquare, and Yelp API's the goal was to perform EDA, identify relevant variables, and perform multi-variable regression analysis to understand the relationship between the independent variables and the number of free bikes or empty bike slots available. 

## Process
#### Step 1: Gather data from City Bikes API and identify target region
#### Step 2: Pull relevant bike station data from City Bikes
#### Step 3: Use City Bikes latitude/longitude locations to pull POI data from FourSquare
#### Step 4: Use City Bikes latitude/longitude locations to pull POI data from Yelp
#### Step 5: Explore, clean, and format output data from FourSquare JSON file
#### Step 6: Explore, clean, and format output data from Yelp JSON file
#### Step 7: Combine extracted data for further processing
#### Step 8: Create relevant tables using SQLite 
#### Step 9: Create regression models based on two identified dependent variables
#### Step 10: Compare results from each model

## Results
All three (3) API's provided significant information that was combined to create the overall models. Specifically, the City Bikes API provided wholistic and complete information on Bike Stations. The FourSquare API provided good POI information, however, was limited to 10 results per endpoint, which limited the results of the overal analysis. The Yelp API provided complimentary POI information, however, in addition it provided ratings and review counts, along with 20 results per endpoint connection. One downside to the Yelp API is it was limited 500 GET requests per day, which resulted in me distilling the Bike Station count from 772 to 500 to accomodate this. One limitation in both API's is they provided name and some grouping data, however, for the high level analysis this project required, this was done manually, which added a source of error and distilled the results.

Two regression models were made for the number of empty slots at a bike station or number of free bikes available. Overall, the two variables are inversely related with the only external factor being the number of available slots at a bike station. Interesting, the regression analysis yielded a strong correlation of 0.745 whereas the number of free bikes had a weak correlation of 0.139. Another interesting observation was that both models dropped number of restaurants, which went against intution. One hypothesis for this is given that the downtown core of Toronto is saturated with restaurants this is not a deciding factor locals, however, given the data was pulled at a single point in time (as highlighted in the Challenges section) it is difficult to draw absolute conclusions. Finally, given the two variables are strongly correlated, it was interesting to observe model variability. Given more time, I would have liked to create a third model that calculates available bikes or spots as a percentage of bike station size, to avoid the externality factor. 

## Challenges 
There are three main challenges I identified in this project:

**1) Single Point in Time Data Pulls** - The data, specifically for City Bikes, was pulled at a single point in time which opens the data to significant external noise such as seasonality, time of day, weather, etc. Despite being strategic about when this data was pulled (Friday night in Toronto) there are many external factors that could have affected the results of the model.

**2) API End Point Limitations** - FourSquare and Yelp both had POI endpoint limitations of 10 and 20 results respectively per latitude/longitude GET request. Given how densely populated downtown Toronto is, this often meant results were not extended to the full 1000m radius. Overall this was not a huge concern for me given how densely populated and closely packed bike stations are in the city, however, it would have been interesting to compare the regression output against a dataset without result limits.

**3) Limited Model Options** - Given the challenges highlighted in #1 and #2 this resulted in limited time to construct a data set to conduct the regression analysis on. For example, I used key word searches to aggregate restaurants, bars, parks, etc. together, which did not fully encompass the overall data available. 


## Future Goals
My future goals are directly correlated to the three (3) challenges outlined above:

**1) Complete Multiple Data Pulls** - Given more time, I would have liked to use additional data pulls from City Bikes to remove seasonality and additional baises from the data set. Some examples would be different times of day, seasons, weather conditions, and controlling for external factors such as events, concerts, sports games, etc. This would be an exhaustive exercise, likely needing to look at historical bike data, but would remove any bias to the time of day data pull experienced in the data set

**2) Remove API Result Limitations** - To construct a complete list of independnt variables for modelling, I would have liked to omit the API endpoint result limitations. This could be done in two ways, the simplest being to pay for API access and get complete data. However, from an academic setting, this data could be gathered step-wise over a number of days by finding a way to pull radius data in increments (ie. 0-100m, 100-200m, etc.) if this option existed in both FourSquare and Yelp. 

**3) Create Different Datasets** - Due to time constraints, the raw data was cleaned following one hypothesis I had that the main key drivers of bike stations would be restaurant, bar, store, and park count. However, there are other independent variables that could have been extracted from the dataset given more time. This would allow for additional regression models to be built, creating a more complete model catalogue to identify the model of best fit. 
