Casting: returns the array cast to the new type.
'''python
arr = np.array([0, 1, 2])
print(arr.dtype)
arr = arr.astype(np.float32) #casting to a new datatype
print(arr.dtype)
'''

Fill numpy a placeholder: NaN & Infinity
'''python
arr = np.array([np.nan, 1, 2])
arr = np.array([-np.inf, 5]) # np.nan and np.inf都不能用integer type(dtype=np.int32)
'''
