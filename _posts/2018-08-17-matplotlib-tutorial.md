

```python
from IPython.display import Image;from datetime import date
from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity = "all"
```

<font size="5"><center><h2>Intro To Python For Data Analysis - Part 1</h2></center></font>
<h6>01 Oct,2019</h6>
<h6>By: Vishnu Prakash Singh</h6>

### Data Visualisation using matplotlib


```python
from matplotlib import pyplot as plt

ts = pd.Series(np.random.randn(1000),
           index=pd.date_range('1/1/2019', periods=1000))
ts = ts.cumsum()

ts.plot();
```


```python
x = np.arange(0,4*np.pi,0.1)   # start,stop,step
y = np.sin(x)
z = np.cos(x)
fig = plt.figure()
plt.plot(x,y,x,z)
plt.xlabel('x values from 0 to 4pi');   
plt.ylabel('sin(x) and cos(x)');
plt.title('Plot of sin and cos from 0 to 4pi');
plt.legend(['sin(x)', 'cos(x)']);     
plt.show();
```


![png](output_4_0.png)



```python
#saving the plot
fig.savefig('sine_cos_cuve.png')
```

##### Subplots in matplotlib


```python
plt.subplot(1,2,1);
plt.plot(x,y, 'blue');
plt.subplot(1,2,2);
plt.plot(x,z, 'orange');
```


![png](output_7_0.png)


### Reading Titanic Dataset
[Download From Here](https://web.stanford.edu/class/archive/cs/cs109/cs109.1166/problem12.html)


```python
path = 'C:/Users/392256/Documents/Intro to Python'   # change the path to your file location
titanic_data = pd.read_csv(f'{path}/titanic.csv')
titanic_data.head(3)
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
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>Siblings/Spouses Aboard</th>
      <th>Parents/Children Aboard</th>
      <th>Fare</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>3</td>
      <td>Mr. Owen Harris Braund</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>7.2500</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>Mrs. John Bradley (Florence Briggs Thayer) Cum...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>71.2833</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>3</td>
      <td>Miss. Laina Heikkinen</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.9250</td>
    </tr>
  </tbody>
</table>
</div>



#### Scatter Plot


```python
# create a figure and axis
fig, ax = plt.subplots()

# scatter plot of Fare vs Age
ax.scatter(titanic_data[titanic_data.Fare<50].Age, titanic_data[titanic_data.Fare<50].Fare)
# set a title and labels
ax.set_title('Fare vs Age Scatter Plot');
ax.set_xlabel('Age');
ax.set_ylabel('Fare');
```


![png](output_11_0.png)


#### Line Chart


```python
# get columns to plot
columns = ['Age', 'Fare']
# create x data
x_data = range(0, titanic_data[titanic_data.Fare>50].shape[0])
# create figure and axis
fig, ax = plt.subplots()
# plot each column
for column in columns:
    ax.plot(x_data, titanic_data[titanic_data.Fare>50][column]);
# set title and legend
ax.set_title('Fare vs Age line chart');
ax.set_xlabel('Age');
ax.set_ylabel('Fare');
ax.legend();

#plt.plot(range(0, titanic_data.shape[0]), max(titanic_data.Age)*titanic_data['Fare']/max(titanic_data.Fare),
 #      range(0, titanic_data.shape[0]),titanic_data.Age);
#ax.legend()
```

    No handles with labels found to put in legend.
    


![png](output_13_1.png)


##### Histogram


```python
# create figure and axis
fig, ax = plt.subplots()
# plot histogram
ax.hist(titanic_data['Age'])
# set title and labels
ax.set_title('Age Histogram');
ax.set_xlabel('Age in years');
ax.set_ylabel('Frequency');
```


![png](output_15_0.png)


##### Bar Chart


```python
# create a figure and axis 
fig, ax = plt.subplots() 
# count the occurrence of each class
data1 = titanic_data['Pclass'].value_counts() 
# get x and y data1 
points = data1.index 
frequency = data1.values 
# create bar chart 
ax.bar(points, frequency) 
# set title and labels 
ax.set_title('Passenger Class Bar Chart');
ax.set_xlabel('Passenger Class');
ax.set_ylabel('Frequency');
```


![png](output_17_0.png)


##### Box Plot

##### Box Plot of Age Variable


```python
fig, ax = plt.subplots();
ax.set_title('Multiple Samples with Different sizes');
ax.boxplot(titanic_data.Age);
ax.set_ylabel('Age in years');
```


![png](output_20_0.png)


##### Box Plot of Age variable grouped by survive using matplotlib


```python
data = [titanic_data.loc[titanic_data['Survived']==0, 'Age'],titanic_data.loc[titanic_data['Survived']==1, 'Age']]
fig, ax = plt.subplots();
ax.set_title('BoxPlot of Age grouped by Survival');
ax.boxplot(data);
ax.set_xlabel('Survived');
ax.set_ylabel('Age in years');
plt.xticks([1, 2], [0,1]);
```


![png](output_22_0.png)


##### Box Plot of Age variable grouped by survive using Pandas


```python
titanic_data[['Age','Survived']].boxplot(by='Survived');
```


![png](output_24_0.png)


<h1><center>THE END</h1>
