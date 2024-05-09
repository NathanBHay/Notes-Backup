Field of vision algorithms are used to determine whether a given actor has vision. This is usually found in video games.

# Ray Casting
Ray Casting is an approach to field of vision that works through firing a series of rays out to determine visibility. These rays usually implement [[Line Drawing|line drawing]] algorithms with a obstruction check. The speed and the ability of the algorithm to function depends on the amount of rays being cast. There are a few approaches to choosing how many rays to cast. The most basic is all potential destinations. This method is slow as it recomputes many values. Casting around the perimeter is a common approach that while repeating many values is relatively fast. As the radius increases the number of artefacts increases. More advanced approaches use a fixed number of rays.

# Shadow Casting
