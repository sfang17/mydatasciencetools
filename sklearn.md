# sklearn maneuvers

## Scalers
```python
from sklearn.preprocessing import MinMaxScaler, StandardScaler

scaler = MinMaxScaler()
scaler = StandardScaler()
scaler.fit(d) # this fits the scale and stores scaling params
scaler.transform(d2)
```
