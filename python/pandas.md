Pandas is used for working with data sets, it is used to analyze data. It has functions for analyzing, cleaning, exploring, and manipulating data.

__What Can Pandas Do?__
Pandas gives you answers about the data. Like:
- Is there a correlation between two or more columns?
- What is average value?
- Max value?
- Min value?

Pandas are also able to delete rows that are not relevant, or contains wrong values, like empty or NULL values. This is called cleaning the data.

- `pandas.__version__` - return the version of pandas 
- `pandas.read_csv()` - read csv file and store in data frame
- `pandas.DataFrame()` - 
- `dataframe.toString()` - return entire dataframe as string representation, it will output the entire DataFrame to the console. If you have a large DataFrame with many rows, without toString() pandas will only return the first 5 rows, and the last 5 rows.

# Series
A Pandas Series is like a column in a table. 
```
name=["Jack","John","Mark","Zuck"]
student_table = pd.Series(a)
```
The above script generate name column in student table.

you can access each column value by their index.

you can also overried the index label with your custom label by `index` argument.
```
student_table = pd.Series(name,index = ["a", "b", "c","d"])
```
now you can access it both by number index as well as you custom index.
```
print(student_table["a"])
print(student_table.iloc[0]) # student_table[0] will be removed
```

if you use dictornary instead of list, the keys of the dictionary become the labels
```
name={"a":"Jack","b":"John","c":"Mark","d":"Zuck"}
```
if label is set `index` argument is used to get specific item, if not it set label

# DataFrame
A Pandas DataFrame is a 2 dimensional data structure, like a 2 dimensional array, or a table with rows and columns.
```
data = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}
```

`loc` attribute return one or more specified row
```
print(df.loc[0]) # return first row
```