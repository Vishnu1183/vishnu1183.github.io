---
title: "Python Tutorials part III Pandas Tutorial"
date: 2019-09-20
tags: [pandas, python, jupyter]
excerpt: "This tutorial contains pandas functions used for cleaning data."
mathjax: "true"
---
<!---<font size="5"><center><h2>Intro To Python For Data Analysis - Part 1</h2></center></font>-->
<h6>01 Oct,2019</h6>
<h6>By: Vishnu Prakash Singh</h6>

```python
from IPython.display import Image;from datetime import date
from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity = "all"
```
### Pandas Series
* Pandas Series is a one-dimensional labeled array capable of holding data of any type 
* The axis labels are collectively called index. 
* Labels need not be unique but must be a hashable type.

```python
import pandas as pd
data = pd.Series(np.random.randint(10, 20,6), index=pd.date_range('20130101', periods=6))
print('Type of the series is ' + str(type(data)))
```
Type of the series is <class 'pandas.core.series.Series'>

```python
print('Index of the series is ' + str(data.index))
```

Index of the series is DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04','2013-01-05', '2013-01-06'],dtype='datetime64[ns]', freq='D')

```python
print('Values of the series is ' + str(data.values))
```
Values of the series is [12 14 18 12 13 10]

```python
print('Data Type of the series is ' + str(data.dtype))
```
Data Type of the series is int32

### Pandas DataFrame
```python
np.random.seed(47)
df = pd.DataFrame({'ID': map(str,np.arange(103,120,3)),   # map function maps str function to each item of list
                     'DATE': pd.date_range('20190101', periods=6),
                     'VALUE': np.round(np.random.uniform(1000, 5000,6),2),
                     'VOLUME': np.random.randint(1, 20,6),
                     'SET': np.random.choice(["test", "train"],6)})
df.shape
df
```
(6, 5)

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>2019-01-01</td>
      <td>1453.95</td>
      <td>14</td>
      <td>train</td>
    </tr>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>2019-01-02</td>
      <td>4897.93</td>
      <td>18</td>
      <td>train</td>
    </tr>
    <tr>
      <th>2</th>
      <td>109</td>
      <td>2019-01-03</td>
      <td>3914.94</td>
      <td>19</td>
      <td>test</td>
    </tr>
    <tr>
      <th>3</th>
      <td>112</td>
      <td>2019-01-04</td>
      <td>2405.87</td>
      <td>19</td>
      <td>test</td>
    </tr>
    <tr>
      <th>4</th>
      <td>115</td>
      <td>2019-01-05</td>
      <td>3830.42</td>
      <td>12</td>
      <td>train</td>
    </tr>
    <tr>
      <th>5</th>
      <td>118</td>
      <td>2019-01-06</td>
      <td>4198.42</td>
      <td>2</td>
      <td>test</td>
    </tr>
  </tbody>
</table>
</div>



##### Checking data type of all columns


```python
df.dtypes
```
    ID                object
    DATE      datetime64[ns]
    VALUE            float64
    VOLUME             int32
    SET               object
    dtype: object

##### info() returns various details of the dataframe
```python
df.info()
```
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 6 entries, 0 to 5
    Data columns (total 5 columns):
    ID        6 non-null object
    DATE      6 non-null datetime64[ns]
    VALUE     6 non-null float64
    VOLUME    6 non-null int32
    SET       6 non-null object
    dtypes: datetime64[ns](1), float64(1), int32(1), object(2)
    memory usage: 344.0+ bytes
    
###### describe() shows a quick statistic summary of your data:

```python
df.describe()   # only takes numeric columns under consideration
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>VALUE</th>
      <th>VOLUME</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>6.000000</td>
      <td>6.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>3450.255000</td>
      <td>14.000000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1272.159191</td>
      <td>6.542171</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1453.950000</td>
      <td>2.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2762.007500</td>
      <td>12.500000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>3872.680000</td>
      <td>16.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>4127.550000</td>
      <td>18.750000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>4897.930000</td>
      <td>19.000000</td>
    </tr>
  </tbody>
</table>
</div>

##### Viewing pandas data
```python
df.head(2)
df.tail(2)
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>2019-01-01</td>
      <td>1453.95</td>
      <td>14</td>
      <td>train</td>
    </tr>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>2019-01-02</td>
      <td>4897.93</td>
      <td>18</td>
      <td>train</td>
    </tr>
  </tbody>
</table>
</div>

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>115</td>
      <td>2019-01-05</td>
      <td>3830.42</td>
      <td>12</td>
      <td>train</td>
    </tr>
    <tr>
      <th>5</th>
      <td>118</td>
      <td>2019-01-06</td>
      <td>4198.42</td>
      <td>2</td>
      <td>test</td>
    </tr>
  </tbody>
</table>
</div>

###### Display the index, columns:

```python
df.index.to_list() # converting index to list for better printing
df.columns
```
[0, 1, 2, 3, 4, 5]

Index(['ID', 'DATE', 'VALUE', 'VOLUME', 'SET'], dtype='object')

###### pandas to numpy
###### Note DataFrame.to_numpy() does not include the index or column labels in the output.


```python
df.to_numpy()
```
array([['103', Timestamp('2019-01-01 00:00:00'), 1453.95, 14, 'train'],
           ['106', Timestamp('2019-01-02 00:00:00'), 4897.93, 18, 'train'],
           ['109', Timestamp('2019-01-03 00:00:00'), 3914.94, 19, 'test'],
           ['112', Timestamp('2019-01-04 00:00:00'), 2405.87, 19, 'test'],
           ['115', Timestamp('2019-01-05 00:00:00'), 3830.42, 12, 'train'],
           ['118', Timestamp('2019-01-06 00:00:00'), 4198.42, 2, 'test']],
          dtype=object)
          
##### Converting datatype of variable
```python
df.dtypes

df['VOLUME'] = df.VOLUME.astype(str)  # converting from integer to string
df.VOLUME.dtype

df['ID'] = df.ID.astype('category')   # converting from string to factor
df.ID.dtype

df['VOLUME'] = df.VOLUME.astype(int)   # converting from string to integer
df.VOLUME.dtype
```
    ID                object
    DATE      datetime64[ns]
    VALUE            float64
    VOLUME             int32
    SET               object
    dtype: object

dtype('O')

CategoricalDtype(categories=['103', '106', '109', '112', '115', '118'], ordered=False)

dtype('int32')

###### Transposing your data:
```python
df.T.shape  # rows and columns got interchanged
df.T
```
(5, 6)

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>ID</th>
      <td>103</td>
      <td>106</td>
      <td>109</td>
      <td>112</td>
      <td>115</td>
      <td>118</td>
    </tr>
    <tr>
      <th>DATE</th>
      <td>2019-01-01 00:00:00</td>
      <td>2019-01-02 00:00:00</td>
      <td>2019-01-03 00:00:00</td>
      <td>2019-01-04 00:00:00</td>
      <td>2019-01-05 00:00:00</td>
      <td>2019-01-06 00:00:00</td>
    </tr>
    <tr>
      <th>VALUE</th>
      <td>1453.95</td>
      <td>4897.93</td>
      <td>3914.94</td>
      <td>2405.87</td>
      <td>3830.42</td>
      <td>4198.42</td>
    </tr>
    <tr>
      <th>VOLUME</th>
      <td>14</td>
      <td>18</td>
      <td>19</td>
      <td>19</td>
      <td>12</td>
      <td>2</td>
    </tr>
    <tr>
      <th>SET</th>
      <td>train</td>
      <td>train</td>
      <td>test</td>
      <td>test</td>
      <td>train</td>
      <td>test</td>
    </tr>
  </tbody>
</table>
</div>

###### Sorting by an axis:
* axis 0 means row wise operation
* axis 1 means column wise operation

```python
# sorting by the row index
df.sort_index(axis=0, ascending=False)
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>118</td>
      <td>2019-01-06</td>
      <td>4198.42</td>
      <td>2</td>
      <td>test</td>
    </tr>
    <tr>
      <th>4</th>
      <td>115</td>
      <td>2019-01-05</td>
      <td>3830.42</td>
      <td>12</td>
      <td>train</td>
    </tr>
    <tr>
      <th>3</th>
      <td>112</td>
      <td>2019-01-04</td>
      <td>2405.87</td>
      <td>19</td>
      <td>test</td>
    </tr>
    <tr>
      <th>2</th>
      <td>109</td>
      <td>2019-01-03</td>
      <td>3914.94</td>
      <td>19</td>
      <td>test</td>
    </tr>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>2019-01-02</td>
      <td>4897.93</td>
      <td>18</td>
      <td>train</td>
    </tr>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>2019-01-01</td>
      <td>1453.95</td>
      <td>14</td>
      <td>train</td>
    </tr>
  </tbody>
</table>
</div>

```python
# sorting by the column index
df.sort_index(axis=1, ascending=False)
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>VOLUME</th>
      <th>VALUE</th>
      <th>SET</th>
      <th>ID</th>
      <th>DATE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>14</td>
      <td>1453.95</td>
      <td>train</td>
      <td>103</td>
      <td>2019-01-01</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>4897.93</td>
      <td>train</td>
      <td>106</td>
      <td>2019-01-02</td>
    </tr>
    <tr>
      <th>2</th>
      <td>19</td>
      <td>3914.94</td>
      <td>test</td>
      <td>109</td>
      <td>2019-01-03</td>
    </tr>
    <tr>
      <th>3</th>
      <td>19</td>
      <td>2405.87</td>
      <td>test</td>
      <td>112</td>
      <td>2019-01-04</td>
    </tr>
    <tr>
      <th>4</th>
      <td>12</td>
      <td>3830.42</td>
      <td>train</td>
      <td>115</td>
      <td>2019-01-05</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2</td>
      <td>4198.42</td>
      <td>test</td>
      <td>118</td>
      <td>2019-01-06</td>
    </tr>
  </tbody>
</table>
</div>

```python
# sorting by a column
df.sort_values(by='VOLUME', ascending = False)
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>109</td>
      <td>2019-01-03</td>
      <td>3914.94</td>
      <td>19</td>
      <td>test</td>
    </tr>
    <tr>
      <th>3</th>
      <td>112</td>
      <td>2019-01-04</td>
      <td>2405.87</td>
      <td>19</td>
      <td>test</td>
    </tr>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>2019-01-02</td>
      <td>4897.93</td>
      <td>18</td>
      <td>train</td>
    </tr>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>2019-01-01</td>
      <td>1453.95</td>
      <td>14</td>
      <td>train</td>
    </tr>
    <tr>
      <th>4</th>
      <td>115</td>
      <td>2019-01-05</td>
      <td>3830.42</td>
      <td>12</td>
      <td>train</td>
    </tr>
    <tr>
      <th>5</th>
      <td>118</td>
      <td>2019-01-06</td>
      <td>4198.42</td>
      <td>2</td>
      <td>test</td>
    </tr>
  </tbody>
</table>
</div>

### Selection of subset of data
```python
#Selecting a single column, which yields a Series, equivalent to df.ID
df['ID']  # returns pandas.core.series.Series
```

    0    103
    1    106
    2    109
    3    112
    4    115
    5    118
    Name: ID, dtype: category
    Categories (6, object): [103, 106, 109, 112, 115, 118]

```python
#Selecting via [], which slices the rows.
df[0:3]
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>2019-01-01</td>
      <td>1453.95</td>
      <td>14</td>
      <td>train</td>
    </tr>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>2019-01-02</td>
      <td>4897.93</td>
      <td>18</td>
      <td>train</td>
    </tr>
    <tr>
      <th>2</th>
      <td>109</td>
      <td>2019-01-03</td>
      <td>3914.94</td>
      <td>19</td>
      <td>test</td>
    </tr>
  </tbody>
</table>
</div>

###### Selection by label using loc

```python
df.loc[:,['VALUE']] # returns pandas.core.frame.DataFrame
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>VALUE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1453.95</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4897.93</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3914.94</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2405.87</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3830.42</td>
    </tr>
    <tr>
      <th>5</th>
      <td>4198.42</td>
    </tr>
  </tbody>
</table>
</div>

```python
df.loc[0:1]
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>2019-01-01</td>
      <td>1453.95</td>
      <td>14</td>
      <td>train</td>
    </tr>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>2019-01-02</td>
      <td>4897.93</td>
      <td>18</td>
      <td>train</td>
    </tr>
  </tbody>
</table>
</div>

```python
df.loc[1:2:, ['ID', 'VALUE']]
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>VALUE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>4897.93</td>
    </tr>
    <tr>
      <th>2</th>
      <td>109</td>
      <td>3914.94</td>
    </tr>
  </tbody>
</table>
</div>



### Selection by position using iloc
```python
df.iloc[3]
```
    ID                        112
    DATE      2019-01-04 00:00:00
    VALUE                 2405.87
    VOLUME                     19
    SET                      test
    Name: 3, dtype: object

```python
df.iloc[[1, 2, 4], [0, 2]]
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>VALUE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>4897.93</td>
    </tr>
    <tr>
      <th>2</th>
      <td>109</td>
      <td>3914.94</td>
    </tr>
    <tr>
      <th>4</th>
      <td>115</td>
      <td>3830.42</td>
    </tr>
  </tbody>
</table>
</div>

### Boolean indexing
```python
df[df.VALUE > 3500]
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>2019-01-02</td>
      <td>4897.93</td>
      <td>18</td>
      <td>train</td>
    </tr>
    <tr>
      <th>2</th>
      <td>109</td>
      <td>2019-01-03</td>
      <td>3914.94</td>
      <td>19</td>
      <td>test</td>
    </tr>
    <tr>
      <th>4</th>
      <td>115</td>
      <td>2019-01-05</td>
      <td>3830.42</td>
      <td>12</td>
      <td>train</td>
    </tr>
    <tr>
      <th>5</th>
      <td>118</td>
      <td>2019-01-06</td>
      <td>4198.42</td>
      <td>2</td>
      <td>test</td>
    </tr>
  </tbody>
</table>
</div>

```python
df[df.SET.isin(['train'])]  # df[df.SET=='train']
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>2019-01-01</td>
      <td>1453.95</td>
      <td>14</td>
      <td>train</td>
    </tr>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>2019-01-02</td>
      <td>4897.93</td>
      <td>18</td>
      <td>train</td>
    </tr>
    <tr>
      <th>4</th>
      <td>115</td>
      <td>2019-01-05</td>
      <td>3830.42</td>
      <td>12</td>
      <td>train</td>
    </tr>
  </tbody>
</table>
</div>

```python
df[df.SET=='train']
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>2019-01-01</td>
      <td>1453.95</td>
      <td>14</td>
      <td>train</td>
    </tr>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>2019-01-02</td>
      <td>4897.93</td>
      <td>18</td>
      <td>train</td>
    </tr>
    <tr>
      <th>4</th>
      <td>115</td>
      <td>2019-01-05</td>
      <td>3830.42</td>
      <td>12</td>
      <td>train</td>
    </tr>
  </tbody>
</table>
</div>

### Missing data

```python
df1 = df.copy() # creates a copy of dataframe
df1.loc[2,'DATE'] = np.NaN   # replacing value with NA
df1.loc[2:3,'VALUE'] = np.NaN # replacing value with NA
df1.loc[5,'SET'] = np.NaN # replacing value with NA
```


```python
# checking counts of missing values
df1.VALUE.isna().sum()
df1.isna().sum()
```
2

    ID        0
    DATE      1
    VALUE     2
    VOLUME    0
    SET       1
    dtype: int64

```python
#To drop any rows that have missing data.
df1.dropna(how='any')
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>2019-01-01</td>
      <td>1453.95</td>
      <td>14</td>
      <td>train</td>
    </tr>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>2019-01-02</td>
      <td>4897.93</td>
      <td>18</td>
      <td>train</td>
    </tr>
    <tr>
      <th>4</th>
      <td>115</td>
      <td>2019-01-05</td>
      <td>3830.42</td>
      <td>12</td>
      <td>train</td>
    </tr>
  </tbody>
</table>
</div>

```python
#To drop a row specific to a column that have missing data.
df1.dropna(subset = ['SET'],inplace = True) 
# when inplace = True, the output is stored in the same dataframe on which operation is done
df1
```
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>DATE</th>
      <th>VALUE</th>
      <th>VOLUME</th>
      <th>SET</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>2019-01-01</td>
      <td>1453.95</td>
      <td>14</td>
      <td>train</td>
    </tr>
    <tr>
      <th>1</th>
      <td>106</td>
      <td>2019-01-02</td>
      <td>4897.93</td>
      <td>18</td>
      <td>train</td>
    </tr>
    <tr>
      <th>2</th>
      <td>109</td>
      <td>NaT</td>
      <td>NaN</td>
      <td>19</td>
      <td>test</td>
    </tr>
    <tr>
      <th>3</th>
      <td>112</td>
      <td>2019-01-04</td>
      <td>NaN</td>
      <td>19</td>
      <td>test</td>
    </tr>
    <tr>
      <th>4</th>
      <td>115</td>
      <td>2019-01-05</td>
      <td>3830.42</td>
      <td>12</td>
      <td>train</td>
    </tr>
  </tbody>
</table>
</div>

### Operations
```python
df.mean() # df.mean(axis = 0)
```
    ID        1.718435e+16
    VALUE     3.450255e+03
    VOLUME    1.400000e+01
    dtype: float64

```python
 df.mean(1) ## df.mean(axis = 1) ; gives mean for numeric data only
```
    0     733.975
    1    2457.965
    2    1966.970
    3    1212.435
    4    1921.210
    5    2100.210
    dtype: float64



### Apply

Any built in or self written function can be applied to column of a dataframe


```python
max_val_vol = df[['VALUE', 'VOLUME']].apply(max)
max_val_vol
min_val_vol = df[['VALUE', 'VOLUME']].apply(min)
min_val_vol
diff_max_min = max_val_vol-min_val_vol
diff_max_min
```




    VALUE     4897.93
    VOLUME      19.00
    dtype: float64






    VALUE     1453.95
    VOLUME       2.00
    dtype: float64






    VALUE     3443.98
    VOLUME      17.00
    dtype: float64



###### Above operation can be done using lambda function in pyhton
Syntax - lambda arguments : expression


```python
df[['VALUE', 'VOLUME']].apply(lambda x: x.max() - x.min())
```




    VALUE     3443.98
    VOLUME      17.00
    dtype: float64



### Merge / Join


```python
np.random.seed(42)
sales = pd.DataFrame({'order_id' : np.random.randint(100,105,7), 
                      'item' : ['apple', 'guava', 'grape', 'grape','apple', 'guava', 'papaya'],
                     'date' : ['2013-01-03', '2013-01-01','2013-01-02','2013-01-01','2013-01-03','2013-01-03','2013-01-02'] })
sales
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order_id</th>
      <th>item</th>
      <th>date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>apple</td>
      <td>2013-01-03</td>
    </tr>
    <tr>
      <th>1</th>
      <td>104</td>
      <td>guava</td>
      <td>2013-01-01</td>
    </tr>
    <tr>
      <th>2</th>
      <td>102</td>
      <td>grape</td>
      <td>2013-01-02</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>grape</td>
      <td>2013-01-01</td>
    </tr>
    <tr>
      <th>4</th>
      <td>104</td>
      <td>apple</td>
      <td>2013-01-03</td>
    </tr>
    <tr>
      <th>5</th>
      <td>101</td>
      <td>guava</td>
      <td>2013-01-03</td>
    </tr>
    <tr>
      <th>6</th>
      <td>102</td>
      <td>papaya</td>
      <td>2013-01-02</td>
    </tr>
  </tbody>
</table>
</div>




```python
cost = pd.DataFrame({'item': ['apple', 'guava', 'grape'],
                    'cost/kg' : [200,90,170]})
cost
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>item</th>
      <th>cost/kg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>apple</td>
      <td>200</td>
    </tr>
    <tr>
      <th>1</th>
      <td>guava</td>
      <td>90</td>
    </tr>
    <tr>
      <th>2</th>
      <td>grape</td>
      <td>170</td>
    </tr>
  </tbody>
</table>
</div>



##### Left Join


```python
sales_df = sales.merge(cost,on = 'item', how = 'left')
sales_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order_id</th>
      <th>item</th>
      <th>date</th>
      <th>cost/kg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>apple</td>
      <td>2013-01-03</td>
      <td>200.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>104</td>
      <td>guava</td>
      <td>2013-01-01</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>102</td>
      <td>grape</td>
      <td>2013-01-02</td>
      <td>170.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>grape</td>
      <td>2013-01-01</td>
      <td>170.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>104</td>
      <td>apple</td>
      <td>2013-01-03</td>
      <td>200.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>101</td>
      <td>guava</td>
      <td>2013-01-03</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>102</td>
      <td>papaya</td>
      <td>2013-01-02</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



<h6>Right Join</h6>
* sales.merge(cost,on = 'item', how = 'right')

<h6>Inner Join</h6>
* sales.merge(cost,on = 'item', how = 'inner')

##### Row Binding two dataframes


```python
pd.concat([sales,cost], axis = 0)
```

    C:\Users\392256\AppData\Local\Continuum\anaconda3\lib\site-packages\ipykernel_launcher.py:1: FutureWarning: Sorting because non-concatenation axis is not aligned. A future version
    of pandas will change to not sort by default.
    
    To accept the future behavior, pass 'sort=False'.
    
    To retain the current behavior and silence the warning, pass 'sort=True'.
    
      """Entry point for launching an IPython kernel.
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cost/kg</th>
      <th>date</th>
      <th>item</th>
      <th>order_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>2013-01-03</td>
      <td>apple</td>
      <td>103.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>2013-01-01</td>
      <td>guava</td>
      <td>104.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>2013-01-02</td>
      <td>grape</td>
      <td>102.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>2013-01-01</td>
      <td>grape</td>
      <td>104.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>2013-01-03</td>
      <td>apple</td>
      <td>104.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>NaN</td>
      <td>2013-01-03</td>
      <td>guava</td>
      <td>101.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>NaN</td>
      <td>2013-01-02</td>
      <td>papaya</td>
      <td>102.0</td>
    </tr>
    <tr>
      <th>0</th>
      <td>200.0</td>
      <td>NaN</td>
      <td>apple</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>90.0</td>
      <td>NaN</td>
      <td>guava</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>170.0</td>
      <td>NaN</td>
      <td>grape</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



##### Column binding two dataframes


```python
pd.concat([sales,cost], axis = 1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order_id</th>
      <th>item</th>
      <th>date</th>
      <th>item</th>
      <th>cost/kg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>apple</td>
      <td>2013-01-03</td>
      <td>apple</td>
      <td>200.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>104</td>
      <td>guava</td>
      <td>2013-01-01</td>
      <td>guava</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>102</td>
      <td>grape</td>
      <td>2013-01-02</td>
      <td>grape</td>
      <td>170.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>grape</td>
      <td>2013-01-01</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>104</td>
      <td>apple</td>
      <td>2013-01-03</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>101</td>
      <td>guava</td>
      <td>2013-01-03</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>102</td>
      <td>papaya</td>
      <td>2013-01-02</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



### Group by 


```python
# replacing NA in above dataframe by mean
sales_df = sales_df.fillna(sales_df.mean())
sales_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order_id</th>
      <th>item</th>
      <th>date</th>
      <th>cost/kg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>apple</td>
      <td>2013-01-03</td>
      <td>200.000000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>104</td>
      <td>guava</td>
      <td>2013-01-01</td>
      <td>90.000000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>102</td>
      <td>grape</td>
      <td>2013-01-02</td>
      <td>170.000000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>grape</td>
      <td>2013-01-01</td>
      <td>170.000000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>104</td>
      <td>apple</td>
      <td>2013-01-03</td>
      <td>200.000000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>101</td>
      <td>guava</td>
      <td>2013-01-03</td>
      <td>90.000000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>102</td>
      <td>papaya</td>
      <td>2013-01-02</td>
      <td>153.333333</td>
    </tr>
  </tbody>
</table>
</div>



###### calculating order id wise mean cost per kg


```python
mean_cost = sales_df.groupby('order_id')['cost/kg'].mean()
mean_cost
```




    order_id
    101     90.000000
    102    161.666667
    103    200.000000
    104    153.333333
    Name: cost/kg, dtype: float64



### Adding column using Map Function
* objective : Add a column 'mean_cost_per_kg' which contains order id wise average cost per kg.


```python
sales_df['mean_cost_per_kg'] = sales_df.order_id.map(sales_df.groupby('order_id')['cost/kg'].mean().to_dict())
sales_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order_id</th>
      <th>item</th>
      <th>date</th>
      <th>cost/kg</th>
      <th>mean_cost_per_kg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>apple</td>
      <td>2013-01-03</td>
      <td>200.000000</td>
      <td>200.000000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>104</td>
      <td>guava</td>
      <td>2013-01-01</td>
      <td>90.000000</td>
      <td>153.333333</td>
    </tr>
    <tr>
      <th>2</th>
      <td>102</td>
      <td>grape</td>
      <td>2013-01-02</td>
      <td>170.000000</td>
      <td>161.666667</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>grape</td>
      <td>2013-01-01</td>
      <td>170.000000</td>
      <td>153.333333</td>
    </tr>
    <tr>
      <th>4</th>
      <td>104</td>
      <td>apple</td>
      <td>2013-01-03</td>
      <td>200.000000</td>
      <td>153.333333</td>
    </tr>
    <tr>
      <th>5</th>
      <td>101</td>
      <td>guava</td>
      <td>2013-01-03</td>
      <td>90.000000</td>
      <td>90.000000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>102</td>
      <td>papaya</td>
      <td>2013-01-02</td>
      <td>153.333333</td>
      <td>161.666667</td>
    </tr>
  </tbody>
</table>
</div>



##### Getting data in/out


```python
# writing data in excel or csv file

#path = '/mapr/hdpbiu/_392256_vishnu/softwares_for_new_joinee'   # /mapr/hdpbiu = /Biu_load  for server
path = 'C:/Users/392256/Documents/Intro to Python'  # 

sales_df.to_csv(f'{path}/sales_df.csv', index = False)
sales_df.to_excel(f'{path}/sales_df.xlsx', sheet_name='Sheet1', index = False)
#sales_df.to_parquet(f'{path}/sales_df', engine = 'auto',index = False)
```

##### Reading from an csv or excel file


```python
from datetime import datetime
df = pd.read_csv(f'{path}/sales_df.csv', dtype = {'order_id' : str })
df.dtypes
```




    order_id             object
    item                 object
    date                 object
    cost/kg             float64
    mean_cost_per_kg    float64
    dtype: object



##### Reading Other file formats

* pd.read_excel for reading excel files
* pd.read_parquet for reading parquet files
* pd.read_clipboard for reading from clipboard
* pd.read_pickle for reading pickle files in which ML models are stored

<h1><center>THE END</h1>
