#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

#define MAX_STACK_SIZE 100

typedef struct {
    int data[MAX_STACK_SIZE];
    int top;
} Stack;

void initializeStack(Stack *stack) {
    stack->top = -1;
}

int isEmpty(Stack *stack) {
    return stack->top == -1;
}

int isFull(Stack *stack) {
    return stack->top == MAX_STACK_SIZE - 1;
}

void push(Stack *stack, int value) {
    if (isFull(stack)) {
        printf("Stack overflow!\n");
        return;
    }
    stack->data[++stack->top] = value;
}

int pop(Stack *stack) {
    if (isEmpty(stack)) {
        printf("Stack underflow!\n");
        return -1;
    }
    return stack->data[stack->top--];
}

int evaluatePostfix(char postfix[]) {
    Stack stack;
    initializeStack(&stack);

    for (int i = 0; postfix[i] != '\0'; i++) {
        char ch = postfix[i];
        if (isdigit(ch)) {
            push(&stack, ch - '0');
        } else {
            int operand2 = pop(&stack);
            int operand1 = pop(&stack);
            
            switch(ch) {
                case '+':
                    push(&stack, operand1 + operand2);
                    break;
                case '-':
                    push(&stack, operand1 - operand2);
                    break;
                case '*':
                    push(&stack, operand1 * operand2);
                    break;
                case '/':
                    push(&stack, operand1 / operand2);
                    break;
                default:
                    printf("Invalid operator: %c\n", ch);
                    return -1;
            }
        }
    }
    return pop(&stack);
}

int main() {
    char postfixExpression[] = "53*82/+";
    int result = evaluatePostfix(postfixExpression);
    
    if (result != -1) {
        printf("Result of postfix expression %s is: %d\n", postfixExpression, result);
    }

    return 0;
}
