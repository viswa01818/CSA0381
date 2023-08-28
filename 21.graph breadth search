#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

#define MAX_VERTICES 100

struct Queue {
    int front, rear, size;
    unsigned capacity;
    int* array;
};

struct Queue* createQueue(unsigned capacity) {
    struct Queue* queue = (struct Queue*)malloc(sizeof(struct Queue));
    queue->capacity = capacity;
    queue->front = queue->size = 0;
    queue->rear = capacity - 1;
    queue->array = (int*)malloc(queue->capacity * sizeof(int));
    return queue;
}

bool isQueueEmpty(struct Queue* queue) {
    return queue->size == 0;
}

void enqueue(struct Queue* queue, int item) {
    queue->rear = (queue->rear + 1) % queue->capacity;
    queue->array[queue->rear] = item;
    queue->size++;
}

int dequeue(struct Queue* queue) {
    if (isQueueEmpty(queue))
        return -1;
    int item = queue->array[queue->front];
    queue->front = (queue->front + 1) % queue->capacity;
    queue->size--;
    return item;
}

struct Graph {
    int V;
    int** adjMatrix;
};

struct Graph* createGraph(int vertices) {
    struct Graph* graph = (struct Graph*)malloc(sizeof(struct Graph));
    graph->V = vertices;
    graph->adjMatrix = (int**)malloc(vertices * sizeof(int*));
    for (int i = 0; i < vertices; i++) {
        graph->adjMatrix[i] = (int*)malloc(vertices * sizeof(int));
        for (int j = 0; j < vertices; j++)
            graph->adjMatrix[i][j] = 0;
    }
    return graph;
}

void addEdge(struct Graph* graph, int src, int dest) {
    graph->adjMatrix[src][dest] = 1;
    graph->adjMatrix[dest][src] = 1; // For undirected graph
}

void BFS(struct Graph* graph, int startVertex) {
    bool visited[MAX_VERTICES] = { false };
    struct Queue* queue = createQueue(graph->V);

    visited[startVertex] = true;
    enqueue(queue, startVertex);

    while (!isQueueEmpty(queue)) {
        int currentVertex = dequeue(queue);
        printf("%d ", currentVertex);

        for (int i = 0; i < graph->V; i++) {
            if (graph->adjMatrix[currentVertex][i] && !visited[i]) {
                visited[i] = true;
                enqueue(queue, i);
            }
        }
    }
}

int main() {
    int vertices = 6;
    struct Graph* graph = createGraph(vertices);

    addEdge(graph, 0, 1);
    addEdge(graph, 0, 2);
    addEdge(graph, 1, 3);
    addEdge(graph, 1, 4);
    addEdge(graph, 2, 4);
    addEdge(graph, 3, 4);
    addEdge(graph, 3, 5);
    addEdge(graph, 4, 5);

    int startVertex = 0;
    printf("Breadth First Traversal (starting from vertex %d): ", startVertex);
    BFS(graph, startVertex);
    printf("\n");

    return 0;
}
