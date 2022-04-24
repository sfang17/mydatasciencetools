# R and pandas maneuvers

## Select
```python
select(df, -var)

df.drop('var', 1)
df.insert(loc=idx, column='var', value=[]) # inserting columns
```

## Arrange/sort
```python
arrange(df, var)
arrange(df, desc(var))

df.sort_values('var', ascending=False)
```

## Grouping
```python
df %>% group_by(group1, group2)
df %>% ungroup()

df.groupby('group1')
df.groupby(['group1', 'group2'])
df.reset_index() / or when grouping: df.groupby('group1', as_index=False)
```

## Summarize/agg by group
```python
df %>%
  group_by(group1, group2) %>%
  summarize(mean_var = mean(var), sum_var = sum(var), count_var = n(), first_var = first(var))

df.groupby('group1')['var1'].mean()
df.groupby('group1')['var1'].agg({'mean_col' : np.mean()}) # pass dict to specify column name
df.groupby(['group1', 'group2'])['var1'].agg(['mean', 'sum', 'count', 'size']) # size counts NaNs
```

## Distinct
```python
df %>% distinct(var) # returns dataframe with unique values of var

df.drop_duplicates()
df.drop_duplicates(subset='var') # returns df with unique values of var
```

## Sample
```python
sample_n(df, 100)
sample_frac(df, 0.5)

df.sample(100)
df.sample(frac=0.5)
```

## Get uniques
```python
table(df$var1)
table(df$var1, df$var2)

df['var'].value_counts()
df.crosstab(index=df['index var'], columns=df['column var'], margins=True) # margins show totals
```

## Concat/binding
```python
rbind(df1, df2)
cbind(df1, df2)

pd.concat([df1, df2], axis=0)
pd.concat([df1, df2], axis=1)
```

## Pivoting
```python
df %>% pivot_longer(cols, names_to='name for columns', values_to='name for values')
df %>% pivot_wider(names_from = `column names`, values_from = `column value`)

pd.melt(df, id_vars=['constant row'], value_vars=['col1', 'col2'], var_name='var name', value_name='val name')
pd.pivot(columns = 'column names', values = 'column value')
```

## Recoding
```python
df %>% mutate(var = recode(var, 'class1' = 'reclass1', 'class2' = 'reclass2', .default='default'))

df['var'].replace({'class1': 'reclass1', 'class2': 'reclass2'}, inplace = True)
```

## Apply
```python
apply(df, MARGIN, func)
lapply(list/vec, func)
sapply(list/vec, func) # outputs a vector

df['var'].apply(func)

def func(x):
  return dosomething(x['var'], x['var2'], x['var3'])
df.apply(func) # multiple columns
```

## Onehotting
```python
library('caret')
df_ = df %>% select(c(cols, to , onehot))
df_onehot = data.frame(predict(dummyVars('~.', data=df_), newdata=df_))

pd.get_dummies(df['col'], prefix='prefix')
```
