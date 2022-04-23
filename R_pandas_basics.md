# Some basic R and pandas maneuvers

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

## Sample
R
```R
sample_n(df, 100)
sample_frac(df, 0.5)
```

Python
```python
df.sample(100)
df.sample(frac=0.5)
```

## Get number of unique values
R
```R
table(df$var1)
table(df$var1, df$var2)
```

Python
```python
df['var'].value_counts()

# margins show totals
df.crosstab(index=df['index var'], columns=df['column var'], margins=True)
```

## Concat/binding
R
```R
rbind(df1, df2)
cbind(df1, df2)
```

Python
```python
pd.concat([df1, df2], axis=0)
pd.concat([df1, df2], axis=1)
```

## Pivoting
R
```R
# from wide format
df %>% pivot_longer(cols, names_to='name for columns', values_to='name for values')
# from long format
df %>% pivot_wider(names_from = `column names`, values_from = `column value`)
```

Python
```python
pd.melt(df, id_vars=['constant row'], value_vars=['col1', 'col2'], var_name='var name', value_name='val name')
pd.pivot(columns = 'column names', values = 'column value')
```
