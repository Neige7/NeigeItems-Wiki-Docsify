# 高级应用

​直接展示例子:

```
stringTest:
  A:
    type: strings
    values:
    - test1
    - test2
  B:
    type: strings
    values:
    - test3
    - test4
```

如上配置节点后

调用`<stringTest.A>`将返回`test1`或`test2`

调用`<stringTest.B>`将返回`test3`或`test4`

如果这个节点是一个全局节点, 你可以通过

```
 globalsections:
 - stringTest
```

引用该节点
