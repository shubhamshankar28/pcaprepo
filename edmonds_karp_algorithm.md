### Topic name -  
Flows

### Sub-topic - put the sub-topic name here
Edmonds-Karp algorithm
<br>

### Definition
#### norep
<br>

1. Edmonds-Karp algorithm is one of the ways of implementing the Ford-Fulkerson Algorithm.
2. In particular the Edmonds-Karp algorithm uses breadth first search to compute the augmenting path.
3. Hence if there are multiple augmenting paths the path with smallest length is selected.
4. This way of choosing the augmenting path effectively leads to the computation of the shortest path in O(V*E*E) time.

 
```
EdmondKarp( n, SourceNode, DestinationNode, AdjacencyMatrix, CapacityMatrix)
    MaxFlow = 0
    ResidualMatrix[n][n] = CapacityMatrix[n][n]
    // We  initialize the ResidualMatrix to the CapacityMatrix
    minflow = 0
    AugmentingPath = []
    while true:
        bfs(CapacityMatrix , AdjacencyMatrix, SourceNode, TargetNode , ResidualMatrix. minflow, AugmentingPath )
        if(minflow == 0):
            break  
        for each edge(u,v) in AugmentingPath:
            ResidualMatrix[u][v] = ResidualMatrix - minflow
            ResidualMatrix[v][u] = ResidualMatrix + minflow
        Maxflow = Maxflow + minflow
        AugmentingPath = []
        minflow = 0
        //Remove the entries already stored in the AugmentingPath  
    return MaxFlow
```
#### Explanation
1. We begin by initializing the Maxflow and ResidualMatrix variables.
2. At each iteration we will be using the minflow and AugmentingPath variables so these are also initialized
3. At each iteration we are calling the bfs() function. We pass AdjacencyMatrix, SourceNode, TargetNode, ResidualMatrix as parameters. In addition to this minflow
and AugmentingPath are also passed. The bfs() function stores the appropriate path in the AugmentingPath variable, it also stores the minimum flow value along this
path in the minflow variable. Note that we are passing all the values by reference here so changes made in the bfs() function will be reflected in the EdmondKarp
function
4. After this we iterate along the edges in the AugmentingPath and subtract minflow from the forward edge and add minflow to the backward edges, the value of MaxFlow
is incremented.
5. The minflow and AugmentingPath variables are set to their initial values so that they can be safely used in the next iteration
6. At the end we simply return the MaxFlow value.




### Explanation (along with examples)

<br>

### Application(Only 1)
#### *A Medium level question or application along with the approach to solve the same and the pseudocode should be given here. Kindly remove this line before creating a PR

<br>
