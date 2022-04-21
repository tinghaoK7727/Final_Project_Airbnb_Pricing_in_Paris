# Final-Project: Pricing of Airbnb in Paris

## Project Goal
As one of the most visited cities in the world, Paris is with no doubts a top destination for Airbnb and its users. In this project we would like to explore the various relations among listing locations, visitor reviews, accomodation types and their potential implications on the overall pricing per night. With this project travellers who are interested in visiting Paris should be able to have a glance at the distribution of different kinds of listings within the city, and be able to predict the price range of the stay per night based on given information such as 'arrondissement' (district), number of guests, and accommodation type.

## Workflow

**Data collection:** 

We acquired listing information of Airbnb in Paris via Airbnb Scraper and extracted data including prices listed on the 19th of April 2022. 

**Data preparation:**

As the original data taken from Airbnb Scraper included a few columns with information not necessarily related to the result of this project, we first deleted some irrelevant or duplicated columns and then created new columns for further analysis with the help of get dummies encoding method. 

Also, we have spotted and removed outliers by executing a boxplot on the price per night column. Listings with price per night higher than 5000 euros and rows with NaN values were also dropped from our dataset.

Finally, in order to better categorize listings in Paris by their arrondissements, we used the latitude and longitude data to locate each address on Google Map to extract their post codes and we took all that contained '75' at the beginning. (*'75' is the code of Paris)

**EDA:**

For EDA, some patterns were discovered in our dataset (figures described as in average):

- The arrondissements with the highest number of listings are: 11th, 18th, 3rd, 10th and 15th, each with more than 600 listings per district. The arrondissement with the least listings is the 16th.
- The 1st, 6th, 7th and 8th arrondissements are the most expensive in terms of price per night (per person). Whereas the 19th and the 20th are the areas with the least expensive listings.
- Most of the listings in Paris can host up to 4 people and in the 1rst, 2nd, 3rd and 8th there are quite a few listings that can host up to 5 or more guests.
- Some correlations have been discovered: 'price group' vs 'number of guests' are 66% positively correlated and 'price group' vs 'arrondissement' are 36% positively correlated.
- The priciest accommodatiom types can be found in 'Entire Place' with prices as high as 4000 euros per night whereas the cheapest ones are found in 'Shared Rooms'. 
- In terms of price per person, the most expensive type of accommodation is 'Hotel Rooms' at 99.9 euros per person per night and the cheapest type is 'Shared Rooms' at 38.4 euros per person per night.
- Based on accommodation types, we have an average number of 3-4 guests for 'Entire Place', 2 guests for both 'Hotel Rooms' and 'Private Rooms' and 1 guest for 'Shared Rooms'.
- Due to the nature of Airbnb, 'Entire Place' represents 84% of total listings, 'Private Rooms' at 11%, and very little percentage for 'Hotel Rooms' and 'Shared Rooms' each with a representation of less than 1%.
- Listings which cost less than 200 euros per night represent 76% of total listings in Paris.

**Data Modeling:** 

Wtih the cleaned data, several machine learning models were tested in order to find models that can more accurately predict the price range of an Airbnb
lisitng given its arrondissement, listing size, and the type of dwelling (hotel rooms, entire place, priate rooms and shared rooms).

In order to predict the price range of Airbnb listings, we first created **4 bins** with the following price ranges: Bin 1 for **0-50 euros/night**, Bin 2 for **50-100 euros/night**, Bin 3 for **100-300 euros/night**, and Bin 4 for **over 300 euros/night**. Then we created the target set including only the price group values, and the rest of the variables went to the features set.

Following, we divided the datasets into train and test sets with 80% of train data and 20% of test data for the modeling.


## Modeling Approach

**Random Forest Classifier**

**Model ComplementNB**

**SGD Classifier**

**Passive Aggressive Classifier**

**Gradient Boosting Classifier**

**Bagging Classifier**

- Tested the models by originally having 11 price bins with each having a difference of 50 euros; Later reduced to 5 bins by having a difference of 100 euros in terms of price per night
- Price taken on the 18/04
- Feature selection: trial and test ('Star' removed)

## Key Findings

## Future Opportunities

## Extra information
- Trello link: https://trello.com/b/EMd3rnKW/final-project
- Presentation slides: https://docs.google.com/presentation/d/10WPmQiWsZiQyVnyJX3tzoE7p7ieWUKsDF27AI_u8dsM/edit?usp=sharing

