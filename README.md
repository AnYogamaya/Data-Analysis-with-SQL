# Data-Analysis-with-SQL
Data Analysis - Data cleaning and EDA using MySQL

## Project Walkthrough

1. Import Dataset
2. Clean Data
3. Analyse Data

### 1: Import our data:
The dataset we are using is from Real World Fake Data In Data.world
They have AMAZING datasets that are very interesting and in a variety of fields.

First off, we need a database that we will import our data into it. We can either create a new one or just use an existing one. I chose the former.
![1_iKtDz19zh3mAopk9eQi7KA](https://user-images.githubusercontent.com/102911384/192278774-6d8ef31d-fb20-4acd-85ea-830933715b21.png)

To load that data into a table in the database we need to create a table that will match it. Like this:
![2](https://user-images.githubusercontent.com/102911384/192279703-9d648067-a309-4e2e-a24a-47d7c0db9fea.png)

### 2: Clean the data:
1. When we created the table, the call_timestamp is a date, using a char datatype. This is because : Back in the csv file, the call timestamp was in this format: mm-dd-YYYY. which in human words mean: two digits for month, two digits for day and four digits for year. This is not acceptable in MySQL which it’s default format is: yyyy-MM-dd. That is why we made it into a string and then fix it up later in MySQL.
2. You might’ve noticed that all the empty values which were in the original/csv dataset that were in the csat_score(customer satisfaction score), got converted to zero’s Instead of null values, which will mess up our aggregations because the minimum score is 1 and not 0.

Let’s fix them:

It’s pretty straightforward to be honest, we just call the function str_to_date() and give it our column and the way the date is formatted in it (pay attention here, not the format *we* want, but the format that the string is already in it):
![3](https://user-images.githubusercontent.com/102911384/192281857-2b734fdd-482d-4312-8b55-79e47a198c7c.png)

Now to our next problem. The zero’s in the csat_score. There are two options: either we set them to NULL, or we just leave them be and then when we query the table we just add the clause WHERE csat_score != 0. But I will set them to nulls in this way:


### 3: EDA of Dataset.
