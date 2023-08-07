在C语言中，`malloc()`函数用于动态分配内存空间。它的原型如下：

```c
void* malloc(size_t size);
```

`malloc()`函数接受一个`size_t`类型的参数，表示需要分配的内存空间大小（以字节为单位）。它会返回一个指向分配的内存空间的指针，或者返回`NULL`表示分配失败。

下面是一个使用`malloc()`函数的例子：

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int* numbers;
    int size;

    printf("请输入数组大小：");
    scanf("%d", &size);

    // 使用malloc动态分配内存
    numbers = (int*)malloc(size * sizeof(int));

    if (numbers == NULL) {
        printf("内存分配失败\n");
        return 1;
    }

    printf("请输入%d个整数：\n", size);
    for (int i = 0; i < size; i++) {
        scanf("%d", &numbers[i]);
    }

    printf("你输入的数组是：\n");
    for (int i = 0; i < size; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");

    // 释放动态分配的内存
    free(numbers);

    return 0;
}
```

在上述例子中，我们首先使用`malloc()`函数动态分配了一个整型数组所需的内存空间，然后通过`sizeof(int)`计算每个整数占用的字节数，并将其与数组大小相乘，以得到需要分配的总字节数。如果内存分配成功，`malloc()`函数将返回一个指向分配的内存空间的指针，我们将其赋值给`numbers`变量。

在使用完动态分配的内存之后，我们需要调用`free()`函数来释放这块内存空间，以便系统可以重新利用它。
