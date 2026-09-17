# ECE-2112-PA-4

**Made by: Myk Zachary Marcian M. San Miguel | 2ECE-D 2026-'27**

This repository contains the contents of Programming Assignment 4 for our Advanced Computer Programming Course this S.Y. 2026-2027. This programming assignment covers three Python problems regarding Data Wrangling and Visualization.

Before we start, we need to load the pandas library so we can use it. After loading the pandas library, we would then load a `.csv` dataset supplied named `cars.csv`
```python
import pandas as pd
#This lets us use the pandas library

import matplotlib.pyplot
# This lets us utilize the matplotlib library
```
---

## Part A: Positional and Label-Based Slicing
### Objective
Create a DataFrame named `VisComm` that contains students whose `Track` is `Communication`. Retain only these columns, in the order of `Name`, `Gender`, `Math`, `Electronics`, `Average`
### Discussion
**Functions used:**
- `.read_excel()` - loads an excel file frm your folder/storage
- `.loc[row_indexer, column_indexer]` - selects the rows and columns by their index or by their name
- `len()` , gets the length of the DataFrame within the parenthesis

> `data = pd.read_excel('board2.xlsx')`

For the first line, we used the function `.read_excel('board2.xlsx')` from the Pandas library to load an Excel file from our storage which is named `board2.xlsx`.
> `data['Average']=((data['Math'])+(data['Electronics'])+(data['GEAS'])+(data['Communication']))/4`

The second line basically just gets the average grades from the four subjects which are `Math`, `Electronics`, `GEAS`, `Communication`.
> `VisComm = data.loc[(data['Track']=='Communication')&(data['Hometown']=='Visayas'), ['Name', 'Gender', 'Math', 'Electronics', 'Average']]`

This gets the data of students with a Communications Track and a Hometown of Visayas. Then only their `Name`, `Gender`, grades in `Math`, `Electronics`, as well as their `Average` grade.

Now that were done with getting the required data, we will then output the obtained data. The entire code should look like:

```python
data = pd.read_excel('board2.xlsx')
data['Average']=((data['Math'])+(data['Electronics'])+(data['GEAS'])+(data['Communication']))/4

VisComm = data.loc[(data['Track']=='Communication')&(data['Hometown']=='Visayas'), ['Name', 'Gender', 'Math', 'Electronics', 'Average']]

#The function below outputs/displays the result and the required data
display(VisComm)
print('Number of Rows: ', len(VisComm))
```

## Part B: Model Lookup
### Objective
Create a second DataFrame named `VisFemale` containing students whose `Hometown` is `Visayas` and whose `Gender` is `Female`. Retain the `Name`, `Track`, `GEAS`, `Electronics`, `Average`
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
```python
trackM = data.pivot_table(index='Track',values='Average',aggfunc='mean').reset_index()
genderM = data.pivot_table(index='Gender',values='Average',aggfunc='mean').reset_index()
hometownM = data.pivot_table(index='Hometown',values='Average',aggfunc='mean').reset_index()
display(trackM, genderM, hometownM)

bar, (track, gender, hometown) = plt.subplots(1,3,figsize=(16,5))

track.bar(trackM['Track'],trackM['Average'],color='black')
track.set(title='Mean Average by Track',xlabel='Tracks',ylabel='Average')
gender.bar(genderM['Gender'],genderM['Average'],color='gray')
gender.set(title='Mean Average by Gender',xlabel='Gender',ylabel='Average')
hometown.bar(hometownM['Hometown'], hometownM['Average'],color='#F5B427')
hometown.set(title='Mean Average by Hometown',xlabel='Hometowns',ylabel='Average')

bar.text(.12, -.1, 'Interpretations: \n', fontsize=20)
bar.text(.13, -.2, 'In the Track Category, the Communication track has the highest sample mean  67.9750.\n'
                    'In the Gender category, Male has the highest sample mean, which is 67.1833.\n'
                    'For the hometowns, Luzon got the highest sample mean, which is 68.0833.', fontsize=17)
plt.show()
```
---
## Final Remarks

## History 
**September 16, 2026** - This repository was created and initial .ipynb file was uploaded\

**September 17, 2026** - Added the excel file and the README as well as the .ipynb file were revised

**September 18, 2026** - The README and .ipynb file were further revised and beautified
