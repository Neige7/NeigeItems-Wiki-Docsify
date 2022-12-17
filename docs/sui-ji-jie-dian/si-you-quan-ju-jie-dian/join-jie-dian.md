# Join节点

```
节点ID:
  type: join
  list:
    - 第一行
    - 第二行
    - 第三行
    - 第四行
  separator: "-"
  prefix: '<'
  postfix: '>'
  limit: 3
  truncated: "..."
  transform: |-
    return this.it + "哈哈"
```

简介: 将list中的多段文本连接成一段文本

* list 待操作的列表
* separator 分隔符 (默认为", ")
* prefix 前缀 (默认无前缀)
* postfix 后缀 (默认无后缀)
* limit 限制列表长度
* truncated 超过长度的部分用该符号代替 (默认直接吞掉超过长度的部分)
* transform 对列表的每一行进行一些操作 (使用javascript函数)

示例中的节点将返回:

```
<第一行哈哈-第二行哈哈-第三行哈哈-...>
```

由于该节点功能较其他节点更加复杂,  因此我为它编写了多个示例配置帮助理解, 如下:

```
# 帮助理解list
JoinTest1:
  material: STONE
  lore:
    # 结果: 1, 2, 3, 4, 5
    - 'join节点: <test>'
  sections:
    test:
      type: join
      # 待操作的列表
      list:
        - 1
        - 2
        - 3
        - 4
        - 5
# 帮助理解separator
JoinTest2:
  material: STONE
  lore:
    # 结果: 1-2-3-4-5
    - 'join节点: <test>'
  sections:
    test:
      type: join
      list:
        - 1
        - 2
        - 3
        - 4
        - 5
      # 分隔符(默认为", )
      separator: "-"
# 帮助理解prefix及postfix
JoinTest3:
  material: STONE
  lore:
    # 结果: <1, 2, 3, 4, 5>
    - 'join节点: <test>'
  sections:
    test:
      type: join
      list:
        - 1
        - 2
        - 3
        - 4
        - 5
      # 前缀
      prefix: "<"
      # 后缀
      postfix: ">"
# 帮助理解limit
JoinTest4:
  material: STONE
  lore:
    # 结果: 1, 2, 3
    - 'join节点: <test>'
  sections:
    test:
      type: join
      list:
        - 1
        - 2
        - 3
        - 4
        - 5
      # 限制长度
      limit: 3
# 帮助理解truncated
JoinTest5:
  material: STONE
  lore:
    # 结果: 1, 2, 3, ...
    - 'join节点: <test>'
  sections:
    test:
      type: join
      list:
        - 1
        - 2
        - 3
        - 4
        - 5
      limit: 3
      # 超过长度的部分用该符号代替
      truncated: "..."
# 帮助理解transform
JoinTest6:
  material: STONE
  lore:
    # 结果: 2, 3, 4, 5, 6
    - 'join节点: <test>'
  sections:
    test:
      type: join
      list:
        - 1
        - 2
        - 3
        - 4
        - 5
      # 对列表中的每个元素进行一定操作
      # this.it代表当前元素
      # this.index代表当前序号(0代表第一个, 1代表第二个, 以此类推)
      # this.player代表玩家
      # this.vars(String string)用于解析节点
      # List<String> this.list代表节点中的list
      transform: |-
        // 尝试将当前元素转换为整数, 并加一, 然后保留整数
        return (parseInt(this.it) + 1).toFixed(0)
# 利用join节点插入多行lore
JoinTest7:
  material: STONE
  lore:
    # 等同于:
    # - 第一行
    # - 第二行
    # - 第三行
    #
    # 这个节点应该单独占据一行
    # 不要在这行写其他文本(比如'join节点: <test>')
    # 具体请自行测试
    - '<test>'
  sections:
    test:
      type: join
      list:
        - 第一行
        - 第二行
        - 第三行
      # 像下面这样写分隔符、前缀和后缀
      # 即可达到调用多行lore的效果
      separator: "\\n"
      prefix: '"'
      postfix: '"'
```

