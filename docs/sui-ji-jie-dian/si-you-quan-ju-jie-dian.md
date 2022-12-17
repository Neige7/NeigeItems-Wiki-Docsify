# 全局/私有节点

> 节点配置内全面支持节点调用/PAPI调用

## 路径

所有全局节点配置文件应存放于`plugins/NeigeItems/GlobalSections`文件夹

重复 ID 的节点仍然会被加载，但可能互相覆盖

最后哪个节点活下来。。。随缘了属于是

## 字符串节点

```
节点ID:
  type: strings
  values:
  - test1
  - test2
```

结果将在values中随机获取一个值

每个值被选中的几率相等

## 随机数节点

```
节点ID:
  type: number
  min: 1
  max: 2
  fixed: 3
```

* `min` 随机数的最小值
* `max` 随机数的最大值
* `fixed` 小数保留位数

## Gaussian节点

```
节点ID:
  type: gaussian
  base: 100
  spread: 0.1
  maxSpread: 0.5
  fixed: 1
  min: 0
  max: 10000
```

简介: 类似MMOItems的, 符合正态分布的随机数, 随机数大概率在base附近, 小概率出现极大或极小的数值

* `spread` 基础数值
* `spread` 浮动单位
* `maxSpread` 浮动范围上限
* `fixed` 小数保留位数 (默认为1)
* `min` 随机数的最小值
* `max` 随机数的最大值

### 详细介绍:

* `base`是基础数值, 随机数将以其为中心, 随机散布

* `spread`是浮动单位, 决定了随机数散步的幅度

  比如base设置为100, spread设置为0.1, 根据正态分布:

  使用该节点生成大量随机数

  68.27%的随机数介于90-110

  95.45%的随机数介于80-120

  99.74%的随机数介于70-130

  以此类推......

* `maxSpread`是浮动范围上限, 限制了随机数的浮动极限, 防止出现过于离谱的数字

  比如我将maxSpread设置为0.3, 根据正态分布:

  0.26%的随机数将小于70或大于130, 即超过了0.3的幅度, 那么经过maxSpread的限制:

    小于70的随机数将变为70, 而大于130的随机数将变为130

* `fixed`是取整位数, 默认为1

  比如随机数值为123.456, fixed设置为1, 那么你将得到123.4

  比如随机数值为123.456, fixed设置为0, 那么你将得到123

* `min`是随机数的最小值, `max`是随机数的最大值, 超过范围的随机数将被限制

  比如随机数值为123, min设置为200, 那么你将得到200

  比如随机数值为123, max设置为100, 那么你将得到100

## 公式节点

```
节点ID:
  type: calculation
  formula: 1+2+3<global-number-1>
  min: 1
  max: 100
  fixed: 3
```

* `formula` 待计算公式，支持代入节点及PAPI变量
* `min` 结果的最小值
* `max` 结果的最大值
* `fixed` 小数保留位数

## 权重节点

```
节点ID:
  type: weight
  values:
  - 5::第一行
  - 1::第二行
```

values的格式为 权重::文本

结果将在values中根据权重随机获取一个值

例如，在该示例节点中

将有5/6的几率返回"第一行"，1/6的几率返回"第二行"

## JavaScript节点

```
节点ID:
  type: js
  path: ExampleScript.js::main
  # (可选)
  # args: 
  # - 参数1
  # - 参数2
```

path的格式为 脚本路径::调用函数

args项可选，args的所有内容将作为参数传入被调用函数

例如，在该示例节点中

将调用`plugins/NeigeItems/Scripts/ExampleScript.js`脚本文件中的main函数

并返回main函数的返回值

## Join节点

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

* `list` 待操作的列表
* `separator` 分隔符 (默认为", ")
* `prefix` 前缀 (默认无前缀)
* `postfix` 后缀 (默认无后缀)
* `limit` 限制列表长度
* `truncated` 超过长度的部分用该符号代替 (默认直接吞掉超过长度的部分)
* `transform` 对列表的每一行进行一些操作 (使用javascript函数)

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

## 继承节点

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

## 简单节点

```
节点ID: 值
```

如上所示，你直接添加节点的值。你可以搭配即时声明节点，优化你的配置。

比如：

```
节点ID: <strings::测试字符串1_测试字符串2_测试字符串3>
```

等效于

```
节点ID:
  type: strings
  values:
  - 测试字符串1
  - 测试字符串2
  - 测试字符串3
```
