
# `quantitative`

## `euclidean_dist_matrix`

```
Calculates the Euclidean distance matrix for a data matrix using SciPy.

Parameters (inputs)
----------
X: a Pandas or Polars DataFrame or a NumPy array. It represents a data matrix.

Returns (outputs)
-------
M: the Euclidean distance matrix between the rows of `X`.
```

## `euclidean_dist`

```
Calculates the Euclidean distance between a pair of vectors.

Parameters (inputs)
----------
xi, xr: a pair of Pandas or Polars Series or DataFrames, or Numpy arrays. They represent a couple of statistical observations of quantitative variables. 

Returns (outputs)
-------
The Euclidean distance between the observations `xi` and `xr`.
```

## `minkowski_dist_matrix`

```
Calculates the Minkowski distance matrix for a data matrix using SciPy.

Parameters (inputs)
----------
X: a Pandas or Polars DataFrame or a NumPy array. It represents a data matrix.
q: the parameters that defines the Minkowski form. Some particular cases: q=1 := Manhattan, q=2 := Euclidean.

Returns (outputs)
-------
M: the Minkowski(`q`) distance matrix between the rows of `X`.
```

## `minkowski_dist`


```
Calculates the Minkowski distance between a pair of vectors.

Parameters (inputs)
----------
xi, xr: a pair of quantitative vectors. They represent a couple of statistical observations.
q: the parameters that defines the Minkowski form. Some particular cases: q=1 := Manhattan, q=2 := Euclidean.

Returns (outputs)
-------
The Minkowki(`q`) distance between the observations `xi` and `xr`.
```


## `canberra_dist_matrix`

```
Calculates the Canberra distance matrix for a data matrix using SciPy.

Parameters (inputs)
----------
X: a pandas/polars DataFrame or a NumPy array. It represents a data matrix.

Returns (outputs)
-------
M: the Canberra distance matrix between the rows of `X`.
```

## `canberra_dist`

```
Calculates the Canberra distance between a pair of vectors.

Parameters (inputs)
----------
xi, xr: a pair of quantitative vectors. They represent a couple of statistical observations.

Returns (outputs)
-------
The Canberra distance between the observations `xi` and `xr`.
```


## `pearson_dist_matrix`

```
Calculates the Pearson distance matrix for a data matrix using SciPy.

Parameters (inputs)
----------
X: a pandas/polars DataFrame or a NumPy array. It represents a data matrix.

Returns (outputs)
-------
M: the Pearson distance matrix between the rows of X.
```


## `mahalanobis_dist_matrix`

```
Calculates the Mahalanobis distance matrix for a data matrix using SciPy.

Parameters (inputs)
----------
X: a pandas/polars DataFrame or a NumPy array. It represents a data matrix.

Returns (outputs)
-------
M: the Mahalanobis distance matrix between the rows of X.
```


## `mahalanobis_dist`


```
Calculates the Mahalanobis distance between a pair of vectors.

Parameters (inputs)
----------
xi, xr: a pair of quantitative vectors. They represent a couple of statistical observations.
S: the covariance matrix of the data matrix to which `xi` and `xr` belong.

Returns (outputs)
-------
The Mahalanobis distance between the observations `xi` and `xr`.
```



## `robust_maha_dist_matrix`

```
Calculates the Robust Mahalanobis distance matrix for a data matrix `X` using SciPy and a robust estimation of the covariance matrix.

Parameters (inputs)
----------
X: a pandas/polars DataFrame or a NumPy array. It represents a data matrix.
S_robust: the robust covariance matrix of `X`.

Returns (outputs)
-------
M: the Robust Mahalanobis distance matrix between the rows of X.
```


## `robust_maha_dist`

```
Calculates the Robust Mahalanobis distance between a pair of vectors.

Parameters (inputs)
----------
xi, xr: a pair of quantitative vectors. They represent a couple of statistical observations.
S_robust: the robust covariance matrix of the data matrix to which `xi` and `xr` belong.

Returns (outputs)
-------
The Robust Mahalanobis distance between the observations `xi` and `xr`.
```