# test_5_17
#include <stdio.h>
#define Maxvertexnum 100
typedef struct{
	char ver[Maxvertexnum];
	int Edge[Maxvertexnum];
	int vexnum,arcnum;
}MGraph;
//图的遍历
//广度优先遍历(BFS)
bool visited[MAX_VERTEX_NUM];//标记访问数组
//辅助队列实现（应对非连通图）
void BFSTraverse(Graph G){
	for(int i=0;i<G.vexnum;++i)
		visited[i] = FALSE;
	InitQueue(Q);
	for(int i=0;i<G.vexnum;++i){
		if(!visited[i])
			BFS(G,i);
	}
}

void BFS(Graph G,int v){
	visit(v);
	visited(v) = TRUE;
	EnQueue(Q,v);
	while(!IsEmpty(Q))
	{
		DeQueue(Q,V);
		for(int w=FirstNeighbor(G,v);w>=0;w=NextNeighbor(G,v,w))
		{
			if(!visited[w])
			{
				visit(w);
				visited[w] = TRUE;
				EnQueue(Q,w);
			}
		}
	}
}
//深度优先遍历(DFS)
bool visited[MAX_VERTEX_NUM];
//函数调用栈（应对非连通图）
void DFSTraverse(Graph G){
	for(int v=0;v<G.vexnum;++v)
		visited[v] = FALSE;
	for(int v=0;v<G.vexnum;++v){
		if(!visited[v])
			DFS(G,v);
	}
}

void DFS(Graph G,int v){
	visit(v);
	visited[v] = TRUE;
	for(int w=FirstNeighbor(G,v);w>=0;w=NextNeighbor(G,v,w))
	{
		if(!visited[w]){
			DFS(G,w);
		}
	}
}
void BFS_MTN_Distance(Graph G,int u){
	for(int i=0;i<G.vexnum;++i){
		d[i] = *;
		path[i] = -1;
	}
	d[u] = 0;
	visited[u] = TRUE;
	EnQueue(Q,u);
	while(!IsEmpty(Q))
	{
		DeQueue(Q,u);
		for(int w=FirstNeighbor(G,u),w>=0;w=NextNeighbor(G,u,w))
		{
			if(!visited[w])
			{
				d[w] = d[u] + 1;
				path[w] = u;
				visited[w] = TRUE;
				EnQueue(Q,w);
			}
		}
	}
}
