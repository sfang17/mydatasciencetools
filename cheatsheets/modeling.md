# modeling code

## pca
```python
from sklearn.decomposition import PCA

pca = PCA(n_components=2)
pcs = pca.fit_transform(d_train_scaled)
d_pca = pd.DataFrame(data = pcs, columns = ['pc1', 'pc2'])
```

## imputation
```python
from sklearn.impute import KNNImputer
imputer = KNNImputer(n_neighbors=2, weights="uniform")
d_imputed = imputer.fit_transform(d)

from sklearn.experimental import enable_iterative_imputer # multivariable imputer
from sklearn.impute import IterativeImputer
imp_mean = IterativeImputer(random_state=0)
imp_mean.fit(d)
imp_mean.fit_transform(d) # or you can just fit transform
IterativeImputer(random_state=0)
imp_mean.transform(X)
```

## eval metrics
[metrics](https://scikit-learn.org/stable/modules/model_evaluation.html)
```python
from sklearn.metrics import *
```

## models
```python
# classification
from sklearn.linear_model import LogisticRegression
from sklearn.svm import SVC
from sklearn.naive_bayes import GaussianNB
from sklearn.naive_bayes import MultinomialNB
from sklearn.linear_model import SGDClassifier
from sklearn.neighbors import KNeighborsClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.ensemble import GradientBoostingClassifier
from lightgbm import LGBMClassifier # num_leaves +>var, min_data_in_leaf +<var, max_depth +>var
from xgboost.sklearn import XGBClassifier # max_depth +>var[3,15], min_child_weight +>var[3,15], gamma +<var[0,3]

# regression
from sklearn.linear_model import LinearRegression
from lightgbm import LGBMRegressor
from xgboost.sklearn import XGBRegressor
from catboost import CatBoostRegressor
from sklearn.linear_model import SGDRegressor
from sklearn.kernel_ridge import KernelRidge
from sklearn.linear_model import ElasticNet
from sklearn.linear_model import BayesianRidge
from sklearn.ensemble import GradientBoostingRegressor
from sklearn.svm import SVR
```

## model training w/ grid
```python
# model training
hyper_parameters = {'max_depth': [3], 'min_child_weight': [3], 'gamma': [0]}
model            = xgb.XGBRegressor(eval_metric=mean_absolute_error, seed=1337)
cross_validation = KFold(n_splits=5, shuffle=True, random_state=1337) # could also be stratified kfold (for categorical outcomes, classification)
grid_search      = GridSearchCV(model, hyper_parameters, n_jobs=8, cv=cv, verbose=2, refit=True)
grid_search.fit(x_train, y_train)
```

## model evaluation
```python
# model eval
y_pred_test  = grid_search.predict(x_test)
y_pred_train = grid_search.predict(x_train)
```
