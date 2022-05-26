# Minimum Spanning Tree

## Definitions
- Tree : a connected acyclic graph
- Spanning Tree : a undirected graph is a subset of its edges that forms a tree connecting all vertices
- The weight of a spanning tree is the sum of the weights of its edges
- A minimal spanning tree in a graph is a spanning tree of minimal weight
- Partitions are just splitting a set into subsets.

## Union & Find
### Pseudo code with Complexity
#### Arrays
```
function Init(n)
  for i = 0 . . . n − 1 do
    P[i] = i
  return P
```
Complexity : O(n)
```
function Find(x,P)
  return P[x]
```

Complexity : O(1)
```
function Union(x,y,P)
  for i = 0 . . . n − 1 do
    if P[i] == P[y] then
      P[i] = P[x]
```
Complexity : O(n)

## Prim's algorithm
TL;DR : Select starting node and then always take the edge with the smallest weight from selected nodes
### Complexity 
(Same as Dijkstra's algorithm)
- O(|V|2) is we use an **array for d** (distance)
- O(|E| log |V|) if we use a **priority queue**, because of the updates

### Pseudo code
```
function Prim(G):
  for s vertex of G do
    d[s], π[s] = +∞, ∅
  Choose a vertex s0 and set d[s0] = 0
  todo = all vertices
  T = ∅
  while todo != ∅ do
    s = Extract the element of todo that minimizes d
    if s != s0 then
      Add s − π[s] to T
    for s,w−→ t in E do
      if w < d[t] then
        d[t], π[t] = w, s
  return T
```
### Gif 
Faster gif

![Alt Text](https://im2.ezgif.com/tmp/ezgif-2-41ea185801.gif)

Longer gif with extra steps

![Alt Text](https://cdn.discordapp.com/attachments/958020328037175346/979431978086588436/ezgif-2-d4006ce8b6.gif)


## Kruskal’s algorithm
TL;DR : Select edges in increasing weight order, as long as it doesn't create a loop
### Complexity
- O(|E| log |E|) = O(|E| log |V|) for sorting (as |V| ≤ |E|²)
- O(|E| log∗|E|) for the union & find operations
So the **bottleneck** is the **sorting preprocess**, costing O(|E| log |V|)

### Pseudo code
```
function Kruskal(G):
  Sort the edges by increasing weight
  π, h = init(V)
  T = ∅
  for s − t in increasing weight order do
    if find(x,π) != find(y,π) then
      Add s − t to T
      union(x,y,π,h)
  return T
```
### Gif
![Alt Text](https://cdn.discordapp.com/attachments/958020328037175346/979438187392950312/Kruskal_Algorithm_gif.gif)
