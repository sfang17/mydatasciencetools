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

fig, ax = plt.subplots() # need a subplot for heatmap
hm = ax.imshow(d.corr())
```

## Axis
```python
plt.xlabel('X')
plt.ylabel('Y')
plt.xlim(0, 10)
plt.ylim(0, 10)
plt.xticks(x, ['labels'], rotation=20)
plt.yticks(x, ['labels'], rotation=20)

ax.set_xticklabels([''] + d.corr().columns.tolist(), rotation=90) # relabel for heatmaps
ax.set_yticklabels([''] + d.corr().index.to_list())
```

## Legend
```python
plt.legend(loc='best, lower right')
plt.colorbar(hm) # colobar for heatmap
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
plt.plot([0,'xylim'], [0,'xylim']) # x = y

a, b = np.polyfit(x, y, 1)  # line of best fit
plt.plot(x, a*x+b)
```

## labels
```python
plt.title()

for label, i, j in zip(labels, x, y):
    plt.annotate(label, (i, j))
```
