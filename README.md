# Amazon Vine Analysis
## Overview of the Analysis
An analysis of the Amazon reviews written by members of the paid Amazon Vine program was performed to see if there is any bias toward favorable reviews from Vine members. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

## Coding
For this analysis a book review dataset was chosen, with reviewers given books ratings from one to five stars.  Sampling the dataset revealed that the books appeared to span all genres of fiction and non-fiction.  PySpark was used to perform the ETL process in order to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Pandas was then used to determine if there was any bias toward favorable reviews from Vine members in the dataset. A summary of the results and suggestions for future analyses can be found below.

The screenshot below shows a portion of the Python code created in Colab and referencing PySpark in order to extract the book review dataset.  After downloading the data, it is placed into a dataframe where it is cleaned and filtered.  
![PySpark was used to extract the dataset](screenshots/vine_review2.png)

The screenshot below shows the AWS RDS instance which was used to route the cleaned data from the Colab notebook to into a postgres database.  After this, pgAdmin software was used to export the cleaned data to a cvs file so it could be used on a local machine
![an AWS RDS instance transferred data to pgAdmin](screenshots/vine_review1.png)

## Results
The results of book reviews analysis can be seen in the table below.  The initial dataset contained 1,048,575 reviews.  In order to ensure quality reviews, only reviews from individuals who had performed 20 or more overall reviews were considered.  From this smaller set of reviewers, only those who 50% of readers found helpful were used.  This left 403,809 book reviews left for the analysis.  From this subset of reviews, it was determined that:
* Of the 403,809 high quality reviews, 403,807 were non-Vine reviews and only 2 were Vine reviews 
* 242,889 of the non-Vine reviews were five-star and 1 of the 2 Vine reviews were five-star.
* The percentage of non-Vine reviews that were five-star was 60%, while it was 50% for Vine reviewers.
  

![vine and non-vine reviews for books are compared](screenshots/vine_review3.png)

## Summary
Given that only a couple of the reviews were from Vine reviewers, it is impossible to say whether or not there is any positive bias for reviews in the Vine program.  It is not feasible to compare 2 reviews to over 400,000 reviews.  What can be said is that non-Vine reviewers tend toward positive bias as 60% of their reviews are five-star ratings on a scale of 1 to 5.  This means every 3 out of 5 books they read and review is given the highest rating possible and most likely means an uneven distribution of ratings between each of the five levels.  Given an equitable rating system one would assume approximately 20% of the reviews would be five-star ratings.  

In order to better test whether there is any bias toward favorable reviews from Vine members, datasets from items that are not as popular as books should be imported, cleaned and tested.  A significant larger number of Vine reviews most be found from individuals who perform a lot of reviews in order to test whether or not there is any bias.  Once a dataset with a significant amount of Vine reviewers is found, summary statistics should be performed in order to determine if there is any difference in the way paid and non-paid individuals perform reviews.  If the mean ratings of the two types of reviewers fall within the standard deviation of the measurements, it should be assumed there is no bias.  If the mean ratings of the two types of reviewers fall outside the standard deviation of the measurement, bias in the reviews either positive or negative should be assumed.  

Lastly, given the observation that over 400,000 reviews for books were done by non-Vine reviewers, it can be inferred that the Amazon Vine program does not need to pay individuals to review books as there are already so many willing individuals who love books and will happily do so.  Following this assumption, it can also be inferred that people who enjoy books and are willing to review them for free are more likely to give the books a higher star rating than an unbiased reader.    


