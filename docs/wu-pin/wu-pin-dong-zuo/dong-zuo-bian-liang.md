# 动作变量

在物品动作中，你可以使用即时声明节点，并通过特殊的物品节点调用物品的nbt及节点缓存。

以默认配置为例：

```
actionTest:
  material: STONE
  nbt:
    test1: "666"
    test2: 
      test3: "777"
    test4:
    - "888"
    - "999"
  sections:
    test: "000"
```

```
actionTest:
  all: 
  - "console: say 名为test1的NBT的值为: <nbt::test1>"
  - "console: say 名为test2.test3的NBT的值为: <nbt::test2.test3>"
  - "console: say 名为test4.0的NBT的值为: <nbt::test4.0>"
  - "console: say 名为test4.1的NBT的值为: <nbt::test4.1>"
  - "console: say 名为test的节点的值为: <data::test>"
  - "console: say 随机数尝试: <number::0_10_2>"
```

后台返回值如下

```
[Server] 名为test1的NBT的值为: 666
[Server] 名为test2.test3的NBT的值为: 777
[Server] 名为test4.0的NBT的值为: 888
[Server] 名为test4.1的NBT的值为: 999
[Server] 名为test的节点的值为: 000
[Server] 随机数尝试: 0.74
```

用法类似于即时声明节点，data表示调用节点，nbt表示调用物品nbt。

一层一层id以小数点"."分隔
