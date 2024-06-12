# OpenMP

OpenMP is a directive-based API for developing parallel programs on **shared memory architectures**.

## Simple Loop

```C++
#include <omp.h>
#include <stdio.h>

int main()
{
    omp_set_num_threads(3);
    #pragma omp parallel
    {
        
        int tid;
        tid = omp_get_thread_num();
        #pragma omp for
        for(int i=0;i<10;i++){
            printf("current i is %d from %d\n", i, tid);
        }
    }
}
```
Output
```
current i is 0 from 0
current i is 1 from 0
current i is 2 from 0
current i is 3 from 0
current i is 7 from 2
current i is 8 from 2
current i is 9 from 2
current i is 4 from 1
current i is 5 from 1
current i is 6 from 1
```

### Schedule

It is used to determine how to divide loop. For example, we can have block partition by this:
```C++
#include <omp.h>
#include <stdio.h>

int main()
{
    omp_set_num_threads(3);
    #pragma omp parallel
    {
        
        int tid;
        tid = omp_get_thread_num();
        #pragma omp for schedule(static,2)
        for(int i=0;i<10;i++){
            printf("current i is %d from %d\n", i, tid);
        }
    }
}
```
Output
```
current i is 0 from 0
current i is 1 from 0
current i is 6 from 0
current i is 7 from 0
current i is 2 from 1
current i is 3 from 1
current i is 8 from 1
current i is 9 from 1
current i is 4 from 2
current i is 5 from 2
```

## Synchronizaztion

There are two kinds of data depedency:
- Instruction-level
- Loop-carried 

### Critical

```C++
#include <stdio.h>
#include <omp.h>

int main() {
    int total_count = 0;
    omp_set_num_threads(3);
    #pragma omp parallel
    {
        int thread_count = 0;

        for (int i = 0; i < 1000; i++){
            thread_count++;
        }

        #pragma omp critical
        {
            total_count += thread_count;
        }
    }

    printf("Total count: %d\n", total_count);
    return 0;
}

```
Output
```
Total count: 3000
```

In this example, `critical` is used to ensure the `total_count += thread_count;` will be execute in turn.

### Atomic

The former example can be rewriten as 
```C++
#include <stdio.h>
#include <omp.h>

int main() {
    int total_count = 0;
    omp_set_num_threads(3);
    #pragma omp parallel
    {
        int thread_count = 0;

        for (int i = 0; i < 1000; i++){
            thread_count++;
        }

        #pragma omp atomic
        total_count += thread_count;
        
    }

    printf("Total count: %d\n", total_count);
    return 0;
}

```
Output
```
Total count: 3000
```

### Barrier

`barrier` explicitly provides a point that all threads must reach before proceed following code.

### Instruction-Level Data Dependency

- Flow dependency
    ```
    a=b+c
    d=a*e
    ```
- Anti-dependency
    ```
    b=a+c
    a=d*e
    ```
- Output dependency
    ```
    a=a+c
    a=d*e
    ```

### Loop-Carried Data Dependency

```C++
for(i=0;i<n;i++){
    a[i]=b[i]+e[i];
    d[i]=c*a[i+1];
}
```
As to update `d[i]`, `a[i+1]` is used, we need to ensure `a[i+1]` won't be changed until `d[i]` has been updated. Therefore, we can't directly parallelize it with OpenMP.

To eliminate the dependency, we can use two loops instead. We firstly update `d[i]` and update `a[i]` later.
```C++
#pragma omp parallel for
for(i=0;i<n;i++){
    d[i]=c*a[i+1];
}
#pragma omp parallel for
for(i=0;i<n;i++){
    a[i]=b[i]+e[i];
}
```

Given another example:
```C++
int i, j, A[MAX];
j = 5;
for (i=0; i<MAX; i++){
    j +=2;
    A[i] = big(j); 
}
```
we can't directly parallelize it because `j` is cumulative. To slove this problem, we can make connection between `j` and private value `i`.
```C++
int i, j, A[MAX];
j = 5;
for (i=0; i<MAX; i++){
    j = 5+2*(i+1);
    A[i] = big(j); 
}
```

## Reduction Operation


## Parallel beyond For Loops

### Section

```C++
#include <stdio.h>
#include <omp.h>

int main() {

    int a=1,b=10,c=100;
    int e,f,x,y,z;

    #pragma omp parallel sections 
    {
        #pragma omp section
        e=a+1;
        #pragma omp section
        f=b+10;

    }
    #pragma omp parallel sections 
    {

        #pragma omp section
        x=e*2;
        #pragma omp section
        y=f+2;
        
    }
    z=x+y;
    printf("x = %d, y = %d, z = %d",x,y,z);

    return 0;
}

```
Output
```
x = 4, y = 22, z = 26
```

### Firstprivate

It ensure the private value will be initialized in parallel code.
```C++

#include <stdio.h>
#include <omp.h>

int main()
{
    int tmp = 0;
    #pragma omp parallel for firstprivate(tmp)
    for (int i=1; i<=10; i++){
        tmp += i; 
        printf("tmp: %d\n",tmp);
    }
}
```
Output
```
tmp: 2
tmp: 9
tmp: 5
tmp: 8
tmp: 3
tmp: 10
tmp: 6
tmp: 7
tmp: 4
tmp: 1
```
### Tasks

```C++
#include <stdio.h>
#include <stdlib.h>
#include <omp.h>

// 定义链表节点结构
struct Node {
    int data;
    struct Node* next;
};

// 创建一个新节点
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

// 打印链表节点数据的任务
void processNode(struct Node* node) {
    printf("Node value: %d processed by thread %d\n", node->data, omp_get_thread_num());
}

int main() {
    // 创建链表
    struct Node* head = createNode(1);
    head->next = createNode(2);
    head->next->next = createNode(3);
    head->next->next->next = createNode(4);
    head->next->next->next->next = createNode(5);
    head->next->next->next->next->next = createNode(6);
    omp_set_num_threads(3);
    #pragma omp parallel
    {
        #pragma omp single
        {
            struct Node* current = head;
            while (current != NULL) {
                // 创建任务来处理当前节点
                #pragma omp task firstprivate(current)
                {
                    processNode(current);
                }
                current = current->next;
            }
        }
    }

    // 释放链表
    struct Node* current = head;
    while (current != NULL) {
        struct Node* next = current->next;
        free(current);
        current = next;
    }

    return 0;
}
```
Output
```
Node value: 1 processed by thread 0
Node value: 3 processed by thread 2
Node value: 5 processed by thread 2
Node value: 2 processed by thread 1
Node value: 4 processed by thread 0
Node value: 6 processed by thread 2
```