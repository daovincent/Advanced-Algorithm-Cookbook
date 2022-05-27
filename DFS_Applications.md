DFS Application
---

Table of Contents
---
- [Topological sorting](#topological-sorting)
  - [Ieiunium explicandum (Quick explanation)](#ieiunium-explicandum-quick-explanation)
    - [Complexity](#complexity)
    - [Explanation x Pseudo Code](#explanation-x-pseudo-code)
  - [Pure pseudo code](#pure-pseudo-code)


# Topological sorting
Find a dependency order in a graph, to do so we will have to use a timed DFS
## Ieiunium explicandum (Quick explanation)
### Complexity
```
Over all complexity for matrices -> O(|V|^3)
Over all complexity for lists -> O(|V|+|E|)
```
### Explanation x Pseudo Code
```
|RECURSIVE FUNCTION| params (L,v,G,s)
I- set the vertex [s] to true in the visited [v] list 
II- loop through all successors [t] of the vertex [s] in the graph [G]
    |- if the current vertex [t] is not visited
    	|- call the RECURSIVE FUNCTION again
III- add the the vertex [s] at the begging of  the order list [L]    
|GLOBAL FUNCTION| (G)
I- from 0 to the number of vertices perpare a list called visited [v] and set all the values to false
II- prepare an empty list [L] (this will contain the order)
III- loop through all the vertices of the Graph [for s in vertices of G]
   |- if the current vertex is not visited 
      |- call the RECURSIVE FUNCTION
IV- return L 
```
## Pure pseudo code
```
TopoRec(L,v,G,s):
 v[s] = true
 for t successors of s in G:
   if !v[t]:
     TopoRec(L,v,G,s)
 add s to the begging of T


TopoWarpper(G):
  for s vertex in G:
   v[s]= false
  L = []
  for s vertex in G:
   if !v[s]:
    TopoRec(L,v,G,s) 
return L	

```

