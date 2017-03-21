# Project2_Jump-Point-Search-Algorithm
  The pathfinding algorithm is ubiquitous in videogames, so it is important to know how to apply it to the game and how to optimized. In this research I will cover the optimized method of A* pathfinding algorithm, the Jump Point Search algorithm (JPS), which can speed up A* by orders of magnitude.

Firstly, I will show you the comparision between A* algorithm and JPS algorithm, so you can figure out that JPS is way better for long distances than A*.
* A* Algorithm in Baldurs Gate 
![](https://harablog.files.wordpress.com/2011/09/bg_astar.png)
* JPS Algorithm in Baldurs Gate 
![](https://harablog.files.wordpress.com/2011/09/bg_jps.png)

You can check out the different types of pathfinding in this website: http://qiao.github.io/PathFinding.js/visual/
## Optimizations
To travel long distances, one way to optimize the A* algorithm would be to separate in zones the map and make pathfinding from one zone to another and then, inside the zone, finish the path applying the pathfinding again from the position where you have entered the zone to the destination.
Since the research is about the implementation of Jump Point search I will be more into the main theme than other optimizations.
## Algorithm
JPS can be described in terms of two simple pruning rules which are	applied recursively during search: one rule is specific to straight steps, the other for diagonal steps. The key intuition in both cases is to prune the set of immediate neighbours around a node by trying to prove that an optimal path (symmetric or otherwise) exists from the parent of the current node to each neighbour and that path does not involve visiting the current node. 
### Neighbour Pruning
![IdentifySuccessors](http://i.imgur.com/GAuaPja.png)

What this does is eliminate nodes that are not interesting to our path. For this we use the direction from the parent as the main guideline.

![](https://harablog.files.wordpress.com/2011/09/jps_natural.png)         
> Neighbour Pruning example

![](https://harablog.files.wordpress.com/2011/09/jps_forced.png)
> Forced Neighbour example
  
We apply these pruning rules during search as follows: instead of generating each natural and forced neighbour we instead recursively prune the set of neighbours around each such node. Intuitively, the objective is to eliminate symmetries by recursively “jumping over” all nodes which can be reached optimally by a path that does not visit the current node. We stop the recursion when we hit an obstacle or when we find a so-called jump point successor. 
Jump points are interesting because they have neighbours that cannot be reached by an alternative symmetric path: the optimal path must go through the current node.

![](http://i.imgur.com/57oCIRp.png)
