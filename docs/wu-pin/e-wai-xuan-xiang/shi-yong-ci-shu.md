# 使用次数

```
ExampleItem4:
  material: STONE
  lore:
  - '物品使用次数: %neigeitems_charge%/%neigeitems_maxCharge%'
  options:
    charge: 10
```

`charge` 该物品可使用的次数 (可触发物品动作的次数)

!> 配置使用次数后，物品动作中的`consume.amount`项将失去作用
