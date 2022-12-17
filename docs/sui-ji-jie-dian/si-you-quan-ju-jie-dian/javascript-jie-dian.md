# JavaScript节点

```
节点ID:
  type: js
  path: ExampleScript.js::main
  # (可选)
  # args: 
  # - 参数1
  # - 参数2
```

path的格式为 脚本路径::调用函数

args项可选，args的所有内容将作为参数传入被调用函数

例如，在该示例节点中

将调用`plugins/NeigeItems/Scripts/ExampleScript.js`脚本文件中的main函数

并返回main函数的返回值
