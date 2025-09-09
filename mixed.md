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

### Example 

```python
from PyDistances.mixed import GGowerDistMatrix

data_url = "https://raw.githubusercontent.com/FabioScielzoOrtiz/PyDistances-demo/refs/heads/main/data/madrid_houses_processed.csv"

data = pd.read_csv(data_url)

quant_cols = ['sq_mt_built', 'n_rooms', 'n_bathrooms', 'n_floors', 'buy_price']
binary_cols = ['is_renewal_needed', 'has_lift', 'is_exterior', 'has_parking']
multiclass_cols = ['energy_certificate', 'house_type']

p1 = len(quant_cols)
p2 = len(binary_cols)
p3 = len(multiclass_cols)

ggower_dist_matrix = GGowerDistMatrix(p1=p1, p2=p2, p3=p3,
                                      d1="robust_mahalanobis", d2="jaccard", d3="hamming",
                                      robust_method="trimmed", alpha=0.07, epsilon=0.05, 
                                      n_iters=20, weights=None)

ggower_dist_matrix.compute(X=data)
```
```
array([[0.        , 2.21871457, 1.93429293, ..., 1.94305438, 3.1223396 ,
        2.26768279],
       [2.21871457, 0.        , 1.22327246, ..., 2.38753004, 2.64304949,
        2.00865696],
       [1.93429293, 1.22327246, 0.        , ..., 2.36077974, 2.50019632,
        1.63811682],
       ...,
       [1.94305438, 2.38753004, 2.36077974, ..., 0.        , 2.9036275 ,
        1.75869492],
       [3.1223396 , 2.64304949, 2.50019632, ..., 2.9036275 , 0.        ,
        3.03987403],
       [2.26768279, 2.00865696, 1.63811682, ..., 1.75869492, 3.03987403,
        0.        ]])
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

### Example 


```python
from PyDistances.mixed import GGowerDist

data = pd.read_csv(data_url)

xi = data.iloc[2,:]
xr = data.iloc[10,:]

quant_cols = ['sq_mt_built', 'n_rooms', 'n_bathrooms', 'n_floors', 'buy_price']
binary_cols = ['is_renewal_needed', 'has_lift', 'is_exterior', 'has_parking']
multiclass_cols = ['energy_certificate', 'house_type']

p1 = len(quant_cols)
p2 = len(binary_cols)
p3 = len(multiclass_cols)

ggower_dist = GGowerDist(p1=p1, p2=p2, p3=p3, 
                         d1="robust_mahalanobis", d2="jaccard", d3="hamming", 
                         robust_method="trimmed", alpha=0.07, epsilon=0.05, 
                         n_iters=20, weights=None)

ggower_dist.fit(X=data)

ggower_dist.compute(xi=xi, xr=xr)
```
```
1.7385809635103606
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

### Example

```python
fastGGower = FastGGowerDistMatrix(frac_sample_size=0.03, random_state=123, p1=p1, p2=p2, p3=p3, 
                                  d1='robust_mahalanobis', d2='jaccard', d3='hamming', 
                                  robust_method='trimmed', alpha=0.07, epsilon=0.05)

fastGGower.compute(data_pd)

fastGGower.D_GGower
```
```
array([[0.        , 2.05362912, 2.1156306 , ..., 1.98033012, 1.68049866,
        2.77877277],
       [2.05362912, 0.        , 2.59692511, ..., 2.04280891, 3.04461163,
        1.90396833],
       [2.1156306 , 2.59692511, 0.        , ..., 2.43490678, 3.23741394,
        2.74362843],
       ...,
       [1.98033012, 2.04280891, 2.43490678, ..., 0.        , 2.79584785,
        1.86529973],
       [1.68049866, 3.04461163, 3.23741394, ..., 2.79584785, 0.        ,
        2.74932529],
       [2.77877277, 1.90396833, 2.74362843, ..., 1.86529973, 2.74932529,
        0.        ]])
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

### Example

```python
from PyDistances.mixed import RelMSDistMatrix

data_url = "https://raw.githubusercontent.com/FabioScielzoOrtiz/PyDistances-demo/refs/heads/main/data/madrid_houses_processed.csv"

data = pd.read_csv(data_url)

quant_cols = ['sq_mt_built', 'n_rooms', 'n_bathrooms', 'n_floors', 'buy_price']
binary_cols = ['is_renewal_needed', 'has_lift', 'is_exterior', 'has_parking']
multiclass_cols = ['energy_certificate', 'house_type']

p1 = len(quant_cols)
p2 = len(binary_cols)
p3 = len(multiclass_cols)

relms_dist_matrix = RelMSDistMatrix(p1=p1, p2=p2, p3=p3, 
                                    d1="robust_mahalanobis", d2="jaccard", d3="hamming", 
                                    robust_method="trimmed", alpha=0.07, epsilon=0.05, 
                                    n_iters=20, weights=None)

relms_dist_matrix.compute(X=data_pd[0:2000])
# Warning: for the whole sample, time > 23 mins.                                      
```
```
array([[ 0.        , 15.46117954, 15.40756806, ..., 15.32605925,
        15.44377892, 15.52438765],
       [15.46117867,  0.        , 15.3698612 , ..., 15.40913592,
        15.39775349, 15.49629569],
       [15.40756786, 15.36986068,  0.        , ..., 15.37663682,
        15.30916165, 15.4579883 ],
       ...,
       [15.32605924, 15.40913592, 15.37663682, ...,  0.        ,
        15.40950905, 15.37371301],
       [15.44377893, 15.39775347, 15.30916165, ..., 15.40950905,
         0.        , 15.52255903],
       [15.5243876 , 15.49629553, 15.45798823, ..., 15.37371302,
        15.52255903,  0.        ]])
```