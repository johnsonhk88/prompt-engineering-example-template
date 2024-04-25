# Prompt 1 Importing the Dataset
Write a Python code that can perform the following tasks.
1. Read the CSV file, located on a given file path, into a pandas data frame, assuming that the first row of the file can be used as the headers for the data.
2. Print the first 5 rows of the dataframe to verify correct loading.


# Responses

Sure! Here is a Python code that can perform the tasks you mentioned:

```python
import pandas as pd

# Specify the file path where the CSV file is located
file_path = "your_file_path_here.csv"

# Read the CSV file into a pandas data frame
df = pd.read_csv(file_path)

# Print the first 5 rows of the dataframe
print(df.head())
```

This code will read the CSV file located at the specified file path into a pandas data frame, assuming that the first row of the file can be used as the headers for the data. It will then print the first 5 rows of the dataframe to verify that the data has been loaded correctly.



# Prompt 2  Data Preparation (Data Cleaning)
Write a python code that performs the following tasks:
1. Identify the columns of a data frame with missing values.
2. Replace the missing values thus identified with mean value of the column.
3. Deletes the duplicate entries from the data frame.


# Response
Certainly! Here is a Python code that can perform the tasks you mentioned:

```python
import pandas as pd

# Assume 'df' is the pandas data frame you are working with

# Identify columns with missing values
columns_with_missing_values = df.columns[df.isnull().any()]

# Replace missing values with mean value of the column
for column in columns_with_missing_values:
    mean_value = df[column].mean()
    df[column].fillna(mean_value, inplace=True)

# Delete duplicate entries
df.drop_duplicates(inplace=True)
```

This code will first identify the columns in the data frame 'df' that have missing values and then replace those missing values with the mean value of the respective column. Finally, it will remove any duplicate entries from the data frame.


# Prompt 3 Data Insights and Visualization
Write a python code that identifies the top 5 attributes with highest correlation with the target attribute in a data frame.

# Response
Certainly! Here is a Python code that can identify the top 5 attributes with the highest correlation with the target attribute in a data frame:

```python
import pandas as pd

# Assume 'df' is the pandas data frame you are working with
# Assume 'target_column' is the name of the target attribute

# Calculate the correlation matrix
correlation_matrix = df.corr()

# Sort the correlations with the target attribute
correlations_with_target = correlation_matrix[target_column].sort_values(ascending=False)

# Identify the top 5 attributes with the highest correlation with the target attribute
top_5_correlations = correlations_with_target[1:6]

print(top_5_correlations)
```

This code will first calculate the correlation matrix for the data frame 'df'. It will then sort the correlations with the target attribute in descending order and identify the top 5 attributes with the highest correlation with the target attribute. Finally, it will print out the top 5 attributes with their correlation values.


# Prompt 4
Write a python code that counts the number of entries in a dataframe with each unique value of a specific attribute.


# Response
Certainly! Here is a Python code that can count the number of entries in a dataframe with each unique value of a specific attribute:

```python
import pandas as pd

# Assume 'df' is the pandas data frame you are working with
# Assume 'specific_attribute' is the name of the specific attribute you want to count unique values for

# Count the number of entries with each unique value of the specific attribute
unique_value_counts = df['specific_attribute'].value_counts()

print(unique_value_counts)
```

This code will count the number of entries in the dataframe 'df' with each unique value of the specific attribute specified. It will then print out the counts for each unique value.



# Prompt 5
Write a python code that creates a Seaborn box plot between a source and target attributes of a dataframe.



# Response
Certainly! Here is a Python code that can create a Seaborn box plot between a source and target attribute of a dataframe:

```python
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt

# Assume 'df' is the pandas data frame you are working with
# Assume 'source_attribute' is the name of the source attribute
# Assume 'target_attribute' is the name of the target attribute

# Create a box plot using Seaborn
sns.boxplot(x=df['source_attribute'], y=df['target_attribute'])

# Show the plot
plt.show()
```

This code will create a Seaborn box plot between the specified source and target attributes of the dataframe 'df'. The box plot will provide a visual representation of the distribution of the target attribute based on the values of the source attribute.


# Prompt 6
Write a python code that creates a regression plot between a source attribute and a target attribute.


# Response
Certainly! Here is a Python code that can create a regression plot between a source attribute and a target attribute:

```python
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt

# Assume 'df' is the pandas data frame you are working with
# Assume 'source_attribute' is the name of the source attribute
# Assume 'target_attribute' is the name of the target attribute

# Create a regression plot using Seaborn
sns.regplot(x=df['source_attribute'], y=df['target_attribute'])

# Show the plot
plt.show()
```

This code will create a regression plot between the specified source and target attributes of the dataframe 'df'. The regression plot will show the relationship between the source attribute and the target attribute, along with a regression line that represents the best-fit line for the data.


# Model Development and Evaluation

# Prompt 7
Write a python code to fit a linear regression model on a target variable on basis of a source variable. Calculate the R^2 values and MSE values for this model.


# Response
Certainly! Here is a Python code that fits a linear regression model on a target variable based on a source variable, calculates the R^2 value, and Mean Squared Error (MSE) for this model:

```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_squared_error
import pandas as pd

# Assume 'df' is the pandas data frame you are working with
# Assume 'source_attribute' is the name of the source attribute
# Assume 'target_attribute' is the name of the target attribute

# Create the feature matrix X and target vector y
X = df[['source_attribute']]
y = df['target_attribute']

# Fit a linear regression model
model = LinearRegression()
model.fit(X, y)

# Predict the target variable
y_pred = model.predict(X)

# Calculate R^2 value
r2 = r2_score(y, y_pred)

# Calculate Mean Squared Error (MSE)
mse = mean_squared_error(y, y_pred)

print("R^2 value:", r2)
print("Mean Squared Error (MSE):", mse)
```

This code will fit a linear regression model on the target variable based on the source variable in the dataframe 'df'. It will then calculate the R^2 value, which represents the goodness of fit of the model, and the Mean Squared Error (MSE), which quantifies the average squared difference between the predicted and actual values.


# Prompt 8
Write a python code to fit a linear regression model on a target variable on basis of a set of source variables. Calculate the R^2 values and MSE values for this model.


# Response
Certainly! Here is a Python code that fits a linear regression model on a target variable based on a set of source variables, calculates the R^2 value, and Mean Squared Error (MSE) for this model:

```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_squared_error
import pandas as pd

# Assume 'df' is the pandas data frame you are working with
# Assume 'source_attributes' is a list of names of the source attributes
# Assume 'target_attribute' is the name of the target attribute

# Create the feature matrix X and target vector y
X = df[source_attributes]
y = df['target_attribute']

# Fit a linear regression model
model = LinearRegression()
model.fit(X, y)

# Predict the target variable
y_pred = model.predict(X)

# Calculate R^2 value
r2 = r2_score(y, y_pred)

# Calculate Mean Squared Error (MSE)
mse = mean_squared_error(y, y_pred)

print("R^2 value:", r2)
print("Mean Squared Error (MSE):", mse)
```

This code will fit a linear regression model on the target variable based on the set of source variables in the dataframe 'df'. It will then calculate the R^2 value, which represents the goodness of fit of the model, and the Mean Squared Error (MSE), which quantifies the average squared difference between the predicted and actual values.


# Prompt 9
Write a python code that can perform the following tasks.

1. Create a pipeline with standard scalar, second degree polynomial features and linear regression model.
2. Fit this pipeline for a target variable using a set of source attributes from a dataframe.
3. Evaluate the R^2 and MSE values for the trained model.


# Response
Certainly! Here is a Python code that can perform the tasks you mentioned:

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler, PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_squared_error
import pandas as pd

# Assume 'df' is the pandas data frame you are working with
# Assume 'source_attributes' is a list of names of the source attributes
# Assume 'target_attribute' is the name of the target attribute

# Create the feature matrix X and target vector y
X = df[source_attributes]
y = df['target_attribute']

# Create a pipeline with StandardScaler, PolynomialFeatures, and LinearRegression
pipeline = Pipeline([
    ('scaler', StandardScaler()),
    ('poly_features', PolynomialFeatures(degree=2)),
    ('regression', LinearRegression())
])

# Fit the pipeline
pipeline.fit(X, y)

# Predict the target variable
y_pred = pipeline.predict(X)

# Calculate R^2 value
r2 = r2_score(y, y_pred)

# Calculate Mean Squared Error (MSE)
mse = mean_squared_error(y, y_pred)

print("R^2 value:", r2)
print("Mean Squared Error (MSE):", mse)
```

This code will create a pipeline with StandardScaler, PolynomialFeatures (second degree), and LinearRegression. It will fit the pipeline on the target variable based on the set of source attributes in the dataframe 'df', and then evaluate the R^2 value and Mean Squared Error (MSE) for the trained model.


# Prompt 10
Write a python code that can perform the following tasks.

1. Assuming that a subset of the attributes of a data frame are source attributes and one of the attributes is a target attribute, split the data into training and testing data assuming the testing data to be 20%.
2. Create and fit a Ridge regression model using the training data, setting the regularization parameter to 0.1.
3. Calculate the MSE and R^2 values for the Ridge Regression model using the testing data.


# Response
Certainly! Here is a Python code that can perform the tasks you mentioned:

```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import Ridge
from sklearn.metrics import r2_score, mean_squared_error
import pandas as pd

# Assume 'df' is the pandas data frame you are working with
# Assume 'source_attributes' is a list of names of the source attributes
# Assume 'target_attribute' is the name of the target attribute

# Create the feature matrix X and target vector y
X = df[source_attributes]
y = df['target_attribute']

# Split the data into training and testing sets (80% training, 20% testing)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Create and fit a Ridge regression model with regularization parameter = 0.1
ridge_model = Ridge(alpha=0.1)
ridge_model.fit(X_train, y_train)

# Predict the target variable using the testing data
y_pred = ridge_model.predict(X_test)

# Calculate R^2 value
r2 = r2_score(y_test, y_pred)

# Calculate Mean Squared Error (MSE)
mse = mean_squared_error(y_test, y_pred)

print("R^2 value:", r2)
print("Mean Squared Error (MSE):", mse)
```

This code will first split the data into training and testing sets (80% training, 20% testing) based on the source and target attributes provided in the dataframe 'df'. It will then create and fit a Ridge regression model with a regularization parameter of 0.1 using the training data. Finally, it will calculate the R^2 value and Mean Squared Error (MSE) for the Ridge Regression model using the testing data.


# Prompt 11
Write a python code that can perform the following tasks.

1. Assuming that a subset of the attributes of a data frame are source attributes and one of the attributes is a target attribute, split the data into training and testing data assuming the testing data to be 20%.
2. Apply second degree polynomial scaling to the training and testing data.
3. Create and fit a Ridge regression model using the training data, setting the regularization parameter to 0.1.
4. Calculate the MSE and R^2 values for the Ridge Regression model using the testing data.


# Response
Certainly! Here is a Python code that can perform the tasks you mentioned:

```python
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import Ridge
from sklearn.metrics import r2_score, mean_squared_error
import pandas as pd

# Assume 'df' is the pandas data frame you are working with
# Assume 'source_attributes' is a list of names of the source attributes
# Assume 'target_attribute' is the name of the target attribute

# Create the feature matrix X and target vector y
X = df[source_attributes]
y = df['target_attribute']

# Split the data into training and testing sets (80% training, 20% testing)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Apply second degree polynomial scaling to the training and testing data
poly = PolynomialFeatures(degree=2)
X_train_poly = poly.fit_transform(X_train)
X_test_poly = poly.transform(X_test)

# Create and fit a Ridge regression model with regularization parameter = 0.1
ridge_model = Ridge(alpha=0.1)
ridge_model.fit(X_train_poly, y_train)

# Predict the target variable using the testing data
y_pred = ridge_model.predict(X_test_poly)

# Calculate R^2 value
r2 = r2_score(y_test, y_pred)

# Calculate Mean Squared Error (MSE)
mse = mean_squared_error(y_test, y_pred)

print("R^2 value:", r2)
print("Mean Squared Error (MSE):", mse)
```

This code will split the data into training and testing sets (80% training, 20% testing) based on the source and target attributes provided in the dataframe 'df'. It will then apply second degree polynomial scaling to the training and testing data, create and fit a Ridge regression model with a regularization parameter of 0.1 using the training data, and finally calculate the R^2 value and Mean Squared Error (MSE) for the Ridge Regression model using the testing data.


# Prompt 12
Write a python code that can perform the following tasks.

1. Assuming that a subset of the attributes of a data frame are source attributes and one of the attributes is a target attribute, split the data into training and testing data assuming the testing data to be 20%.
2. Apply second degree polynomial scaling to the training and testing data.
3. Create and fit a Grid search on Ridge regression with cross validation using the training data, for a set of values of the parameter alpha.
4. Calculate the MSE and R^2 values for the Ridge Regression model using the testing data.


# Response
Certainly! Here is a Python code that can perform the tasks you mentioned:

```python
from sklearn.model_selection import train_test_split, GridSearchCV
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import Ridge
from sklearn.metrics import r2_score, mean_squared_error
import pandas as pd

# Assume 'df' is the pandas data frame you are working with
# Assume 'source_attributes' is a list of names of the source attributes
# Assume 'target_attribute' is the name of the target attribute

# Create the feature matrix X and target vector y
X = df[source_attributes]
y = df['target_attribute']

# Split the data into training and testing sets (80% training, 20% testing)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Apply second degree polynomial scaling to the training and testing data
poly = PolynomialFeatures(degree=2)
X_train_poly = poly.fit_transform(X_train)
X_test_poly = poly.transform(X_test)

# Create Ridge regression model
ridge = Ridge()
parameters = {'alpha': [0.1, 1, 10]}  # Set of values for the parameter alpha

# Perform Grid search with cross validation
ridge_grid = GridSearchCV(ridge, parameters, cv=5)
ridge_grid.fit(X_train_poly, y_train)

# Predict the target variable using the testing data
y_pred = ridge_grid.predict(X_test_poly)

# Calculate R^2 value
r2 = r2_score(y_test, y_pred)

# Calculate Mean Squared Error (MSE)
mse = mean_squared_error(y_test, y_pred)

print("R^2 value:", r2)
print("Mean Squared Error (MSE):", mse)
```

This code will first split the data into training and testing sets (80% training, 20% testing) based on the source and target attributes provided in the dataframe 'df'. It will then apply second degree polynomial scaling to the training and testing data, create a Ridge regression model, perform a Grid search with cross validation for a set of values of the parameter alpha using the training data, and finally calculate the R^2 value and Mean Squared Error (MSE) for the Ridge Regression model using the testing data.

