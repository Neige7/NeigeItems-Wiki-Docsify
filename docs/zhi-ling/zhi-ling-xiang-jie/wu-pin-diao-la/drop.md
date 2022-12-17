---
description: >-
  /ni drop [物品ID] [数量] [世界名] [X坐标] [Y坐标] [Z坐标] [是否反复随机] [物品解析对象] (指向数据) >    
  于指定位置掉落NI物品
---

# drop

* \[物品ID] NI物品ID
* \[数量] 获取的数量，默认为1
* \[世界名] 物品掉落世界的名称
* \[X坐标] 物品掉落世界的X轴坐标
* \[Y坐标] 物品掉落世界的Y轴坐标
* \[Z坐标] 物品掉落世界的Z轴坐标
* (是否反复随机) 默认为true
* (物品解析对象) 用于物品解析的玩家ID\
  &#x20;                        用于解析物品内的PAPI变量及随机节点
* (指向数据) 字符串化JSON文本\
  &#x20;                 形如{"string-1":"文本文本文本"}\
  &#x20;                 这样物品生成时string-1的值将变为文本文本文本

{% hint style="info" %}
如果你想让MM怪物被玩家击杀后掉落NI物品，你可以直接查看下方页面：
{% endhint %}

{% content-ref url="../../../cha-jian-shi-pei/mythicmobs/ni-wu-pin-diao-la/" %}
[ni-wu-pin-diao-la](../../../cha-jian-shi-pei/mythicmobs/ni-wu-pin-diao-la/)
{% endcontent-ref %}
