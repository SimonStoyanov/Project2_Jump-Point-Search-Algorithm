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
