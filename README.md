# INCOME-CLASSIFIER
Explore the possibility of classifying income based on an individual’s personal information.

Census data is one of the largest sources of a variety of statistical information related to
population. It typically includes information related to Age, Gender, Household composition,
Employment Details, Accommodation Details, and so on. Till recent years, collecting census
data has been a manual process involving field visits and registrations. With advances in
technology, the methods of collecting this data have improved to a great extent. And so is the
population! With a population of more than 7 billion, one can imagine the volume of the census
data associated with it. This data is collected from a variety of sources such as manual entries,
online surveys, data from social media and search engines and is in various formats. Traditional
database systems are inefficient at handling such data. This is where Big Data Technologies
come into picture.

As per a study by U.S. Census Bureau, analytics on census data could have been helpful during
the Great Recession in various ways such as avoiding job loss in Supply-Chain businesses,
reducing housing foreclosure rates, and so on.
Big Data Analytics refers to a set of tools and methods used to obtain knowledge from
information. Application of Big Data Analytics on census data can facilitate better decision
making in various Government and Industrial sectors such as Healthcare, Education, Finance,
Retail, and Housing. One such application is an Income Classifier. In this project, let us take a
sample of world census data and build an Income Classifier using various Big Data Techniques
described in subsequent sections.

# LEARNING OBJECTIVES

1. HDFS and Hive for Data Storage and Management
2. Data Ingestion using Sqoop
3. Machine Learning using PySpark
This Project is divided into three parts to cover the above learning objectives.

# DATASET
The dataset named censusdata.csv is provided in your LMS. We will be using the same dataset
for all the three parts.
• Input: The dataset contains 15 columns
• Targeted Column: Income; the income is provided in the form of two values: <=50k or
>50k
• Number of other columns:14; these are demographics and other features used for
describing a person
List of Attributes:
• age: continuous
• workclass: Private, Self-emp-not-inc, Self-emp-inc, Federal-gov, Local-gov, State-gov,
Without-pay, Never-worked
• fnlwgt: continuous.
• education: Bachelors, Some-college, 11th, HS-grad, Prof-school, Assoc-acdm, Assoc-voc,
9th, 7th-8th, 12th, Masters, 1st-4th, 10th, Doctorate, 5th-6th, Preschool
• education-num: continuous
• marital-status: Married-civ-spouse, Divorced, Never-married, Separated, Widowed,
Married-spouse-absent, Married-AF-spouse
• occupation: Tech-support, Craft-repair, Other-service, Sales, Exec-managerial, Prof-
specialty, Handlers-cleaners, Machine-op-inspct, Adm-clerical, Farming-fishing,

Transport-moving, Priv-house-serv, Protective-serv, Armed-Forces
• relationship: Wife, Own-child, Husband, Not-in-family, Other-relative, Unmarried
• race: White, Asian-Pac-Islander, Amer-Indian-Eskimo, Other, Black
• sex: Female, Male
• capital-gain: continuous
• capital-loss: continuous
• hours-per-week: continuous
• native-country: United-States, Cambodia, England, Puerto-Rico, Canada, Germany,
Outlying-US(Guam-USVI-etc), India, Japan, Greece, South, China, Cuba, Iran, Honduras,
Philippines, Italy, Poland, Jamaica, Vietnam, Mexico, Portugal, Ireland, France,
Dominican-Republic, Laos, Ecuador, Taiwan, Haiti, Columbia, Hungary, Guatemala,
Nicaragua, Scotland, Thailand, Yugoslavia, El-Salvador, Trinadad&Tobago, Peru, Hong,
Holand-Netherlands
• income: >50K, <=50K

# TASKS
1. HDFS AND HIVE

Problem Statement 1
Census Analytics is a project where you need to collect the data of people along with their
incomes. As the census data is usually in large volume, the analysis of the data will be a
cumbersome task. To overcome this, we will be using the Hadoop Ecosystem.

As a first step, you need to load the data into HDFS and create a table in Hive that can be used
for querying the data. You have to create different types of tables and execute queries, as
mentioned below and compare the time required for execution for different types of tables.
Steps to be performed:
1. Download the dataset named censusdata.csv that is provided in your LMS
2. Load the downloaded data into HDFS
3. Create an internal table in Hive to store the data
a. Create the table structure
b. Load the data from HDFS into the Hive table
4. Create an internal table in Hive with partitions
a. Create a Partition Table in Hive using “workclass” as the Partition Key
b. Load data from the staging table (Table created in Step 3) into this table
5. Create an external table in Hive to hold the same data stored in HDFS
6. Create an external table in Hive with partitions using “workclass” as Partition Key
7. For each of the four tables created above, perform the following operations
• Find out the number of adults based on income and gender. Note the time taken for
getting the result
• Find out the number of adults based on income and workclass. Note the time taken
for getting the result
• Write your observations by comparing the time taken for executing the commands
between:
a. Internal & External Tables
b. Partitioned & Non-partitioned Tables
8. Delete the internal as well as external tables. Comment on the effect on data and
metadata after the deletion is performed for both internal and external tables.

2. DATA INGESTION
Problem Statement 2
In a similar scenario as above, the data is available in a MySQL database. Due to the inefficiency
of RDBMS systems to store and analyze Big Data, it is recommended that we move the data to
the Hadoop Ecosystem.
Ingest the data from MySQL database into Hive using Sqoop. Data pipeline needs to be created
to ingest data from an RDBMS into Hadoop Cluster and then load data into Hive.

To make the analysis faster, use Spark on top of Hive after getting data into the Hadoop cluster.
Using Spark, query different tables from Hive to analyze the dataset.
Steps to be performed:
1. Create the necessary structure in a MySQL database using the steps mentioned below:
a. Create a new database in MySQL with the name midproject
b. Create a table in this database with the name census_adult to store the input
dataset
c. Load the dataset into the table
d. Verify whether data is loaded properly
e. Verify the table for unwanted data such as ‘?’,’Nan’ and ‘Null’
f. Get the counts for the columns which contain unwanted data
g. Clean the data by replacing the unwanted data with others

2. Import the above data from MySQL into a Hive table using Sqoop
3. Connect to PySpark using web console to access the created Hive table. Perform the
following queries and note the time taken for execution in each of the queries.
a. Query the table to get the number of adults based on income and gender
b. Query the table to get the number of adults based on income and workclass
Hint: To access Hive tables using Spark console, use the following commands:

>>pyspark2
>>from pyspark.context import SparkContext
>>from pyspark.sql import HiveContext
>>sqlContext = HiveContext(sc)

4. Access the following two tables created as part of Problem 1 (HDFS and Hive) and
perform the steps as mentioned below:
a. Access Hive External Table with partition
i. Query the table to get the number of adults based on income and gender
ii. Query the table to get the number of adults based on income and
workclass

b. Access Hive Internal Table with Partition
i. Query the table to get the number of adults based on income and gender
ii. Query the table to get the number of adults based on income and
workclass

Make a note of the time taken for getting the result in comparison with the time taken to get
results with Hive.

5. Comment on the time taken for executing these commands using Spark as compared to
the time taken for execution in Hive (Problem Statement 1).

3. INCOME CLASSIFIER
Problem Statement 3
Income Classifier is an application that will be used to classify individuals based on the annual
income. An individual’s annual income may be influenced by various factors such as age,
gender, occupation, education level, and so on.
Write a program to build classification models using PySpark. Explore the possibility of
classifying income based on an individual’s personal information. Perform the following steps to
build and compare different classifiers. Use Jupyter Notebook to write the program.
Steps to be performed:
1. Load data using PySpark
2. Perform Exploratory Data Analysis (EDA) and Data Cleaning based on the following
points:
a. Find the shape and schema of the dataset
b. Obtain insights (statistics) of different columns
c. Obtain the Unique values of Categorical Columns
d. Check if any unwanted values are present in the data such as Null, ? or NaN
e. Remove unwanted values if present in any of the columns (numerical as well
as categorical columns)
f. Obtain the relationship between different columns using covariance which
shows the degree of interdependence of the two columns
g. Obtain distinct values and their counts in categorical columns.
h. Create a crosstab on two different columns (example, age & workclass)
i. Perform an “Integer Type Check” on the columns of the Spark DataFrame
and display the columns satisfying the same
j. Obtain correlation between the above columns using pandas scatter plot

3. Data Preprocessing
Since we are going to use classification algorithms like Logistic Regression, we will have
to convert all the categorical columns in the dataset to numerical values. We can
achieve this using
1) Category Indexing
In this, we assign a numerical value to each category (eg: Male: 0, Female: 1)
2) One-Hot Encoding
This converts categories into binary vectors with at most one nonzero value
(eg: (Blue: [1, 0]), (Green: [0, 1]), (Red: [0, 0]))

In this step, we will be using a combination of Category Indexing and One-Hot Encoding
a. Conversion of categorical columns into Numerical Columns
i. Category Indexing using string indexing for all categorical columns
ii. Label Indexing for income column as income_class
(Note: Make sure that the output column name for Income should be
income_class)
iii. One Hot Encoding which generates binary columns for features
iv. Use Vector assembler to get a single vector column for features
v. Make it as an array of stages so that it can be passed to a pipeline

4. Build the Pipeline to perform multiple tasks
a. Pass the stages of Data Preprocessing (created in Step 3) to the pipeline to
create an instance with the stages
b. Estimator that can fit on a DataFrame to produce a model
c. Transform the DataFrame with features to DataFrame with predictions
d. Generate a DataFrame which can hold a variety of datatypes including
feature vectors

5. Split the dataset into two parts (80%-20%) as Train and Test Datasets
a. Check the shape of the datasets
b. Check the distribution of income class (0,1) in train and test dataset
6. Build the following Classifiers
a. Logistic Regression
b. Decision Tree
c. Random Forest
d. Gradient Boosted Tree
e. Naïve Bayes
Common Tasks for all the Classifiers:
• Train and Evaluate the Model
• Print ROC metrics & model accuracy
• Tune the Hyperparameters and print the improved accuracy

Compare the accuracy of the 5 models and comment on the models which performed better as
compared to other in the list
