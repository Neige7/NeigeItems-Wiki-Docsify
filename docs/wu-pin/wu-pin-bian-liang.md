# 物品变量

## 简介

你可以在物品的名称/Lore中添加某些占位符

这些占位符将根据当前物品的nbt被发包替换

该功能仅对于生存模式的玩家生效

## 变量列表

* `%neigeitems_charge%` 物品当前剩余使用次数

* `%neigeitems_maxCharge%` 物品最大使用次数



* `%neigeitems_nbt_XXXXX%` 物品对应NBT的值

    例：`%neigeitems_nbt_NeigeItems.id%`

* `%neigeitems_nbtnumber_保留小数位数_XXXXXX%` 物品对应NBT的值(进行取整)

    例：`%neigeitems_nbtnumber_0_NeigeItems.hashCode%`
