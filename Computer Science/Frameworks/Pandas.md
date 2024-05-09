Pandas is a [[Python]] library used within [[Data Science]] fields to manipulate data to create a format where data can be analysed. Pandas uses a [[Abstract Datatypes|data structure]] called a **Data frame**, which functions as a representation of a spreadsheet. ## Pandas Syntax
Pandas can be imported as `import pandas` with `pd` being the shorthand convention. Pandas can read most files with the simple operation:
```python
file = pd.read_csv('Csv File')
file = pd.read_json('Json File')
```
Where the result is a data frame which contains csv's or json's data, with the first row being a header. A more general way to create a data frame is with the statement:
```python
df = pd.Dataframe(data)
```
**Export** methods include an export to csv through the `to_csv()` command.

# Data Selection
A column can be accessed through traditional dictionary indexing methods. It can also display multiple if delineated with a comma. **Slices** also exist within pandas, and allow rows and columns to be removed given an index or a header name. The **location** command called with `df.loc[column comparison value]` can be used to find values given a condition proves true. Thus, location can be used to extract data from the data frame as to create a new data frame with less entries.

# Data Previews
The **head** command, found with `df.head`, can be used to display the top 5 rows, while **tail** called as `df.tail` displays the bottom 5. The `df.shape` command is used to find the dimensions of the dataset. The `df.describe` is used to create a premade sheet that gives information such as median, average, and other similar operations.

# Operations on Dataset
The series command creates a new data frame that contains a series of categorical data as the header. This can be done on a data set as to categorise the data entries by a value. For example:
```python
ser = pd.Series(data, index)
```
Data can be aggregated by columns as to produce a result given the provided functions. This includes a `.sum`, `.median`, `.mean` or any similar operations.

The **group by** operation is used to combine a column based on another column. This is usually used to aggregate a set of data producing a column with categories based on the column, and a result aggregated on the actual column. This can be written as
```python
aggregate_set = pd.groupby(column)[actual column].operation
```

# Merge
The merge operation merges two data frames about a certain value set.
```python
merged_set = pd.merge(dataset1, dataset2, on='column')
```
This allows two sets to be merged, removing all values that don't contain the column being merged upon.

# Cleaning Data
**Empty entries** result in a `na` being put into the data frame. To remove these you can simply:
```python
df.dropna()
```
This removes all blank entries from the rows. A fill operation can also be done as to replace all blank entries. This can be written as:
```python
df.fillna(value)
```
Both these commands have a `subset` argument which allows the removal of blank cells only on a given column.

Columns with **duplicates** can be removed simply with the command:
```python
df.drop_duplicates
```
This removes all duplicates, and can be further refined to only a subset of duplicates. Furthermore the `duplicated` command can be used to return a Boolean based on the values that are duplicates.

$$x\in[1,length)$$
