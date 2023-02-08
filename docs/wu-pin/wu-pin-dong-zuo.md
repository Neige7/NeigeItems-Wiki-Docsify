# 物品动作

## 简介

通过左键/右键、食用/饮用、丢弃/捡起物品等方式，触发一系列物品动作（支持papi变量与即时节点）
<br />可自定义每次是否消耗物品、消耗的物品数量、物品冷却、触发方式、触发条件

## 路径

所有物品动作配置文件应存放于`plugins/NeigeItems/ItemActions`文件夹
<br />重复配置同一 ID 的物品不会导致报错，但可能互相覆盖
<br />最后哪套动作活下来。。。随缘了属于是

## 配置

以默认指令配置为例

```
ExampleItem2:
  left:
    actions:
      - "tell: 你正尝试触发&e ExampleItem2 &f物品"
      - condition: perm("item.ExampleItem2")
        actions:
          - "console: say &e%player_name% &f拥有&e item.ExampleItem2 &f权限"
          - "command: say 我拥有&e item.ExampleItem2 &f权限"
        deny:
          - "tell: 你没有&e item.ExampleItem2 &f权限"
    sync:
      - "tell: 你好, 这条消息通过主线程发送"
ExampleItem3:
  left:
    cooldown: 3000
    group: test2
    consume:
      condition: perm("item.ExampleItem3")
      amount: 1
      deny:
        - "tell: 你没有&e item.ExampleItem3 &f权限"
    actions:
      - "tell: 你正尝试触发&e ExampleItem3 &f物品"
```

## 结构

一个物品的动作配置可以表示为如下结构:

* 物品ID
  * 触发类型
    * 冷却时间(cooldown)
    * 冷却组(group)
    * 消耗信息(consume)
      * 消耗条件(condition)
      * 消耗数量(amount)
      * 不满足条件/数量不足时执行的动作(deny)
    * 同步执行的物品动作(sync)
    * 异步执行的物品动作(actions)

## 触发类型

| 触发类型 | 含义 |
| :----: | :----: |
| left | 手持物品左键点击 |
| right | 手持物品右键点击 |
| all | 手持物品左键或右键点击 |
| shift_left | 潜行状态手持物品左键点击 |
| shift_right | 潜行状态手持物品右键点击 |
| shift_all | 潜行状态手持物品左键或右键点击 |
| eat | 饮用/食用物品 |
| drop | 丢弃物品 |
| pick | 拾取物品 |

## 冷却时间

冷却时间的单位是毫秒(ms), 支持解析动作变量及即时声明节点, 如:

```
# 冷却时间为3秒
test1:
  left:
    cooldown: 3000
    actions:
      - "tell: 你好"
# 冷却时间为随机5-10秒
test2:
  left:
    cooldown: <number::5000_10000>
    actions:
      - "tell: 你好"
# 冷却时间为物品中名为 test1 的NBT的值
test3:
  left:
    cooldown: <nbt::test1>
    actions:
      - "tell: 你好"
# 冷却时间为 %player_level% 这个PAPI变量的解析值
test4:
  left:
    cooldown: <papi::player_level>
    actions:
      - "tell: 你好"
```

## 冷却组

冷却组默认为`触发类型-物品ID`, 如:

```
test1:
  left:
    cooldown: 3000
    actions:
      - "tell: 你好"
test2:
  left:
    cooldown: 3000
    group: 'left-test1'
    actions:
      - "tell: 你好"
```

上述test1及test2物品的left触发器共享冷却时长

## 消耗信息

消耗信息中可配置消耗条件、消耗数量及不满足条件/数量不足时执行的动作, 如:

```
test1:
  left:
    consume:
      # 检测是否持有 test1 权限
      condition: 'perm("test1")'
      # 消耗一个
      amount: 1
      # 未满足条件/数量不足时执行的动作
      deny:
       - 'tell: 你没有 test1 权限'
    actions:
      - 'tell: 你持有 test1 权限, 成功消耗了 1 个 test1 物品'
```

其中, amount支持代入动作变量及即时声明节点, 如:

```
# 需消耗 test1 NBT值数量的物品
test1:
  left:
    consume:
      amount: <nbt::test1>
    actions:
      - 'tell: 物品消耗成功'
# 随机消耗5-10个物品
test2:
  left:
    consume:
      amount: <number::5_10>
    actions:
      - 'tell: 物品消耗成功'
# 消耗玩家等级数量个物品
test3:
  left:
    consume:
      amount: <papi::player_level>
    actions:
      - 'tell: 物品消耗成功'
# 消耗玩家等级数量个物品, 数据保留0位小数, 最小值限定为1, 最大值限定为10
test4:
  left:
    consume:
      amount: <fastcalc::<papi::player_level>_0_1_10>
    actions:
      - 'tell: 物品消耗成功'
```

deny项在条件不满足/数量不足时都会触发, 意味着你可以不书写condition项, 只写amount和deny:

```
test1:
  left:
    consume:
      amount: 2
      deny:
      - 'tell: 你真的太逊了, 连2个物品都拿不出来'
    actions:
      - 'tell: 物品消耗成功'
```

关于condition和actions的具体写法, 详见[动作类型](wu-pin/wu-pin-dong-zuo/dong-zuo-lei-xing.md)和[条件类型](wu-pin/wu-pin-dong-zuo/tiao-jian-lei-xing.md)