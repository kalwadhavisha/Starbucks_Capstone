# Starbucks_Capstone

Project in Data Scientist Nanodegree of Udacity.
Medium Post on this project: https://medium.com/@havisha.kalwad/starbucks-data-analysis-and-promotional-offer-recommendation-1951515b29c8

## Table of Contents
1. Project Motivation
2. File Descriptions
3. Results
4. Licensing, Authors, and Acknowledgements

## Project Motivation
It is the Starbuck's Capstone Challenge of the Data Scientist Nanodegree in Udacity. The dataset is obtained from the program that creates the data, simulates how people make purchasing decisions and how those decisions are influenced by promotional offers. The aim is to make a recommendation engine that recommends Starbucks which offer should be sent to a particular customer.

We are interested to answer the following two questions:

1. Which demographic groups respond best to which offer type?
1. Which offer should be sent to a particular customer with confidence that the customer would make more purchases.

## File Descriptions

This data set is a simplified version of the real Starbucks app because the underlying simulator only has one product whereas Starbucks actually sells dozens of products.

The data is contained in three files:

portfolio.json - containing offer ids and meta data about each offer (duration, type, etc.)
profile.json - demographic data for each customer
transcript.json - records for transactions, offers received, offers viewed, and offers completed
Here is the schema and explanation of each variable in the files:

portfolio.json

- id (string) - offer id
- offer_type (string) - the type of offer ie BOGO, discount, informational
- difficulty (int) - the minimum required to spend to complete an offer
- reward (int) - the reward is given for completing an offer
- duration (int) - time for the offer to be open, in days
- channels (list of strings)

profile.json

- age (int) - age of the customer
- became_member_on (int) - the date when customer created an app account
- gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
- id (str) - customer id
- income (float) - customer's income

transcript.json

- event (str) - record description (ie transaction, offer received, offer viewed, etc.)
- person (str) - customer id
- time (int) - time in hours since the start of the test. The data begins at time t=0
- value - (dict of strings) - either an offer id or transaction amount depending on the record

## Results
Based on the transcript records, we build an user-item-matrix that represents how users responded to the offers they received. 
We then split the records into the training set and the test set and trained our SVD algorithm to predict how a user responses to a particular offer.

We achieved the lowest mean square error around 0.002506 with 15 latent features (250 iterations) with the training set and around 0.003734 with 10 latent features (250 iterations) with the testing set. 
After that, we created a recommendation engine that recommends Starbucks which offer should be sent to a particular user.

Later we found out which demographic groups respond best to which offer type. 
1. Females respond much better than men, in both BOGO and discount. 
2. But men reacted better to discount than BOGO. 
3. We also found that it is better to promote the offer via social media for all gender types. 
4. Among the ten offers, sending buy 10 dollars get 2 dollars off within 10 days offer via email, web, mobile and social makes Starbucks gain more. It is the best offer so far!

# Licensing, Authors, Acknowledgements
Credits to Starbucks and Udacity
