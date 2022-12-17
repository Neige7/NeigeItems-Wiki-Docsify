# papi节点

```
<papi::player_name>
```

参数为待解析文本

!> 节点解析前，物品会先全局解析一次papi变量。
因此直接写出的papi变量是不需要使用papi节点进行解析的。
papi节点存在的意义是应对经过拼接的papi文本。
例如`<papi::<string-1><string-2>>`，
`<string-1>`返回`player_`，
`<string-2>`返回`name`。
