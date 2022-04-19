# cytnx references

## cytnx.zeros

**cytnx.zeros(*shape, dtype=?, device=?*)**

Return a new tensor of given shape and type, filled with zeros.

### Parameters
* shape : *int or tuple of ints*
    Shape of the new array, e.g., ``(2, 3)`` or ``2``.
* dtype : *data-type, optional*
    The desired data-type for the array, e.g., `numpy.int8`.  Default is
    `numpy.float64`.

### Returns
out : ndarray
    Array of zeros with the given shape, dtype, and order.


```{admonition} See Also
* zeros_like : Return an array of zeros with shape and type of input.
* empty : Return a new uninitialized array.
* ones : Return a new array setting values to one.
* full : Return a new array of given shape filled with value.
```

### Examples
```python
>>> cytnx.zeros(5)

Total elem: 5
type  : Double (Float64)
cytnx device: CPU
Shape : (5)
[0.00000e+00 0.00000e+00 0.00000e+00 0.00000e+00 0.00000e+00 ]
```

```python
>>> cytnx.zeros((5,), dtype=cytnx.Int16)

Total elem: 5
type  : Int16
cytnx device: CPU
Shape : (5)
[   +0    +0    +0    +0    +0 ]
```

```python
>>> cytnx.zeros((2, 1))

Total elem: 2
type  : Double (Float64)
cytnx device: CPU
Shape : (2,1)
[[0.00000e+00 ]
 [0.00000e+00 ]]
```

```python
>>> s = (2,2)
>>> cytnx.zeros(s)

Total elem: 4
type  : Double (Float64)
cytnx device: CPU
Shape : (2,2)
[[0.00000e+00 0.00000e+00 ]
 [0.00000e+00 0.00000e+00 ]]
 ```
