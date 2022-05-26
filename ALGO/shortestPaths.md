# Shortest Paths
 **Negative cycles** are **never allowed**, otherwise there would be no "shortest path"

# Table of Contents
1. [Definitions](#Definitions)
2. [DFS](#DFS)
3. [BFS](#BFS)
4. [Bellman-Ford](#Bellman-Ford)
5. [Floyd-Warshall](#Floyd-Warshall)

## Definitions
- Path : a sequence of edges, where each end vertex of an edge is the starting edge of the next one
- Circuit : a path that begins and ends at the same vertex.
- Backward edges are the one linking a vertex to one of its ancestor (or itself) in the forest
- The strongly connected component (SCC) of a given vertex s is the set of vertices Cs that contains all the vertices such that there is a path from s to t, and a path from t to s.


## DFS ( Depth-first search Algorithm )
![Alt Text](https://cdn.discordapp.com/attachments/909979010409328762/978739577386856468/Depth-First-Search.gif)
### Complexity 
n = number of nodes / vertex / sommets

e = number of edges 
- Tree : O ( n ) 
- Matrix : O ( n²)
- Adjacency list : O ( n + e )

### Pseudo code
```
function RecDFS(G,s,Visited)
  Visited[s] = True
  for t successor of s do
    if not Visited[t] then
      RecDFS (G, t,Visited)

function DFS(G)
  for s vertex of G do
  Visited[s] = False
  for s vertex of G do
    if not Visited[s] then
      RecDFS(G,s,Visited)
```
#### DFS Variants 
Same algorythm, same complexity

##### Color DFS : 
- Set 3 colors ( states ) for each vertes such as : Not visited / During visit / Visited
- All vertex are initialized as "Not visited"
- First line of the recursive function : set vertex as "During visit"
- Last line of the recursive function : set vertex as "Visited"
- Before the recursive call in recursive function : if During visit → edge is backwards edge

##### Time DFS : 
- Set a counter at the start of the function
- Each vertex has a "start" and an "end" for the time of the visit
- At start of the recursive function : Start of vertex = counter then increment counter
- At the end of the recursive function : End of vertex = counter then increment counter
- Before the recursive call in the recursive function : check if start of the target node is not set in order to call the recursive function
- If before recursive call, target Start of target node is set but not End of target node, then it is a backwards edge

## BFS ( Breadth-First Search Algorithm )
![Alt Text](https://cdn.discordapp.com/attachments/809911471525331026/964583168873209936/Animated_BFS.gif)

### Complexity 
- Matrix : O ( n²)
- Adjacency list : O ( n + e )

### Pseudo code
```
function BFS(G, s0)
  for s vertex of G do
    d[s] = +∞
  d[s0] = 0
  todo = Queue(s0)
  while todo 6= ∅ do
    s = Dequeue(todo)
    for t successor of s do
      if d[t] == +∞ then
        d[t] = d[s] + 1
        Enqueue(todo, t)
  return d
```
- This algorithm computes the shortest weights (=distance)
- d[s] is +∞ while s is not visited
- when d[s] takes a value, it is the weight from s0 to s

In order to get the shortest path : 

# Dijkstra

Shortest path from one node to all nodes (Negative nodes are not allowed)

## Ieiunium explicandum (Quick explanation)
### Complexity 
```
initialization -> O(|V|)
the updates cost -> O(|E|)
Minimum extraction :
 array -> O(|V^2|)
 heap -> O(|E|log|V|)
```
### Explanation x Pseudo Code
```
I- prepare a list of that contain distance [d] to some vertex to [-∞]
II- perpare a list of predecessors [π] to ∅
III- pick a starting vertex [s0] and set it distnace to 0 [d[s0] = 0]
IV- prepare a list called todo that contains all the vertices [Todo=[all vertices]]
V- while [Todo] is not empty 
  |a- [s]find the element in [Todo] that minimise the distance[d] and remove it from [Todo] 
  |b- loop throught the edges of s  [s -(w)-> t] in the graph[G]
      |-if the sum of the distance on [s] and the current weight[w] is less than the distance on [t]
      |- assign the distance of t to the the sum[d[t] = d[s]+w] and the predecessor of [t] to [s]  [π[t] = s]
VII- return π,d       
```
### Pure Pseudo Code 
```
Dijktra(G,s0) :
 for v in vertices of G :	
   d[v] = -∞
   π[v] = ∅
 Todo = [all vertices of G]
 While Todo !=  ∅ :
  s = extract element that minimise d in Todo
  for s-(w)->t in Edgs of s:
   if d[s]+w < d[t]:
     d[t] = d[s]+w
     π[t] = t
return π, d    	    
```
### Gif
![Alt Text](https://cdn.discordapp.com/attachments/909979010409328762/978740365374947368/Dijkstra_Animation.gif)

## Bellman-Ford

Shortest path from **one** node to **all** nodes, negative edges **allowed**
![Alt_Text](https://cdn.discordapp.com/attachments/763805435140505660/979412723232305162/output-onlinegiftools.gif)

## Floyd-Warshall 

Shortest path between **all** pairs of vertices, negative edges **allowed**
