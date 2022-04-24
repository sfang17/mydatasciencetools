# matplotlib maneuvers

Great resources: [gfg](https://www.geeksforgeeks.org/matplotlib-practice-exercise-and-solutions/)

## Basics
```python
import matplotlib.pyplot as plt

plt.figure(figsize=(5,5), dpi=120) # overall size

plt.plot(x,y,'colormarker', label='forlegend')
plt.scatter(x,y)
plt.step(x,y)
plt.bar(x,y)
plt.boxplot(x) # can take list
plt.hist(x) # can take list
```

## Axis
```python
plt.xlabel('X')
plt.ylabel('Y')
plt.xlim(0, 10)
plt.ylim(0, 10)
```

## Legend
```python
plt.legend(loc='best, lower right')
```

## Subplotting
```python

fig, ax = plt.subplots(2, 2) # grid
ax[0,0].scatter(x, y)
ax[0,1].plot(x, y)
ax[1,0].plot(x, y)
ax[1,1].plot(x, y)
```

## Lines
```python
plt.axhline(y, color='k', linestyle='dotted', linewidth=5) # horizontal
plt.axvline(x) # vertical

a, b = np.polyfit(x, y, 1)  # line of best fit
plt.plot(x, a*x+b)
```
