# Final-Project: Pricing of Airbnb in Paris

## Project Goal
As one of the most visited cities in the world, Paris is with no doubts a top destination for Airbnb and its users. In this project we would like to explore the various relations among listing locations, visitor reviews, accomodation types and their potential implications on the overall pricing per night. With this project travellers who are interested in visiting Paris should be able to have a glance at the distribution of different kinds of listings within the city, and be able to predict the price range of the stay per night based on given information such as 'arrondissement' (district), number of guests, and accommodation type.

## Workflow

**Data collection:** 

Acquire listing information of Airbnb in Paris via Airbnb API and extracted data including prices listed on the 18th of April 2022. 

(to include link?)

**Data preparation:**

As the original data taken from Airbnb API included a few columns with information not necessarily related to the result of this project, we first deleted some irrelevant or duplicated columns and then created new columns for further analysis with the help of get dummies encoding method. 

Also, we have spotted and removed outliers by executing a boxplot on pricing. Listings with price per night higher than 5000 euros were dropped from our dataset.

Finally, in order to better categorize listings in Paris by their arrondissements, we used the latitude and longitude data to locate each address on Google Map to extract the post codes and took all that contained '75' at the beginning. ('75' is the code of Paris)

**EDA:**

Clusters were spooted by running a KMeans clustering. (Best K found with elbow method at K = 8), 8 listing clusters plotted.

Listing prices were centralised at 0-200 EUR / night

Some NaN values found and dropped

**Data Modeling:** 

When cleaned data, severl machine learning models were tested in the hope of building a model that can accurately predict the price range of an Airbnb lisitng given its location (latitude and longitude), listing size, and the type of dwelling (hotel rooms, entire place, priate rooms and shared rooms).



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

