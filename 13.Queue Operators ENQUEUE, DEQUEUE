#include <stdio.h>
#include <stdlib.h>

#define MAX_QUEUE_SIZE 100

typedef struct {
    int data[MAX_QUEUE_SIZE];
    int front, rear;
} Queue;

void initializeQueue(Queue *queue) {
    queue->front = -1;
    queue->rear = -1;
}

int isEmpty(Queue *queue) {
    return queue->front == -1;
}

int isFull(Queue *queue) {
    return (queue->rear + 1) % MAX_QUEUE_SIZE == queue->front;
}

void enqueue(Queue *queue, int value) {
    if (isFull(queue)) {
        printf("Queue is full, cannot enqueue!\n");
        return;
    }

    if (isEmpty(queue)) {
        queue->front = 0;
    }

    queue->rear = (queue->rear + 1) % MAX_QUEUE_SIZE;
    queue->data[queue->rear] = value;
}

int dequeue(Queue *queue) {
    if (isEmpty(queue)) {
        printf("Queue is empty, cannot dequeue!\n");
        return -1;
    }

    int value = queue->data[queue->front];

    if (queue->front == queue->rear) {
        queue->front = -1;
        queue->rear = -1;
    } else {
        queue->front = (queue->front + 1) % MAX_QUEUE_SIZE;
    }

    return value;
}

void displayQueue(Queue *queue) {
    if (isEmpty(queue)) {
        printf("Queue is empty!\n");
        return;
    }

    int index = queue->front;

    while (index != queue->rear) {
        printf("%d ", queue->data[index]);
        index = (index + 1) % MAX_QUEUE_SIZE;
    }

    printf("%d\n", queue->data[index]);
}

int main() {
    Queue queue;
    initializeQueue(&queue);

    enqueue(&queue, 10);
    enqueue(&queue, 20);
    enqueue(&queue, 30);

    printf("Queue elements: ");
    displayQueue(&queue);

    int dequeuedValue = dequeue(&queue);
    if (dequeuedValue != -1) {
        printf("Dequeued element: %d\n", dequeuedValue);
    }

    printf("Queue elements after dequeue: ");
    displayQueue(&queue);

    return 0;
}
