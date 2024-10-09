NumPy is a Python library used for working with arrays. It also has functions for working in domain of linear algebra, fourier transform, and matrices.

## Why Use NumPy?
In Python we have lists that serve the purpose of arrays, but they are slow to process.

NumPy aims to provide an array object that is up to 50x faster than traditional Python lists.

The array object in NumPy is called `ndarray`, it provides a lot of supporting functions that make working with ndarray very easy.

## Why is NumPy Faster Than Lists?
NumPy arrays are stored at one continuous place in memory unlike lists, so processes can access and manipulate them very efficiently.

This behavior is called locality of reference in computer science.

# Creating Array
NumPy is used to work with arrays. The array object in NumPy is called ndarray. We can create a NumPy `ndarray` object by using the `array()` function.
```
import numpy as np
arr = np.array([1, 2, 3, 4, 5])
print(arr)
print(type(arr))
```
`type()`: This built-in Python function tells us the type of the object passed to it. Like in above code it shows that `arr` is `numpy.ndarray` type.

To create an ndarray, we can pass a list, tuple or any array-like object into the array() method, and it will be converted into an ndarray
```
arr = np.array((1, 2, 3, 4, 5))
print(arr)
```
### Dimensions
- `0-D` or `Scalar` array are the elements in an array
- `1-D` or `uni-dimensional` array have 0-D array as it's element
- `2-D` array have 1-D array as it's element. These are often used to represent matrix or 2nd order tensors. NumPy has a whole sub module dedicated towards matrix operations called `numpy.mat`

```
zero = np.array(42)
one = np.array([1, 2, 3, 4, 5])
two = np.array([[1, 2, 3], [4, 5, 6]])
three = np.array([[[1, 2, 3], [4, 5, 6]], [[1, 2, 3], [4, 5, 6]]])
```

- `ndim` as attribute return the dimension and as argument set the dimension
```
arr = np.array([1, 2, 3, 4], ndmin=5)
print(arr.ndim)
```
