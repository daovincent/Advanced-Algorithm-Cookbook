# Minimum Spanning Tree

## Definitions
- Tree : a connected acyclic graph
- Spanning Tree : a undirected graph is a subset of its edges that forms a tree connecting all vertices
- The weight of a spanning tree is the sum of the weights of its edges
- A minimal spanning tree in a graph is a spanning tree of minimal weight

## Prim's algorithm

### Complexity 
- O(|V|2) is we use an array for d (distance)
- O(|E| log |V|) if we use a priority queue, because of the updates

### Pseudo code
```
function Prim(G)
  for s vertex of G do
    d[s], π[s] = +∞, ∅
  Choose a vertex s0 and set d[s0] = 0
  todo = all vertices
  T = ∅
  while todo 6= ∅ do
    s = Extract the element of todo that minimizes d
    if s 6= s0 then
      Add s − π[s] to T
    for sw−→ t in E do
      if w < d[t] then
        d[t], π[t] = w, s
  return T
```
