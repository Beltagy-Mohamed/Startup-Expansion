# Startup Expansion Data Analysis

## Overview

This repository contains a data analysis project focused on studying the expansion of startups in America. The dataset includes information about various stores, with key metrics related to sales, marketing spend, revenue, profit, Return on Marketing Spend (ROMS), and ROMS percentage.

## Code Snippet

```python
#!/usr/bin/env python
# coding: utf-8

# # Import Libraries 

import pandas as pd 
import numpy as np 
import seaborn as sns
import matplotlib.pyplot as plt

# # import Data

startups = pd.read_excel('C:\\Users\\peltage\\Source\\startup-expansion.xlsx')

startups.info()

startups[['Marketing Spend','Revenue']].describe().round(2)

# #  

# # Data Preprocessing 

startups['City'].nunique()
startups['City'].unique()
startups['City'].value_counts()

startups['State'].nunique()
startups['State'].unique()
startups['State'].value_counts()

startups['Sales Region'].unique()
startups['Sales Region'].value_counts()

startups['New Expansion'].unique()
startups['New Expansion'].value_counts()

startups.isna().sum()
startups.duplicated().sum()

# #  

# # Analysis Data 

startups.sample(15)

startups['Sales Region'].value_counts().plot.bar()

startups['New Expansion'].value_counts().plot.bar()

startups['Profit'] = startups['Revenue'] - startups['Marketing Spend']

startups[startups['New Expansion'] == 'Old'].groupby(['State']).sum()['Revenue'].nlargest(10)

startups[startups['New Expansion'] == 'New'].groupby(['State']).sum()['Revenue'].nlargest(10)

startups['ROMS'] = round((startups['Profit'] / startups['Marketing Spend']) * 100 , 2)

startups['ROMS%'] = startups['ROMS'] / 100

startups.to_csv('Startups_Ex.csv')
```

## Key Questions Explored

1. **Geographic Analysis:**
   - Which cities and states have the highest number of startup expansions?
   - How are sales regions distributed across the dataset?

2. **Performance Metrics:**
   - What is the average revenue and profit for stores in new expansions compared to existing ones?
   - How does Return on Marketing Spend vary across different sales regions?

3. **Correlation Analysis:**
   - Is there a correlation between marketing spend and revenue/profit?
   - How does the ROMS percentage correlate with other metrics?

## Tools and Libraries Used

- **Programming Language:** Python
- **Data Analysis Libraries:** Pandas, NumPy, Seaborn, Matplotlib

## Getting Started

1. Clone the repository to your local machine.
2. Install the required Python libraries using `pip install -r requirements.txt`.
3. Open and run the Jupyter Notebook (`Startup_Expansion_Analysis.ipynb`) to explore the analysis.

## Contribution Guidelines

Contributions are welcome! If you find issues or want to enhance the analysis, please submit a pull request or open an issue.

## License

This project is licensed under the [MIT License](LICENSE).
