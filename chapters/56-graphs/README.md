# 56. Graphs

## Representations
Adjacency matrix uses O(V²) storage and O(1) edge lookup. Adjacency lists use O(V+E) storage and are efficient for sparse graphs.

## BFS example with adjacency matrix
~~~c
#include <stdio.h>
#define V 5

void bfs(int g[V][V], int start){
    int q[V],front=0,rear=0,seen[V]={0};
    q[rear++]=start;seen[start]=1;
    while(front<rear){
        int u=q[front++];printf("%d ",u);
        for(int v=0;v<V;v++)
            if(g[u][v]&&!seen[v]){seen[v]=1;q[rear++]=v;}
    }
}
int main(void){
    int g[V][V]={{0,1,1,0,0},{1,0,0,1,0},{1,0,0,0,1},{0,1,0,0,1},{0,0,1,1,0}};
    bfs(g,0);putchar('\n');
}
~~~

## Major algorithms
BFS/DFS: O(V+E) with adjacency lists. Dijkstra handles non-negative edge weights. Bellman-Ford permits negative edges and detects reachable negative cycles. Floyd-Warshall solves all-pairs shortest paths in O(V³). Kruskal and Prim solve minimum spanning tree problems under their respective graph assumptions. Topological sorting applies to DAGs.

## Common mistakes
Confusing directed and undirected edges, forgetting disconnected components, revisiting nodes without a visited set, and applying Dijkstra to negative-weight edges.

## Practice
Implement DFS, connected components, cycle detection, topological sort, Dijkstra, Bellman-Ford, Kruskal, and Prim.