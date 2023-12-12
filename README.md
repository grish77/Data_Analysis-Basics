# Data_Analysis-Basics
## Basic Concepts in Data Analysis using Python.

<p> To read any data using Python's Pandas package, there are two important factors to consider: format and file path. Format is the way data is encoded. We can usually tell different encoding schemes by looking at the ending of the file name. Some common encodings are CSV, JSON, XLSX, HDF, and so forth. 
In Pandas, the read_csv method can read in files with columns separated by commas into a Pandas data frame. Reading data in Pandas can be done quickly in three lines. First, import Pandas, then define a variable with a file path. And then use the read_csv method to import the data. However, read_csv assumes the data contains a header. </p>

## Basic insights from the data
- Understand your Data before you begin Analysis
- Should check the data types and data distribution
- locate the potential issues with the data

### Why should we check the data types in a dataframe?
- Potential info and type mismatch (proper data type to specific column)
- In pandas, we use 'dataframe.dtypes' to check the data types

## Accessing Databases using Python
There is a mechanism by which the Python program communicates with the DBMS. The Python code connects to the database using API calls.

DB API is Python standard API for accessing relational databases. It is a standard that allows you to write a single program that works with multiple kinds of relational databases instead of writing a separate program for each one. If you learn the DB API functions, then you can apply that knowledge to use any database with Python. The two main concepts in the Python DB API are connection objects and query objects.
#### Connection Objects
You use connection objects to connect to a database and manage your transactions
- Database connections
- Manage transactions

#### Cursor Objects
Cursor objects are used to run queries. You open a cursor object and then run queries. The cursor works similar to a cursor in a text processing system, where you scroll down in your result set and get your data into the application. Cursors are used to scan through the results of a database.

<h2>Save Dataset</h2>
<p>
Correspondingly, Pandas enables us to save the dataset to csv. By using the <code>dataframe.to_csv()</code> method, you can add the file path and name along with quotation marks in the brackets.
</p>
<p>
For example, if you would save the dataframe <b>df</b> as <b>automobile.csv</b> to your local machine, you may use the syntax below, where <code>index = False</code> means the row names will not be written.
</p>



<p>
When you use df.describe(include='all') in pandas, it generates descriptive statistics for each column in the DataFrame, including both numerical and categorical columns. The include='all' argument ensures that summary statistics for all columns are included.
</p>

<p>
Here's what each part of the output typically represents:
</p>
<ul>
<li>count: Number of non-null values in each column.</li>
<li>mean: Mean or average value.</li>
<li>std: Standard deviation, a measure of the amount of variation or dispersion of a set of values.</li>
<li>min: Minimum value.</li>
<li>25%: First quartile (25th percentile).</li>
<li>50% (median): Median or second quartile (50th percentile).</li>
<li>75%: Third quartile (75th percentile).</li>
<li>max: Maximum value.</li>
</ul>
<p>
For categorical data, you'll see additional information:
</p>
<ul>
<li>unique: Number of unique values.</li>
<li>top: Most frequently occurring value.</li>
<li>freq: Frequency of the most frequently occurring value.</li>
</ul>

## Data pre-processing in Python 
Data pre-processing is a necessary step in data analysis. It is the process of converting or mapping data from one raw form into another format to make it ready for further analysis. Data pre-processing is often called data cleaning or data wrangling.
#### steps:
- Identify and handle missing values
- Data Formatting 
- Data Normalization (centering/scaling)
- Data Binning
- Turn Categorical to numeric variables

### Dealing with missing Values in Python 
<p>Missing values occur when no data value is stored for a variable (feature) in an observation.
Could be represented as "?", "N/A", "NaN", 0 or just a blank cell</p>

### solution 
- check with the data collection source
- drop the missing value
- Replace the missing values 
    - Replace with the average (of similar datapoints)
    - replace it by frequency 
    - replace it based on other functions
- leave it as missing data 
<p>
We can use dataframes.dropna() funcition to drop the NaN in pd dataframe. We can do this in multiple ways</p>
<code> df.dropna(subset["column_name"], axis = 0)</code>
<p>Or</p>
<code> df["column_name"] = df["column_name"].dropna()</code>
<p> To replace the missing values in python, we use the syntax:</p>
<code>df.replace(missing_value, new_value)</code>

### Data formatting in python 
<p> Data is usually collected from different places, by different people, which may be stored in different formats. Data formatting means bringing data into a common standard of expression that allows users to make meaningful comparisons. As a part of dataset cleaning, data formatting ensures that data is consistent and easily understandable. For example, people may use different expressions to represent New York City, such as N.Y., Ny, NY, and New York. Sometimes this unclean data is a good thing to see.</p>
<p> To correctly identify the data types of each column of the dataframe and format it accordingly, we can use <code>dataframe.dtypes</code>. And to convert the data types, use <code> dataframe.astype()</code> command.</p>

### Data Normalization 
<p> We can normalize the values of the features in a dataset to make them more consistent and within certain range.Normalization enables a fairer comparison between the different features, making sure they have the same impact. It is also important for computational reasons. Here is another example that will help you understand why normalization is important. Consider a data set containing two features: age and income, where age ranges from 0 to 100, while income ranges from 0 to 20,000 and higher. Income is about 1,000 times larger than age and ranges from 20,000 to 500,000. So these two features are in very different ranges. When we do further analysis, like linear regression, for example, the attribute "income" will intrinsically influence the result more due to its larger value. But this doesn't necessarily mean it is more important as a predictor. So the nature of the data biases the linear regression model to weigh income more heavily than age. To avoid this, we can normalize these two variables into values that range from 0 to 1.</p>
<p> There are several ways to Normalize data. some of the most frequently used techniques are:</p>
<li>Simple feature scaling(Xnew = Xold/Xmax)</li>
<li>Min-Max scaling(Xnew = (Xold - Xmin)/(Xmax-Xmin)</li>
<li>Z-score scaling(Xnew = Xold - mean/SD)</li>

<h3>Binning</h3>
<p> GBinning is when you group values together into bins. For example, you can bin age into 0-5, 6-10, 11-15 and so on. Sometimes binning can improve accuracy of the predictive models. In addition, sometimes we use data binning to group a set of numerical values into a smaller number of bins to have a better understanding of the data distribution.</p>

### Converting categorical variables into quantitative variables
Most statistical models cannot take in objects or strings as input, and for model training, only take the numbers as inputs. We can perform the conversion by adding dummy variables for each unique category. This technique of converting categorical variables to dummy variables is called one-hot encoding. 
One drawback of one-hot encoding might be that it creates new binary columns for each category in the original column and results in larger number of columns.

## Exploratory Data Analysis

### Descriptive Statistics
<p> When you begin to analyze data, it's important to first explore your data before you spend time building complicated models. One easy way to do so is to calculate some descriptive statistics for your data. Descriptive statistical analysis helps to describe basic features of a dataset and obtains a short summary about the sample and measures of the data. Let's show you a couple different useful methods. One way in which we can do this is by using the describe function in pandas. Any NaN values are automatically skipped in these statistics. This function will give you a clearer idea of the distribution of your different variables. You could have also categorical variables in your dataset. These are variables that can be divided up into different categories or groups and have discrete values. One way you can summarize the categorical data is by using the function <code> value_counts()</code>. 
 Don’t forget the method "value_counts" only works on pandas series, not pandas dataframes. As a result, we only include one bracket df['Sell'], not two brackets df[['Sell']].</p>
 
### Box Plots
<p> Box plots make it easy to compare between groups. In this example, using box plot, we can see the distribution of different categories of the Sell price feature over Beds feature.
These are variables that describe a 'characteristic' of a data unit, and are selected from a small group of categories. The categorical variables can have the type "object" or "int64". A good way to visualize categorical variables is by using boxplots.</p>

### Scatter Plots
Oftentimes, we tend to see continuous variables in our data. These data points are numbers contained in some range. A scatter lot is a good way to visualize the relationship between continuous variables. Each observation in a scatter plot is represented as a point and the plot shows the relationship between to variables. The predictor variable is the variable that you are using to predict an outcome. In this case, our predictor variable is the 'List' or listing price. The target variable is the variable that you are trying to predict. In this case, our target variable is 'Taxes'. In a scatter plot, we typically set the predictor variable on the x-axis or horizontal axis, and we set the target variable on the y-axis or vertical axis.We are using the Matplotlib function scatter here, taking in x and a y variable. Something to note is that it's always important to label your axes and write a general plot title so that you know what you're looking at.

### Groupby method
The groupby method is used on categorical variables, groups the data into subsets according to the different categories of that variable. You can group by a single variable, or you can group by multiple variables by passing in multiple variable names. As an example, let's say we are interested in finding the average price of vehicles and observe how they differ between different types of body styles and drive wheels variables. To do this, we first pick out the three data columns we are interested in, which is done in the first line of code. We then group the reduced data according to drive wheels and body style in the second line. Since we are interested in knowing how the average price differs across the board, we can take the mean of each group and append this bit at the very end of the line 2. The data is now grouped into subcategories, and only the average price of each subcategory is shown.

<p>This grouped data is much easier to visualize when it is made into a pivot table. A pivot table is like an Excel spreadsheet, with one variable along the column and another along the row. We can convert the dataframe to a pivot table using the method "pivot" to create a pivot table from the groups.</p>
<p>Often, we won't have data for some of the pivot cells. We can fill these missing cells with the value 0, but any other value could potentially be used as well. It should be mentioned that missing data is quite a complex subject and is an entire course on its own.</p>

## Correlation 
<p> Correlation is a statistical metric for measuring to what extent different variables are interdependent. In other words, when we look at two variables over time, if one variable changes, how does this affect change in the other variable? For example, smoking is known to be correlated to lung cancer, since you have a higher chance of getting lung cancer if you smoke. In another example, there is a correlation between umbrella and rain variables, where more precipitation means more people use umbrellas. Also, if it doesn't rain, people would not carry umbrellas. Therefore, we can say that umbrellas and rain are interdependent and by definition they are correlated.But correlation does not imply causation. 

<p> Continuous numerical variables are variables that may contain any value within some range. They can be of type "int64" or "float64". A great way to visualize these variables is by using scatterplots with fitted lines.

In order to start understanding the (linear) relationship between an individual variable and the price, we can use "regplot" which plots the scatterplot plus the fitted regression line for the data. This will be useful later on for visualizing the fit of the simple linear regression model as well.</p>

## Pearson Correlation 
<p> It is used to measure the srenght of the correlation between continuous numerical variables. It gives of two values, the correlation coefficient nad the p-value. The value of correlation coefficient ranges from -1 to 1. The value closer to 1 means positive correlation and the value closer to -1 mean negative correlation. the value 0 means no correlation. The p-value less than 0.001 means the strong certainty about the correlation that we calculated, a value between 0.001 and 0.05 gives us moderate certainty, a value between 0.05 and 0.1 will give us a weak certainty, and a p-value larger than 0.1 will give us no certainty of correlation at all. We can say that there is a strong correlation when the correlation coefficient is close to one or -1 and the p-value is less than 0.001.</p>

## Model Development
<p> In data analytics, we often use Model Development to help us predict future observations from the data we have.
A model will help us understand the exact relationship between different variables and how these variables are used to predict the result. We will predict the price of a car using the above dataset. We will explore ML model (regression: simple, multiple and polynomial). A model or estimator can be thought of as a mathematical equation used to predict a value given one or more other values, relating one or more independent variables or features to dependent variables. For example, you input a car models highway miles per gallon as the independent variable or feature. The output of the model or dependent variable is the price.</p>
<p> To fit the model in Python, first we import linear model from scikit-learn. Then create a linear regression object using the constructor. We define the predictor variable and target variable. Then use the method fit to fit the model and find the parameters b0 and b1, the input are the features and the targets. We can obtain a prediction using the method predict. The output is an array. The array has the same number of samples as the input x.</p>

### Residual Plot 
The residual plot represents the error between the actual value. Examining the predicted value and actual value, we see a difference. We obtained that value by subtracting the predicted value and the actual target value. We then plot that value on the vertical axis with the dependent variable as the horizontal axis. Similarly, for the second sample, we repeat the process, subtracting the target value from the predicted value, then plotting the value accordingly. Looking at the plot gives us some insight into our data. We expect to see the results to have zero mean distributed evenly around the x-axis with similar variance. There is no curvature. This type of residual plot suggests a linear plot is appropriate. 
<p>We can use seaborn to plot the residual plot. <code>sns.residplot(df["independentVar"], df["DependentVar"])</code></p>

### Distribution Plot 
<p>A distribution plot counts the predicted value versus the actual value. These plots are extremely useful for visualizing models with more than one independent variable or feature.
    
## In-sample Evaluation 
<p>When evaluating our models, not only do we want to visualize the results, but we also want a quantitative measure to determine how accurate the model is.</p>

<p>Two very important measures that are often used in Statistics to determine the accuracy of a model are:</p>
<ul>
    <li><b>R^2 / R-squared</b></li>
    <li><b>Mean Squared Error (MSE)</b></li>
</ul>
    
<b>R-squared</b>

<p>R squared, also known as the coefficient of determination, is a measure to indicate how close the data is to the fitted regression line.</p>
    
<p>The value of the R-squared is the percentage of variation of the response variable (y) that is explained by a linear model.</p>



<b>Mean Squared Error (MSE)</b>

<p>The Mean Squared Error measures the average of the squares of errors. That is, the difference between actual value (y) and the estimated value (ŷ).</p>

### Simple Linear Regression vs Multiple Linear Regression 
<p>Usually, the more variables you have, the better your model is at predicting, but this is not always true. Sometimes you may not have enough data, you may run into numerical problems, or many of the variables may not be useful and even act as noise. As a result, you should always check the MSE and R^2.</p>

models, we look at a combination of both the R-squared and MSE to make the best conclusion about the fit of the model.
<ul>
