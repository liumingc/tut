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
2、github特有，fence

    ```javascript
    function add(x, y) {
        return x + y
    }
    ```

Q：如果有netsted fence，该怎么处理？

3、行内，使用`引用

### 链接

```
1、[参考这里](http://google.com.hk "title")
2、[参考这里][]
 [参考这里]: http://google.com.hk "title"
3、[txt][id]
 [id]: http://url "title"
```

### 内嵌图片

```
![alt txt](path/to/img "title")
```

### 表格
使用`-|`构造表格。

|name | job | salary|
|----|----|----|
|k | programmer | &infin;|

### bold　＆　italic
`*`表示italic，`**`表示强调
