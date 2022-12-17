# 掉落物归属

以默认配置为例

```
ownerTest:
  material: STONE
  name: 你捡我啊
  options:
    owner: Neige
```

上述物品通过/ni drop或击杀MM怪物掉落该物品, 该物品首次拾取只能由Neige完成

你可以将owner填写为%player\_name%, 这样就是谁击杀就属于谁了

首次拾取后将不再有掉落物归属效果

服务器重启后效果重置 (掉了, 关服了, 再次开服, 谁都能捡)

!> 通过/ni get或/ni give直接获取拥有掉落物归属的物品
<br />物品将包含特殊nbt (用于记录归属人)
<br />但通过/ni drop或击杀MM怪物掉落的物品将不包含该nbt (掉落的时候移除了)