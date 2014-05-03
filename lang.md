## C

### 缺点
- 宏不够强大
- 考虑下面的代码
```c
typedef struct node;

struct node {
  node *left, *right;
  int value;
};
```
为什么需要`typedef`才能在struct node中定义left、right? Go倒是改好了，只需要type就行。
也许C这样做，是为了方便编译器。
- 有时候很啰嗦。
```c
#include <stdio.h>
#include <stdlib.h>
```
如果像下面这样，就简洁一点
```
#include (
  <stdio.h>
  <stdlib.h>
)
```
Go也改好了。归结起来，还是C语言的宏不够强大、方便。

## Scheme

Scheme的变量，是跟value绑定的。每次都要到运行时到环境中去查找，开销太大了。
相反，静态语言的变量，通常是跟一个内存位置相关，在编译/链接的时候就确定了，运行时查找的开销为O(1)。
