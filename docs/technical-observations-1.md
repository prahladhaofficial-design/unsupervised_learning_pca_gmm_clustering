# Technical Observations 1


Project 4: Derivations and Observations
Prahladha
1 1. Dimensionality Reduction (Principal Component Analysis
 PCA)
1.1 1(c) PCA Eigenvalue Problem
The goal of PCA is to find directions in the data that maximize variance. Consider the data matrix
X = [x , x , . . . , x ]  RhwN ,
1 2 N
where each x is a vectorized image of dimension hw.
i
Mean Vector:
N
1 (cid:88)
 = I .
N i
i=1
Mean-Centered Data:
x = I  .
i i
Covariance Matrix:
1
C = XXT  Rhwhw.
N
PCA Eigenvalue Problem:
Cu = u.
Detailed Mathematical Derivation
1. Let the mean-centered data matrix be
X  = [x , x , . . . , x ].
1 2 N
2. The covariance matrix is
1
C = X  X  T .
N
3. PCA seeks a direction u maximizing the variance of projected data:
Var(uT x) = uT Cu.
4. Impose the constraint u = 1 and form the Lagrangian:
L(u, ) = uT Cu  (uT u  1).
5. Take derivative w.r.t. u and set to zero:
2Cu  2u = 0  Cu = u.
Thus PCA directions are eigenvectors of C, and eigenvalues correspond to variances.
1


Variance Interpretation
Eigenvectors with the largest eigenvalues represent directions of maximum data variance.
Dimensionality Reduction
Selecting the top-K eigenvectors
U = [u , u , . . . , u ]
K 1 2 K
forms a K-dimensional subspace capturing most of the variance.
1.2 1(d) Projection and Reconstruction in PCA Subspace
Let x be a mean-centered test vector.
test
Projection
z = U T x .
test k test
Reconstruction
I = U z + .
test k test
Reconstruction Error
hw
MSE(I , I ) = 1 (cid:88) (I (i)  I (i)) 2 .
test test hw test test
i=1
Compression vs. Quality
Increasing k improves reconstruction but reduces compression. Very small k yields blurred outputs.
2 2. Unsupervised Learning (K-Means and GMM)
2.1 2(a) K-Means Clustering
Objective Function
K-Means minimizes the Within-Cluster Sum of Squares (WCSS):
N
(cid:88)
L(Z, A) = x  z 2.
i A(xi)
i=1
Derivation of K-Means Updates
1. E-step (Project): Assign x to the nearest centroid:
i
A(x ) = arg min x  z 2.
i i k
k
2. M-step (Update): Given projects, minimize
(cid:88)
x  z 2
i k
i:A(xi)=k
2


w.r.t z . Taking derivative and setting to zero:
k
(cid:88) 1 (cid:88)
2(z  x ) = 0  z = x .
k i k |C | i
k
i:A(xi)=k i:A(xi)=k
Thus centroids are cluster means.
Complexities
Time:
O(IKN d)
Space:
O(N d + Kd + N ).
Limitations
Spherical assumptions, poor for elongated clusters, sensitive to outliers.
2.2 2(b) Gaussian Mixture Models (GMM)
Let latent variable Z indicate the cluster of x .
i i
Complete Data Log-Likelihood
N K
(cid:88) (cid:88)
log p(X, Z | ) = 1 [log  + log N (x |  ,  )] .
{Zi=k} k i k k
i=1 k=1
E-Step: Responsibilities
 N (x |  ,  )
 = k i k k .
ik (cid:80)K
 N (x |  ,  )
j=1 j i j j
M-Step: Parameter Updates
Mixing weights:
N
1 (cid:88)
 =  .
k N ik
i=1
Means:
(cid:80)N
 x
 = i=1 ik i .
k (cid:80)N

i=1 ik
Covariances:
(cid:80)N  (x   )(x   )T
 = i=1 ik i k i k .
k (cid:80)N

i=1 ik
Soft vs Hard Projects
GMM assigns probabilities; K-Means assigns a single cluster.
3
