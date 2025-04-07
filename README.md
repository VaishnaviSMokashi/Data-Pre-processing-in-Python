A] These are core libraries - 
1) pandas is used for data manipulation and analysis. You need pandas to load and handle your dataset.
2) numpy helps with numerical operations (especially arrays). numpy is often used in ML for handling arrays/matrices efficiently.
3) matplotlib.pyplot is used for plotting graphs. matplotlib is great for visualizing the data before and after processing.

B] read_csv() is one of the most common ways to import tabular data into Python. We use it whenever we’re starting with raw data stored in a CSV file.

C] X gets all columns except the last one — these are your features (independent variables).
Y gets the last column — this is your target (dependent variable).
.values converts the result into NumPy arrays for ML models.
Why :- You need to separate inputs (features) and outputs (target) before training a model.
When to use :- Right after loading your data — essential before applying preprocessing or modeling.

D] ML models can’t handle missing values (NaNs), so you need to fill them with something (mean, median, mode, etc.). Using the mean is a common strategy for numerical data.
SimpleImputer is used to handle missing values (like NaNs). It replaces missing values in columns 1 and 2 of X with the mean of those columns.
fit() learns the mean from the data.
transform() applies the learned mean to fill in missing values.
Use this whenever you have missing numerical data. Choose strategy='mean', 'median', or 'most_frequent' depending on the data distribution.

E] ML models can’t work with text — they need numerical input.
One-hot encoding is preferred when categories are not ordinal (e.g., "France", "Germany", "Spain").
This code encodes the first column (index 0) of X, which contains categorical data (like country names).
OneHotEncoder() converts each unique category into a binary column (0 or 1).
ColumnTransformer applies this encoding only to the specified column and leaves the rest untouched.
fit_transform() applies this encoding, and np.array() ensures the output is a NumPy array.
Use OneHotEncoder when your categorical features have no natural order. If the feature has an order (like "Low", "Medium", "High"), you might use OrdinalEncoder instead.

F] Training Set: Used to train (fit) the model — this is where the model “learns.”
Testing Set: Used to evaluate how well the model performs on unseen data — this tests generalization.
Common practice is to split 80% for training, 20% for testing, but you might also use 70/30 or even cross-validation.

G] Feature Scaling means standardizing or normalizing the range of independent variables (features) in your data so they are on the same scale.
It reshapes your data so that all features have the same level of influence. This means the model won’t favor one feature just because it has larger values.
