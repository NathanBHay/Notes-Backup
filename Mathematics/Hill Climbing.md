Hill climbing is an [[Optimisation|optimisation]] technique that can be used to find a solution to a problem. It is an iterative algorithm that functions by computing the solution at a given point, before comparing the next solution by moving values incrementally. This is continues until a local optima is found. Due to this the algorithm is poor at finding global optima. Hill climbing is used in cases where there are very few local optima (such as convex problems) and a simple algorithm is desired.

# Exploration vs Exploitation
Exploration and exploitation are two opposing ideas when it comes to the decision of hill climbing heuristics. **Exploration** is searching a larger search space in order to find a more optimal solution, while **exploitation** is limiting the search space to more promising candidates. Exploitation is usually considered more computationally efficient however restricts itself to local optima while exploration allows for more variety at the cost of more computations. The best heuristics balance these to ensure the algorithm is fast while also finding local optima.

# Variants
There are a variety of basic improvements that can be done to the original algorithm. Most of these are done to address the problem of local optima. Here are some basic improvements:
- **Steepest ascent hill climbing** is a technique which computes a list of successors before choosing the best. With the amount and distance between the successors making the algorithm more efficient. 
- **Stochastic hill climbing** selects neighbours at random before computing if its better.
- **Random-restart hill climbing** also called shotgun hill climbing is an approach of using multiple instances of hill climbing with different initial conditions to find a solution.

## Simulated Annealing
Simulated annealing is an approximation technique for [[Optimisation|discrete optimisation]] problems. It can be considered an expansion of hill climbing that uses a heuristic that varies the neighbour search.  This approach is good for cases where the search space is too large, and a general approximation is all that is required. The algorithm works by randomly changing a value in a direction by a variable amount. This amount is called the **temperature** and as the iteration count increases this temperature decreases refining the search to a more local optima. 