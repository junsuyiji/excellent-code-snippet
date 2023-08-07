`realloc()`函数用于重新分配之前通过`malloc()`、`calloc()`或`realloc()`函数分配的内存空间。它的原型如下：

```c
void* realloc(void* ptr, size_t size);
```

`realloc()`函数接受两个参数，第一个参数`ptr`是之前分配的内存空间的指针，第二个参数`size`表示需要重新分配的内存空间大小（以字节为单位）。`realloc()`函数会返回一个指向重新分配的内存空间的指针，或者返回`NULL`表示分配失败。

下面是一个使用`realloc()`函数的例子：

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

    int newSize;
    printf("请输入新的数组大小：");
    scanf("%d", &newSize);

    // 使用realloc重新分配内存
    numbers = (int*)realloc(numbers, newSize * sizeof(int));

    if (numbers == NULL) {
        printf("内存分配失败\n");
        return 1;
    }

    printf("请输入%d个新的整数：\n", newSize);
    for (int i = 0; i < newSize; i++) {
        scanf("%d", &numbers[i]);
    }

    printf("你输入的新数组是：\n");
    for (int i = 0; i < newSize; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");

    // 释放动态分配的内存
    free(numbers);

    return 0;
}
```

在上述例子中，我们首先使用`malloc()`函数动态分配了一个整型数组所需的内存空间，然后通过`sizeof(int)`计算每个整数占用的字节数，并将其与数组大小相乘，以得到需要分配的总字节数。如果内存分配成功，`malloc()`函数将返回一个指向分配的内存空间的指针，我们将其赋值给`numbers`变量。

然后，我们通过`realloc()`函数重新分配内存空间，传入之前分配的内存空间的指针`numbers`和新的大小`newSize`。如果内存分配成功，`realloc()`函数将返回一个指向重新分配的内存空间的指针，我们将其赋值给`numbers`变量。

最后，我们释放动态分配的内存空间，以便系统可以重新利用它。注意，当使用`realloc()`函数重新分配内存空间时，如果新的大小小于之前分配的大小，那么超出新大小的部分将被丢弃。如果新的大小大于之前分配的大小，那么超出旧大小的部分将保持未初始化的状态。因此，为了避免数据丢失，我们在重新分配内存后需要重新输入新的数据。
