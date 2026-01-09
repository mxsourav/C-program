#include <stdio.h>

void insertElements(float arr[], int *n) {
    int i;
    printf("Enter number of elements: ");
    scanf("%d", n);

    for (i = 0; i < *n; i++) {
        printf("Enter element %d: ", i + 1);
        scanf("%f", &arr[i]);
    }
}

void display(float arr[], int n) {
    int i;
    for (i = 0; i < n; i++) {
        printf("%.2f ", arr[i]);
    }
    printf("\n");
}

/* Insertion Sort Ascending */
void insertionAsc(float arr[], int n) {
    int i, j;
    float key;

    for (i = 1; i < n; i++) {
        key = arr[i];
        j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}

/* Insertion Sort Descending */
void insertionDesc(float arr[], int n) {
    int i, j;
    float key;

    for (i = 1; i < n; i++) {
        key = arr[i];
        j = i - 1;
        while (j >= 0 && arr[j] < key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}

/* Selection Sort Ascending */
void selectionAsc(float arr[], int n) {
    int i, j, min;
    float temp;

    for (i = 0; i < n - 1; i++) {
        min = i;
        for (j = i + 1; j < n; j++) {
            if (arr[j] < arr[min])
                min = j;
        }
        temp = arr[i];
        arr[i] = arr[min];
        arr[min] = temp;
    }
}

/* Selection Sort Descending */
void selectionDesc(float arr[], int n) {
    int i, j, max;
    float temp;

    for (i = 0; i < n - 1; i++) {
        max = i;
        for (j = i + 1; j < n; j++) {
            if (arr[j] > arr[max])
                max = j;
        }
        temp = arr[i];
        arr[i] = arr[max];
        arr[max] = temp;
    }
}

int main() {
    float arr[100];
    int n = 0;
    int choice, subChoice;

    do {
        printf("\n--- MENU ---\n");
        printf("1. Insert Elements\n");
        printf("2. Insertion Sort\n");
        printf("3. Selection Sort\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
        case 1:
            insertElements(arr, &n);
            break;

        case 2:
            printf("a. Ascending\nb. Descending\n");
            printf("Enter choice: ");
            scanf(" %c", &subChoice);

            if (subChoice == 'a') {
                insertionAsc(arr, n);
                display(arr, n);
            } else if (subChoice == 'b') {
                insertionDesc(arr, n);
                display(arr, n);
            }
            break;

        case 3:
            printf("a. Ascending\nb. Descending\n");
            printf("Enter choice: ");
            scanf(" %c", &subChoice);

            if (subChoice == 'a') {
                selectionAsc(arr, n);
                display(arr, n);
            } else if (subChoice == 'b') {
                selectionDesc(arr, n);
                display(arr, n);
            }
            break;

        case 4:
            printf("Exiting program...\n");
            break;

        default:
            printf("Invalid choice!\n");
        }

    } while (choice != 4);

    return 0;
}
