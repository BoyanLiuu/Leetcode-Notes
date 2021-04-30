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

### Graph Traversal:

### Graph Traversal Algorithm:



![](../.gitbook/assets/image%20%2883%29.png)

#### BFS:

* All the nodes at a certain level are traversed before moving on to the next level.
* To build a graph based on BFS, start traversing from any vertex, call it currentVertex. If the adjacent vertices are yet already not visited, then print their values. Then, move on to children of the currentVertex.
* **Using queue**

```text
    public static String bfsTraversal(Graph g, int source) {

        String result = "";
        int num_of_vertices = g.vertices;

        //Boolean Array to hold the history of visited nodes (by default-false)
        //Make a node visited whenever you enqueue it into queue
        boolean[] visited = new boolean[num_of_vertices];

        //Create Queue(Implemented in previous lesson) for Breadth First Traversal and enqueue source in it
        Queue<Integer> queue = new Queue<>(num_of_vertices);

        //add current node in to queue
        queue.enqueue(source);
        visited[source] = true;

        //Traverse while queue is not empty
        while (!queue.isEmpty()) {

            //Dequeue a vertex/node from queue and add it to result
            int current_node = queue.dequeue();

            result += String.valueOf(current_node);

            //Get adjacent vertices to the current_node from the array,
            //and if they are not already visited then enqueue them in the Queue
            DoublyLinkedList<Integer>.Node temp = null;
            if(g.adjacencyList[current_node] != null)
                temp = g.adjacencyList[current_node].headNode;
            //loop adjacent list
            while (temp != null) {

                if (!visited[temp.data]) {
                    queue.enqueue(temp.data);
                    visited[temp.data] = true; //Visit the current Node
                }
                temp = temp.nextNode;
            }
        }//end of while
        return result;
    }
```

#### DFS:

* Starting from any node, we keep moving to an adjacent node until we reach the farthest level. Then we move back to the starting point and pick another adjacent node. Once again, we probe till the farthest level and move back. This process continues until all nodes are visited.
* **Using stack**
* In the dfs\(\) function we start from the source vertex and then each node is pushed into the stack. Whenever a node is pushed into the stack, the nodes from its adjacency list are pushed into the stack as well. Then, it is marked visited in the visited list. Now we can understand why we need the stack because it keeps popping out the new adjacent nodes \(giving you a node at a new level\) instead of returning the previous nodes that we pushed in.

```text
    public static String dfsVisit(Graph g, int source, boolean[] visited) {

        String result = "";


        //Create Stack(Implemented in previous lesson) for Depth First Traversal and Push source in it
        Stack<Integer> stack = new Stack<Integer>(g.vertices);

        stack.push(source);

        //Traverse while stack is not empty
        while (!stack.isEmpty()) {

            //Pop a vertex/node from stack and add it to the result
            int current_node = stack.pop();
            result += String.valueOf(current_node);
            
            //Get adjacent vertices to the current_node from the array,
            //and if they are not already visited then push them in the stack
            DoublyLinkedList<Integer>.Node temp = null;
            if(g.adjacencyList[current_node] !=null)
                temp = g.adjacencyList[current_node].headNode;

            while (temp != null) {

                if (!visited[temp.data]) {
                    stack.push(temp.data);
                    
                }
                temp = temp.nextNode;
            }
            //Visit the node
            visited[current_node] = true;
        }//end of while
        return result;
    }
```







## Easy:

## Medium:

## Hard:

## Problem I struggle:

