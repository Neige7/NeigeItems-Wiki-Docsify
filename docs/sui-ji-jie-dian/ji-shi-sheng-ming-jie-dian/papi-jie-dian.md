# PAPI节点

```
<papi::player_name>
```

参数为待解析文本

!> 节点解析前，物品会先全局解析一次papi变量。
<br />因此直接写出的papi变量是不需要使用papi节点进行解析的。
<br />papi节点存在的意义是应对经过拼接的papi文本。
<br />例如`<papi::<string-1><string-2>>`
<br />`<string-1>`返回`player_`
<br />`<string-2>`返回`name`
