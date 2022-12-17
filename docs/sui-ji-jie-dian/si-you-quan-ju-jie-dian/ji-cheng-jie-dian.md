# 继承节点

```
节点ID:
  type: inherit
  template: 待继承节点ID
```

如上，相当于继承了对应节点的所有内容。例如：

```
sections:
  templateTest: <strings::text1_text2_text3>
  inheritTest:
    type: inherit
    template: templateTest
```

其中templateTest有可能返回"text1"，"text2"或"text3"。

inheritTest同样有可能返回"text1"，"text2"或"text3"。

