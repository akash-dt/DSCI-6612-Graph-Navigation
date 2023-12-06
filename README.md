# DSCI-6612-Graph-Navigation 
Course Project for DSCI-6612 Intro to Artificial Intelligence

Introduction: 
The project will implement the A* algorithm, a widely used and efficient graph search algorithm for finding the shortest path between two nodes in a graph. The A* algorithm enhances Dijkstra's algorithm by incorporating a heuristic function to guide the search towards the goal node more efficiently. The heuristic function provides an estimate of the remaining distance from each node to the goal node, allowing the algorithm to prioritize nodes that are likely to be closer to the goal.
For these projects, we have used pedestrian paths around and inside our campus [University of New Haven, CT, USA] any location can be used just by defining the name of the place. The code is a jupyter notebook file consisting of all steps implemented in series.

Requirements:
Google API Key [Generate a Google Maps API key for reverse geocoding]</br>
Name of the Place [ Name of the place you want to generate graph and search path]</br>

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


Going forward the project refers to unique for each node to traverse the graph and find the shortest path the name and address for reference are saved in edge_data.csv and node_data.csv

Implementation:
To find the best algorithm to find the shortest distance efficiently multiple heuristics were implemented and tested and compared.

A* algorithm with heuristic.<br />
f(n)=g(n)+h(n).<br />
Where:.<br />
g(n) is the actual cost from the start node to node n, .<br />
h(n) is the  heuristic from node n to the goal..<br />
.<br />
Heuristic Implemented:
-> Null Heuristic: Does not provide any value to heuristic passes 0 {Equivalent to implementing Dijkstra's algorithm}

-> Haversine Heuristic : 
h(node, goal) = R*acos (sin (latnode) sin(latgoal) + cos(latnode) cos(latgoal) cos(longoal)<br /> 
Where:<br />
• latnode and lonnode are the latitude and longitude of the current node, latgoal and longoal are the latitude and longitude of the goal,<br />
• R is the Earth's radius.<br />
<br />
-> Euclidean Distance:
h(n)=√(Xgn)2 + (Yg - Yn)2<br />
Where:<br />
(xg, Yg) are the coordinates of the goal.<br />
(2n, Yn) are the coordinates of the current node.<br />

-> Octile Distance:
h(n) = D x (dx+dy) + (D2-2 × D) x min (dæ, dy) x
<br />
Where:<br />
-h(n) is the octile distance heuristic from node n to the goal,<br />
-D is the cost of moving horizontally or vertically,<br />
-D2 is the cost of moving diagonally,<br />
dr is the absolute difference in x-coordinates between the current node and the goal,<br />
dy is the absolute difference in y-coordinates between the current node and the goal.<br />

->Chebyshev Distance
h(n) = D x max(dx, dy)<br />
Where:<br />
-h(n) is the Chebyshev distance heuristic from node n to the goal,<br />
-D is the cost of moving horizontally, vertically, or diagonally,<br />
-da is the absolute difference in x-coordinates between the current node and the goal<br />
- dy is the absolute difference in y-coordinates between the current node and the goal<br />

Comparison :
For comparison, the same pair of start and end nodes are given to all a* with the heuristic and Depth First Search Search and Breath First Search algorithm. The number of nodes expanded and the shortest distance found is used as an evaluation methodology to find the most efficient algorithm.

Visualization:
Each implementation is visualized using the folium library to create a map plot of the graph, the number of nodes expanded, and the shortest path found.
The black outline resembles the whole graph, the yellow lines show nodes expanded and the red line highlights the shortest path found along with its size.

Results:
![image](https://github.com/akash-dt/DSCI-6612-Graph-Navigation/assets/153000756/faa4e81e-5bd1-4044-a63d-a34dd7715aed)
The following table shows five randomly drawn pairs of nodes and the shortest distance found between them using all algorithms along with the number of nodes expanded. Additionally, the shortest route found is compared with the shortest route found for the same pair of nodes using Google Maps.
Null Heuristic            |  Haversine Heuristic | Euclidean Distance Heuristic | Octile Distance Heuristic |Chebyshev Heuristic 
:-------------------------:|:-------------------------:| :--------------------: | :-------------------------:| :---------------------:|
![image](https://github.com/akash-dt/DSCI-6612-Graph-Navigation/assets/153000756/eefa6b0a-ce0e-4f64-898b-e9cff39f2e0d) |  ![image](https://github.com/akash-dt/DSCI-6612-Graph-Navigation/assets/153000756/422d071b-adab-4695-8c23-76cafb8db6e8)|![image](https://github.com/akash-dt/DSCI-6612-Graph-Navigation/assets/153000756/84a8c840-be8a-4854-8e21-63113b5bae05)|![image](https://github.com/akash-dt/DSCI-6612-Graph-Navigation/assets/153000756/7bf2addc-5268-470f-86f3-864cb1be2f4c)|![image](https://github.com/akash-dt/DSCI-6612-Graph-Navigation/assets/153000756/2048ee67-cbb3-4234-af5c-14552824cb11)

Comparison with Search Algorithm
DFS          |  Haversine Heuristic | BFS
:-------------------------:|:-------------------------:| :--------------------: 
![image](https://github.com/akash-dt/DSCI-6612-Graph-Navigation/assets/153000756/bcc65128-17a1-410f-a5fb-6298459aa8ed) |  ![image](https://github.com/akash-dt/DSCI-6612-Graph-Navigation/assets/153000756/422d071b-adab-4695-8c23-76cafb8db6e8)|![image](https://github.com/akash-dt/DSCI-6612-Graph-Navigation/assets/153000756/84eeeeed-2c2f-4690-be1a-2a9b782d1e70)


Conclusion:
The A* Search algorithm with the Haversine Heuristic is the most efficient algorithm to find the shortest distance for these project because it found the shortest past by expanding the least number of nodes. Other heuristics gave the same result as the null heuristic because the weight of each edge is the same as the actual distance between the nodes and heuristics are not able to deliver any advantage over it.








