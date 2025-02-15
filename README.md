# Global Gasoline Price Analysis


## Table of content

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Collection](#data-collection)
- [Data Preparation](#data-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Findings](#findings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#references)



### Project Overview
In this project, I scraped, cleaned, analyzed, and visualized data on the price of gasoline by country worldwide to understand global pricing trends and identify regional disparities.

![Screenshot 2024-12-16 3 51 22 PM](https://github.com/user-attachments/assets/d292c661-b613-412a-9bb3-5127cc2f01dc)



### Data Sources
Data for this project was sourced from  [GlobalPetrolPrices.com](https://www.globalpetrolprices.com/), a comprehensive platform providing up-to-date fuel price information across countries worldwide. 




### Tools 
- Python (BeautifulSoup, Requests, and pandas) 
- Google Sheet
- Looker Studio




### Data Collection
The data was scraped using Python libraries Beautiful Soup and Requests to ensure accurate and detailed insights into global gasoline price trends. Specifically, the following tasks were performed: 
- Importing the Libraries
```python 3
from bs4 import BeautifulSoup
import requests
import pandas as pd
```

- Specifying the URL
  ```python 3
  url = 'https://www.globalpetrolprices.com/gasoline_prices/'
  ```

- Sending an HTTP request to the website and retrieving the HTML content

```python 3
page = requests.get(url)
soup = BeautifulSoup(page.text, 'html')
soup
```

- Parsing the HTML content to extract the relevant data fields

  ```python 3
  data_column1 = soup.find_all('a', {'class': 'graph_outside_link'})
  data_column2 = soup.find_all('div', {'id': 'graphic'})
  ```
  
- Cleaning and structuring the extracted data into a tabular format using pandas

  ``` python 3
  column_columnA = [column.text.strip() for column in data_column1]
  column_columnB = [column2.text.strip() for column2 in data_column2]
  column_columnC = [item.strip() for item in column_columnB[0].split('\n\n')]
  df = pd.DataFrame({'Countries': column_columnA, 'Gasoline price': column_columnC})
  print(df)
  ```
- Exporting the cleaned dataset to a CSV file for further analysis and visualization
  ``` python 3
  df.to_csv('worldwide gasoline prices.csv', index = False)
  ```



### Data Preparation
The data was cleaned using Google Sheets. Specifically, the following tasks were performed:

- Importing the scraped data into Google Sheets
- Formatting columns for clarity, such as separating country names and currency format of gasoline prices
- Handling inconsistent data
- Adding country specific data to categorize countries by regions, GDP, population, and oil producing status (oil producing or non-oil producing) for comparative analysis



 ### Exploratory Data Analysis
  
In this phase, the dataset was explored to answer key questions about global gasoline price trends, including:
- What are the cost of gasoline across different countries worldwide?
- What are the regional variations in gasoline prices across different countries worldwide?
- How do gasoline prices vary across oil-producing versus non-oil-producing countries?




### Findings
The findings derived rom this analysis are as follows:

- Regional variations in gasoline prices were evident with regions like Western and Northern Europe experiencing higher prices than Asia and Africa
- The gasoline prices of oil-producing countries were typically lower, whereas non-oil-producing countries faced higher prices due to imported crude oil costs.


### Recommendations 
In light of the findings from the data analysis, the following recommendations are proposed:
- For oil-producing countries, consider revising subsidies to better align domestic gasoline prices with international market rates, thereby reducing fiscal strain.

- In non-oil-producing countries, implementing taxes that reflect environmental and economic costs could better manage fuel consumption and improve revenue.
- For countries with higher gasoline prices due to economic factors, policies aimed at economic diversification could help alleviate fuel cost pressures.
- Regularly updating subsidies and taxes based on global crude oil prices and domestic economic conditions can help maintain stable gasoline pricing.



### Limitations 

1. The analysis is based solely on the data available from [GlobalPetrolPrices.com](https://www.globalpetrolprices.com/), which may not capture the most up-to-date or comprehensive gasoline pricing data across all countries.  
2. The dataset does not include factors such as geopolitical influences or environmental policies that could impact gasoline prices.
3.  The study does not differentiate between temporary price fluctuations due to market volatility and long-term pricing trends, which could affect the findings.   
5. The inclusion of oil-production status might oversimplify the complexity of subsidies and pricing mechanisms within different countries.


### References
GlobalPetrolPrices.com. (n.d.). Retrieved from https://www.globalpetrolprices.com/

