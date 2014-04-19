# awk

## 简介
我有时候用awk处理一些表单数据。
awk语句模式如下：

	pattern { action }

如果省略pattern，则默认为总是匹配；如果省略action，则默认为打印
语句由分号或者换行符 分割。

## 变量
`$0, $1, $2, ...`

## 流程控制
	*if*(expr) statement [ *else* statement ]
	*while*(expr) statement
	*for*(expr1; expr2; expr3) statement
	*for*(var *in* array) statement
	*do* statement *while*(expr)
	*break*
	*continue*
	{ [ statement ... ] }
	expr
	*print* [ expr-list ] [ > expr ]
	*printf* format [ , expr-list ] [ > expr ]
	*return* [ expr ]
	*next*
	*nextfile*
	*delete* array [ expr ]
	*delete* array
	*exit* [ expr ]

## 例子
