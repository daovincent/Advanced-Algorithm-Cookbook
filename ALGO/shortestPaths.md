# Shortest Paths
 **Negative cycles** are **never allowed**, otherwise there would be no "shortest path"

# Table of Contents
1. [Definitions](#Definitions)
2. [DFS](#DFS)
3. [BFS](#BFS)
4. [Bellman-Ford](#Bellman-Ford)
5. [Floyd-Warshall](#Floyd-Warshall)

## Definitions
- Backward edges are the one linking a vertex to one of its ancestor (or itself) in the forest

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

## Dijkstra
Shortest path from **one** node to **all** nodes
![Alt Text](https://cdn.discordapp.com/attachments/909979010409328762/978740365374947368/Dijkstra_Animation.gif)

## Bellman-Ford

Shortest path from **one** node to **all** nodes, negative edges **allowed**

## Floyd-Warshall 

Shortest path between **all** pairs of vertices, negative edges **allowed**
