# 14.Topological Sort

## Summary:

* Topological Sort is used to find a linear ordering of elements that have dependencies on each other. For example, if event ‘B’ is dependent on event ‘A’, ‘A’ comes before ‘B’ in topological ordering.

### Fundamental concepts related to topological sort:

* **Source**:  Any node that has no incoming edge and has only outgoing edges is called a source
* **Sink**:  Any node that has only incoming edges and no outgoing edge is called a sink.
* So, we can say that a topological ordering starts with one of the sources and ends at one of the sinks.
* A topological ordering is possible only when the graph has no directed cycles, i.e. if the graph is a Directed Acyclic Graph \(DAG\). If the graph has a cycle, some vertices will have cyclic dependencies which makes it impossible to find a linear ordering among vertices.
* To find the topological sort of a graph we can traverse the graph in a Breadth First Search \(BFS\) way. We will start with all the sources, and in a stepwise fashion, save all sources to a sorted list. We will then remove all sources and their edges from the graph. After the removal of the edges, we will have new sources, so we will repeat the above process until all vertices are visited

![](../.gitbook/assets/image%20%2835%29.png)

### Implementation:

1. **Time Complexity:**
   1. O\(V+E\), we visited a source only once and each edge will be accessed and removed once.
2. **Space Complexity:**
   1. O\(V+E\), Since we are storing all of the edges for each vertex in an adjacency list
3. **Initialization**
   1. We will store the graph in Adjacency Lists, which means each parent vertex will have a list containing all of its children. We will do this using a HashMap where the ‘key’ will be the parent vertex number and the value will be a List containing children vertices.
   2. To find the sources, we will keep a HashMap to count the in-degrees i.e., count of incoming edges of each vertex. Any vertex with ‘0’ in-degree will be a source.
4. **Build the graph and find in-degrees of all vertices**
   1. We will build the graph from the input and populate the in-degrees HashMap.
5.  **Find all sources**
   1. All vertices with ‘0’ in-degrees will be our sources and we will store them in a Queue.
6. **Sort:**
   1. For each source, do the following things:
      1. Add it to the sorted list.
      2. Get all of its children from the graph
      3. Decrement the in-degree of each child by 1
      4. If a child's in-degree becomes 0 add it to the sources Queue
   2. Repeat step one until the source queue is empty

```text
  public static List<Integer> sort(int vertices, int[][] edges) {
    List<Integer> sortedOrder = new ArrayList<>();
    if (vertices <= 0)
      return sortedOrder;

    // a. Initialize the graph
    HashMap<Integer, Integer> inDegree = new HashMap<>(); // count of incoming edges for every vertex
    HashMap<Integer, List<Integer>> graph = new HashMap<>(); // adjacency list graph
    for (int i = 0; i < vertices; i++) {
      inDegree.put(i, 0);
      graph.put(i, new ArrayList<Integer>());
    }

    // b. Build the graph
    for (int i = 0; i < edges.length; i++) {
      int parent = edges[i][0], child = edges[i][1];
      graph.get(parent).add(child); // put the child into it's parent's list
      inDegree.put(child, inDegree.get(child) + 1); // increment child's inDegree
    }

    // c. Find all sources i.e., all vertices with 0 in-degrees
    Queue<Integer> sources = new LinkedList<>();
    for (Map.Entry<Integer, Integer> entry : inDegree.entrySet()) {
      if (entry.getValue() == 0)
        sources.add(entry.getKey());
    }

    // d. For each source, add it to the sortedOrder and subtract one from all of its children's in-degrees
    // if a child's in-degree becomes zero, add it to the sources queue
    while (!sources.isEmpty()) {
      int vertex = sources.poll();
      sortedOrder.add(vertex);
      List<Integer> children = graph.get(vertex); // get the node's children to decrement their in-degrees
      for (int child : children) {
        inDegree.put(child, inDegree.get(child) - 1);
        if (inDegree.get(child) == 0)
          sources.add(child);
      }
    }

    if (sortedOrder.size() != vertices) // topological sort is not possible as the graph has a cycle
      return new ArrayList<>();

    return sortedOrder;
  }
```

## Easy:

## Medium:

### [207. Course Schedule](https://leetcode.com/problems/course-schedule/)

* Use exact fundamental idea of topological sort.
* \*\*\*\*[**210. Course Schedule II**](https://leetcode.com/problems/course-schedule-ii/)\*\*\*\*
* **Find it the given Directed Graph has a cycle in it or not**
  * 最后判断 我们找到的 ordered 是否包含所有的 vertices





## Hard：

### Find all the Tasks sequence:

![](../.gitbook/assets/image%20%2836%29.png)

* Use recursive approach with Backtracking to consider all sources at any step

```text
  public static void printOrders(int tasks, int[][] prerequisites) {
    List<Integer> sortedOrder = new ArrayList<>();
    if (tasks <= 0)
      return;

    // a. Initialize the graph
    HashMap<Integer, Integer> inDegree = new HashMap<>(); // count of incoming edges for every vertex
    HashMap<Integer, List<Integer>> graph = new HashMap<>(); // adjacency list graph
    for (int i = 0; i < tasks; i++) {
      inDegree.put(i, 0);
      graph.put(i, new ArrayList<Integer>());
    }

    // b. Build the graph
    for (int i = 0; i < prerequisites.length; i++) {
      int parent = prerequisites[i][0], child = prerequisites[i][1];
      graph.get(parent).add(child); // put the child into it's parent's list
      inDegree.put(child, inDegree.get(child) + 1); // increment child's inDegree
    }

    // c. Find all sources i.e., all vertices with 0 in-degrees
    Queue<Integer> sources = new LinkedList<>();
    for (Map.Entry<Integer, Integer> entry : inDegree.entrySet()) {
      if (entry.getValue() == 0)
        sources.add(entry.getKey());
    }

    printAllTopologicalSorts(graph, inDegree, sources, sortedOrder);
  }

  private static void printAllTopologicalSorts(HashMap<Integer, List<Integer>> graph,
      HashMap<Integer, Integer> inDegree, Queue<Integer> sources, List<Integer> sortedOrder) {
    if (!sources.isEmpty()) {
      for (Integer vertex : sources) {
        sortedOrder.add(vertex);
        Queue<Integer> sourcesForNextCall = cloneQueue(sources);
        // only remove the current source, all other sources should remain in the queue for the next call
        sourcesForNextCall.remove(vertex);
        List<Integer> children = graph.get(vertex); // get the node's children to decrement their in-degrees
        for (int child : children) {
          inDegree.put(child, inDegree.get(child) - 1);
          if (inDegree.get(child) == 0)
            sourcesForNextCall.add(child); // save the new source for the next call
        }

        // recursive call to print other orderings from the remaining (and new) sources
        printAllTopologicalSorts(graph, inDegree, sourcesForNextCall, sortedOrder);

        // backtrack, remove the vertex from the sorted order and put all of its children back to consider 
        // the next source instead of the current vertex
        sortedOrder.remove(vertex);
        for (int child : children)
          inDegree.put(child, inDegree.get(child) + 1);
      }
    }

    // if sortedOrder doesn't contain all tasks, either we've a cyclic dependency between tasks, or 
    // we have not processed all the tasks in this recursive call
    if (sortedOrder.size() == inDegree.size())
      System.out.println(sortedOrder);
  }

  // makes a deep copy of the queue
  private static Queue<Integer> cloneQueue(Queue<Integer> queue) {
    Queue<Integer> clone = new LinkedList<>();
    for (Integer num : queue)
      clone.add(num);
    return clone;
  }
```



### [269. Alien Dictionary](https://leetcode.com/problems/alien-dictionary/)

### [444. Sequence Reconstruction](https://leetcode.com/problems/sequence-reconstruction/)

### [310. Minimum Height Trees](https://leetcode.com/problems/minimum-height-trees/)

## The Problem I struggle:

* 207
* Find all the Tasks sequence

