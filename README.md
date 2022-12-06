
# Nigeria Covid-19 cases analysis using clustering Algorithm 

According to the official website of the Nigeria Center for Disease and Control, covid-19 cases confirmed is 266,283, and 3,155 was recorded. 
This analysis is aimed at analyzing these cases using an unsupervised Algorithm (clustering Algorithm) to find patterns and also check the cluster of similar states and also made the deduction on the states that need to be alerted 
## Installation

To run this file, the following steps should be followed

```bash
  Download Anaconda or python 3x
  pip install requirements.txt
```
    
## Run Locally

Clone the project

```bash
  git clone https://https://github.com/elugabriel/covid-19-Analysis
```

locate the file with .ipynb extention

```bash
  open with anaconda
```

Install dependencies

```bash
pip install requirements.txt
```




## Methodology
There are quite a number of techniques that was adopted in this analysis and this 
will be presented sep by step and performed on the jupyter notebook. 


## Web Scrapping 
The first stage of the analysis was to extract the dataset from the official website of 
NCDC. This is due to the fact that the data was not readily available in the data repository. 
The code for the Scrapping is shown below





```bash
 import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import urllib.request
from pprint import pprint
from html.parser import HTMLParser
import requests
```

```bash
 from bs4 import BeautifulSoup as bs 
 r = requests.get('https://covid19.ncdc.gov.ng') 
 soup = bs(r.content)
 table = soup.select('table#custom1')[0]
 columns = table.find('thead').find_all('th')
```
This return a table comprising of the dataset
## Data Exploration and picking the Right number of cluster
The next stage in the analysis is checking for missing data and since the data is not large, this is detected by mere inspection of the data. 
The next task in the analysis was to determine the right number of K (cluster) which is a crucial part of clustering algorithm.
Elbow method was used and was ploted using matplotlib

The graph above shows that the best K is 3 which was used to build the clustering algorithm

## Result and Deduction
After visualizing the cluster using scatter plot, it was discovered that some states shared the same / similar covid-19 instances. some of these states are not given much attention. 
There are three main cluster or groups as deplicted by the chart.

    1. States with low number of confrim cases and low death cases, Majority of states fall under this category the states that fall 
       under this categories include Abia
        Adamawa, 
        Akwa Ibom, 
        Anambra, 
        Bauchi, 
        Bayelsa, 
        Benue, 
        Borno,
        Cross River, 
        Ebonyi, 
        Ekiti, 
        Enugu, 
        Gombe, 
        Imo, 
        Jigawa, 
        Kaduna, 
        Kano, 
        Katsina, 
        Kebbi, 
        Kogi, 
        Niger, 
        Ogun, 
        Osun, 
        Plateau, 
        Sokoto, 
        Taraba, 
        Yobe, 
        Zamfara

              
    2. States with low number of confrim cases and high death cases. The state under this category include
        Kwara
        Nasarawa
        Ondo
        From the analysis, these states needs more medical attentions because the result suggested that
        many of the patients don't survive it. This can be improved through increase in medical personel and 
        equipment.
    
    3. The tird category are the one with low number of confrim cases and high death rate. state under this category are 
        Edo
        FCT
        Oyo
        Rivers
    5. There is a state which doesn't belong to any of these categories. Lagos state,
        The analysis sees it as an outliers because the it's pattern cannot be related to any of the state
        It has an extreme high number of cases as well as the death cases. This states require more 
        medical attentions and personel
## Authors

- [@Gabriel](https://www.github.com/elugabriel)

