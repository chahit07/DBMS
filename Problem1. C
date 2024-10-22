#include <stdio.h>
#include <stdlib.h>

#define MAX_SIZE 100

// Function to insert an element at a given index
void insert(int arr[], int *size, int element, int index) {
    if (*size >= MAX_SIZE) {
        printf("Array is full, cannot insert element.\n");
        return;
    }

    if (index < 0 || index > *size) {
        printf("Invalid index!\n");
        return;
    }

    // Shift elements to the right to make space for the new element
    for (int i = *size; i > index; i--) {
        arr[i] = arr[i - 1];
    }
    arr[index] = element;
    (*size)++;
    printf("Inserted %d at index %d.\n", element, index);
}

// Function to delete an element at a given index
void delete(int arr[], int *size, int index) {
    if (*size <= 0) {
        printf("Array is empty, cannot delete element.\n");
        return;
    }

    if (index < 0 || index >= *size) {
        printf("Invalid index!\n");
        return;
    }

    // Shift elements to the left to fill the gap
    for (int i = index; i < *size - 1; i++) {
        arr[i] = arr[i + 1];
    }
    (*size)--;
    printf("Deleted element at index %d.\n", index);
}

// Function to search for an element by value and return its index
int search(int arr[], int size, int element) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == element) {
            return i;  // Return the index of the element
        }
    }
    return -1;  // Element not found
}

// Function to display the array
void display(int arr[], int size) {
    if (size == 0) {
        printf("Array is empty.\n");
        return;
    }

    printf("Array elements: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[MAX_SIZE];
    int size = 0;  // Initial size of the array
    int choice, element, index;

    while (1) {
        printf("\nArray Indexing Operations:\n");
        printf("1. Insert\n");
        printf("2. Delete\n");
        printf("3. Search\n");
        printf("4. Display\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter element to insert: ");
                scanf("%d", &element);
                printf("Enter index to insert at: ");
                scanf("%d", &index);
                insert(arr, &size, element, index);
                break;

            case 2:
                printf("Enter index to delete element from: ");
                scanf("%d", &index);
                delete(arr, &size, index);
                break;

            case 3:
                printf("Enter element to search: ");
                scanf("%d", &element);
                index = search(arr, size, element);
                if (index == -1) {
                    printf("Element not found.\n");
                } else {
                    printf("Element %d found at index %d.\n", element, index);
                }
                break;

            case 4:
                display(arr, size);
                break;

            case 5:
                printf("Exiting...\n");
                exit(0);

            default:
                printf("Invalid choice, please try again.\n");
        }
    }

    return 0;
}
