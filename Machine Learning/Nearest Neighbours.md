Nearest neighbours is a [[Machine Learning|machine learning]] algorithm which makes predictions based upon the similarity to the $k$-nearest neighbour. More formally this works by finding the $k$ individuals in the training data that are most similar to the new individual in terms of predictor values.

There are a variety of similarity measures which can be used. The most common being the Euclidean distance between the two values in $p$-dimensional predictor space. This follows: 
$$d(x,x')=\biggl[\sum_{j=1}^p(x_j-x_j')^2\biggr]$$

The algorithm works by following:
1. Calculating the distance from each individual in the training data to the new individual. $d_i=d(x_i,x')$ for $i=1,\dots,n$.
2. Sort the individuals from smallest $d_i$ to the largest.
3. Denote the targets in the sorted list by $y^{(1)},\dots,y^{(n)}$, and use the individuals with the smallest $d_i$ to predict $y'$.
