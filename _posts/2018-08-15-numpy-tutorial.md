---
layout: post
title: "Python Tutorials part II- Numpy Tutorial"
date: 2019-09-20
tags: [markdown, python, md, jupyter]
excerpt: "This tutorial contains basic numpy functions used for data analysis."
---

```python
from IPython.display import Image;from datetime import date
from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity = "all"
```

<font size="5"><center><h2>Intro To Python For Data Analysis - Part 1</h2></center></font>
<h6>01 Oct,2019</h6>
<h6>By: Vishnu Prakash Singh</h6>

### Numpy Array

* NumPy, which stands for Numerical Python
* Consists of multidimensional array objects
* Mathematical and logical operations on arrays can be performed
* It has been built to work with the N-dimensional array, linear algebra, random number.
* TensorFlow and Scikit learn use NumPy array to compute the matrix multiplication in the back end.
* An ndarray is a multidimensional container of items of the same type and size.


```python
import numpy as np
list1 = [1,9,8,3]
# converting python list to numpy array
arr1d  = np.array(list1)

# Print the array and its type
arr1d
print('Class of array is ' + str(type(arr1d)))
print('Type of array is ' + str(arr1d.dtype))
print('Shape of array is ' + str(np.shape(arr1d)))
print('Size of array is ' + str(np.size(arr1d)))
```




    array([1, 9, 8, 3])



    Class of array is <class 'numpy.ndarray'>
    Type of array is int32
    Shape of array is (4,)
    Size of array is 4
    

##### Arithmetic Operations on Numpy Array


```python
# list1 + 5 #gives an error

# Add 5 to each element of arr1d
arr1d + 5
```




    array([ 6, 14, 13,  8])



##### Creating a 2d array from a list of lists


```python
list2 = [[1,2,3],[4,5,6]]
arr2d = np.array(list2) 
print('Class of array is ' + str(type(arr2d)))
print('Type of array is ' + str(arr2d.dtype))
print('Shape of array is ' + str(np.shape(arr2d)))
print('Size of array is ' + str(np.size(arr2d)))
```

    Class of array is <class 'numpy.ndarray'>
    Type of array is int32
    Shape of array is (2, 3)
    Size of array is 6
    

[source](https://docs.scipy.org/doc/numpy/user/quickstart.html)

##### Creating numpy arrays


```python
# Create an array of zeros
np.zeros((2,3))
# Create an array of ones
np.ones((2,3))
# Create an array of random values
np.empty( (2,2))
```




    array([[0., 0., 0.],
           [0., 0., 0.]])






    array([[1., 1., 1.],
           [1., 1., 1.]])






    array([[1.14383058e-311, 1.94861032e-153],
           [4.23894309e+175, 1.96545743e-152]])




```python
# Returns 9 values evenly spaced over {0,2}
np.linspace( 0, 2, 9 ) 
# Returns values with step size 5, endpoint is excluded
np.arange( 10, 31, 5 ) 
# Returns values with start = 0 & step size=5, endpoint is excluded
np.arange( 12 )
```




    array([0.  , 0.25, 0.5 , 0.75, 1.  , 1.25, 1.5 , 1.75, 2.  ])






    array([10, 15, 20, 25, 30])






    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11])



##### Reshaping an Array


```python
# changes the shape of the array 
a = np.arange(12).reshape(2,6)
a
a.shape
#converts nD array in 1D array
b = a.ravel()
b
b.shape
```




    array([[ 0,  1,  2,  3,  4,  5],
           [ 6,  7,  8,  9, 10, 11]])






    (2, 6)






    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11])






    (12,)



##### Basic Operations on numpy array


```python
np.random.seed(1183)
arr = np.random.randint(low = 1,high = 10,size = (2,3))
arr
```




    array([[7, 8, 6],
           [4, 5, 2]])




```python
# squaring numpy array
arr**2
# calculation sin function
10*np.sin(arr)
# calculating logical expression
arr<4
```




    array([[49, 64, 36],
           [16, 25,  4]], dtype=int32)






    array([[ 6.56986599,  9.89358247, -2.79415498],
           [-7.56802495, -9.58924275,  9.09297427]])






    array([[False, False, False],
           [False, False,  True]])




```python
# calculating exponential of array
np.exp(arr)
# calculating square root of array
np.sqrt(arr)
```




    array([[1096.63315843, 2980.95798704,  403.42879349],
           [  54.59815003,  148.4131591 ,    7.3890561 ]])






    array([[2.64575131, 2.82842712, 2.44948974],
           [2.        , 2.23606798, 1.41421356]])




```python
# sum of each element of array
arr.sum()
# min of array
arr.min()
# cumulative sum of array
arr.cumsum()                
```




    array([[ 7, 11,  4, 16],
           [ 6, 10, 19,  1],
           [19, 13,  1, 16]])






    32






    2






    array([ 7, 15, 21, 25, 30, 32], dtype=int32)




```python
# sum of each column
arr.sum(axis=0)
# min of each row
arr.min(axis=1)
# cumulative sum along each row
arr.cumsum(axis=1)                  
```




    array([11, 13,  8])






    array([6, 2])






    array([[ 7, 15, 21],
           [ 4,  9, 11]], dtype=int32)



##### Basic Mathematical Operation on 1D array


```python
a = np.array( [20,30,40,50] )
b = np.arange( 1, 5 )
b
```




    array([1, 2, 3, 4])




```python
#Addition of 2 arrays
a+b        #np.add(a,b)
#Subtraction of 2 arrays
a-b        # np.subtract(a,b)
#Multiplication of 2 arrays
a*b        # np.multiply(a,b) 
#Division of 2 arrays
a/b         # np.divide(a,b)
```




    array([21, 32, 43, 54])






    array([19, 28, 37, 46])






    array([ 20,  60, 120, 200])






    array([20.        , 15.        , 13.33333333, 12.5       ])




```python
# sum of all elements of nD array
c.sum()
# Minimum of all elements of nD array
c.min()
# Max of all elements of nD array
c.max()
# Transpose of nD array
c.T
```




    25






    4






    8






    array([[7, 6],
           [8, 4]])



##### Basic Operations on numpy nD array


```python
# creating random matrix for matrix operations
np.random.seed(1183)
c = np.random.randint(low = 1,high = 10,size = (2,2))
c
d = np.random.randint(low = 1,high = 10,size = (2,2))
d
```




    array([[7, 8],
           [6, 4]])






    array([[5, 2],
           [7, 1]])




```python
#Addition of 2 nD arrays
c+d
#Subtraction of 2 nD arrays
c-d
```




    array([[12, 10],
           [13,  5]])






    array([[ 2,  6],
           [-1,  3]])




```python
# elementwise product
c * d                       
# mctrix product
c @ d               
# another matrix product
c.dot(d)                    
```




    array([[35, 16],
           [42,  4]])






    array([[91, 22],
           [58, 16]])






    array([[91, 22],
           [58, 16]])



##### Indexing and Slicing


```python
np.random.seed(10)
e = np.random.randint(low = 1,high = 10,size = (10,))
e
#prints value present at index 2
e[2]
#prints value present at index 3 to (6-1)
e[3:6]
```




    array([5, 1, 2, 1, 2, 9, 1, 9, 7, 5])






    2






    array([1, 2, 9])




```python
#Replacing a value in an array
e[-1] = -25
e
#Replacing values in an array
e[0:8:2] = -99   # -99 can be replaced with any array of length e[0:8:2]
e
```




    array([  5,   1,   2,   1,   2,   9,   1,   9,   7, -25])






    array([-99,   1, -99,   1, -99,   9, -99,   9,   7, -25])




```python
# Reversing an array
e[ : :-1]
```




    array([-25,   7,   9, -99,   9, -99,   1, -99,   1, -99])




```python
# Generating array using function

def f(x,y):
...     return 5*x+4*y
...
f = np.fromfunction(f,(2,4),dtype=int)
f
```




    array([[ 0,  4,  8, 12],
           [ 5,  9, 13, 17]])



##### Stacking of Arrays


```python
g = np.floor(10*np.random.random((2,2)))
g
h = np.ceil(10*np.random.random((2,2)))
h
```




    array([[5., 2.],
           [5., 5.]])






    array([[4., 8.],
           [9., 2.]])




```python
#Vertical Stacking
np.vstack((g,h))
#Horizontal Stacking
np.hstack((g,h))
# Columns Stacking
np.column_stack((g,h)) 
# column and horizontal stacking of 1D array gives same result
```




    array([[5., 2.],
           [5., 5.],
           [4., 8.],
           [9., 2.]])






    array([[5., 2., 4., 8.],
           [5., 5., 9., 2.]])






    array([[5., 2., 4., 8.],
           [5., 5., 9., 2.]])




```python
i = np.array([4.,2.])
j = np.array([3.,8.])
np.column_stack((i,j))
np.hstack((i,j))
# column and horizontal stacking of 1D array gives different result
```




    array([[4., 3.],
           [2., 8.]])






    array([4., 2., 3., 8.])




```python
from numpy import newaxis  # increases array dimension by 1
g[:,newaxis]
g[:,newaxis].shape
g[newaxis,:]
g[newaxis,:].shape
```




    array([[[5., 2.]],
    
           [[5., 5.]]])






    (2, 1, 2)






    array([[[5., 2.],
            [5., 5.]]])






    (1, 2, 2)




```python
# using newaxis function, both coumn and horizontal stacking
np.column_stack((a[:,newaxis],b[:,newaxis]))
np.hstack((a[:,newaxis],b[:,newaxis]))   # the result is the same
```




    array([[4., 3.],
           [2., 8.]])






    array([[4., 3.],
           [2., 8.]])



##### Splitting an array


```python
k = np.floor(10*np.random.random((2,12)))
k
np.hsplit(k,3)   # Split a into 3
type(np.hsplit(k,3))
np.hsplit(k,(3,4))   # Split a after the third and the fourth column
```




    array([[0., 8., 4., 4., 5., 6., 5., 0., 9., 3., 3., 4.],
           [0., 0., 2., 2., 0., 4., 5., 7., 8., 1., 4., 9.]])






    [array([[0., 8., 4., 4.],
            [0., 0., 2., 2.]]), array([[5., 6., 5., 0.],
            [0., 4., 5., 7.]]), array([[9., 3., 3., 4.],
            [8., 1., 4., 9.]])]






    list






    [array([[0., 8., 4.],
            [0., 0., 2.]]), array([[4.],
            [2.]]), array([[5., 6., 5., 0., 9., 3., 3., 4.],
            [0., 4., 5., 7., 8., 1., 4., 9.]])]



##### Deep Copy


```python
l = k.copy()         # no new object is created
k is l          # a and b are two names for the same ndarray object
l.shape = 3,8    # changes the shape of a
l.shape
k.shape           # if one gets changed, other gets changed too
```




    False






    (3, 8)






    (2, 12)



##### Shallow copy


```python
l = k          # no new object is created
k is l          # a and b are two names for the same ndarray object
l.shape = 3,8    # changes the shape of a
l.shape
k.shape           # if one gets changed, other gets changed too
```




    True






    (3, 8)






    (3, 8)



##### Indexing with Arrays of Indices


```python
m = np.arange(1,13)**2                       # the first 12 square numbers
m
mi = np.array( [ 1,1,3,8,5 ] )              # an array of indices
m[mi]                                       # the elements of a at the positions i

mj = np.array( [ [ 3, 4], [ 9, 7 ] ] )      # a bidimensional array of indices
m[mj]                                       # the same shape as j
```




    array([  1,   4,   9,  16,  25,  36,  49,  64,  81, 100, 121, 144],
          dtype=int32)






    array([ 4,  4, 16, 81, 36], dtype=int32)






    array([[ 16,  25],
           [100,  64]], dtype=int32)




```python
a = np.arange(12).reshape(3,4)
a
i = np.array( [ [0,1],                        # indices for the first dim of a
                 [1,2] ] )
j = np.array( [ [2,1],                        # indices for the second dim
                 [3,3] ] )

a[i,j]                                     # i and j must have equal shape
a[i,2]
a[:,j]
a[:,2]
a[i]
```




    array([[ 0,  1,  2,  3],
           [ 4,  5,  6,  7],
           [ 8,  9, 10, 11]])






    array([[ 2,  5],
           [ 7, 11]])






    array([[ 2,  6],
           [ 6, 10]])






    array([[[ 2,  1],
            [ 3,  3]],
    
           [[ 6,  5],
            [ 7,  7]],
    
           [[10,  9],
            [11, 11]]])






    array([ 2,  6, 10])






    array([[[ 0,  1,  2,  3],
            [ 4,  5,  6,  7]],
    
           [[ 4,  5,  6,  7],
            [ 8,  9, 10, 11]]])




```python

time = np.linspace(20, 145, 5)                 # time scale
data = np.sin(np.arange(20)).reshape(5,4)      # 4 time-dependent series
time
data

ind = data.argmax(axis=0)                  # index of the maxima for each series
ind

time_max = time[ind]                       # times corresponding to the maxima

data_max = data[ind, range(data.shape[1])] # => data[ind[0],0], data[ind[1],1]...

time_max
data_max

np.all(data_max == data.max(axis=0))

```




    array([ 20.  ,  51.25,  82.5 , 113.75, 145.  ])






    array([[ 0.        ,  0.84147098,  0.90929743,  0.14112001],
           [-0.7568025 , -0.95892427, -0.2794155 ,  0.6569866 ],
           [ 0.98935825,  0.41211849, -0.54402111, -0.99999021],
           [-0.53657292,  0.42016704,  0.99060736,  0.65028784],
           [-0.28790332, -0.96139749, -0.75098725,  0.14987721]])






    array([2, 0, 3, 1], dtype=int64)






    array([ 82.5 ,  20.  , 113.75,  51.25])






    array([0.98935825, 0.84147098, 0.99060736, 0.6569866 ])






    True




```python
a = np.arange(12).reshape(3,4)
b = a > 4
b                                          # b is a boolean with a's shape
a[b]



```


```python
a = np.arange(12).reshape(3,4)
b1 = np.array([False,True,True])             # first dim selection
b2 = np.array([True,False,True,False])       # second dim selection

a[b1,:]                                   # selecting rows
array([[ 4,  5,  6,  7],
       [ 8,  9, 10, 11]])

a[b1]                                     # same thing
array([[ 4,  5,  6,  7],
       [ 8,  9, 10, 11]])

a[:,b2]                                   # selecting columns
array([[ 0,  2],
       [ 4,  6],
       [ 8, 10]])

a[b1,b2]                                  # a weird thing to do
array([ 4, 10])
```


```python
a = np.array([2,3,4,5])
b = np.array([8,5,4])
c = np.array([5,4,6,8,3])
ax,bx,cx = np.ix_(a,b,c)
ax

bx
cx
ax.shape, bx.shape, cx.shape
result = ax+bx*cx
result
result[3,2,4]

a[3]+b[2]*c[4]
```




    array([[[2]],
    
           [[3]],
    
           [[4]],
    
           [[5]]])






    array([[[8],
            [5],
            [4]]])






    array([[[5, 4, 6, 8, 3]]])






    ((4, 1, 1), (1, 3, 1), (1, 1, 5))






    array([[[42, 34, 50, 66, 26],
            [27, 22, 32, 42, 17],
            [22, 18, 26, 34, 14]],
    
           [[43, 35, 51, 67, 27],
            [28, 23, 33, 43, 18],
            [23, 19, 27, 35, 15]],
    
           [[44, 36, 52, 68, 28],
            [29, 24, 34, 44, 19],
            [24, 20, 28, 36, 16]],
    
           [[45, 37, 53, 69, 29],
            [30, 25, 35, 45, 20],
            [25, 21, 29, 37, 17]]])






    17






    17




```python
import numpy as np
a = np.array([[1.0, 2.0], [3.0, 4.0]])

np.linalg.inv(a)

u = np.eye(2) # unit 2x2 matrix; "eye" represents "I"
u

np.trace(u)  # trace

y = np.array([[5.], [7.]])
np.linalg.solve(a, y)

np.linalg.eig(j)

```




    array([[-2. ,  1. ],
           [ 1.5, -0.5]])






    array([[1., 0.],
           [0., 1.]])






    2.0






    array([[-3.],
           [ 4.]])






    (array([0.69722436, 4.30277564]), array([[-0.60889368, -0.3983218 ],
            [ 0.79325185, -0.91724574]]))



##### [structured-arrays](https://docs.scipy.org/doc/numpy/user/basics.rec.html#structured-arrays)


```python
x = np.array([('Rex', 9, 81.0), ('Fido', 3, 27.0)],
              dtype=[('name', 'U10'), ('age', 'i4'), ('weight', 'f4')])
x


x[1]

x['age']

x['age'] = 5
x
```




    array([('Rex', 9, 81.), ('Fido', 3, 27.)],
          dtype=[('name', '<U10'), ('age', '<i4'), ('weight', '<f4')])






    ('Fido', 3, 27.)






    array([9, 3])






    array([('Rex', 5, 81.), ('Fido', 5, 27.)],
          dtype=[('name', '<U10'), ('age', '<i4'), ('weight', '<f4')])



##### Basic Operations¶


```python

```


```python

```


```python

# Create an array of ones
np.ones((3,4))

# Create an array of zeros
np.zeros((2,3,4),dtype=np.int16)

# Create an array with random values
np.random.random((2,2))

# Create an empty array
np.empty((3,2))

# Create a full array
np.full((2,2),7)

# Create an array of evenly-spaced values
np.arange(10,25,5)

# Create an array of evenly-spaced values
np.linspace(0,2,9)
```




    array([[1., 1., 1., 1.],
           [1., 1., 1., 1.],
           [1., 1., 1., 1.]])






    array([[[0, 0, 0, 0],
            [0, 0, 0, 0],
            [0, 0, 0, 0]],
    
           [[0, 0, 0, 0],
            [0, 0, 0, 0],
            [0, 0, 0, 0]]], dtype=int16)






    array([[0.82614537, 0.88732649],
           [0.85561316, 0.16463622]])






    array([[0., 0.],
           [0., 0.],
           [0., 0.]])






    array([[7, 7],
           [7, 7]])






    array([10, 15, 20])






    array([0.  , 0.25, 0.5 , 0.75, 1.  , 1.25, 1.5 , 1.75, 2.  ])




```python

```


```python

```


```python

```


```python

```


```python

```

<h3><center>Common Numpy Functions</center></h3>
    

| Numpy Functions             | Description                      |
|-----------------------------|----------------------------------|
|  my_array.shape             |  Get the dimensions of the array |
|  np.append(other_array)     | Append items to an array         |
|  np.insert(my_array, 1, 5)  | Insert items in an array         |
|  np.delete(my_array,[1])    | Delete items in an array         |
|  np.mean(my_array)          | Mean of the array                |
|  np.median(my_array)        | Median of the array              |
|  my_array.corrcoef()        | Correlation coefficient          |
|  np.std(my_array)           | Standard deviation               |

<h1><center>THE END</h1>
