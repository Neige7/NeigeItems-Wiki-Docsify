# 不高兴篇

不高兴篇应对不愿意看wiki的傻逼，在本节，我可能大量引用wiki内链接，告诉你这个傻逼，这个问题wiki里已经你妈的写了。

## 随机物品

NeigeItems是一个随机物品库，理应可以写出随机物品。
<br />我们需要通过NeigeItems中的随机节点达成写出随机物品的目的。
<br />随机节点分为[私有节点](sui-ji-jie-dian/si-you-quan-ju-jie-dian.md)和[即时节点](sui-ji-jie-dian/ji-shi-sheng-ming-jie-dian.md)。由于这些东西我都写过，我直接把链接贴出来，看不懂就自杀吧。

[私有节点配置](wu-pin/wu-pin-pei-zhi/README.md?id=随机节点)

```
随机名称的铁剑:
  material: IRON_SWORD
  name: <weight-1>
  sections:
    weight-1:
      type: weight
      values:
      - 5::名字1
      - 4::名字2
      - 3::名字3
      - 2::名字4
      - 1::名字5
```

该物品的名字：
* `5/15`概率为`名字1`
* `4/15`概率为`名字2`
* `3/15`概率为`名字3`
* `2/15`概率为`名字4`
* `1/15`概率为`名字5`

[即时节点配置](kai-shi/mo-ren-pei-zhi.md?id=itemsexampleitemyml)
```
ExampleItem:
  material: LEATHER_HELMET
  lore:
  - '即时声明字符串节点测试: <strings::number-1_weight-1>'
```

该物品的Lore：
* `1/2`概率为`即时声明字符串节点测试: number-1`
* `1/2`概率为`即时声明字符串节点测试: weight-1`