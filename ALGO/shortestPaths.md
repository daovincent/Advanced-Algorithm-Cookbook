# Shortest Paths
**Negative cycles** are **never allowed**, otherwise there would be no "shortest path"

## BFS
![Alt Text](https://cdn.discordapp.com/attachments/809911471525331026/964583168873209936/Animated_BFS.gif)
## DFS
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
## Dijkstra
Shortest path from **one** node to **all** nodes
![Alt Text](https://cdn.discordapp.com/attachments/909979010409328762/978740365374947368/Dijkstra_Animation.gif)

## Bellman-Ford

Shortest path from **one** node to **all** nodes, negative edges **allowed**

## Floyd-Warshall 

Shortest path between **all** pairs of vertices, negative edges **allowed**
