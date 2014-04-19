# awk

### 简介
我有时候用awk处理一些表单数据。
awk语句模式如下：

	pattern { action }

如果省略pattern，则默认为总是匹配；如果省略action，则默认为打印
语句由分号或者换行符 分割。

### 变量
`$0, $1, $2, ...`

### 流程控制

	<em>if</em>(expr) statement [ *else* statement ]
	<em>while</em>(expr) statement
	<em>for</em>(expr1; expr2; expr3) statement
	<em>for</em>(var *in* array) statement
	<em>do</em> statement *while*(expr)
	<em>break</em>
	<em>continue</em>
	{ [ statement ... ] }
	expr
	<em>print</em> [ expr-list ] [ > expr ]
	<em>printf</em> format [ , expr-list ] [ > expr ]
	<em>return</em> [ expr ]
	<em>next</em>
	<em>nextfile</em>
	<em>delete</em> array [ expr ]
	<em>delete</em> array
	<em>exit</em> [ expr ]

### 例子
