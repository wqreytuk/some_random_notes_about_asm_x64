# 函数调用中的栈

源代码：

```c
#include <stdio.h>

int fuck(int p1, int p2, int p3, int p4, int p5, int p6, int p7, int p8, int p9, int p10) {
    return (p1 + p2 + p3 + p4 + p5 + p6 + p7 + p8 + p9 + p10);
}

int main()
{
    fuck(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
    return 0;
}
```

汇编代码：

![image-20230321123233283](https://raw.githubusercontent.com/wqreytuk/img_repo/main/tylgERDEpC.jpg)

可以看到，剩下的6个通过栈进行传递的参数，入栈的顺序是倒着的，最后一个参数先入栈，因为栈是向下增长的，所以地址会越来越小

## x64中使用栈传递的参数的长度都是8bytes

```c
#include<stdio.h>
void test(int a, short b, int c, int d, short e, int g, short ee, int eg) {
	printf("%d\n", a + b + c + e + g + ee + eg);
}
int main() {
	test(1, 2, 3, 4, 5, 4, 5, 5);
	printf("123");
	return 0;
}
```

可以看到，不管是word还是dword，在栈中都是占用8bytes

![image](https://user-images.githubusercontent.com/48377190/227868615-24e77b94-4e65-4c46-b43d-4abe86488497.png)
