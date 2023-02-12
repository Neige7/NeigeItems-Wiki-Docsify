# 条件类型

## 原理

条件解析本质上是执行一段javascript代码, 为了追求更高的性能, 我对用于解析条件的脚本引擎做了特殊设置。
<br />因此需要注意: 不要在condition内进行变量声明
<br />请使用`variables["test"] = 1`代替`var test = 1`
<br />为降低javascript上手门槛, 我内置了很多用于条件判断的函数。

## 注意

!> 不要在condition内进行变量声明!!!
<br />如: 
<br />  test = 1
<br />  var test = 1
<br />  let test = 1
<br />  const test = 1
<br />这将产生严重的线程安全问题

对此, 我提供了替代方案:
将变量存放于默认提供的名为`variables`的HashMap如:
```
variables["test"] = 1
```

## 默认存在的类/对象

### 类

`java.util.Calendar`
<br />`java.util.concurrent.ThreadLocalRandom`

`org.bukkit.Bukkit`
<br />`org.bukkit.ChatColor`
<br />`org.bukkit.GameMode`

`pers.neige.neigeitems.utils.ItemUtils`
<br />`pers.neige.neigeitems.utils.SectionUtils`
<br />`pers.neige.neigeitems.manager.HookerManager`

### 单例

`ActionManager` = `pers.neige.neigeitems.manager.ActionManager.INSTANCE`
<br />`ConfigManager` = `pers.neige.neigeitems.manager.ConfigManager.INSTANCE`
<br />`ItemEditorManager` = `pers.neige.neigeitems.manager.ItemEditorManager.INSTANCE`
<br />`ItemManager` = `pers.neige.neigeitems.manager.ItemManager.INSTANCE`
<br />`ItemPackManager` = `pers.neige.neigeitems.manager.ItemPackManager.INSTANCE`

### 对象

`bukkitScheduler` = `Bukkit.getScheduler()`
<br />`bukkitServer` = `Bukkit.getServer()`
<br />`consoleSender` = `bukkitServer.getConsoleSender()`
<br />`pluginManager` = `Bukkit.getPluginManager()`
<br />`plugin` = `pluginManager.getPlugin("NeigeItems")`

`player` = `触发玩家`
<br />`itemStack` = `触发物品`
<br />`itemTag` = `触发物品NBT`
<br />`event` = `触发事件`
<br />`variables` = `HashMap<String, Any?>()`
<br />`value` = `仅存在与check节点: check节点中传入的值`

## 同时满足(&&)

> 同时满足多个条件

```
condition: '条件1 && 条件2'
```

示例:

```
# 持有权限 test1 及 test2
condition: 'perm("test1") && perm("test2")'
```

## 满足一个(||)

> 满足多个条件中的一个

```
condition: '条件1 || 条件2'
```

示例:

```
# 持有权限 test1 或持有权限 test2
condition: 'perm("test1") || perm("test2")'
```

## 同时满足与满足一个嵌套使用

> 懂不懂括号的含金量

```
condition: '(条件1 || 条件2) && 条件3'
```

示例:

```
# 持有权限 test1 或持有权限 test2 的同时, 持有权限test3
condition: '(perm("test1") || perm("test2")) && perm("test3")'
```

## 是否相等(==, ===)

> 字符串记得用引号包起来

```
# papi变量 %player_name% 的解析值是否等于 Neige
condition: 'papi("%player_name%") == "Neige"'
condition: 'papi("%player_name%") === "Neige"'
```

== 比较的是值, ===比较的是值和类型

```
# 满足条件
condition: '"10" == 10'
# 不满足条件, 因为一个是字符串一个是数字
condition: '"10" === 10'
```

不想动脑子可以无脑使用==

## 大小判断(><)

> 字符串记得用引号包起来

```
# 懂?
condition: '10 > 10'
condition: '10 < 10'
condition: '10 >= 10'
condition: '10 <= 10'

# papi变量 %player_level% 的解析值是否大于等于 10
condition: 'Number(papi("%player_level%")) >= 10'
```

## 字符串转数字(Number, parseInt, parseFloat)

> 字符串记得用引号包起来

```
condition: 'Number("10") === 10'
condition: 'parseInt("10") === 10'
condition: 'parseFloat("10.0") === 10.0'
```

## 权限检测(perm)

> 字符串记得用引号包起来

```
# 玩家是否拥有 权限名 权限
condition: 'perm("权限名")'
```

## 替换颜色代码(color)

> 字符串记得用引号包起来

```
condition: 'color("&7nb666") == "§7nb666"'
```

## 解析PAPI变量(papi)

> 字符串记得用引号包起来

```
# papi变量 %player_name% 的解析值是否等于 Neige
condition: 'papi("%player_name%") == "Neige"'
```

## 解析即时节点(parse)

> 字符串记得用引号包起来

```
# 即时节点 <strings::test1_test2> 的解析值是否等于 test1
condition: 'parse("<strings::test1_test2>") == "test1"'
```

## 解析动作变量(parseItem)

> 字符串记得用引号包起来

```
# 检测test1这条NBT的值是否等于"666"
condition: 'parseItem("<nbt::test1>") == "666"'

# 检测test1这条data的值是否等于"666"
condition: 'parseItem("<data::test1>") == "666"'
```

## 获取指向数据(data)

> 字符串记得用引号包起来

```
# 当前NI物品名为"test"的节点值是否等于"666"
condition: 'data["test"] == "666"'
```

## 获取NBT文本(getNBT)

> 字符串记得用引号包起来

```
# getNBT获取的NBT值全是转成字符串的
# 检测test这条NBT的值是否等于"666"
condition: 'getNBT("test") == "666"'

# 可以用.分隔不同层级的键
# 当前检测的NBT对应在物品中体现为:
# test:
#   test: "666"
condition: 'getNBT("test.test") == "666"'
```

## 获取NBT值(getNBTTag)

> 字符串记得用引号包起来

`getNBTTag`获取的NBT都是ItemTag的形式, 需要你自行转换后对比
<br />如:
<br />`getNBTTag("test").asString() == "666"`
<br />`getNBTTag("test").asDouble() == "666"`
<br />`getNBTTag("test").asInt() == "666"`
<br />`getNBTTag("test").asFloat() == "666"`
<br />`getNBTTag("test").asByte() == "1"`

```
# getNBT获取的NBT值全是转成字符串的
# 检测test这条NBT的值是否等于"666"
condition: 'getNBTTag("test").asString() == "666"'

# 可以用.分隔不同层级的键
# 当前检测的NBT对应在物品中体现为:
# test:
#   test: "666"
condition: 'getNBTTag("test.test").asString() == "666"'
```

## 随机数(random)

```
# 生成一个0-1的随机数, 检测其是否大于等于0.5
condition: 'random() >= 0.5'

# 生成一个5-10的随机数, 检测其是否大于等于7
condition: 'random(5, 10) >= 7'
```

## 随机概率(chance)

```
# 50%返回满足条件
condition: 'chance(0.5)'

# 50%返回满足条件
condition: 'chance(50, 100)'
```

## 连击检测(chance)

```
# 检测ComboTest组是否完成了left-right-left连击
condition: 'combo("ComboTest", ["left", "right", "left"])'
```
请结合[组合技记录](wu-pin/wu-pin-dong-zuo/dong-zuo-lei-xing?id=组合技记录)了解

默认500ms内点击算作连击, 可通过配置文件修改

## 玩家IP(address)

> 字符串记得用引号包起来

```
condition: 'address() == "127.0.0.1"'
```

## 获取/修改飞行能力(allowFlight)

```
# 玩家可以飞行(双击空格起飞)
condition: 'allowFlight()'

# 设置玩家可以飞行, 并返回true满足条件
condition: 'allowFlight(true)'
```

## 获取/修改飞行状态(fly)

```
# 玩家正在飞行
condition: 'fly()'

# 设置玩家正在飞行, 并返回true满足条件
condition: 'fly(true)'
```

## 飞行速度(flySpeed)

```
# 玩家飞行速度是否等于1
condition: 'flySpeed() == 1'

# 将玩家飞行速度设置为10, 然后判断一下是否等于10以满足条件
condition: 'flySpeed(100) == 10'
```

## 行走速度(walkSpeed)

```
# 玩家行走速度是否等于1
condition: 'walkSpeed() == 1'

# 将玩家行走速度设置为10, 然后判断一下是否等于10以满足条件
condition: 'walkSpeed(100) == 10'
```

## 攻击冷却(attackCooldown)

```
# 是否冷却完毕
condition: 'attackCooldown() == 1'
```

## 重生点坐标(bedSpawnX/Y/Z)

```
# 重生点位于1, 1, 1
condition: 'bedSpawnX() == 1 && bedSpawnY() == 1 && bedSpawnY() == 1'
```

## 格挡状态(blocking)

```
# 玩家是否正在格挡
condition: 'blocking()'
```

## 指南针坐标(compassTargetX/Y/Z)

```
# 指南针坐标位于1, 1, 1
condition: 'compassTargetX() == 1 && compassTargetY() == 1 && compassTargetY() == 1'
```

## 本月日期(day/dayOfMonth)(1-31)

```
# 今儿1号
condition: 'day() == 1'
```

## 本周日期(dayOfWeek)(1-7)

```
# 今儿周一
condition: 'dayOfWeek() == 1'
```

## 本年日期(dayOfYear)(1-365)

```
# 今儿元旦
condition: 'dayOfYear() == 1'
```

## 月份(month)(1-12)

```
# 今儿一月
condition: 'month() == 1'
```

## 年份(year)

```
# 今儿3202年了
condition: 'year() == 3202'
```

## 小时(hour)

```
# 现在八点
condition: 'hour() == 8'
```

## 分钟(minute)

```
# 这小时刚过去15分钟
condition: 'minute() == 15'
```

## 秒(second)

```
# 这分钟刚过去15秒
condition: 'second() == 15'
```

## 本月周数(weekInMonth)

```
# 现在是本月第一周
condition: 'weekInMonth() == 1'
```

## 上午/下午(amOrPm)(0/1)

```
# 现在是上午
condition: 'amOrPm() == 0'

# 现在是下午
condition: 'amOrPm() == 1'
```

## 时间戳(time)

```
# 1970年1月1日0时0分0秒到现在, 经过了1000000000毫秒
condition: 'time() == 1000000000'
```

## 死亡状态(dead)

```
# 玩家是否死亡
condition: 'dead()'
```

## 是否首次登录(firstPlay)

```
# 玩家是否首次登录
condition: 'firstPlay()'
```

## 疲劳度(exhaustion)

```
# 玩家疲劳度是否等于0.1
condition: 'exhaustion() == 0.1'

# 将玩家疲劳度设置为0.1, 然后判断一下是否等于0.1以满足条件
condition: 'exhaustion(0.1) == 0.1'
```

## 获取/修改经验值(exp)

```
# 玩家经验值是否等于100
condition: 'exp() == 100'

# 将玩家经验值设置为100, 然后判断一下是否等于100以满足条件
condition: 'exp(100) == 100'
```

## 给予经验(addExp)

```
# 给予100经验(本函数必定返回null)
condition: 'addExp(100) == null'

# 给予100经验,然后判断玩家经验值是否等于100
condition: 'addExp(100);exp() == 100'
```

## 扣除经验(takeExp)

```
# 扣除100经验(本函数必定返回null)
condition: 'takeExp(100) == null'

# 扣除100经验,然后判断玩家经验值是否等于100
condition: 'takeExp(100);exp() == 100'
```

## 获取/修改等级(level)

```
# 玩家等级是否等于100
condition: 'level() == 100'

# 将玩家等级设置为100, 然后判断一下是否等于100以满足条件
condition: 'level(100) == 100'
```

## 给予等级(addLevel)

```
# 给予100等级(本函数必定返回null)
condition: 'addLevel(100) == null'

# 给予100等级,然后判断玩家等级是否等于100
condition: 'addLevel(100);level() == 100'
```

## 扣除等级(takeLevel)

```
# 扣除100等级(本函数必定返回null)
condition: 'takeLevel(100) == null'

# 扣除100等级,然后判断玩家等级是否等于100
condition: 'takeLevel(100);level() == 100'
```

## 获取/修改饥饿度(level)

```
# 玩家饥饿度是否等于10
condition: 'food() == 10'

# 将玩家饥饿度设置为10, 然后判断一下是否等于10以满足条件
condition: 'food(10) == 10'
```

## 给予饥饿度(addFood)

```
# 给予100饥饿度(本函数必定返回null)
condition: 'addFood(00) == null'

# 给予10饥饿度,然后判断玩家饥饿度是否等于10
condition: 'addFood(10);food() == 10'
```

## 扣除饥饿度(takeFood)

```
# 扣除100饥饿度(本函数必定返回null)
condition: 'takeFood(10) == null'

# 扣除10饥饿度,然后判断玩家饥饿度是否等于10
condition: 'takeFood(10);food() == 10'
```

## 获取/修改游戏模式(gamemode)(ADVENTURE/CREATIVE/SPECTATOR/SURVIVAL)

> 字符串记得用引号包起来

```
# 玩家是否处于生存模式
condition: 'gamemode() == "SURVIVAL"'

# 将玩家设置为生存模式, 然后判断是否处于生存模式, 以满足条件
condition: 'gamemode("SURVIVAL");gamemode() == "SURVIVAL"'
```

## 获取/修改滑翔状态(guilding)

```
# 玩家正在滑翔
condition: 'guilding()'

# 设置玩家正在滑翔, 并返回true满足条件
condition: 'guilding(true)'
```

## 获取/修改发光状态(glowing)

```
# 玩家正在发光
condition: 'glowing()'

# 设置玩家正在发光, 并返回true满足条件
condition: 'glowing(true)'
```

## 获取/修改重力状态(gravity)

```
# 玩家是否拥有重力
condition: 'gravity()'

# 设置玩家拥有重力, 并返回true满足条件
condition: 'gravity(true)'
```

## 生命值(health)

```
# 玩家当前生命值大于10
condition: 'health() > 10'
```

## 最大生命值(maxHealth)

```
# 玩家当前最大生命值大于10
condition: 'maxHealth() > 10'
```

## 玩家名(name)

> 字符串记得用引号包起来

```
# 玩家名为Neige
condition: 'name() == "Neige"'
```

## 获取/修改剩余氧气(remainingAir)

```
# 玩家剩余氧气是否等于10
condition: 'remainingAir() == 10'

# 将玩家剩余氧气设置为10, 然后判断一下是否等于10以满足条件
condition: 'remainingAir(10) == 10'
```

## 睡觉状态(sleeping)

```
# 玩家是否正在睡觉
condition: 'sleeping()'
```

## 获取/修改潜行状态(sneaking)

```
# 玩家正在潜行
condition: 'sneaking()'

# 设置玩家正在潜行, 并返回true满足条件
condition: 'sneaking(true)'
```

## 获取/修改疾跑状态(sprinting)

```
# 玩家正在疾跑
condition: 'sprinting()'

# 设置玩家正在疾跑, 并返回true满足条件
condition: 'sprinting(true)'
```

## 获取/修改游泳状态(swimming)

```
# 玩家正在游泳
condition: 'swimming()'

# 设置玩家正在游泳, 并返回true满足条件
condition: 'swimming(true)'
```

## 所处世界(world)

> 字符串记得用引号包起来

```
# 玩家正处在名为world的世界中
condition: 'world() == "world"'
```
