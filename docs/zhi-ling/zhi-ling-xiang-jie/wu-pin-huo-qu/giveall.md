# giveAll

> /ni giveAll [物品ID] (数量) (是否反复随机) (指向数据) > 根据ID给予所有人NI物品

* `[物品ID]` NI物品ID
* `(数量)` 获取的数量 (默认为1)
* `(是否反复随机)` 默认为true
* `(指向数据)` 字符串化JSON文本

    形如`{"string-1":"文本文本文本"}`

    这样物品生成时`string-1`的值将变为`文本文本文本`