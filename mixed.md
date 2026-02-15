# `mixed`

## `generalized_gower_dist_matrix`

```
Calculates the Generalized Gower matrix for a data matrix.

Parameters (inputs)
----------

X: a pandas/polars data-frame or a numpy array. Represents a data matrix.

p1, p2, p3: number of quantitative, binary and multi-class variables in the considered data matrix, respectively. Must be a non negative integer.

d1: name of the distance to be computed for quantitative variables. Must be an string in ['euclidean', 'minkowski', 'canberra', 'mahalanobis', 'robust_mahalanobis']. 

d2: name of the distance to be computed for binary variables. Must be an string in ['sokal', 'jaccard'].

d3: name of the distance to be computed for multi-class variables. Must be an string in ['hamming'].

q: the parameter that defines the Minkowski distance. Must be a positive integer.

robust_method: the robust_method to be used for computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

alpha : a real number in [0,1] that is used if `robust_method` is 'trimmed' or 'winsorized'. Only needed when d1 = 'robust_mahalanobis'.

epsilon : parameter used by the Delvin transformation. epsilon=0.05 is recommended. Only needed when d1 = 'robust_mahalanobis'.

n_iter : maximum number of iterations run by the Delvin algorithm. Only needed when d1 = 'robust_mahalanobis'.

weights: the sample weights. Only used if provided and d1 = 'robust_mahalanobis'.  

Returns (outputs)
-------

D: the Generalized Gower matrix for the data matrix `X`.
```

## `generalized_gower_dist`

```
Calculates the Generalized Gower distance between a pair of mixed data vectors.

Parameters (inputs)
----------

xi, xr: 1D array-like. They represent a couple of statistical observations (mixed data vectors).

p1, p2, p3: number of quantitative, binary and multi-class variables in the considered data vectors, respectively. Must be a non negative integer.

d1: name of the distance to be computed for quantitative variables. Must be an string in ['euclidean', 'minkowski', 'canberra', 'mahalanobis', 'robust_mahalanobis']. 

d2: name of the distance to be computed for binary variables. Must be an string in ['sokal', 'jaccard'].

d3: name of the distance to be computed for multi-class variables. Must be an string in ['hamming'].

q: the parameter that defines the Minkowski distance. Must be a positive integer.

S: the covariance matrix (standard or robust) to be used. Only needed when d1 is 'mahalanobis' or 'robust_mahalanobis'.

geom_var_1, geom_var_2, geom_var_3: geometric variability of the quantitative, binary, and multi-class distances, respectively. Used to standardize the squared distances.

Returns (outputs)
-------

dist: the Generalized Gower distance between the observations `xi` and `xr`.
```

## `related_metric_scaling_dist_matrix_faster`

```
Calculates a faster estimation of the Related Metric Scaling matrix for a data matrix.

Parameters (inputs)
----------

X: a pandas/polars data-frame or a numpy array. Represents a data matrix.

p1, p2, p3: number of quantitative, binary and multi-class variables in the considered data matrix, respectively. Must be a non negative integer.

d1: name of the distance to be computed for quantitative variables. Must be an string in ['euclidean', 'minkowski', 'canberra', 'mahalanobis', 'robust_mahalanobis']. 

d2: name of the distance to be computed for binary variables. Must be an string in ['sokal', 'jaccard'].

d3: name of the distance to be computed for multi-class variables. Must be an string in ['hamming'].

q: the parameter that defines the Minkowski distance. Must be a positive integer.

robust_method: the robust_method to be used for computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

alpha : a real number in [0,1] that is used if `robust_method` is 'trimmed' or 'winsorized'. Only needed when d1 = 'robust_mahalanobis'.

epsilon : parameter used by the Delvin transformation. epsilon=0.05 is recommended. Only needed when d1 = 'robust_mahalanobis'.

n_iter : maximum number of iterations run by the Delvin algorithm. Only needed when d1 = 'robust_mahalanobis'.

weights: the sample weights. Only used if provided and d1 = 'robust_mahalanobis'.  

tol: a tolerance value to round the close-to-zero eigenvalues of the Gramm matrices.

Gs_PSD_trans: controls if a transformation is applied to enforce positive semi-definite Gramm matrices.

d: a parameter that controls the omega definition involved in the transformation mentioned above.    

Returns (outputs)
-------

D: the Related Metric Scaling matrix for the data matrix `X`.
```