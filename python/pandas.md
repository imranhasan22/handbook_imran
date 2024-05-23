Pandas is used for working with data sets, it is used to analyze data. It has functions for analyzing, cleaning, exploring, and manipulating data.

__What Can Pandas Do?__
Pandas gives you answers about the data. Like:
- Is there a correlation between two or more columns?
- What is average value?
- Max value?
- Min value?

Pandas are also able to delete rows that are not relevant, or contains wrong values, like empty or NULL values. This is called cleaning the data.

- `pandas.__version__` - return the version of pandas 
- `pandas.DataFrame()` - 
- `pd.options.display.max_rows` - return or set the system maximum number of row

# Series
A Pandas Series is like a column in a table. 
```
name=["Jack","John","Mark","Zuck"]
student_table = pd.Series(name)
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
if label is set `index` argument is used to get specific item, if not, it set label.

The length of data and the length of `index` argument should be same. The data used in __series__ or __dataframe__ can be anytype.

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
print(df.loc[[0,2]]) # return specified index - 0th, 2nd
print(df.loc[0:2]) # return list of indexes from 0 to 2
```

you can override the label in dataframe also
```
df = pd.DataFrame(data, index = ["a", "b", "c","d"])
```

# File Reading
## CSV
`pandas.read_csv()` - read csv file and store in data frame

If you have a large DataFrame with many rows, Pandas will only return the first 5 rows, and the last 5 rows
```
df = pd.read_csv('data.csv')
print(df)
```
`dataframe.toString()` - return entire dataframe as string representation, it will output the entire DataFrame to the console.
```
df = pd.read_csv('data.csv')
print(df.to_string())
```

## JSON
`pandas.read_json()` - read json file and store in data frame

JSON objects have the same format as Python dictionaries. If your JSON code is not in a file, but in a Python Dictionary, you can load it into a DataFrame directly:

# Data Cleaning
Data cleaning means fixing bad data in your data set. Bad data could be:
- Empty cells
- Data in wrong format
- Wrong data
- Duplicates

## Remove Rows
`df.dropna()` - return a new Data Frame with no empty cells
```
df = pd.read_csv('data.csv')
new_df = df.dropna()
print(new_df.to_string())
```
If you want to change the original DataFrame, use the `inplace = True` argument:
```
df = pd.read_csv('data.csv')
df.dropna(inplace = True)
print(df.to_string())
```
It will NOT return a new DataFrame, but it will remove all rows containing NULL values from the original DataFrame.

## Replace Empty Values
`fillna()` method allows to replace empty cells with a value.
```
df.fillna(130, inplace = True)
```
It will replace all empty cells in the whole data frame. If you want to replace empty value on specified column, then specify them.
```
df["Calories"].fillna(130, inplace = True)
```
__For multiple column:__
```
fill_values = {
    "Calories": 130,
    "Protein": 0.0,
    "Fat": 0.0
}
df.fillna(value=fill_values, inplace=True)
```

## Replacing with Mean, Median, Mode
```
x = df["Calories"].mean() # you can also use median(), mode()[0]
df["Calories"].fillna(x, inplace = True)
```