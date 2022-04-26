# Numpy maneuvers

## Types/values
```python
# types
np.int64
np.float32
np.bool
np.nan

# values
np.nan
np.inf
np.NINF
```

## Generate
```python
# scalars
np.arange(start, stop, step)
np.linspace(start, stop, num)
np.random.normal(loc=mean, scale=stdev, size=n)
np.random.choice(x, size) # resample

# mats
np.zeros((shape))
np.ones((shape))
np.empty((shape))
np.random.random((shape))
```

## Inspection
```python
arr.dtype
arr.astype(int)
arr.isnan()
arr.isnull()
arr.isfinite()
arr.isinf()
```
