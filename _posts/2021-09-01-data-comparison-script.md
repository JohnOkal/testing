This project helped me answer the frequent business question, "What was X value yesterday, last week, last quarter, last year?"

Reasons for why data changes are numerous yet managers and executives always wonder what is the cause? Arriving at the root cause for why values change within financial data is important since financial data is time series based. For example, if a past for a $10 transaction now shows $11, that could pose big problems. The case for most things in financial reporting is that many smaller components add to the one final reporting metric. Risks to FSLI, auditing support, among many other concerns are all reasons that tracking changes is an important tool. This technique is step one in the problem-solving process. How are you supposed to determine a root cause if you don't know where to start on which underlying number changed?

### Code
It is important to note that in order for this code to work, the data structure must remain unchanged from one time period to the next. Column name changes will cause the script to be uncomparable.

First, we import relevant libraries and CSV's. CSV files can be stored locally or in a database.
```python
one = pd.read_csv('filepath/name.csv')
one.to_csv('filepath/name - yesterday.csv', index=False)

yesterday = pd.read_csv('filepath/name - yesterday.csv')

# Identify any columns that are datetime
columns = [
column 1,
column 2,
column 3
]


```
