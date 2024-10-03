# NYC Airbnb Price Analysis and Dashboard

## Project Overview
This project aims to analyze the pricing of Airbnb listings in New York City using Python for data cleaning and preparation, and Tableau for interactive visualizations. The main objective is to understand the factors influencing Airbnb prices, such as neighborhood, room type, and availability.

## Table of Contents
1. [Data Cleaning and Preparation](#data-cleaning-and-preparation)
2. [Exploratory Data Analysis](#exploratory-data-analysis)
3. [Tableau Visualizations](#tableau-visualizations)
4. [Conclusion and Insights](#conclusion-and-insights)

## Data Cleaning and Preparation
The initial steps of this project focused on loading the dataset, handling missing values, and performing basic feature engineering using Python. Below are the steps followed:

### 1. Loading the Dataset
The dataset was loaded using `pandas` and explored to understand its structure and identify any missing values.

```python
import pandas as pd

# Load the cleaned dataset
file_path = r'C:\Users\Christopher Pruna\Desktop\Airbnb Data Analysis Project\Cleaned_NYC_Airbnb.csv'
airbnb_df = pd.read_csv(file_path)
print(airbnb_df.head())
2. Handling Missing Values
We filled missing values in the reviews_per_month column with zeros and dropped any unnecessary columns.

python
Copy code
# Fill missing values in 'reviews_per_month' with 0
airbnb_df['reviews_per_month'].fillna(0, inplace=True)
3. Feature Engineering
A new feature, price_per_person, was created to analyze the price effectiveness of each listing.

python
Copy code
# Create 'price_per_person' feature
airbnb_df['price_per_person'] = airbnb_df.apply(
    lambda row: row['price'] / row['accommodates'] if row['accommodates'] > 0 else 0, axis=1
)
4. Saving the Cleaned Dataset
The cleaned dataset was saved to be used in Tableau for visualization.

python
Copy code
# Save the cleaned dataset
clean_file_path = r'C:\Users\Christopher Pruna\Desktop\Airbnb Data Analysis Project\Cleaned_NYC_Airbnb.csv'
airbnb_df.to_csv(clean_file_path, index=False)
print("Cleaned dataset saved successfully.")
Exploratory Data Analysis
The EDA was performed to understand the distribution of prices and the relationship between different features.

Price Distribution
A histogram was created to visualize the distribution of Airbnb prices.

python
Copy code
import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(10, 6))
sns.histplot(airbnb_df['price'], bins=50, kde=True, color='skyblue')
plt.title('Distribution of Listing Prices')
plt.xlabel('Price ($)')
plt.ylabel('Number of Listings')
plt.show()
Tableau Visualizations
After cleaning and preparing the dataset, we used Tableau to create interactive visualizations. Below are the visualizations and their descriptions:

1. Price vs. Number of Reviews
This scatter plot shows the relationship between price per night and the number of reviews. Higher-priced listings tend to have fewer reviews.


2. Map View of Listings
The map visualization highlights the locations of Airbnb listings across NYC, with larger dots representing higher prices.


3. Average Price by Neighborhood Group
This bar chart compares the average price across different boroughs in NYC. Manhattan has the highest average price, followed by Brooklyn.


4. Average Price by Room Type
This bar chart shows the average price for each room type. Entire homes/apartments are significantly more expensive than private or shared rooms.


Conclusion and Insights
Based on the analysis, the following conclusions were drawn:

Manhattan is the most expensive borough for Airbnb listings.
Entire homes/apartments are generally more expensive compared to private or shared rooms.
Listings with higher prices tend to have fewer reviews, possibly indicating they are less popular or affordable for the average visitor.
Future Work
Future analysis can include:

Understanding the impact of specific amenities on price.
Predictive modeling to forecast prices based on various features.
Contact
For any questions or feedback, please reach out to Christopher Pruna.
