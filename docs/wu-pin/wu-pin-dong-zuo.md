# 物品动作

## 简介

通过左键/右键、食用/饮用、丢弃/捡起物品，触发一系列物品动作（支持papi变量）

可自定义每次是否消耗物品、消耗的物品数量、物品冷却、触发方式

## 路径

所有物品动作配置文件应存放于plugins/NeigeItems/ItemActions文件夹

重复配置同一 ID 的物品不会导致报错，但可能互相覆盖

最后哪套动作活下来。。。随缘了属于是

## 配置

以默认指令配置为例

```
ExampleItem:
  consume:
    cooldown: 3000
    amount: 1
    left: true
    right: true
  left:
  - "console: say He's name is %player_name%"
  - "command: say My name is %player_name%"
  right: 
  - "console: say He's name is %player_name%"
  - "command: say My name is %player_name%"
  all: 
  - "console: say He's name is %player_name%"
  - "command: say My name is %player_name%"
ExampleItem3:
  cooldown: 3000
  all: 
  - "console: say He's name is %player_name%"
  - "command: say My name is %player_name%"
```

* ExampleItem 即物品ID，对应ID的物品交互后将触发下列指令组
  * cooldown 代表物品使用冷却（不消耗）
  * consume 代表物品使用后将消耗
    * cooldown 物品消耗冷却时间
    * amount 每次消耗几个物品（大于这个数量才可以消耗并触发动作）
    * left 左键点击物品是否消耗
    * right 右键点击物品是否消耗
    * all 左右键点击物品是否消耗
    * eat 食用/引用物品是否消耗
    * drop 丢弃物品是否消耗
    * pick 捡起物品是否消耗
  * left 左键行为将触发下方动作组
    * 物品动作
  * leftSync 左键行为将同步触发下方动作组
    * 物品动作
  * right 右键行为将触发下方动作组
    * 物品动作
  * rightSync 右键行为将同步触发下方动作组
    * 物品动作
  * all 左/右键行为都将触发下方动作组
    * 物品动作
  * allSync 左/右键行为都将同步触发下方动作组
    * 物品动作
  * eat 食用/引用行为将触发下方动作组
    * 物品动作
  * eatSync 食用/引用行为将同步触发下方动作组
    * 物品动作
  * drop 丢弃行为都将触发下方动作组
    * 物品动作
  * dropSync 丢弃行为都将同步触发下方动作组
    * 物品动作
  * pick 捡拾行为都将触发下方动作组
    * 物品动作
  * pickSync 捡拾行为都将同步触发下方动作组
    * 物品动作
  * cooldown 代表物品使用冷却（不消耗）


!> 如果同时配置消耗冷却（consume.cooldown）和使用冷却（cooldown）
后者将被前者覆盖

!> Q：什么是“同步触发”？Sync后缀意味着什么？
A：“同步触发”意味着全程在主线程进行（默认异步进行）。如果你在编写自定义动作时有某些特定需求，需要保证线程安全，你可能会用到该功能。正常情况下，你不需要添加Sync后缀，不需要理解什么是“同步触发”。
