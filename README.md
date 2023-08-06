# AStarSearch
A* algorithm finds the shortest paths using cost and heuristic estimates.

## Introduction
The A* search algorithm is a popular and widely used graph traversal and pathfinding algorithm in computer science and artificial intelligence. It is employed to find the shortest path between two nodes in a graph while considering the actual cost of moving between nodes and a heuristic estimate of the remaining cost to reach the goal.

A* combines two key components: 

1. **G-Cost (Actual Cost):** This represents the cost of moving from the starting node to the current node along a particular path.

2. **H-Cost (Heuristic Cost):** This estimates the cost to reach the goal from the current node, typically calculated using a heuristic function. The heuristic function should be admissible (never overestimate the actual cost) and consistent (satisfy the triangle inequality property).

A* uses a priority queue to explore nodes in the graph. It selects nodes to explore based on a combination of their G-Cost and H-Cost, giving priority to nodes with lower total estimated costs (G + H). By considering both the cost incurred and the estimated cost to reach the goal, A* efficiently navigates towards the goal while avoiding unnecessary exploration.

During its execution, A* gradually expands nodes, updating their G-Costs and H-Costs as new paths are discovered. Once the goal node is reached, the algorithm terminates, and the path can be reconstructed by tracing back from the goal node to the start node using the stored information.

A* is widely used in various applications, including robotics, computer games, route planning, and artificial intelligence systems. Its efficiency and ability to find optimal paths make it a fundamental tool for solving problems involving pathfinding and graph traversal.

## Problem Scenario                                    
On holiday, and a flight currently wants to travel to Bucharest from Arad. But there is no direct way to Bucharest from Arad. However, the cities are connected with each other like a graph. The distance between the connected cities is given. The flight wants to travel in the most optimal way. To find the optimal path to travel, another piece of information is provided: the straight line distance between any city and the final destination (Bucharest). 
Now apply A* search to determine the most optimal value for the route Arad to Bucharest and help the flight. You have to use the straight line distance as the heuristic value for the cities.
City	Heuristic value	City	Heuristic value
Arad	366	Mehadia	241
Bucharest	0	Neamt	234
Craiova	160	Oradea	380
Eforie	161	Pitesti	100
Fagaras	176	Rimnicu Vilcea	193
Dobreta	242	Timisoara	329
Hirsova	151	Urziceni	80
lasi	226	Vaslui	199
Lugoj	244	Zerind	374
For simplicity assume these notations
Arad	A	Neamt	F
Bucharest	Z	Oradea	B
Craiova	S	Pitesti	P
Eforie	T	Rimnicu Vilcea	R
Fagaras	O	Timisoara	C
Dobreta	V	Urziceni	D
Hirsova	N	Vaslui	H
lasi	Q	Zerind	E
Lugoj	G		
Mehadia	L		

INPUTS
Your txt file should take each node followed by each destination it can reach and their corresponding distance and heuristics. You are to read the file then ask the user to input the starting and the destination point.

OUTPUTS
The output will contain the total distance from the starting point to the destination followed by printing the nodes it followed to calculate the distance.

SAMPLE INPUT
In the text file:
Arad 366 Zerind 75 Sibiu 140 Timisoara 118
Zerind 374 Arad 75 Oradea 71
Oradea 380 Zerind 71 Sibiu 151
... ... ... ... ... ...
Bucharest 0 Pitesti 101 Fagaras 211 Giurgiu 90 Urziceni 85
Giurgiu 77 Bucharest 90
... ... ... ... ... …

The text file is arranged as follows:

Each line starts with a node followed by the heuristic of that node
Then the neighboring nodes and the distance from the parent node is given as a pair
All neighboring city-distance pairs are listed after the heuristic.

For example, the text file starts with Arad which has a heuristic of 366. It is the parent node to Zerind, Sibiu and Timisoara which are 75, 140 and 118 km away from Arad. Notice that since Bucharest is the End node which is why it has a heuristic of 0.

In console:
Start node: Arad
Destination: Bucharest

Sample output
Path: Arad -> Sibiu -> Rimnicu -> Pitesti -> Bucharest
Total distance: 418 km

If there is no path found from the Start node to the End node, simply print “NO PATH FOUND”

### Input text
Arad 366 Zerind 75 Timisoara 118 Sibiu 140
Craiova 160 Dobreta 120 RimnicuVilcea 146 Pitesti 138
Eforie 161 Hirsova 86
Fagaras 176 Sibiu 99 Bucharest 211
Giurgiu 77 Bucharest 90
Mehadia 241 Lugoj 70 Dobreta 75
Neamt 234 lasi 87
Sibiu 253 Oradea 151 Arad 140 RimnicuVilcea 80 Fagaras 99
Oradea 380 Zerind 71 Sibiu 151
Pitesti 100 RimnicuVilcea 97 Craiova 138 Bucharest 101
RimnicuVilcea 193 Sibiu 80 Craiova 146 Pitesti 97
Dobreta 242 Mehadia 75 Craiova 120
Hirsova 151 Urziceni 98 Eforie 86
lasi 226 Vaslui 92 Neamt 87
Lugoj 244 Timisoara 111 Mehadia 70
Timisoara 329 Arad 118 Lugoj 111
Urziceni 80 Bucharest 85 Hirsova 98 Vaslui 142
Vaslui 199 Urziceni 142 lasi 92 
Zerind 374 Oradea 71 Arad 75
Bucharest 0 Fagaras 211 Pitesti 101 Giurgiu 90 Urziceni 85

## Code explanation.
The code above implements the A* search algorithm to find the shortest path between nodes in a graph with associated costs and heuristic values. Here's a breakdown of the code:

1. **`A_star_search` Function**: This function performs the A* search algorithm. It takes four arguments: the graph `g` (in the form of a dictionary of dictionaries representing the edges and their costs), the starting node `s`, the destination node `des`, and the heuristic values `heu_val` for each node. It returns a tuple containing the parent dictionary and the total cost of the path.

2. **`show_path` Function**: This function uses the result from the A* search to display the path and its total distance. It takes the graph, starting node, destination node, and heuristic values as arguments.

3. **File Reading and Graph Initialization**: The code reads input from a file located at the specified path. It constructs graph `g` using a dictionary of dictionaries to represent the edges and their associated costs. The heuristic values are stored in the `heu_val` dictionary.

4. **A* Search Algorithm Execution**: The `show_path` function is then called with the specified source and destination nodes, and the heuristic values. It calls the `A_star_search` function to find the shortest path and associated cost. The path is reconstructed using the parent dictionary, and the result is displayed.

5. **User Input**: The program prompts the user to enter the starting and destination nodes.

6. **Path Reconstruction and Display**: The code reconstructs the path from the parent dictionary obtained from the A* search and displays the path nodes in sequence, along with the total distance.

Please note that the given code relies on the input format in the "input.txt" file and certain assumptions about the structure of the graph. Additionally, the heuristic values provided play a key role in guiding the A* search algorithm toward the goal more efficiently.

## Conclusion
In conclusion, the A* search algorithm stands as a versatile and influential tool in the realm of computer science and artificial intelligence. With its ability to efficiently find the shortest path between nodes in a graph, A* strikes a balance between optimality and practicality by incorporating both actual costs and heuristic estimates. This enables it to navigate through complex graphs and deliver optimal solutions in various applications, such as route planning, robotics, and gaming.

A* algorithm's success lies in its intelligent exploration strategy, which prioritizes nodes with the lowest estimated total cost. This strategy not only ensures optimality in terms of finding the shortest path but also significantly reduces the number of nodes explored compared to other uninformed search algorithms.

However, A* is not without limitations. Its effectiveness heavily relies on the quality of the heuristic function. An inappropriate or poorly designed heuristic can lead to suboptimal or incorrect results. Additionally, in scenarios where the graph is particularly large or intricate, the algorithm's memory and computational requirements might become demanding.

Incorporating A* into various problem-solving domains requires a nuanced understanding of graph theory, heuristics, and the specific characteristics of the problem at hand. Despite its limitations, A* remains a cornerstone algorithm, showcasing the power of combining informed decision-making with efficient exploration to find optimal solutions within the vast landscape of computational challenges.
