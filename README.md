# Amazon Vine Analysis
## Overview of the Analysis
An analysis of the Amazon reviews written by members of the paid Amazon Vine program was performed to see if there is any bias toward favorable reviews from Vine members. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

## Coding
For this analysis a book review dataset was chosen, with reviewers given books ratings from one to five stars.  Sampling the dataset revealed that the books appeared to span all genres of fiction and non-fiction.  PySpark was used to perform the ETL process in order to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Pandas was then used to determine if there was any bias toward favorable reviews from Vine members in the dataset. A summary of the results and suggestions for future analyses can be found below.

The screenshot below shows a portion of the Python code created in Colab and referencing PySpark in order to extract the book review dataset.  After downloading the data it is placed into a dataframe where it is cleaned and filtered.  
![PySpark was used to extract the dataset](screenshots/vine_review2.png)

The screenshot below shows the AWS RDS instance which was used to route the cleaned data from the Colab notebook to into a postgres database.  After this, pgAdmin software was used to export the cleaned data to a cvs file so it could be used on a local machine
![an AWS RDS instance transferred data to pgAdmin](screenshots/vine_review1.png)

## Results
The results of book reviews analysis can be seen in the table below.  The initial dataset contained 1,048,575 reviews.  In order to ensure quality reviews, only reviews from individuals who had performed 20 or more overall reviews were considered.  From this smaller set of reviewers, only those who 50% of readers found helpful were used.  This left 403,809 book reviews left for the analysis.  From this subset of reviews it was determined that:
* Of the 403,809 high quality reviews, only 2 were Vine reviews while 403,807 were non-Vine reviews.
* One of the Vine reviews was five-star, while 242,889 of the non-Vine reviews were five-star.
* The percentage of Vine reviews that were five-star was 50%, while it was 60% for non-Vine reviewers.   

![vine and non-vine reviews for books are compared](screenshots/vine_review3.png)

## Summary
 

