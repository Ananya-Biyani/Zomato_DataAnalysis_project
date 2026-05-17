Zomato Restaurant Data Analysis | Python Data Analytics Project

An exploratory data analysis (EDA) project using Python to analyze restaurant trends, customer preferences, online ordering behavior, ratings, and pricing patterns from Zomato restaurant data.

This project demonstrates practical skills in:

Data Cleaning
Exploratory Data Analysis (EDA)
Data Visualization
Customer Behavior Analysis
Business Insight Generation
Python Analytics Libraries

Project Overview

The objective of this project is to analyze Zomato restaurant data and uncover meaningful insights about:

Restaurant categories
Customer voting trends
Ratings distribution
Online vs offline ordering behavior
Cost preferences among customers
Restaurant service patterns

Using Python visualization libraries such as Matplotlib and Seaborn, the project transforms raw restaurant data into actionable business insights.

Tech Stack
Technology	Purpose
Python	Data Analysis
Pandas	Data Cleaning & Manipulation
NumPy	Numerical Operations
Matplotlib	Data Visualization
Seaborn	Statistical Visualization
Jupyter Notebook	Analysis Environment

Dataset Information

The dataset contains restaurant-related information such as:

Column Name	Description
name	Restaurant name
online_order	Online order availability
book_table	Table booking availability
rate	Restaurant rating
votes	Number of customer votes
approx_cost(for two people)	Approximate cost for two
listed_in(type)	Restaurant category/type

Project Workflow
1️. Data Loading
Imported Zomato dataset using Pandas.
Performed initial dataset inspection.
import pandas as pd

dataframe = pd.read_csv("Zomato data .csv")

2️. Data Cleaning

Performed:
Rating column transformation
Data type corrections
Removal of unwanted formatting
Rating Conversion
def handleRate(value):
    value = str(value).split('/')
    value = value[0]
    return float(value)

dataframe['rate'] = dataframe['rate'].apply(handleRate)

3. Exploratory Data Analysis (EDA)

Analyzed:

Restaurant categories
Customer votes
Ratings distribution
Spending behavior
Online ordering patterns

Analysis & Insights
🔹 Restaurant Type Analysis
Objective

Identify which restaurant category is most common.

Visualization
sns.countplot(x=dataframe['listed_in(type)'])
Insight
Majority of restaurants fall under the Dining category.

Customer Vote Trends
Objective

Analyze which restaurant types receive the highest customer engagement.

Visualization
groupeddata = dataframe.groupby("listed_in(type)")["votes"].sum()
Insight
Dining restaurants receive the highest number of customer votes

🔹 Ratings Distribution Analysis
Objective

Understand overall restaurant rating trends.

Visualization
plt.hist(dataframe['rate'], bins=10)
Insight
Most restaurants are rated between 3.5 and 4.0.

Cost Preference Analysis
Objective

Analyze spending preferences among customers.

Visualization
sns.countplot(x=dataframe['approx_cost(for two people)'])
Insight
Most couples prefer restaurants with an approximate cost of ₹300.

🔹 Online vs Offline Order Ratings
Objective

Compare ratings between restaurants accepting online orders and offline-only restaurants.

Visualization
sns.boxplot(x='online_order', y='rate', data=dataframe)
Insight
Restaurants accepting online orders generally receive better ratings compared to offline-only restaurants.

🔹 Online Order Heatmap Analysis
Objective

Analyze restaurant types and their online ordering patterns.

Visualization
pivot_table = dataframe.pivot_table(
    index='listed_in(type)',
    columns='online_order',
    aggfunc='size',
    fill_value=0
)

sns.heatmap(pivot_table, annot=True, cmap="YlGnBu", fmt='d')
Insight
Dining restaurants primarily receive offline orders.
Cafes receive more online orders.
Customers prefer in-person dining for restaurants and online ordering for cafes.
💡 Key Business Insights
Dining restaurants dominate the market share.
Customer engagement is highest for dining restaurants.
Restaurants with online ordering options tend to receive better ratings.
Mid-range restaurants (~₹300 for two people) are most preferred by customers.
Consumer behavior differs significantly across restaurant categories.

📈 Skills Demonstrated
Data Cleaning
Exploratory Data Analysis (EDA)
Data Visualization
Business Insight Generation
Customer Behavior Analysis
Python Programming
Pandas Data Manipulation
Seaborn & Matplotlib Visualization

Restaurant analytics helps businesses:

Understand customer preferences
Improve customer satisfaction
Optimize pricing strategies
Enhance online ordering experience
Increase customer engagement

This project demonstrates how data analysis can drive better business decisions in the food and restaurant industry.

