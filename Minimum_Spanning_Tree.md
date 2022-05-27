Minimum Spanning Tree
---

Table of Contents
---
- [Minimum Spanning Tree](#minimum-spanning-tree)
- [Table of Contents](#table-of-contents)
- [Definitions](#definitions)
- [Union & Find](#union--find)
      - [Find](#find)
      - [Union](#union)
  - [Pseudo code with Complexity](#pseudo-code-with-complexity)
    - [Arrays](#arrays)
    - [Trees](#trees)
    - [Balanced Trees](#balanced-trees)
- [Prim's algorithm](#prims-algorithm)
  - [Complexity](#complexity)
  - [Pseudo code](#pseudo-code)
  - [Gif](#gif)
- [Kruskal’s algorithm](#kruskals-algorithm)
  - [Complexity](#complexity-1)
  - [Pseudo code](#pseudo-code-1)
  - [Gif](#gif-1)

## Definitions
- Tree : a connected acyclic graph
- Spanning Tree : a undirected graph is a subset of its edges that forms a tree connecting all vertices
- The weight of a spanning tree is the sum of the weights of its edges
- A minimal spanning tree in a graph is a spanning tree of minimal weight
- Partitions are just splitting a set into subsets.

## Union & Find
The purpose of the Union & Find structure is to efficiently represent a partition.

In other words, we have a set of elements that we want to assemble in order to get groups of elements. We also want to be able to determine which element belongs in which group.
##### Find
Find lets us "find" out the group an element belongs to, which is represented by one of it's elements, kind of like a leader (root of a tree for example).

This is also used to "compact" the whole "branch" of a tree, so further calculations will be more efficient.
##### Union 
This is the operation that lets us fuse two groupe together. Its purpose is also to make sure trees remain as shallow as possible (deep trees = longer computing time for most algorithms).

That is why when fusing trees with Union, the smaller tree is put under the bigger one.

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

#### Trees 
```
function Find(x,π)
  if π[x] == x then
    return x
  return Find (π[x], π)
```
Complexity : O(height)
```
function Union(x,y,π)
  idx = Find(x, π)
  idy = Find(y, π)
  π[idx] = idy
```
Complexity: O(height)

#### Balanced Trees
Init : Same as tree but with height parameter </br>
Find : Same as Tree but Complexity: O(t log n) without compression and  O(t × log∗n) with commpression</br>
Union : Complexity change depending on the used Find function if the find do height compressionit will be  O(t × log∗n)</br> ortherwise O(t log n)

The find can be changed to compress the height here how it's done 
```
functin Find(x,π)
  if x== π[x]
    return x
  π[x] = Find(x,π)
  return π[x]
```
```
function Union(x,y,π,h)
  idx = Find(x, π)
  idy = Find(y, π)
  if h[idx] ≤ h[idy] then
    π[idx] = idy
    if h[idx] == h[idy] then
      h[idy] + +
  else
    π[idy] = idx
```

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
