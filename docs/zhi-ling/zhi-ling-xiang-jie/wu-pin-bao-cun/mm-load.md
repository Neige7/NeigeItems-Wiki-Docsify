---
description: /ni mm load [物品ID] (保存路径) > 将对应ID的MM物品保存为NI物品
---

# mm load

* \[物品ID] 待转换的MM物品ID
* (保存路径) 物品存储的文件路径，默认为配置文件中的Main.MMItemsPath\
  &#x20;                 形如test.yml，将存储于plugins/NeigeItems/Items/test.yml

{% hint style="info" %}
如果物品ID重复（已存在对应ID的NI物品）

将保存失败并提示
{% endhint %}
