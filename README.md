# Final-Project: Pricing of Airbnb in Paris

## Project Goal
As one of the most visited cities in the world, Paris is with no doubts a top destination for Airbnb and its users. In this project we would like to explore the various relations among listing locations, listing sizes, accomodation types and their potential implications on the overall pricing per night. With this project travellers who are interested in visiting Paris should be able to have a glance at the distribution of different kinds of listings within the city, and be able to predict the price range of the stay per night based on given information such as 'arrondissement' (district), number of guests, and accommodation type.

## Workflow

**Data collection:** 

We acquired listing information of Airbnb in Paris via **Airbnb Scraper** and extracted data including prices listed on the **19th of April 2022**. 

**Data preparation:**

As the original data taken from Airbnb Scraper included a few columns with information not necessarily related to the result of this project, we first deleted some irrelevant or duplicated columns and then created new columns for further analysis with the help of get dummies encoding method. 

Also, we have spotted and removed outliers by executing a boxplot on the price per night column. Listings with price per night higher than 5000 euros and rows with NaN values were also dropped from our dataset.

Furthermore, to add more features to the existing ones and to better correspond to the potential needs of travelers in Paris, we picked 6 hot tourist spots 
(**Arc of Triumph, Eiffel Tower, Champs Elysées, Montmartre, Louvre, Notre Dame**) in the city and with their coordinates we created extra columns to show the distance bewteen those attractions and each listing.

Finally, in order to better categorize listings in Paris by their **arrondissements**, with the help of **geopy** and **geocode** libraries, we used the latitude and longitude data to locate each address on Google Map to extract their post codes and we took all that contained '75' at the beginning. (*'75' is the code of Paris) And as we have 11000 rows of data, we divided the task into 2 subsets and each person ran 5500 of rows to get the addresses.

**EDA:**

For EDA, some patterns were discovered in our dataset (figures described as in average):

- The arrondissements with the highest number of listings are: 11th, 18th, 3rd, 10th and 15th, each with more than 600 listings per district. The arrondissement with the least listings is the 16th.
- The 1st, 6th, 7th and 8th arrondissements are the most expensive in terms of price per night (per person). Whereas the 19th and the 20th are the areas with the least expensive listings.
- Most of the listings in Paris can host up to 4 people and in the 1rst, 2nd, 3rd and 8th there are quite a few listings that can host up to 5 or more guests.
- Column 'price group' and column 'number of guests' are 66% positively correlated.
- The priciest accommodatiom types can be found in 'Entire Place' with prices as high as 4000 euros per night whereas the cheapest ones are found in 'Shared Rooms'. 
- In terms of price per person, the most expensive type of accommodation is 'Hotel Rooms' at 99.9 euros per person per night and the cheapest type is 'Shared Rooms' at 38.4 euros per person per night.
- Based on accommodation types, we have an average number of 3-4 guests for 'Entire Place', 2 guests for both 'Hotel Rooms' and 'Private Rooms' and 1 guest for 'Shared Rooms'.
- Due to the nature of Airbnb, 'Entire Place' represents 84% of total listings, 'Private Rooms' at 11%, and very little percentage for 'Hotel Rooms' and 'Shared Rooms' each with a representation of less than 1%.
- Listings which cost less than 200 euros per night represent 76% of total listings in Paris.

**Model testing preparation:** 

Wtih the cleaned data, several machine learning models were tested in order to find models that can more accurately predict the price range of an Airbnb
lisitng given its arrondissement, listing size, and the type of dwelling (hotel rooms, entire place, priate rooms and shared rooms).

In order to predict the price range of Airbnb listings, we first created **4 bins** with the following price ranges: **Bin 1** for **0-50 euros/night**, **Bin 2** for **50-100 euros/night**, **Bin 3** for **100-300 euros/night**, and **Bin 4** for **over 300 euros/night**. Then we created the target set including only the price group values, and the rest of the variables went to the features set.

Following, we divided the datasets into train and test sets with 80% of train data and 20% of test data for the modeling.


## Model Testing

To find the best fitted models, we ran several tests and also did a TPOT test to make sure we have included the most suitable models in our test set.

**Random Forest Classifier:**

Random Forest Classifier appeared to be one of the best performing models we had. We reached an average prediction accuracy at **63%**. It is slightly more accurate at predicting the Bin 4 price range (at 65%).

**Model ComplementNB:**

With ComplementNB we had an average prediction accuracy rate at **56%**. Though it was not as performing as the previous one, this model somehow showed a higher accuracy rate while predicitng Bin 3 price range with 68% of precision.

**SGD Classifier:**

Next, our test with SGD Classifier gave us an average accuracy rate of **63%**. For predicting Bin 1 price range, this model showed a precision rate as high as 79%.

**Passive Aggressive Classifier:**

Passive Aggressive Classifier was the least performing model we tested out of the 7. Though it had an accuracy rate of 85% while predicting Bin 3 prices, the average accuracy rate was very low at **46%**.

**Gradient Boosting Classifier:**

Following we have the Gradient Boosting Classifier which demonstrated an average accuracy rate of **67%** which was on par with Random Forest Classifier. Similarly to Random Forest Classifier, this model also had the highest precision rate at predicitng Bin 4 prices at 74% of precision expected.

**Bagging Classifier:**

Furthermore, we tested the Bagging Classifier and had an average accuracy rate at **64%**. Following the same pattern as its better performing peers, this method was best at predciting Bin 4 prices with a precision rate at 67%.

**Extra Tree Classifier:**

To wrap up our model testing session, we opted for the Extra Tree Classifier and the results showed an average accuracy rate at **62%**. The performance was slightly better for predicting Bin 3 prices with a pecision rate at 65%.

## Key Findings

- Pricing distribution of listings: as expected, from our results we can see that the least pricy listings are mostly located at the outskirts of the city whereas the priciest ones are more centrally located. Similarly, for the 6 landmarks we picked, the closer the listing is to the sites, the more expensive the it would be, and vice versa.

- Prediction outcomes: we used the 7 models to check the precision of our predictions on 3 listings. One selected from our dataset and two (cosy/jaccuzi) randomly picked from airbnb website. It turned out that all 7 models employed had the correct prediction result for the listing from our dataset. And for the two listings randomly picked from airbnb website, 2 out of 7 models had the correct prediction for the cosy listing whereas 4 out of 7 models had the correct prediciton for the jaccuzi listing. Also, it is worth mentioning that **Gradient Boosting Classifier got all 3 prediction tests right**.

## Future Opportunities

Due to the absence of abundant features in our raw data, several improvements could be done if more time and data were given. We expect to further increase the accuracy of our models by taking into account the following features:

**Host information and reviews**: 

With information on hosts and reviews from guests, we could better picture the traveler experience and link it to our price range prediction models. Perhaps certain correlations among these variables could be further explored.

**Occupancy rate of the listing**: 

As we did not have occupancy rate information from Airbnb Scraper, we could not dive into the potential dependencies of room rate on occupancy. According to the law of supply and demand, supposedly a more sought after listing would have more power over its pricing strategy. However, this needs to be tested by including occupancy data in our features.

**Listing facilities**: 

Lastly, we assumed that a listing with jaccuzi and home theater would most likely be pricier than a simple studio. To prove this, we will need to investigate the various facility offerings of the listings as well.

## Extra information
- Trello link: https://trello.com/b/EMd3rnKW/final-project
- Presentation slides: https://docs.google.com/presentation/d/10WPmQiWsZiQyVnyJX3tzoE7p7ieWUKsDF27AI_u8dsM/edit?usp=sharing
- Airbnb listing (cosy) for the prediction: https://www.airbnb.fr/rooms/28298761?_set_bev_on_new_domain=1649168555_MzIzYTliYjZmMWQz&source_impression_id=p3_1650543475_EYnHEktKj%2F5yo52V
- Airbnb listing (jaccuzi) for the prediction: https://www.airbnb.fr/rooms/552611494841797214?check_in=2022-04-19&check_out=2022-04-20&federated_search_id=cf5a3806-a84d-44bb-9af8-5c88222254d7&source_impression_id=p3_1650543504_KQrH1CyiTHHAvHC0

