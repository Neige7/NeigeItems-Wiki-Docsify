# NI物品穿戴

> 相关配置支持解析即时声明变量

在MM怪物的配置中添加

```
NeigeItems:
  Equipment:
  - 穿戴位置: 物品ID 穿戴概率 指向数据 
```

物品ID可以是NI物品ID、MM物品ID或EasyItem物品ID

可用的穿戴位置都有：

* `Helmet` 代表头部
* `Chestplate` 代表胸部
* `Leggings` 代表腿部
* `Boots` 代表脚部
* `MainHand` 代表主手
* `OffHand` 代表副手

穿戴概率默认为1

下面我写一个MM怪物示例配置

```
test1:
  Type: ZOMBIE
  Health: 1
  NeigeItems:
    Equipment:
    # 头部50%几率穿戴ID为"Helmet1"的NI物品(或MM物品、EasyItem物品)
    - 'Helmet: Helmet1 0.5'
    # 胸部100%几率穿戴ID为"Chestplate1"的NI物品(或MM物品、EasyItem物品)
    - 'Chestplate: Chestplate1'
    - 'Leggings: Leggins1 0.5'
    - 'Boots: Boots1 0.5'
    - 'MainHand: MainHand1 0.5'
    - 'OffHand: OffHand1 0.5'
```
