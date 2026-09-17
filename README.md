# ECE-2112-PA-4

**Made by: Myk Zachary Marcian M. San Miguel | 2ECE-D 2026-'27**

This repository contains the contents of Programming Assignment 4 for our Advanced Computer Programming Course this S.Y. 2026-2027. This programming assignment covers three Python problems regarding Data Wrangling and Visualization.

Before we start, we need to load the pandas library so we can use it. After loading the pandas library, we would then load a `.csv` dataset supplied named `cars.csv`
```python
import pandas as pd
#This lets us use the pandas library

import matplotlib.pyplot
# This lets us utilize the matplot library
```
---

## Part A: Positional and Label-Based Slicing
### Objective
Create a DataFrame named `VisComm` that contains student whose `Track` is `Communication`. Retain only these columns, in the order of `Name`, `Gender`, `Math`, `Electronics`, `Average`
### Discussion
- For the first line
```python
data = pd.read_excel('board2.xlsx')
data['Average']=((data['Math'])+(data['Electronics'])+(data['GEAS'])+(data['Communication']))/4

VisComm = data.loc[(data['Track']=='Communication')&(data['Hometown']=='Visayas'), ['Name', 'Gender', 'Math', 'Electronics', 'Average']]
display(VisComm)
print('Number of Rows: ', len(VisComm))
```

## Part B: Model Lookup
### Objective
Create a second DataFrame named `VisFemale` containing student whose `Hometown` is `Visayas` and whose `Gender` is `Female`. Retain the `Name`, `Track`, `GEAS`, `Electronics`, `Average`
### Discussion
```python
VisFemale = data.loc[(data['Gender']=='Female')&(data['Hometown'])=='Visayas'),['Name','Track','GEAS','Electronics','Average']]
display(VisFemale)

display(VisFemale.loc[VisFemale['Average']>=60])
```

## Part C: Multi-Model Subsetting
### Objective
- Compute the mean of `Average` for every category using Pandas
- Display the three summary tables
- Create one figure that contains the three bar charts which contain the `Average` by `Track`, by `Gender`, and by `Hometown`
- Write three statements identifying the category with the highest sample mean for each feature 
### Discussion

---
## Final Remarks

## History 
**September 16, 2026** - This repository was created and initial .ipynb file was uploaded\

**September 17, 2026** - Added the excel file and the README as well as the .ipynb file were revised

**September 18, 2026** - The README and .ipynb file were further revised and beautified
