# 即时声明节点

> 节点配置内全面支持节点调用/PAPI调用

## 格式

`<节点类型::参数1_参数2_参数3...>`

即时声明节点无法指定节点ID, 如有需求，请配置私有/全局节点

## 字符串节点

```
<strings::测试字符串1_测试字符串2_测试字符串3>
```

string节点将在各参数中随机返回一个

## 随机数节点

```
<number::0_10_0>
```

* `参数1` 随机数最小值
* `参数2` 随机数最大值
* `参数3` 保留小数位数

## Gaussian节点

```
<gaussian::100_0.1_0.5_1_0_10000>
```

* `参数1` 基础数值
* `参数2` 浮动单位
* `参数3` 浮动范围上限
* `参数4` 小数保留位数 (默认为1)
* `参数5` 随机数最小值 (可不填)
* `参数6` 随机数最大值 (可不填)

关于Gaussian节点的详细介绍请看:

[Gaussian节点](sui-ji-jie-dian/si-you-quan-ju-jie-dian/gaussian-jie-dian.md)

## 公式节点

```
<calculation::1+1+3+%player_level%_2_5_100>
```

* `参数1` 计算公式
* `参数2` 保留小数位数
* `参数3` 公式结果最小值
* `参数4` 公式结果最大值

## 权重节点

```
<weight::5::权重文本1_1::权重文本2>
```

参数格式 权重::权重文本

节点将根据权重随机返回一个权重文本

例如，在该示例节点中

将有5/6的几率返回"权重文本1"，1/6的几率返回"权重文本2"

## PAPI节点

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

## Javascript节点

```
<js::ExampleScript.js::main>
<js::ExampleScript.js::main_参数1_参数2_...>
```

参数格式 脚本路径::调用函数

或 脚本路径::调用函数\_参数1\_参数2\_...

## 继承节点

```
<inherit::待继承节点ID>
```

如上，相当于继承了对应节点的所有内容。例如：

```
sections:
  templateTest: <strings::text1_text2_text3>
```

```
<inherit::templateTest>
```

其中templateTest有可能返回"text1"，"text2"或"text3"。

即时声明节点"\<inherit::templateTest>"同样有可能返回"text1"，"text2"或"text3"。