# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The goal of this project is to leverage python skills such as retrieving data from API's, parsing data and creating dataframes, and building statistical models. 

## Process
Step 1: Build a BikeStation DataFrame using a single API request

Step 2: Build POI DataFrames using functions for each API and a loop of the BikeStation DataFrame. Using latitude/longitude inputs from each BikeStations, parse through the function's results for relevant data and append lists and restart loop. Resulting lists were used to build DataFrames.

FourSquare Relevant Data: Shortest Distance/Index(Stations)
- Only evaluating nearest locations

Yelp Relevant Data: ALL Distances/Custom Index/Names/Ratings
- Each bike station would end up with more than one sublist for distance/rating/name, but was needed in order to address questions relating to top 10 restaurants. 

Step 3: Join BikeStation and POI DataFrames
- Sort Yelp DataFrame by shortest distance and group by index to bring back to down to 164 entries. 
- Join all 3 on index (represents a bike station id)

Visualizations: 
Used seaborn/matplotlib to plot POI distances against usage or against total bikes

SQL: 
-Created new database and followed same steps for Python to join. 


Step 4: Model
- Using the combined dataframe from step 3, created a multiple linear regression to predict the total bikes based on distance to a nearby POI. 



## Results
The yelp API provided more complete data because if the FourSquare API could not find the requested POI type within the radius, an empty list would be provided. As a result, additional code had to be used to replace empty values. However when the YELP API encountered the same issues, the radius parameter description confirmed that their API will provide data that may exceed the radius in order to avoid empty lists. 

## Challenges:

API Documentation: 
- Each API has their own documentation with some API's having different compatibilities. I.e CityBike API was not compable with using the Param_dict in a get function, and parameters had to be directly specified through the URL. 

Live Data (CityBike API): 
- Have to adjust interpretations because data can fluctuate throughout the day (Running the API request at night will provide different usage rates than during the daytime when people are actively using bikes). 

FourSquare Multiple Categories per Location: 
- Found that results (i.e a restaurant) can have multiple category ID's which made it harder to single down in the API request for a specific category. 

FourSquare Limit Parameter:
- FourSquare's limit parameter having a maximum of 50 results prevented me from analyzing the number of POI types in a 1KM radius because many of the bikestations returned the maximum of 50 results which would not help provide any useful insight. 

Rate Limits
- Yelp had a maximum of 500 API requests per day. Therefore I had to choose a location (Miami with 164) that wouldn't exceed the rate limit. 
- To avoid being locked out from submitting requests, I tested BikeStation input loops against smalller copies (approximately 15 entries) to ensure the number of requests match the number of stations.  


## Future Goals
Build a classification model that predicts if a bike station is likely to be fully used (percentage) based on how many POIs. 
