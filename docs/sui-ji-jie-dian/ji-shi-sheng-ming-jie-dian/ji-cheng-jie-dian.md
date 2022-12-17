# 继承节点

```
<inherit::待继承节点ID>
```

如上，相当于继承了对应节点的所有内容。例如：

```
sections:
  templateTest: <strings::text1_text2_text3>
```

```
<inherit::templateTest>
```

其中templateTest有可能返回"text1"，"text2"或"text3"。

即时声明节点"\<inherit::templateTest>"同样有可能返回"text1"，"text2"或"text3"。
