#include <stdio.h>

int main() {
    int n;
    printf("Enter the number of terms in the Fibonacci series: ");
    scanf("%d", &n);

    int firstTerm = 0, secondTerm = 1;
    int nextTerm;

    printf("Fibonacci Series: %d, %d, ", firstTerm, secondTerm);

    for (int i = 2; i < n; i++) {
        nextTerm = firstTerm + secondTerm;
        printf("%d, ", nextTerm);

        // Update firstTerm and secondTerm for the next iteration
        firstTerm = secondTerm;
        secondTerm = nextTerm;
    }

    printf("\n");
    return 0;
}
