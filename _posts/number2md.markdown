<!-- ---
layout: post
title:  "TESTING"
subtitle: "TESTTT"
date:   2020-11-30 16:30:58 +0100
categories: jekyll update
---
## Exploring the Data

Let's start with importing the necessary libaries, reading in the data, and checking out the dataset.

Note that the last column from this dataset, `'income'`, will be our target label (whether an individual makes more than, or at most, $50,000 annually). All other columns are features about each individual in the census database.


```python
# Import libraries necessary for this project
import numpy as np
import pandas as pd
from time import time
from IPython.display import display # Allows the use of display() for DataFrames

# Import visualisation libraries
import visuals as vs
import seaborn as sns
import matplotlib.pyplot as plt

# Pretty display for notebooks
%matplotlib inline

from __future__ import division

# Load the Census dataset
data = pd.read_csv("census.csv")

# Success - Display the first record
display(data.head(n=1))
```

<iframe title="P2Dashboard - Customer Details" width="1140" height="541.25" src="https://app.powerbi.com/reportEmbed?reportId=e51081eb-f135-48b6-a848-00626e7fca0b&autoAuth=true&ctid=62ea7034-b6de-49ee-be15-cae8e9abc7c6&config=eyJjbHVzdGVyVXJsIjoiaHR0cHM6Ly93YWJpLXVrLXNvdXRoLWItcHJpbWFyeS1yZWRpcmVjdC5hbmFseXNpcy53aW5kb3dzLm5ldC8ifQ%3D%3D" frameborder="0" allowFullScreen="true"></iframe>


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/ -->
