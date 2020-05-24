Numpy中的shuffle VS permutation: numpy.random.shuffle() or numpy.random.permutation()
**参数区别：**
- shuffle的参数只能是array_like，而permutation除了array_like还可以是int类型，如果是int类型，那就随机打乱numpy.arange(int)。
- shuffle返回None，没有返回值，而permutation则返回打乱后的array。

**速度区别：**
array很大的时候应使用shuffle速度更快，但要注意其不返回打乱后的array，而是inplace修改。

Casting: returns the array cast to the new type.
```python
arr = np.array([0, 1, 2])
print(arr.dtype)
arr = arr.astype(np.float32) #casting to a new datatype
print(arr.dtype)
```

Fill numpy a placeholder: NaN & Infinity
```python
arr = np.array([np.nan, 1, 2])
arr = np.array([-np.inf, 5]) 
# np.nan and np.inf都不能用integer type(dtype=np.int32)
```

