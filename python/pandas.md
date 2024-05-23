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

if you want to remove row, based on any specified column, specify it with subset attribute. Like if Date column have null value you want remove the row, then use it
```
df.dropna(subset=['Date'], inplace = True)
```
if any other column have null value, those will not be removed.

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

# Wrong Format
Cells with data of wrong format can make it difficult, or even impossible, to analyze data.

- `to_datetime()` is used to format the date
```
df['Date'] = pd.to_datetime(df['Date'])
```

# Wrong Data
Wrong data does not have to be empty cells or wrong format, it can just be wrong, like if someone registered "199" instead of 1.99.

## Replacing Value
For small data sets you might be able to replace the wrong data one by one, but not for big data set
```
df.loc[7, 'Duration'] = 45
```
To replace wrong data for larger data sets you can create some rules, e.g. set some boundaries for legal values, and replace any values that are outside of the boundaries.
```
for x in df.index:
  if df.loc[x, "Duration"] > 120:
    df.loc[x, "Duration"] = 120
```

## Remove Row
```
for x in df.index:
  if df.loc[x, "Duration"] > 120:
    df.drop(x, inplace = True)
```

# Removing Duplicates
- `duplicated()` method returns a Boolean values for each row
```
print(df.duplicated())
```

- `drop_duplicates()` is used to remove duplicate value
```
df.drop_duplicates(inplace = True)
```

# Inspecting Data
- `info()` - provide summary
- `head()` - return the first nth rows
- `tail()` - return the last nth rows
- `shape` - return a tuple represent the dimension
- `describe()` - generates descriptive statistics like max, min, mean, std etc for numerical columns by default.
- `columns` - returns an Index object containing the column labels 
- `index` - return the index(row label) range
- `dtypes` - return data type of each column
- `isnull()` - return boolean value indicating whether each value is NaN
- `notnull()` - return boolean value indicating whether each value is not NaN
- `sum()`,`mean()`,`median()`,`std()`,`min()`,`max()` - apply on each column and return value according to their name
- `value.counts()` - return a series containing counts of unique values for a given column. Ex: `df['column_name'].value_counts()`
- `sample()` - return random samples, you can specify the number of row with n attribute
- `corr()` - computes pairwise correlation of columns, excluding NA/null values.
- `nunique()` - returns the number of unique values for each column.

# Column Selection
- `df.columnName` or `df["column name"]` return specified column
- `df[["first","second"]]` select multiple column
- `df['column_name'].apply(func)` - applies a function to each value in the column.

you can apply all the inspection method to column

## Column Insertion
1. __Assigning a New Column Directly:__ You can directly assign a new column by specifying the column name and the values. If the column name already exists, this will overwrite the existing column.
```
df = pd.DataFrame({
    "A": [1, 2, 3],
    "B": [4, 5, 6]
})
df["C"] = [7, 8, 9]
```

2. __insert() method:__ allow to insert a column at a specific location
```
df.insert(1, "D", [10, 11, 12])
```

3. __assign() method:__ return new dataframe with additional column. it does not modify the original dataframe uunless you reassign it.
```
df = df.assign(E=[13, 14, 15])
```

4. __Index Based Assignment:__ you can use `loc()` or `iloc()` method.
```
df.loc[:, "F"] = [16, 17, 18]
```