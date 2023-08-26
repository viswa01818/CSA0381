#include <stdio.h>

#define TABLE_SIZE 10

int hashTable[TABLE_SIZE];

void initializeHashTable() {
    for (int i = 0; i < TABLE_SIZE; i++) {
        hashTable[i] = -1;
    }
}

int hashFunction(int key) {
    return key % TABLE_SIZE;
}

void insert(int key, int value) {
    int hashIndex = hashFunction(key);
    
    while (hashTable[hashIndex] != -1) {
        hashIndex = (hashIndex + 1) % TABLE_SIZE;
    }
    
    hashTable[hashIndex] = value;
}

int search(int key) {
    int hashIndex = hashFunction(key);
    
    while (hashTable[hashIndex] != -1) {
        if (hashTable[hashIndex] == key) {
            return hashTable[hashIndex];
        }
        hashIndex = (hashIndex + 1) % TABLE_SIZE;
    }
    
    return -1;
}

int main() {
    initializeHashTable();

    insert(5, 50);
    insert(15, 150);
    insert(25, 250);
    insert(8, 80);

    printf("Value for key 15: %d\n", search(15));
    printf("Value for key 8: %d\n", search(8));
    printf("Value for key 5: %d\n", search(5));
    printf("Value for key 25: %d\n", search(25));
    printf("Value for key 10: %d\n", search(10));

    return 0;
}
