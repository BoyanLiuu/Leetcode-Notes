# Graphs

## Summary:

### Basic:

* Type of Graphs:
  * Undirected
  * Directed
* Degree of Vertex: The total number of edges connected to a vertex. ![](../.gitbook/assets/image%20%2877%29.png) 
  * Degree of 5 = 3
  * Degree of 1  = 2
  * Degree of 6 =1
* Parallel Edges:  Two or more edges that are incident to the same two vertices. ![](../.gitbook/assets/image%20%2876%29.png) 



### Graph Implementation: 

#### Adjacency Matrix:

* The adjacency matrix is a two-dimensional matrix where each cell can contain a 0 or 1. The row and column headings represent the vertices.
* If a cell contains 1, there exists an edge between the corresponding vertices, e.g., Matrix\[0\]\[1\]=1 shows that an edge exists between vertex 0 and 1.

![](../.gitbook/assets/image%20%2872%29.png)

#### Adjacency List:

* An array of Linked Lists is used to store edges between two vertices. The size of the array is equal to the number of vertices. Each index in this array represents a specific vertex in the graph. The entry at the index i of the array contains a linked list containing the vertices that are adjacent to vertex i.

![](../.gitbook/assets/image%20%2874%29.png)

### Complexity of Graph  Operation:

![](../.gitbook/assets/image%20%2881%29.png)

#### Adjacency List: 

* The addition of edge in adjacency lists take constant time, as we only need to insert at the tail in the doubly-linked list with a tail pointer of the corresponding vertex.
* The addition of a vertex is not constant in the worst case. The adjacency list is an array of linked lists. So, we would need to allocate a bigger array, copy the contents from the previous array, which takes O\(n\). But this operation can be considered O\(1\) on average because we could do it smartly as follows. We start with a small array initially. Then, when there is a need to insert a vertex, instead of allocating one size bigger array, we allocate an array that is twice as big. That way, in the long run, the cost of re-allocation is averaged out over many other operations. So, O\(1\) is the average or amortized cost of add vertex in the adjacency list
* Removing an edge takes O\(E\) time because–in the worst case–all the edges could be at a single vertex, and hence, we would have to traverse all E edges to reach the last one.
* Removing a vertex takes O\(V + E\) time because we have to delete all its edges, and then reindex the rest of the list one step back in order to fill the deleted spot.

#### Adjacency Matrix: 

* Edge operations are performed in constant time, as we only need to manipulate the value in the particular cell.
* Vertex operations are performed in O\(V^2\) since we need to add rows and columns. We will also need to fill all the new cells.

#### Comparison:

* If your model frequently manipulates vertices, the adjacency list is a better choice
* If you are dealing primarily with edges, the adjacency matrix is the more efficient approach.

### What is Bipartite Graph:

It is  a special kind of Graph, in which the vertices can be divided into two disjoint sets U and V such that no vertex of U is adjacent to any other vertex in U and no vertex of V is adjacent to any other vertex in V. Vertices in U have edges that connect it to vertices in V.

![](../.gitbook/assets/image%20%2878%29.png)

* All the cycle graphs, a closed chain, that have  at least 3 number of vertices are bipartite
* A cycle graph can be Bi-partite with even vertices  

![](../.gitbook/assets/image%20%2873%29.png)

* A graph cannot be Bipartite if there are an odd number of vertices and has an odd cycle i.e., a cycle between the odd number of vertices.



## Easy:

## Medium:

## Hard:

## Problem I struggle:

