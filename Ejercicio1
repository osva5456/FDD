#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int compare(const void *a, const void *b) {
    return (*(int *)a - *(int *)b);
}

void merge(int *nums1, int m, int *nums2, int n, int *merged) {
    int i = 0, j = 0, k = 0;

    while (i < m && j < n) {
        if (nums1[i] < nums2[j]) {
            merged[k++] = nums1[i++];
        } else {
            merged[k++] = nums2[j++];
        }
    }

    while (i < m) {
        merged[k++] = nums1[i++];
    }

    while (j < n) {
        merged[k++] = nums2[j++];
    }
}

double findMedianSortedArrays(int *nums1, int m, int *nums2, int n) {
    int totalLength = m + n;
    int *merged = (int *)malloc(totalLength * sizeof(int));

    merge(nums1, m, nums2, n, merged);

    double median;
    if (totalLength % 2 == 0) {
        median = (merged[totalLength / 2 - 1] + merged[totalLength / 2]) / 2.0;
    } else {
        median = merged[totalLength / 2];
    }

    printf("Arreglo fusionado y ordenado: ");
    for (int i = 0; i < totalLength; i++) {
        printf("%d ", merged[i]);
    }
    printf("\n");

    free(merged);
    return median;
}

int main() {
    int m, n;

    printf("Ingrese el tamaño del primer arreglo: ");
    scanf("%d", &m);
    
    printf("Ingrese el tamaño del segundo arreglo: ");
    scanf("%d", &n);

    if (m < 0 || n < 0 || m + n > 2000) {
        printf("Los tamaños de los arreglos no son válidos.\n");
        return 1;
    }

    int *nums1 = (int *)malloc(m * sizeof(int));
    int *nums2 = (int *)malloc(n * sizeof(int));

    printf("Ingrese los elementos del primer arreglo: ");
    for (int i = 0; i < m; i++) {
        scanf("%d", &nums1[i]);
    }

    printf("Ingrese los elementos del segundo arreglo: ");
    for (int i = 0; i < n; i++) {
        scanf("%d", &nums2[i]);
    }

    qsort(nums1, m, sizeof(int), compare);
    qsort(nums2, n, sizeof(int), compare);

    clock_t start_time = clock();

    double median = findMedianSortedArrays(nums1, m, nums2, n);

    clock_t end_time = clock();
    
    double time_taken = ((double)(end_time - start_time)) / CLOCKS_PER_SEC;

    printf("La mediana es: %.5f\n", median);
    printf("Tiempo de ejecución: %.5f segundos\n", time_taken);

    free(nums1);
    free(nums2);

    return 0;
}

