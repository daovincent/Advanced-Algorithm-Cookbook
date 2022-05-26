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
  while todo != ∅ do
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
- Initialise an array of predecesors (all null at first)
- In the "If" before the Enqueue, predecessor of [t] is s

# Dijkstra

Shortest path from one node to all nodes (negative nodes are not **allowed**)

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

# Bellman-Ford
Shortest path from **one** node to **all** nodes, (negative edges **allowed**)
## Ieiunium explicandum (Quick explanation)
### Complexity
```
Over all complexity for matrices ->  O(|V|^3)
Over all complexity for listss -> O(|V|x|E|)

```
### Explanation x Pseudo Code
```
I- loop through all vertices of G and prepare a list that contain the distance[d] to every vertex to[-∞] 
and a list that containit predecessors [π] to ∅
II- set the distance of the starting vertex to 0 [d[s0]=0]
III- loop from 1 to vertices-1
   |a- loop through all edges x to y [x-(w)->y ] of the graph[G]
     |-if the the sum of the distance of x[d[x]] and the weight[w] of the edge is less than the the distance of y[d[y]]
       |-assign the distance of y to the sum of the distance of x and the weight of the edge [d[y]=d[x]+w] 
       |-assign the predecessor of y to x [π[y]=x]
IV- return π, d   
```
### Pure pseudo Code
BellManFord(G,s0)
  for v vertices in G
    d[v] = -∞
    π[v] = ∅ 
  d[s0] = 0
  loop from 1 to nBVertices-1
   loop x-(w)->y edges of G;
    if d[x]+w < d[y]
      d[y] = d[x]+w
      π[y] = s
return π, d
### Gif
![Alt_Text](https://cdn.discordapp.com/attachments/763805435140505660/979412723232305162/output-onlinegiftools.gif)

# Floyd-Warshall
Shortest path from one node to all nodes, (negative edges **allowed**)

## Ieiunium explicandum (Quick explanation)
### Complexity
```
Initialization -> O(|V|^2)
Over all complexity -> O(|V|^3)
``` 
### Explanation x Pseudo Code
```
I- double loop(s,t) through the vertices of G and  prepare a 2d list of that contain  distances [s,t] if [s == t] 
the distance is 0 else [-∞] and perpare a 2d list of predecessors [π] to ∅
II- for edges from s to t [s-(w)->] in G if s is diffrent than t than the distance [s, t] is equal to the weight (w)
and predecessor of s,t is s [π] 
III- loop from k to the number of verticies-1  
   |a- double loop(s,t) and 
      |- if the distance froom s to t is bigger than the distance from s to k + k to t [d[s,t] > d[s,k] + d[k,t] 
	|- assign the distance from s to t to the sum of s to k and k to t [d[s,t]=d[s,k]+d[k,t]]
	|- assign the predecessor of s to t [π[s,t]] to the predecessor of k to t [π[k,t]] 
IV- return π,d
```
### Pure pseudo code 
```
FloydWarshall(G):
  for s,t vertices of G do 
   if s == t:
     d[s,t] = 0
   else:
    d[s,t] = -∞
   π[s,t] = ∅ 
  for s-(w)->t edges of G:
   if s!=t:
     d[s,t] = w
     π[s,t] = s
  for k from 0 to vertices-1
    for s,t to vertices-1
     if d[s,t] > d[s,k] + d[k,t]:
        d[s,t] d[s,k] + d[k,t]
	π[s,t] = π[k,t]
return π,d
```
### Gif
A gif is pointless for this algo just check this video 
[video Link](https://www.youtube.com/watch?v=4OQeCuLYj-4)

