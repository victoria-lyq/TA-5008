# TA-5008-HW10-resolution

Here is a recursive algorithm for visiting all the nodes of a graph. Many of you implemented the traversal through looping through the graph's dll from its head to tail. In this example, we not only visited all nodes in a graph, but also iteratively transitions from the current node to an adjacent, unvisited node, until it can no longer find an unexplored node to transition to from its current location. 


To avoid inifite loop, we introduce a int visited field in our graph_node_t struct to keep track of each node that has been visted. 
At create_graph_node method, you will need to set a default value for unvisited node. Let's assume visited = 0 if the current node is never visited
```
typedef struct graph_node{
    int visited; 
    int data;
    dll_t* inNeighbors;
    dll_t* outNeighbors;
} graph_node_t;
```


Here is an example what you can achieve in dfs. In this case, we print out every node in path. Notice that currNode is the starting node of dfs traversal.
```
void dfs_helper(graph_t* g, graph_node_t* currNode){
    currNode->visited = 1;
    printf("%d ", currNode->data);      
    node_t* currOutNeighbor = currNode->outNeighbors->head;
    while (currOutNeighbor != NULL) {
        graph_node_t* outNeighborGraphNode = currOutNeighbor->data;
        if (outNeighborGraphNode->visited = 0){
            dfs_helper(g, outNeighborGraphNode);
        }
        currOutNeighbor = currOutNeighbor -> next;
    }
}
```