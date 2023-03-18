[READ.ME.docx](https://github.com/ajaloons/CIND820_CAPSTONE/files/11007583/READ.ME.docx)
# CIND820_CAPSTONE

PRELIMINARY STATISTICS
First, we import our necessary libraries: Pandas and Numpy
Import our csv file (crimedata.csv) and examine the first 10 rows
  -here we get an idea of the organization of the dataset, and our column names
  -display all the datatypes of our columns
  -check number of rows
  
  We can see missing values represented as '?', so we will replace these values with NaN to make them easier to work with
    -display the sum of the NaNs in each column, then separate out these columns with NaN values and display the sums of each
  Now we can look at the summary statistics of the dataset, as well as general information
  
  Aggregate columns by STATE and find the mean of each column
    -further aggregate by crimes per population columns and check the mean
    -examine minimum and maximum values of each subset
    -find the representation of each STATE in the dataset: how many rows is the state represented by?
    
    
 INITIAL CODE AND RESULTS
 Deal with missing values discovered in preliminary statistics
  -set a drop threshold: columns missing more than 0.5 of their values are to be dropped from the dataset
 
 Decide on target variables: choose 2 with the least amount of missing variables
 
 Deal with missing values in columns that were significantly under the threshold (missing 1-15 values)
  -impute them with the column MODE
  
 Deal with missing values that do not reach the drop threshold but are still significant
    -aggregate the data by STATE: more geographical/social similarities
    -check number of rows per each state
    -impute the missing values with the mean of the state column
      -check which columns the missing values are located in
      -check the ratio of the missing values to the length of the column
        -if the ratio is not significant, impute with the mean of the state
        -if the ratio is significant (0.75+), drop the STATE
      -create a new dataframe with all imputed STATE dataframes
      
  Check ranges of the target variables
  Run correlation matrix for the entire dataset
    -check for most highly correlated columns
  
  Create 2 seperate datasets for our target variables: MURDERS and ROBBERIES
  
  MURDERS DATASET:
  Run correlation matrix and examine correlations between independent variables and dependent variable
  Run correlation matrix for the whole dataset to see which attributes are the most highly correlated
    -drop the columns with a correlation greater than 0.8
    
  Examine the remaining attributes
    -review column summaries (mean, quartiles, etc)
    -review distributions to see how balanced they are
      -check skew values
      -check histograms for distributions
    
  Normalization of the attributes
    -for attributes with NORMAL DISTRIBUTION: 0-1 range
    -for attributes with NON NORM DISTRIBUTION: transform to categorical variable with levels
      -establish each level according to quartiles (to balance them)
    -add new normalized version of the column back to the dataset
    
  Prepare the MURDER DATASET for CLASSIFICATION and REGRESSION models
    -transform target variable into categorical variable for classification
    -transform target variable into normalized 0-1 range for regression
    
 ROBBERIES DATASET:
 Examine correlations between dependent and independent variables
 Run correlation matrix for whole dataset
  -drop highly correlated columns
 
 To avoid repeating the same normalization steps previously done in the MURDERS DATASET, check both dataframes for differences in their columns
  -if all columns are the same, create a new normalized dataset for BOTH datasets based off the normalized columns previously created 
  
 Run the models: The models that will be used will be LOGISTIC REGRESSION, and 3 CLASSIFICATION models: KNN, Decision Tree, Random Forest
  -split the MURDER data into train and test sets
  -run logistic regression model
  -run classification models
    -KNN, Decision Tree, Random Forest
    
  -split the ROBBERIES data into train and test sets
  -run logistic regression
  -run classification models
    -KNN, Decision Tree, Random Forest
  
  Run a confusion matrix for each model
  Run our evaluation metrics (Accuracy, Precison, Recall) and compare
