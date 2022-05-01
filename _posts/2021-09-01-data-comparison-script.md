This project helped me answer the frequent business question, "What was X value yesterday, last week, last quarter, last year?"

Reasons for why data changes are numerous yet managers and executives always wonder what is the cause? Arriving at the root cause for why values change within financial data is important since financial data is time series based. For example, if a past $10 transaction now shows $11, that could pose big problems. The case for most things in financial reporting is that many smaller components add to one final reporting metric. Risks to FSLI, auditing support, among many other concerns are all reasons that tracking changes is an important tool. This technique is step one in the problem-solving process. How are you supposed to determine a root cause if you don't know where to start or which underlying number changed?

### **Code**
It is important to note that in order for this code to work, the data structure must remain unchanged from one time period to the next. Column name changes will cause the script to be uncomparable.

First, we import relevant libraries and CSV's. CSV files can be stored locally or in a database.
```python
import pandas as pd
import numpy as np
import datetime as dt

# Read current day's data
one = pd.read_csv('filepath/name.csv')
# Read yesterday's data
yesterday = pd.read_csv('filepath/name - yesterday.csv')

# Identify any columns that are datetime since we want them to display in a certain way later
columns = [
column1,
column2,
column3
]

# Creating a column called 'time' so that we can determine which dataset each row came from
# This also creates a level of our multi-index columns later
yesterday['time'] = 'Yesterday'
yesterday = yesterday.set_index(['column1','column2'])
yesterday[columns] = yesterday[columns].apply(pd.to_datetime)
yesterday[columns] = yesterday[columns].apply(lambda x: x.dt.strftime('%m/%d/%y'))

today['time'] = 'Today'
today = today.set_index(['column1','column2'])
today[columns] = today[columns].apply(pd.to_datetime)
today[columns] = today[columns].apply(lambda x: x.dt.strftime('%m/%d/%y'))

variable = pd.concat([yesterday, today])
```


