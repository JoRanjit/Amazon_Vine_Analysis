# Amazon_Vine_Analysis
### The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.  

#### In this project we are analyzing the reviews submitted to Amazon on 'FURNITURE' purchases. I will perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. 

<i>I picked 'FURNITURE" as it is a category which is used by a wide-range of customers from all walks of life. </i> 

#### Dataset used is :https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Furniture_v1_00.tsv.gz 


#### The tools used are: PySpark, PostgreSQL, PGAdmin, AmazonAWS and Google Colab Notebooks.

### Part 1:
###### In this part of the project is the ETL process, where we extract data from the Amazon datasets, and then clean, split and store in our PostgreSQL database tables.
We started the project by downloading the 'FURNITURE" dataset from the 50+ available datasets. I classified the furniture review data into 4 different dataframes using PySpark libraries:

* Customers 

![customer_df]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/Customers.PNG)
* Prodcuts

![Product_df]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/Products.PNG)
* Reviews

![Review_id]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/review_id.PNG)
* Vine-reviews

![vine_df]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/vine.PNG)

Then I created 4 datatables using the PGAdmin, connected to the AWS-RDS instance and loaded these dataframes into the database. 

* Customer Table

![customer_table]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/customers%20-%20pgadmin.PNG)

* Product Table

![product_table]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/products%20-%20pgadmin.PNG)

* Review ID Table

![review_table]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/review_id-pgadmin.PNG)

* Vine Table

![vine_table]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/vine-pgadmin.PNG)

### Part 2:

##### In this part of the project analyses the reviews themselves. If the 'Paid Five Star' reviews are biased than the 'Unpaid Five Star' reviews. 
###### The 'Vine' reviews are extracted from the 'FURNITURE' dataset, and loaded into a dataframe. This data is then filtered to retrieve only those reviews which recieved more than 20 votes.

* Step #1 - extract reviews with the helpful vote count is equal or more than 50% of the total votes.

![helpful_df]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/helpful_votes_df.PNG)

* Step #2 - out of the helpful reviews, extract only the five star reviews.

![five_star_df]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/five_star_df.PNG)

* Step #3 - out of the five-star reviews - get the paid and unpaid five start reviews:

![paid_five_star]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/paid_five_star_df.PNG)

![unpaid_five_star]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/unpaid_five_star_df.PNG)

* Step #4 - we calculated the percentages of these reviews to determine if there is any bias in ratings.

![comments]( https://github.com/JoRanjit/Amazon_Vine_Analysis/blob/main/Images/review%20perc%20comments.PNG)

#### From the calculations, we can see that Out of tht total 18155 helpful votes, 8556 were Five Star Reviews. And out of this only 74 were Paid reviews, i.e, 0.01%, and the rest 8482 were Unpaid, i.e, 0.99% votes.

### With this analysis, we can clearly say that - the Amazon Vine Reviews on Furniture dataset does not seem to be impacted whether the reviewers are paid or not. 0.01% Five Star ratings were given by Paid reviewers, while 0.99% of the Five Star ratings were given by Unpaid reviewers.
