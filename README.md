# Week-5

# We will be answering a few questions in this jupyter notebook. First, what is the northernmost airport in the United States?. Second, what is the easternmost airport in the United States?. Third, On February 12th, 2013, which New York area airport had the windiest weather?

import pandas as pd
# We will first be finding the northernmost airport in the United States. In order to do so we will be sorting the data by latitude.
airports = pd.read_csv("https://raw.githubusercontent.com/tidyverse/nycflights13/main/data-raw/airports.csv")
airports.head()
# This result shows that the northernmost airport in the United States, was Dillant Hopkins Airport. 
airports.sort_values("lat", ascending=False).head(8)
# The second question we will be answering is which airport happens to be the easternmost airport in the United States. In order to accurately sort this data and approach this question, I utilized this map: https://www.alamy.com/administrative-map-united-states-with-latitude-and-longitude-image331276569.html.
# This map provided me with a useful set of criteria in order to narrow down the data to find the easternmost airport.  
df = pd.read_csv('https://raw.githubusercontent.com/tidyverse/nycflights13/main/data-raw/airports.csv')
northeast_airports = df[(df['lat'] > 42) & (df['lat'] <= 48) & (df['lon'] >= -75) & (df['lon'] <= -65)]
northeast_airports.sort_values('lat', ascending=False)
#The easternmost airport in the United States was found to be the Northern Aroostook Regional Airport

# Finally, we will be finding which New York area airport had the windiest weather on February 12th, 2013.
speed = pd.read_csv("https://raw.githubusercontent.com/tidyverse/nycflights13/main/data-raw/weather.csv")
speed.head()
speed[(speed["month"]==2) & (speed["day"]==12) & (speed["year"]==2013)].sort_values("wind_speed", ascending=False)
# The data shows that the airport which had the windiest weather on February 12th, 2013 happened to be the Newark Liberty International Airport. However, the windspeed provided by the data is a value that happens to be almost 5x the fastest windspeed ever recorded, so it is safe to assume that that was an incorrect data value entered. Thus, without the correct data being available to us, we are to presume that the airport with the windiest weather on February 12, 2013, was LaGuardia Airport.
