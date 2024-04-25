# Prompt 1
Write a Python code that can perform the following tasks.
Read the CSV file, located on a given file path, into a pandas data frame, assuming that the first row of the file can be used as the headers for the data.


# Response 
import pandas as pd

# Define the file path
file_path = "path/to/your/csv/file.csv"

# Read the CSV file into a pandas data frame
data_frame = pd.read_csv(file_path)

# Assume the first row of the file can be used as the headers for the data
# If the file doesn't have headers, you can remove the 'header' parameter
data_frame = pd.read_csv(file_path, header=0)

# Additional details:
# - The 'pd.read_csv()' function is used to read a CSV file into a pandas data frame.
# - The 'header' parameter in the 'pd.read_csv()' function specifies which row to use as the headers.
#   By default, it is set to 'infer', which means pandas will try to infer the headers from the file.
#   If the headers are in the first row, you can set the 'header' parameter to 0.


# Prompt 2
Write a Python code that performs the following tasks.
1. Develops and trains a linear regression model that uses one attribute of a data frame as the source variable and another as a target variable.
2. Calculate and display the MSE and R^2 values for the trained model


# Response
import pandas as pd
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score

# Assume you have a pandas data frame called 'data_frame' with two columns: 'source_variable' and 'target_variable'

# Extract the source variable and target variable from the data frame
X = data_frame[['source_variable']]
y = data_frame['target_variable']

# Initialize a linear regression model
model = LinearRegression()

# Train the model using the source and target variables
model.fit(X, y)

# Make predictions using the trained model
y_pred = model.predict(X)

# Calculate the mean squared error (MSE)
mse = mean_squared_error(y, y_pred)

# Calculate the coefficient of determination (R^2)
r2 = r2_score(y, y_pred)

# Display the MSE and R^2 values
print("Mean Squared Error (MSE):", mse)
print("Coefficient of Determination (R^2):", r2)

# Additional details:
# - The 'LinearRegression' class from the 'sklearn.linear_model' module is used to create a linear regression model.
# - The 'fit()' method is used to train the model using the source and target variables.
# - The 'predict()' method is used to make predictions using the trained model.
# - The 'mean_squared_error()' function from the 'sklearn.metrics' module is used to calculate the MSE.
# - The 'r2_score()' function from the 'sklearn.metrics' module is used to calculate the R^2 value.


# Prompt 3
Write a Python code that performs the following tasks.
1. Develops and trains a linear regression model that uses some attributes of a data frame as the source variables and one of the attributes as a target variable.
2. Calculate and display the MSE and R^2 values for the trained model.


# Response

import pandas as pd
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score

# Assume you have a pandas data frame called 'data_frame' with multiple columns: 'source_variable_1', 'source_variable_2', ..., 'target_variable'

# Extract the source variables and target variable from the data frame
X = data_frame[['source_variable_1', 'source_variable_2', ...]]
y = data_frame['target_variable']

# Initialize a linear regression model
model = LinearRegression()

# Train the model using the source and target variables
model.fit(X, y)

# Make predictions using the trained model
y_pred = model.predict(X)

# Calculate the mean squared error (MSE)
mse = mean_squared_error(y, y_pred)

# Calculate the coefficient of determination (R^2)
r2 = r2_score(y, y_pred)

# Display the MSE and R^2 values
print("Mean Squared Error (MSE):", mse)
print("Coefficient of Determination (R^2):", r2)

# Additional details:
# - The 'LinearRegression' class from the 'sklearn.linear_model' module is used to create a linear regression model.
# - The 'fit()' method is used to train the model using the source and target variables.
# - The 'predict()' method is used to make predictions using the trained model.
# - The 'mean_squared_error()' function from the 'sklearn.metrics' module is used to calculate the MSE.
# - The 'r2_score()' function from the 'sklearn.metrics' module is used to calculate the R^2 value.



# Prompt 4
Write a Python code that performs the following tasks.
1. Develops and trains multiple polynomial regression models, with orders 2, 3, and 5, that use one attribute of a data frame as the source variable and another as a target variable.
2. Calculate and display the MSE and R^2 values for the trained models.
3. Compare the performance of the models.


# Response
import pandas as pd
import numpy as np
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures
from sklearn.metrics import mean_squared_error, r2_score

# Assume you have a pandas data frame called 'data_frame' with two columns: 'source_variable' and 'target_variable'

# Extract the source variable and target variable from the data frame
X = data_frame[['source_variable']]
y = data_frame['target_variable']

# Initialize lists to store the MSE and R^2 values for each model
mse_values = []
r2_values = []

# Loop through the polynomial orders
for order in [2, 3, 5]:
    # Create polynomial features
    polynomial_features = PolynomialFeatures(degree=order)
    X_poly = polynomial_features.fit_transform(X)

    # Initialize a linear regression model
    model = LinearRegression()

    # Train the model using the polynomial features and target variable
    model.fit(X_poly, y)

    # Make predictions using the trained model
    y_pred = model.predict(X_poly)

    # Calculate the mean squared error (MSE)
    mse = mean_squared_error(y, y_pred)

    # Calculate the coefficient of determination (R^2)
    r2 = r2_score(y, y_pred)

    # Append the MSE and R^2 values to the lists
    mse_values.append(mse)
    r2_values.append(r2)

    # Display the MSE and R^2 values for the current model
    print(f"Polynomial Order {order}:")
    print("Mean Squared Error (MSE):", mse)
    print("Coefficient of Determination (R^2):", r2)
    print()

# Compare the performance of the models
best_order = np.argmin(mse_values)
worst_order = np.argmax(r2_values)

print("Model Comparison:")
print(f"Best Polynomial Order: {best_order + 2}")
print(f"Worst Polynomial Order: {worst_order + 2}")

# Additional details:
# - The 'PolynomialFeatures' class from the 'sklearn.preprocessing' module is used to create polynomial features.
# - The 'fit_transform()' method is used to transform the source variable into polynomial features.
# - The 'degree' parameter in the 'PolynomialFeatures' class specifies the maximum degree of the polynomial features.
# - The 'argmin()' and 'argmax()' functions from the 'numpy' module are used to find the index of the minimum and maximum values in a list, respectively.



# Prompt 5  create pipeline
Write a Python code that performs the following tasks.
1. Create a pipeline that performs parameter scaling, Polynomial Feature generation, and Linear regression. Use the set of multiple features as before to create this pipeline.
2. Calculate and display the MSE and R^2 values for the trained model.


# Reponse

import pandas as pd
import numpy as np
from sklearn.pipeline import make_pipeline
from sklearn.preprocessing import StandardScaler, PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score

# Assume you have a pandas data frame called 'data_frame' with multiple columns: 'source_variable_1', 'source_variable_2', ..., 'target_variable'

# Extract the source variables and target variable from the data frame
X = data_frame[['source_variable_1', 'source_variable_2', ...]]
y = data_frame['target_variable']

# Create a pipeline that performs parameter scaling, polynomial feature generation, and linear regression
pipeline = make_pipeline(
    StandardScaler(),
    PolynomialFeatures(degree=2),
    LinearRegression()
)

# Train the model using the source and target variables
pipeline.fit(X, y)

# Make predictions using the trained model
y_pred = pipeline.predict(X)

# Calculate the mean squared error (MSE)
mse = mean_squared_error(y, y_pred)

# Calculate the coefficient of determination (R^2)
r2 = r2_score(y, y_pred)

# Display the MSE and R^2 values
print("Mean Squared Error (MSE):", mse)
print("Coefficient of Determination (R^2):", r2)

# Additional details:
# - The 'make_pipeline()' function from the 'sklearn.pipeline' module is used to create a pipeline.
# - The 'StandardScaler' class from the 'sklearn.preprocessing' module is used to perform parameter scaling.
# - The 'PolynomialFeatures' class from the 'sklearn.preprocessing' module is used to create polynomial features.
# - The 'LinearRegression' class from the 'sklearn.linear_model' module is used for linear regression.
# - The pipeline automatically applies the transformations in the specified order.


# Prompt 6 Grid search and Ridge regression
Write a Python code that performs the following tasks.
1. Use polynomial features for some of the attributes of a data frame.
2. Perform Grid search on a ridge regression model for a set of values of hyperparameter alpha and polynomial features as input.
3. Use cross-validation in the Grid search.
4. Evaluate the resulting model's MSE and R^2 values.


# Response

import pandas as pd
import numpy as np
from sklearn.model_selection import GridSearchCV, cross_val_score
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import Ridge
from sklearn.metrics import mean_squared_error, r2_score

# Assume you have a pandas data frame called 'data_frame' with multiple columns: 'source_variable_1', 'source_variable_2', ..., 'target_variable'

# Extract the source variables and target variable from the data frame
X = data_frame[['source_variable_1', 'source_variable_2', ...]]
y = data_frame['target_variable']

# Create polynomial features
polynomial_features = PolynomialFeatures()

# Transform the source variables into polynomial features
X_poly = polynomial_features.fit_transform(X)

# Define the hyperparameter values for the grid search
param_grid = {'alpha': [0.1, 1.0, 10.0], 'degree': [2, 3, 4]}

# Initialize a ridge regression model
model = Ridge()

# Perform grid search with cross-validation
grid_search = GridSearchCV(model, param_grid, cv=5)

# Train the model using the polynomial features and target variable
grid_search.fit(X_poly, y)

# Make predictions using the trained model
y_pred = grid_search.predict(X_poly)

# Calculate the mean squared error (MSE)
mse = mean_squared_error(y, y_pred)

# Calculate the coefficient of determination (R^2)
r2 = r2_score(y, y_pred)

# Display the MSE and R^2 values
print("Mean Squared Error (MSE):", mse)
print("Coefficient of Determination (R^2):", r2)

# Additional details:
# - The 'PolynomialFeatures' class from the 'sklearn.preprocessing' module is used to create polynomial features.
# - The 'GridSearchCV' class from the 'sklearn.model_selection' module is used to perform grid search with cross-validation.
# - The 'Ridge' class from the 'sklearn.linear_model' module is used for ridge regression.
# - The 'fit_transform()' method is used to transform the source variables into polynomial features.
# - The 'param_grid' parameter in the 'GridSearchCV' class specifies the hyperparameter values to search over.
# - The 'cv' parameter in the 'GridSearchCV' class specifies the number of folds for cross-validation.
# - The best model found by grid search can be accessed using the 'best_estimator_' attribute of the grid search object.



