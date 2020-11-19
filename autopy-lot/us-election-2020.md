---
jupyter:
  jupytext:
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.2'
      jupytext_version: 1.7.1
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

## Kaggle dataset related code

```python _uuid="8f2839f25d086af736a60e9eeb907d3b93b6e0e5" _cell_guid="b1076dfc-b9ad-4769-8c92-a6c4dae69d19"
# This Python 3 environment comes with many helpful analytics libraries installed
# It is defined by the kaggle/python Docker image: https://github.com/kaggle/docker-python
# For example, here's several helpful packages to load

import numpy as np # linear algebra
import pandas as pd # data processing, CSV file I/O (e.g. pd.read_csv)

# Input data files are available in the read-only "../input/" directory
# For example, running this (by clicking run or pressing Shift+Enter) will list all files under the input directory

import os
for dirname, _, filenames in os.walk('/kaggle/input'):
    for filename in filenames:
        print(os.path.join(dirname, filename))

# You can write up to 20GB to the current directory (/kaggle/working/) that gets preserved as output when you create a version using "Save & Run All" 
# You can also write temporary files to /kaggle/temp/, but they won't be saved outside of the current session
```

## Read the dataset

```python _uuid="d629ff2d2480ee46fbb7e2d37f6b5fab8052498a" _cell_guid="79c7e3d0-c299-4dcb-8224-4455121ee9b0"
pd.read_csv("/kaggle/input/us-election-2020-tweets/hashtag_joebiden.csv")
```

## Extract the required field

```python
followers_count = np.asarray(pd.read_csv("/kaggle/input/us-election-2020-tweets/hashtag_joebiden.csv")['user_followers_count'])
print(len(followers_count))
```

## Extract the first digits and store

```python
benford_map = [0,0,0,0,0,0,0,0,0,0]
excpt = 0
for digits in followers_count:
    try:
        
        digits = float(digits)
        digits = int(digits)
        str_digits = str(digits)
        msd = int(str_digits[0])
        benford_map[msd] = benford_map[msd] + 1
        
    except:
        excpt = excpt + 1
    
print('skipped:' ,excpt)
print(benford_map)

```

## Plot the graph

```python
import matplotlib.pyplot as plt  
fig = plt.figure(figsize = (10, 5)) 
x = [0,1,2,3,4,5,6,7,8,9]
# creating the bar plot 
plt.bar(x[1:], benford_map[1:], color ='blue',  
        width = 0.4) 
plt.xlabel("Most Significant Digits") 
plt.ylabel("Count") 
plt.title("Benford Graph") 
plt.show() 
```

## calculate percentage

```python
ben_map = benford_map[1:]
total = 0
for entry in ben_map:
    total = total + entry


i = 1
output = {}  
for entry in ben_map:
    output[str(i)] = str((entry/total)*100)
    i = i+1
    
print(output)

```

# Satisfied
