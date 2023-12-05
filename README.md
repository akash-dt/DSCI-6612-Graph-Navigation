# DSCI-6612-Graph-Navigation 
Course Project for DSCI-6612 Intro to Artificial Intelligence

Introduction: 
The project will implement the A* algorithm, a widely used and efficient graph search algorithm for finding the shortest path between two nodes in a graph. The A* algorithm enhances Dijkstra's algorithm by incorporating a heuristic function to guide the search towards the goal node more efficiently. The heuristic function provides an estimate of the remaining distance from each node to the goal node, allowing the algorithm to prioritize nodes that are likely to be closer to the goal.
For these projects, we have used pedestrian paths around and inside our campus [University of New Haven, CT, USA] any location can be used just by defining the name of the place. The code is a jupyter notebook file consisting of all steps implemented in series.

Requirements:
Google API Key [Generate a Google Maps API key for reverse geocoding]
Name of the Place [ Name of the place you want to generate graph and search path]

Workflow:
Graph Generation: The code starts by generating a graph based on the place name provided using OpenSourceMaps Library. The graph generated for these project refers to a pedestrian walking path but the same code can be modified to generate a driving path by just defining driving_path as 'driving' instead of 'walking' to get a roadway graph.
Weighting:
The graph generated is a multidirectional network graph i.e. each pair of nodes has two sets of edges or a pair of weights one from each node as starting to another node. To move forward weights of each edge are calculated using the distance between pairs of nodes.
Reverse GeoCoding:
The graph generated does not contain the name and address of the place the node is marked so a reverse geocoding is implemented to get the Google Maps name and address of the node based on lat and long coordinates.

State Space Size:
The final graph has 315 nodes and 918 edges so state space for this graph can be calculated using
Branching factor = Total edges / Total nodes = 918/315 = 2.91 ~= 3

State space size = Number of possible states * Branching factor ^ Depth
Number of possible states =Number of nodes =315

For worst case depth = Number of nodes -1 
Therefor, State Space Size = n* (average_degree) ^ (n - 1) #n = Number of Nodes

