Monte Carlo simulation is a [[Modelling|modelling technique]] used for solving deterministic problems using [[Probability|random]] [[Data Analysis|sampling]]. This type of method is used in cases where solution to the problem is intractable and by using large amounts of random sampling we can find solutions to empirical problems proved by the [[Discrete Probability|law of large numbers]]. Common applications include within [[Optimisation|optimisation]] and analysis of data.

The Monte Carlo method can be described as a four step process following:
1. Define a domain for the samples.
2. Generate samples randomly.
3. Apply a deterministic computation on the samples.
4. Aggregate the results.

The idea of Monte Carlo is rather simple however various factors impact how effective the model can be. The main one is the amount of samples, and the method for generating these samples. Ensuring you have a [[Random Number Generation|RNG]] technique that generates uniformly is important as well as there being many samples. 

Monte Carlo is a slow approach due to the necessity of many computations with deterministic functions which are commonly expensive. The main approach to improving these algorithms is [[Parallelism|parallelism]].

# Buffon's Needle
Buffon's needle is a common example used to explain the Monte Carlo method. The original question is phrased as 'if you drop a needle of length $l$ on a floor of parallel lines $t$ units apart, what is the probability the needle will lie across two strips'. This has a [[Continuous Probability#Probability Density Function|PDF]] calculated as $p=\frac{2}{\pi}\cdot\frac{l}{t}$. Using this idea we can similarly calculate the value of $\pi$ as the amount of cases where given a rectangle with a semi-circle drawn inside how many times does this needle land both inside and outside of the circle. This allows us to create an approximation of $\pi$ where given enough samples we can find an accurate value.