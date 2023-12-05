# DSCI-6612-Graph-Navigation 
Course Project for DSCI-6612 Intro to Artificial Intelligence

Introduction: 
The project will implement the A* algorithm, a widely used and efficient graph search algorithm for finding the shortest path between two nodes in a graph. The A* algorithm enhances Dijkstra's algorithm by incorporating a heuristic function to guide the search towards the goal node more efficiently. The heuristic function provides an estimate of the remaining distance from each node to the goal node, allowing the algorithm to prioritize nodes that are likely to be closer to the goal.
For these projects, we have used pedestrian paths around and inside our campus [University of New Haven, CT, USA] any location can be used just by defining the name of the place. The code is a jupyter notebook file consisting of all steps implemented in series.

Methodology:
A* Heuristic search: A heuristic function, also known simply as a heuristic, is a function that helps guide problem-solving and decision-making processes.

Types of heuristic we used: 
Euclidean Distance Heuristic:
Definition: This heuristic is based on the straight-line distance (as the crow flies) between the current state and the goal.


Manhattan Distance Heuristic:
Definition: Also known as the L1 norm or taxicab distance, this heuristic calculates the sum of the absolute differences in the x and y coordinates between the current state and the goal.


Chebyshev Distance Heuristic:
Definition: This heuristic calculates the maximum of the absolute differences in the x and y coordinates between the current state and the goal.


Octile Distance Heuristic:
Definition: A generalization of the Euclidean distance for grid-based environments that allow both horizontal, vertical, and diagonal movements. It uses a cost of √2 for diagonal movements.


Haversine Distance Heuristic:
The Haversine formula calculates the shortest distance between two points on a sphere, like the Earth. It uses latitude and longitude coordinates and is based on the haversine function. The formula yields the great-circle distance, providing a straight-line distance along the sphere's surface.

