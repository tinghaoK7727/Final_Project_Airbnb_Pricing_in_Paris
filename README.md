# Final-Project: Pricing of Airbnb in Paris

## Project Goal
As one of the most visited cities in the world, Paris is with no doubts a top destination of Airbnb. In this project we would like to explore the various relations among listing locations, visitor reviews, accomodation types and their potential implications on the overall pricing per night. 

## Workflow

**- Data collection:** 

Acquire listing information of Airbnb in Paris via Airbnb API.

**- Data preparation:**

Delete irrelevant information for the project and create new columns for further analysis with the help of get dummies encoding method. 

Pricing outliers were also dropped by executing a boxplot.

**- EDA:**

Clusters were spooted by running a KMeans clustering. (Best K found with elbow method at K = 8), 8 listing clusters plotted.

Listing prices were centralised at 0-200 EUR / night

Some NaN values found and dropped

**- Data Modeling:** 

When cleaned data, severl machine learning models were tested in the hope of building a model that can accurately predict the price range of an Airbnb lisitng given its location (latitude and longitude), listing size, and the type of dwelling (hotel rooms, entire place, priate rooms and shared rooms).



## Approach

- Tested the models by originally having 11 price bins with each having a difference of 50 euros; Later reduced to 5 bins by having a difference of 100 euros in terms of price per night
- Price taken on the 18/04
- Feature selection: trial and test ('Star' removed)

## Key Findings

## Future Opportunities

## Extra information
- Trello link: https://trello.com/b/EMd3rnKW/final-project
- Presentation slides: https://docs.google.com/presentation/d/10WPmQiWsZiQyVnyJX3tzoE7p7ieWUKsDF27AI_u8dsM/edit?usp=sharing

