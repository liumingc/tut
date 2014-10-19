函数与延续


### 函数 (function)
如果把函数看成对象。。。
那么它有哪些字段呢？
`
struct FuncObject {   
	vars   
	pc-link   
	body   
	...   
}   
`
有访问链(vars)，控制链(pc-link)，以及函数体(body)   

* 访问链   
当函数体中出现`b = a + 3;`的时候，b是什么，a又是什么？要访问这些变量，就要通过访问链。   
对于C来说，一个变量要么是形参/局部变量，要么是全局变量。   
* 控制链   
当函数体执行完之后，下一步该做什么？其实函数中的返回地址构成了控制链。   
example：   
`
int add(int a, int b)   
{   
	return a + b;   
}   
`
这个函数中，   
vars包括(a, b)   
函数体为`return a + b;`   
控制链要在运行时才知道。   

既然是对象，那就可以动态创建。创建函数对象的API为：   
`
make-function(vars, pc-link, body)   
`
example:   
`
add = make-function((a, b), 0, "return a + b;")   
`
因为返回地址不确定，所以传递0   

对象还有方法。函数对象的方法为   
`
apply(args, pc-link)   
`


### 延续 (continuation)   
延续也是对象，可以基于函数来实现。   
延续适用于 “如果当时我选择了。。。就好了”这种情形。   
要想回到某个时间点，办法就是保存当时的控制链。   
   
创建一个延续，就是创建一个特殊的函数。   
用伪代码描述apply过程如下   
`
FunctionObject::eval(args, pc-link)   
{   
	extend(this.vars, args);   
	exec(this.body)   
	if(this.pc-link == 0)   
		goto pc-link;   
	else   
		goto this.pc-link;   
}   
`
   
好了，那么很简单，创建延续就是创建函数：   
`
foo-bar()   
{   
	conti = make-function((fn), pc-link, "return")   
}   
`
把执行时的控制链，传给continuation。continuation在后面需要的时候，只要执行apply，就通过原来保存的   
控制链返回到保存点了。


其实在编译器中，最复杂的还是函数了。
在3imp.pdf中，stack实现的VM，要比较env和stack的不同，考虑下面的例子：
`
(define (sum a b)
  (define f (a)
    (if (> a b)
        0
        (+ a (f (1+ a)))))
  (f a))
`
f反复被调用，栈是在不断的变化中。但是，closure f中，访问的b的位置应该一直不变。
stack VM的栈帧如下所示：
---------------------
env  +-------------- dynamic link,用于恢复env
ret
a2
a1
a0   +-------------- env
env1 +-------------- static link，用于访问变量
---------------------

