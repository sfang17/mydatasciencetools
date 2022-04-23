# Some basic R and pandas maneuvers

---
## Select
R
```R
# removing columns
select(df, -var)
```

Python
```Python
# removing columns
df.drop('var', 1)

# inserting columns
df.insert(loc=idx, column='var', value=[])
```

---
## Arrange
R
```R
arrange(df, var)
arrange(df, desc(var))
```

Python
```python
df.sort_values('var', ascending=False)
```

---
## Grouping
R
```R
df %>% group_by(group1, group2)
df %>% ungroup()
```

Python
```python
df.groupby('group1')
df.groupby(['group1', 'group2'])
df.reset_index() / or when grouping: df.groupby('group1', as_index=False)
```

---
## Summarise / Aggregate df by group
R
```R
df %>%
  group_by(group1, group2) %>%
  summarize(mean_var = mean(var),
            sum_var = sum(var),
            count_var = n(),
            first_var = first(var))
```

Python
```python
df.groupby('group1')['var1'].mean()

 # pass dict to specify column name
df.groupby('group1')['var1'].agg({'mean_col' : np.mean()})

# size counts NaNs
df.groupby(['group1', 'group2'])['var1].agg(['mean', 'sum', 'count', 'size'])
```

---
## Distinct
R
```R
df %>% distinct(var) # returns dataframe with unique values of var
```

Python
```python
df.drop_duplicates()
df.drop_duplicates(subset='var') # returns dataframe with unique values of var
```

---
## Sample
R
```python
sample_n(df, 100)
sample_frac(df, 0.5)
```

Python
```R
df.sample(100)
df.sample(frac=0.5) 
```





#
