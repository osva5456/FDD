#include <stdio.h>
#include <time.h>

unsigned long long fibonacci(int n) {
    if (n <= 1)
        return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    int n;
    clock_t start, end;
    double cpu_time_used;

    printf("Ingrese el valor máximo de n: ");
    scanf("%d", &n);

    printf("\nn\tTiempo (ms)\n");
    printf("-----------------\n");

    for (int i = 1; i <= n; i++) {
        start = clock(); 
        for (int j = 0; j < 1000; j++) { 
            fibonacci(i);
        }
        end = clock(); 

        cpu_time_used = ((double)(end - start)) / CLOCKS_PER_SEC * 1000; 
        cpu_time_used /= 1000; 

        printf("%d\t%.2f ms\n", i, cpu_time_used);
        
        if (cpu_time_used > 1000) {
            printf("El cálculo para n=%d tomó demasiado tiempo. Deteniendo.\n", i);
            break;
        }
    }

    return 0;
}
 
