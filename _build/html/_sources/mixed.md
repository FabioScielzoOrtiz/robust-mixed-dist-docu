# `mixed`

## `GGowerDistMatrix`

```
Calculates the Generalized Gower matrix for a data matrix.

-------------------
Constructor method
-------------------

Parameters: (inputs)
----------
p1, p2, p3: number of quantitative, binary and multi-class variables in the considered data matrix, respectively. Must be a non negative integer.

d1: name of the distance to be computed for quantitative variables. Must be an string in ['euclidean', 'minkowski', 'canberra', 'mahalanobis', 'robust_mahalanobis']. 

d2: name of the distance to be computed for binary variables. Must be an string in ['sokal', 'jaccard'].

d3: name of the distance to be computed for multi-class variables. Must be an string in ['hamming'].

q: the parameter that defines the Minkowski distance. Must be a positive integer.

robust_method: the method to be used for computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

alpha : a real number in [0,1] that is used if `method` is 'trimmed' or 'winsorized'. Only needed when d1 = 'robust_mahalanobis'.

epsilon : parameter used by the Delvin transformation. epsilon=0.05 is recommended. Only needed when d1 = 'robust_mahalanobis'.

n_iter : maximum number of iterations run by the Delvin algorithm. Only needed when d1 = 'robust_mahalanobis'.

weights: the sample weights.

fast_VG: whether the geometric variability estimation will be full (False) or fast (True).

VG_sample_size: sample size to be used to make the estimation of the geometric variability.

VG_n_samples: number of samples to be used to make the estimation of the geometric variability.

random_state: the random seed used for the (random) sample elements.

---------------     
Compute method
---------------

Parameters: (inputs)
----------
X: a pandas/polars data-frame or a numpy array. Represents a predictors matrix and is required. 
The first p1 predictors must be the quantitative, followed by the p2 binary predictors, and finally the p3 multiclass predictors.
    
Returns: (outputs)
--------
D: the Generalized Gower matrix for the data matrix `X`.
```


## `GGowerDist`

```
Calculates the Generalized Gower distance for a pair of data observations.

-------------------
Constructor method
-------------------
        
Parameters: (inputs)
-----------

p1, p2, p3: number of quantitative, binary and multi-class variables in the considered data matrix, respectively. Must be a non negative integer.

d1: name of the distance to be computed for quantitative variables. Must be an string in ['euclidean', 'minkowski', 'canberra', 'mahalanobis', 'robust_mahalanobis']. 

d2: name of the distance to be computed for binary variables. Must be an string in ['sokal', 'jaccard'].

d3: name of the distance to be computed for multi-class variables. Must be an string in ['matching'].

q: the parameter that defines the Minkowski distance. Must be a positive integer.

robust_method: the robust_method to be used for computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

epsilon: parameter used by the Delvin algorithm that is used when computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

n_iter: maximum number of iterations used by the Delvin algorithm. Only needed when d1 = 'robust_mahalanobis'.

weights: the sample weights.

VG_sample_size: sample size to be used to make the estimation of the geometric variability.

VG_n_samples: number of samples to be used to make the estimation of the geometric variability.

random_state: the random seed used for the (random) sample elements.

-----------        
Fit method
----------- 

Computes the geometric variability and covariance matrix to be used in 'compute' method, if needed.

Parameters: (inputs)
-----------

X: a pandas/polars data-frame or a numpy array. Represents a predictors matrix and is required. 
The first p1 predictors must be the quantitative, followed by the p2 binary predictors, and finally the p3 multiclass predictors.
            
Returns: (outputs)
--------

D: the Generalized Gower matrix for the data matrix `X`.

---------------
Compute method
---------------
        
Parameters: (inputs)
-----------

xi, xr: a pair of quantitative vectors. They represent a couple of statistical observations.
            
Returns: (outputs)
--------

dist: the Generalized Gower distance between the observations `xi` and `xr`.
```


## `FastGGowerDistMatrix`

```
Calculates the the Generalized Gower matrix of a sample of a given data matrix.

-------------------
Constructor method
-------------------
        
Parameters: (inputs)
-----------

frac_sample_size: the sample size in proportional terms.

p1, p2, p3: number of quantitative, binary and multi-class variables in the considered data matrix, respectively. Must be a non negative integer.

d1: name of the distance to be computed for quantitative variables. Must be an string in ['euclidean', 'minkowski', 'canberra', 'mahalanobis', 'robust_mahalanobis']. 

d2: name of the distance to be computed for binary variables. Must be an string in ['sokal', 'jaccard'].

d3: name of the distance to be computed for multi-class variables. Must be an string in ['matching'].

q: the parameter that defines the Minkowski distance. Must be a positive integer.

robust_method: the method to be used for computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

alpha : a real number in [0,1] that is used if `method` is 'trimmed' or 'winsorized'. Only needed when d1 = 'robust_mahalanobis'.

epsilon: parameter used by the Delvin algorithm that is used when computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

n_iters: maximum number of iterations used by the Delvin algorithm. Only needed when d1 = 'robust_mahalanobis'.

fast_VG: whether the geometric variability estimation will be full (False) or fast (True).

VG_sample_size: sample size to be used to make the estimation of the geometric variability.

VG_n_samples: number of samples to be used to make the estimation of the geometric variability.

random_state: the random seed used for the (random) sample elements.

weights: the sample weights.

---------------
Compute method
---------------

Computes the Generalized Gower function for the defined sample of data.
        
Parameters: (inputs)
-----------

X: a pandas/polars data-frame or a numpy array. Represents a predictors matrix and is required. 
The first p1 predictors must be the quantitative, followed by the p2 binary predictors, and finally the p3 multiclass predictors.
```

## `RelMSDistMatrix`

```
Calculates the Related Metric Scaling matrix for a data matrix.

-------------------
Constructor method
-------------------

Parameters: (inputs)
-----------

p1, p2, p3: number of quantitative, binary and multi-class variables in the considered data matrix, respectively. Must be a non negative integer.

d1: name of the distance to be computed for quantitative variables. Must be an string in ['euclidean', 'minkowski', 'canberra', 'mahalanobis', 'robust_mahalanobis']. 

d2: name of the distance to be computed for binary variables. Must be an string in ['sokal', 'jaccard'].

d3: name of the distance to be computed for multi-class variables. Must be an string in ['matching'].

q: the parameter that defines the Minkowski distance. Must be a positive integer.

robust_method: the robust_method to be used for computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

epsilon: parameter used by the Delvin algorithm that is used when computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

n_iter: maximum number of iterations used by the Delvin algorithm. Only needed when d1 = 'robust_mahalanobis'.

weights: the sample weights.

---------------
Compute method
---------------

Parameters: (inputs)
-----------

X: a pandas/polars data-frame or a numpy array. Represents a predictors matrix and is required. 
The first p1 predictors must be the quantitative, followed by the p2 binary predictors, and finally the p3 multiclass predictors.

tol: a tolerance value to round the close-to-zero eigenvalues of the Gramm matrices.

Gs_PSD_trans: controls if a transformation is applied to enforce positive semi-definite Gramm matrices.

d: a parameter that controls the omega definition involved in the transformation mentioned above.
            
Returns: (outputs)
--------

D: the Related Metric Scaling matrix for the data matrix `X`.
```