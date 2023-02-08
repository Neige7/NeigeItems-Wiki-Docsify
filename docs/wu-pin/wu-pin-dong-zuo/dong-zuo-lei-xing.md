# 动作类型

> 全部动作支持papi变量, 不区分大小写

## 动作写法

物品动作大致可归为三类: 列表式、字符式、条件式:

```
# 字符式
actions: 'tell: 你好'
```

```
# 列表式
actions:
- 'tell: 你好'
- 'tell: 你好'
- 'tell: 你好'
```

```
# 条件式
actions:
  condition: 'perm("test")'
  actions:
  - 'tell: 你好'
  deny:
  - 'tell: 你好'
```

这三种形式可以任意组合, 在此我仅作一例:

```
# 列表式组合条件式
actions:
- 'tell: 你好'
- condition: 'perm("test")'
  actions:
  - 'tell: 你好'
  deny:
  - 'tell: 你好'
- 'tell: 你好'
```

## 发送文本

> 向玩家发送一条消息(可使用&作为颜色符号)

```
- 'tell: &eHello'
```

## 发送文本

> 向玩家发送一条消息(不将&解析为颜色符号)

```
- 'tellNoColor: §eHello, can you see "&"?'
```

## 强制聊天

> 强制玩家发送一条消息(不将&解析为颜色符号)

```
- 'chat: see, I can send "&"!'
```

## 强制聊天

> 强制玩家发送一条消息(可使用&作为颜色符号)

```
- 'chatWithColor: &eHello'
```

## 执行指令(玩家)

> 强制玩家执行一条指令(可使用&作为颜色符号)

```
- 'command: say Hello'
- 'player: say Hello'
```

## 执行指令(玩家)

> 强制玩家执行一条指令(不将&解析为颜色符号)

```
- 'commandNoColor: say Hello'
```

## 执行指令(后台)

> 后台执行一条指令(可使用&作为颜色符号)

```
- 'console: say Hello'
```

## 执行指令(后台)

> 后台执行一条指令(不将&解析为颜色符号)

```
- 'consoleNoColor: say Hello'
```

## 给予金币(Vault)

> 给予玩家一定数量金币

```
- 'giveMoney: 100'
```

## 扣除金币(Vault)

> 扣除玩家一定数量金币

```
- 'takeMoney: 100'
```

## 给予经验

> 给予玩家一定数量经验

```
- 'giveExp: 100'
```

## 扣除经验

> 扣除玩家一定数量经验

```
- 'takeExp: 100'
```

## 设置经验

> 设置玩家当前经验

```
- 'setExp: 100'
```

## 给予经验等级

> 给予玩家一定数量经验等级

```
- 'giveLevel: 100'
```

## 扣除经验等级

> 扣除玩家一定数量经验等级

```
- 'takeLevel: 100'
```

## 设置经验等级

> 设置玩家当前经验等级

```
- 'setLevel: 100'
```

## 给予饱食度

> 给予玩家一定数量饱食度

```
- 'giveFood: 5'
```

## 扣除饱食度

> 扣除玩家一定数量饱食度

```
- 'takeFood: 5'
```

## 设置饱食度

> 设置玩家当前饱食度

```
- 'setFood: 20'
```

## 给予生命值

> 给予玩家一定数量生命值

```
- 'giveHealth: 5'
```

## 扣除生命值

> 扣除玩家一定数量生命值

```
- 'takeHealth: 5'
```

## 设置生命值

> 设置玩家当前生命值

```
- 'setHealth: 20'
```

## 释放MM技能

> 释放MM技能, 对创造模式玩家无效

```
- 'castSkill: 技能名称'
```

## 组合技记录

> 在对应组记录当前触发技能

```
- 'combo: 触发组 触发ID'
```

语言描述较为抽象, 在此我以默认配置为例, 实现左键-右键-左键触发连击技的示范:

```
ComboTest:
  left:
    sync:
      # 在ComboTest组记录, 触发了类型为left的连击
      - "combo: ComboTest left"
      # 检测ComboTest组是否完成了left-right-left连击
      - condition: combo("ComboTest", ["left", "right", "left"])
        actions:
          # 进行对应操作
          - 'tell: &e连击 &bL &f+ &bR &f+ &bL'
          # 已达成最终需要的连击, 清空ComboTest组的连击记录
          - 'comboClear: ComboTest'
        deny:
          # 检测ComboTest组是否完成了left连击
          condition: combo("ComboTest", ["left"])
          actions:
            # 进行对应操作
            - 'tell: &e连击 &bL'
  right:
    sync:
      # 在ComboTest组记录, 触发了类型为right的连击
      - "combo: ComboTest right"
      # 检测ComboTest组是否完成了left-right连击
      - condition: combo("ComboTest", ["left", "right"])
        actions:
          # 进行对应操作
          - 'tell: &e连击 &bL &f+ &bR'
```

## 组合技清除

> 清除对应组的技能记录

```
- 'comboClear: 触发组'
```

## 延时

> 延迟动作执行(单位是tick)

```
- 'delay: 10'
```

## 终止

> 终止动作执行

```
- 'return'
```
