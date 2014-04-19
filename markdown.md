github中使用自定义的markdown。

### 标题
```
# title1
## title2
...
###### title6
```

### 列表
`-+*`开头，为unorder list
`1.` 开头，为order list

### 代码
1、用tab缩进
2、github自动以，fence
```
\`\`\`javascript
function add(x, y) {
    return x + y
}
\`\`\`
```
3、行内，使用`引用

### 链接
```
1、[参考这里](http://google.com.hk "title")
2、[参考这里][]
[参考这里]: http://google.com.hk "title"
[txt][id]
[id]: http://url "title"
```

### 内嵌图片
```
![alt txt](path/to/img "title")
```
