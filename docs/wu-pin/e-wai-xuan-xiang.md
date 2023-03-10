# 额外选项

以默认配置为例:

```
ExampleItem4:
  material: STONE
  lore:
  - '物品使用次数: %neigeitems_charge%/%neigeitems_maxCharge%'
  options:
    charge: 10
```

options下的所有配置项, 即为"额外选项"

## 使用次数

```
ExampleItem4:
  material: STONE
  lore:
  - '物品使用次数: %neigeitems_charge%/%neigeitems_maxCharge%'
  options:
    charge: 10
```

`charge` 该物品可使用的次数 (可触发物品动作的次数)

## 物品光效

```
ExampleItem:
  material: STONE
  options:
    color: GOLD
```

![](_images/物品光效.png)

此选项可以使掉落物产生发光效果

可用颜色有：

* AQUA
* BLACK
* BLUE
* DARK\_AQUA
* DARK\_BLUE
* DARK\_GRAY
* DARK\_GREEN
* DARK\_PURPLE
* DARK\_RED
* GOLD
* GRAY
* GREEN
* LIGHT\_PURPLE
* RED
* WHITE
* YELLOW

## 掉落技能

```
ExampleItem:
  material: STONE
  options:
    dropskill: SkillTest
```

![](_images/掉落技能.gif)

如图所示，此选项可使物品在掉落时触发MM技能。

只有通过/ni drop指令，以及通过击杀MM怪物掉落的NI物品才会触发，玩家主动丢弃不会。

作者并没有图中所示技能的版权，因此不在这里具体写出该技能。

## 掉落物归属

以默认配置为例

```
ownerTest:
  material: STONE
  name: 你捡我啊
  options:
    owner: Neige
```

上述物品通过/ni drop或击杀MM怪物掉落该物品, 该物品首次拾取只能由Neige完成

你可以将owner填写为"%player\_name%", 这样就是谁击杀就属于谁了

首次拾取后将不再有掉落物归属效果

服务器重启后效果重置 (掉了, 关服了, 再次开服, 谁都能捡)

!> 通过/ni get或/ni give直接获取拥有掉落物归属的物品
<br />物品将包含特殊nbt (用于记录归属人)
<br />但通过/ni drop或击杀MM怪物掉落的物品将不包含该nbt (掉落的时候移除了)

## 物品时限

```
物品ID:
  material: STONE
  options:
    itemtime: 物品时限(单位是秒)
```

以默认配置为例

```
itemTimeTest:
  material: STONE
  name: 限时物品-到期时间-<js::ItemTime.js::main_<itemtime>>
  options:
    itemtime: <itemtime>
  sections:
    itemtime: 60
```

搭配默认脚本

```
function main(time) {
    const date = new Date()
    date.setTime(date.getTime() + (Number(time) * 1000))
    return date.getFullYear() + "年" + (date.getMonth() + 1) + "月" + date.getDate() + "日" + date.getHours() + "时" + date.getMinutes() + "分" + date.getSeconds() + "秒"
}
```

可以生成形如`限时物品-到期时间-2022年8月11日21时59分5秒` 的物品，物品到期即自动删除并提示信息。

如默认配置所示，你可以在对应位置放置一个节点，然后通过指向数据给予物品时自定义时长。

例如: /ni give Neige itemTimeTest 1 true {"itemtime":"120"}将给予玩家一个剩余时间120秒的默认物品
