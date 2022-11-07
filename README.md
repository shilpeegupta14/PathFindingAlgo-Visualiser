# PathFindingAlgo-Visualiser

### How to use:
Run command:
- npm start
- npm run build 

### Discussion
BFS, DFS(Recursive & Iterative), Dijkstra, Greedy, & A* Algorithms. 
These algorithms are used to search the tree and find the shortest path from starting node to goal node in the tree.

Blind search algorithms such as breadth-first and depth-first exhaust all possibilities; starting from the given node, 
they iterate over all possible paths until they reach the goal node. These algorithms run in O(V+E), or linear time, 
where V is the number of vertices, and E is the number of edges between vertices.

However, it is not necessary to examine all possible paths. Algorithms such as Greedy, Dijkstra’s algorithm, and 
A* eliminate paths either using educated guesses(heuristics) or distance from source to node V to find the optimal path.
By eliminating impossible paths, these algorithms can achieve time complexities as low as O(E log(V)).

## Demo of Pathfinding algorithms

### Dijkstra Algorithm 
![](https://github.com/shilpeegupta14/images/blob/main/djikstra.gif)


Dijkstra’s algorithm tries to find the shortest path from the starting(root) node to every node, hence we can get 
the shortest path from the starting node to the goal.

Pseudocode: 
1. Assign dis[v] for all nodes = INT_MAX (distance from root node to every other node).
2. Assign dis[root] = 0(distance from root node to itself).
3. Add all nodes to a priority queue.
4. Loop on the queue as long as it's not empty.
   1. In every loop, choose the node with the minimum distance from the root node in the queue(root node will be selected first).
   2. Remove the current chosen node from the queue (vis[current] = true).
   3. If the current chosen node is the goal node, then return it.
   4. For every child of the current node, do the following:
       1. If child node is not already in the queue (already visited), then skip this iteration.
       2. Assign temp = dist[current] + distance from current to child node.
       3. If temp < dist[child], then, assign dist[child] = temp. This denotes a shorter path to child node has been found.
5. If queue is empty, then goal node was not found!

### A* Algorithm
![](https://github.com/shilpeegupta14/images/blob/main/astar.gif)


A* is a combination of Dijkstra and Greedy. It uses distance from the root node plus heuristics distance to the goal. 
The algorithm terminates when we find the goal node.

Pseudocode:
1. Assign dis[v] for all nodes = INT_MAX (distance from root node + heuristics of every node).
2. Assign dis[root] = 0 + heuristic(root, goal) (distance from root node to itself + heuristics).
2. Add root node to priority queue.
3. Loop on the queue as long as it's not empty.
   1. In every loop, choose the node with the minimum distance from the root node in the queue + heuristic (root node will be selected first).
   2. Remove the current chosen node from the queue (vis[current] = true).   
   3. If the current node is the goal node, then return it.
   4. For every child of the current node, do the following:
       1. Assign temp = distance(root, current) + distance(current, child) + heuristic(child, goal).
       2. If temp < dis[child], then, assign dist[child] = temp. This denotes a shorter path to child node has been found.
       3. And, add child node to the queue if not already in the queue (thus, it's now marked as not visited again).
4. If queue is empty, then goal node was not found!

### DFS Algorithm 
![](https://github.com/shilpeegupta14/images/blob/main/dfs.gif)


It starts at the root and explores one of it’s children’s sub tree, and then move to the next child’s sub tree, and so on. 
It uses stack, or recursion to perform the DFS.

Pseudocode:
Recursive
1. Mark the current node as visited(initially current node is the root node)
2. Check if current node is the goal, If so, then return it.
3. Iterate over children nodes of current node, and do the following:
    1. Check if a child node is not visited.
    2. If so, then, mark it as visited.
    3. Go to it's sub tree recursively until you find the goal node(In other words, do the same steps here passing the child node as the current node in the next recursive call).
    4. If the child node has the goal node in this sub tree, then, return it.
3. If goal node is not found, then goal node is not in the tree!

Iterative
1. Add root node to the stack.
2. Loop on the stack as long as it's not empty.
    1. Get the node at the top of the stack(current), mark it as visited, and remove it.
    2. For every non-visited child of the current node, do the following:
        1. Check if it's the goal node, If so, then return this child node.
        2. Otherwise, push it to the stack.
3. If stack is empty, then goal node was not found!



### BFS Algorithm 
![](https://github.com/shilpeegupta14/images/blob/main/bfs.gif)


It starts at the root and explores all of it’s children in the next level(neighbors) before moving to each of the root
children, and then, it explores the children of the root children, and so on. The algorithm uses a queue to perform the BFS.

Pseudocode 
1. Add root node to the queue, and mark it as visited(already explored).
2. Loop on the queue as long as it's not empty.
   1. Get and remove the node at the top of the queue(current).
   2. For every non-visited child of the current node, do the following: 
       1. Mark it as visited.
       2. Check if it's the goal node, If so, then return it.
       3. Otherwise, push it to the queue.
3. If queue is empty, then goal node was not found!
