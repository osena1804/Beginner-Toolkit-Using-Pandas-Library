# Beginner-Toolkit-Using-Pandas-Library
🐼 Pandas Pilot: A Beginner's Toolkit for Data Mastery
Welcome to the Pandas Pilot Toolkit! This project is designed to take you from "Zero to Hero" in data manipulation using Python's most powerful library: pandas.

📖 Table of Contents
Overview

Setup Guide

The Dataset

The Master Script

Troubleshooting

Cheat Sheet

Reference 
🌟 Overview
This project was developed as a Capstone to demonstrate the power of Generative AI-assisted software development. The goal was to build a comprehensive "First-Steps" toolkit for aspiring data analysts.

Using a custom-built dataset (moringa_toolkit.csv), this repository guides users through the core pillars of the Pandas library:

Data Wrangling: Transforming messy, inconsistent raw data into a clean, structured format.

Feature Engineering: Creating new data insights through column transformations.

Exploratory Data Analysis (EDA): Using statistical methods to understand data distributions.

Visual Storytelling: Leveraging Matplotlib to turn code into actionable charts.

🛠️ Setup Guide
To get started, you need a Python environment.

Install Pandas: Open your terminal and run: pip install pandas matplotlib

Verify: Run import pandas as pd in your script.

File Management: Always keep your Python script and your data file (moringa_toolkit.csv) in the same folder.

📂 The Dataset
Create a file named moringa_toolkit.csv and paste the following 20 rows of "messy" bookstore data:

Plaintext

Order_ID,Book_Title,Price,Quantity,Date
101,The Great Gatsby,15.99,1,2023-01-01
102,the great gatsby,15.99,1,2023-01-01
103,1984,,2,2023-01-02
... (add all 20 rows here)
🐍 The Master Script
This script performs the cleaning, transformation, and visualization automatically.

Python

import pandas as pd
import matplotlib.pyplot as plt

# 1. LOAD
try:
    df = pd.read_csv('moringa_toolkit.csv')
    
    # 2. CLEAN
    df['Book_Title'] = df['Book_Title'].str.strip().str.title()
    df = df.drop_duplicates()
    df['Price'] = df['Price'].fillna(df['Price'].median())
    df['Quantity'] = df['Quantity'].fillna(1)

    # 3. TRANSFORM
    df['Total_Revenue'] = df['Price'] * df['Quantity']

    # 4. ANALYZE
    top_books = df.groupby('Book_Title')['Total_Revenue'].sum().sort_values(ascending=False)

    # 5. VISUALIZE
    top_books.head(5).plot(kind='bar', title='Top 5 Books by Revenue')
    plt.ylabel('Revenue ($)')
    plt.show()

except FileNotFoundError:
    print("Error: Ensure 'moringa_toolkit.csv' is in the same folder as this script!")
🔍 Troubleshooting
Error	Likely Cause	Solution
FileNotFoundError	File is in a different folder	Move the CSV to the script's folder
KeyError	Typo in column name	Check df.columns for exact spelling
AttributeError	Used a string function on a whole table	Specify the column: df['Col'].str

Export to Sheets

📜 Quick Cheat Sheet
df.head(): Preview data.

df.info(): Check for missing values.

df.describe(): Get statistical summaries.

df.groupby(): Summarize data by categories.

plt.show(): Display your charts.

Testing & Quality Assurance
To ensure the toolkit remains functional and accurate, the following tests were performed during the development cycle:

Data Integrity Check: Verified that all 20 rows of raw data were processed and that the final output contained zero null values in the Price and Quantity columns.

Path Validation: Tested the script across different directory structures to ensure the FileNotFoundError was handled gracefully.

Transformation Accuracy: Manually cross-checked the Total_Revenue calculation (Price×Quantity) for the first 5 rows to ensure mathematical accuracy.

Visualization Logic: Confirmed that the bar chart correctly displays only the Top 5 books sorted by revenue.

Iteration History
This project followed an Agile Iteration process:

V1.0: Initial script to load and print raw CSV data.

V1.1: Added cleaning logic (capitalization and duplicate removal).

V1.2: Integrated matplotlib for visual reporting.

V1.3 (Final): Refactored file naming conventions and added error handling for a smoother beginner experience.

Reference 

Alex The Analyst. (2023, May 25). Pandas for Beginners [YouTube playlist]. YouTube. https://www.youtube.com/playlist?list=PLUaB-1hjhk8GZOuylZqLz-Qt9RIdZZMBE

pandas development team. "User Guide — pandas 2.3.3 documentation." pandas, 2025, https://pandas.pydata.org/docs/user_guide/index.html.
