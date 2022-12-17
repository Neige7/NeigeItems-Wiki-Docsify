# 默认配置

## config.yml

```
Main:
  # MM物品默认保存路径
  MMItemsPath: MMItems.yml
  # 是否开启debug模式
  Debug: false
Messages:
  # 玩家不在线提示
  invalidPlayer: §e[NI] §6玩家不在线或不存在
  # 给予成功提示
  successInfo: §e[NI] §6成功给予 §f{player} §a{amount} §6个 §f{name}
  # 被给予成功提示(设置为""则不进行提示)
  givenInfo: §e[NI] §6你得到了 §a{amount} §6个 §f{name}
  # 给予成功提示
  dropSuccessInfo: §e[NI] §6成功在 §a{world} §6的 §a{x},{y},{z} §6掉落了 §a{amount} §6个 §f{name}
  # 未知物品提示
  unknownItem: §e[NI] §6找不到ID为 §a{itemID} §6的物品
  # 对应ID物品已存在提示
  existedKey: §e[NI] §6已存在ID为 §a{itemID} §6的物品
  # 未知解析对象提示
  invalidPaser: §e[NI] §6不能针对后台解析物品, 请指定一个玩家
  # 保存成功提示
  successSaveInfo: §e[NI] §6成功将 §f{name} §6以ID §a{itemID} §6保存至 §a{path}
  # MM物品转换完毕提示
  mMImportSuccessInfo: §e[NI] §6成功将所有MM物品保存至 §a{path}
  # 物品列表内, 点击获取物品提示
  clickGiveMessage: §e点击获取该物品
  # 不要保存空气提示
  airItem: §e[NI] §6请不要试图保存空气, 谢谢合作
  # 输入无效数字提示
  invalidAmount: §e[NI] §6无效数字
  # 输入无效世界提示
  invalidWorld: §e[NI] §6无效世界
  # 输入无效坐标提示
  invalidLocation: §e[NI] §6无效坐标
  # 权限不足提示
  insufficientPermissions: §e[NI] §6权限不足
  # 未发现前置插件提示
  invalidPlugin: §e[NI] §6未发现前置插件: {plugin}
  # 物品冷却提示
  itemCooldown: §e物品冷却中! 请等待{time}秒
  # 重载完毕提示
  reloadedMessage: §e[NI] §6重载完毕
  # 无效NBT提示
  invalidNBT: §6[NI] §cNBT加载失败, 请勿在列表型NBT中混用键值对, 数字及字符串
  # 错误物品提示
  invalidItem: '§6[NI] §c物品加载失败, 物品可能缺损数据, 物品ID: §6{itemID}'
  # 给予失败提示
  failureInfo: '§e[NI] §6物品给予失败, 可能原因: 物品未配置材质/玩家已下线'
  # 缺少前置插件提示
  invalidPlugin: '§e[NI] §6未发现前置插件: {plugin}'
  # 未指定物品解析对象提示
  invalidParser: §e[NI] §6不能针对后台解析物品, 请指定一个玩家
  # 物品冷却提示
  itemCooldown: §e物品冷却中! 请等待{time}秒
  # 物品列表内, 点击获取物品提示
  clickGiveMessage: §e点击获取该物品
  # 掉落物归属提示信息
  invalidOwnerMessage: §6无法拾取该物品, 该物品的拥有者是 §f{name}
  # 帮助信息
  helpMessages:
  - §6====================§eNeigeItems§6====================
  - §6==================[]为必填, ()为选填==================
  - §e/ni §flist (页码) §7> 查看所有NI物品
  - §e/ni §fget [物品ID] (数量) (是否反复随机) (指向数据) §7> 根据ID获取NI物品
  - §e/ni §fgive [玩家ID] [物品ID] (数量) (是否反复随机) (指向数据) §7> 根据ID给予NI物品
  - §e/ni §fgiveAll [物品ID] (数量) (是否反复随机) (指向数据) §7> 根据ID给予所有人NI物品
  - §e/ni §fdrop [物品ID] [数量] [世界名] [X坐标] [Y坐标] [Z坐标] (是否反复随机) (物品解析对象) (指向数据) §7>
    于指定位置掉落NI物品
  - §e/ni §fsave [物品ID] (保存路径) §7> 将手中物品以对应ID保存至对应路径
  - §e/ni §fcover [物品ID] (保存路径) §7> 将手中物品以对应ID覆盖至对应路径
  - §e/ni §fmm load [物品ID] (保存路径) §7> 将对应ID的MM物品保存为NI物品
  - §e/ni §fmm cover [物品ID] (保存路径) §7> 将对应ID的MM物品覆盖为NI物品
  - §e/ni §fmm loadAll (保存路径) §7> 将全部MM物品转化为NI物品
  - §e/ni §fmm get [物品ID] (数量) §7> 根据ID获取MM物品
  - §e/ni §fmm give [玩家ID] [物品ID] (数量) §7> 根据ID给予MM物品
  - §e/ni §fmm giveAll [物品ID] (数量) §7> 根据ID给予所有人MM物品
  - §e/ni §freload §7> 重新加载NI物品
  - §e/ni §fhelp §7> 查看帮助信息
  - §6=================================================
# 物品列表格式
ItemList:
  Prefix: §6===========§eNeigeItems§6===========
  Suffix: §6======<< §e{prev} §f{current}§e/§f{total} §e{next} §6>>======
  ItemAmount: 10
  ItemFormat: §6{index}. §a{ID} §6- §f{name}
  Prev: 上一页
  Next: 下一页

```
## GlobalSections/ExampleSection.yml

```
global-strings-1:
  # 随机字符节点
  type: strings
  values:
  - test1
  - test2
global-number-1:
  # 随机数节点
  type: number
  # 随机数最小值
  min: 1
  # 随机数最大值
  max: 2
  # 小数保留位数
  fixed: 3
global-calculation-1:
  # 公式节点
  type: calculation
  # 计算公式
  formula: 1+2+3<global-number-1>
  # 公式结果最小值
  min: 1
  # 公式结果最大值
  max: 100
  # 小数保留位数
  fixed: 3
global-weight-1:
  # 权重字符串节点
  type: weight
  values:
  # 权重::字符串内容
  - 5::第一行
  - 1::第二行
global-js-1:
  # JavaScript节点
  type: js
  # 脚本路径
  path: ExampleScript.js::main

```
## Items/ExampleItem.yml

```
ExampleItem:
  # 物品材质
  material: LEATHER_HELMET
  # 物品CustomModelData(适用于1.14+)
  custommodeldata: 1
  # 物品损伤值
  damage: 1
  # 物品名
  name: §6一件皮革甲
  # 物品Lore
  lore:
  - 'PAPI变量测试: %player_level%'
  - '16进制颜色测试: <#ABCDEF>好耶'
  - '私有简单节点测试: <simple-1>'
  - '私有字符串节点测试: <strings-1>'
  - '私有随机数节点测试: <number-1>'
  - '私有公式节点测试: <calculation-1>'
  - '私有权重节点测试: <weight-1>'
  - '私有JavaScript节点测试: <js-1>'
  - '即时声明字符串节点测试: <strings::number-1_weight-1>'
  - '即时声明随机数节点测试: <number::0_10_0>'
  - '即时声明公式节点测试: <calculation::1+1+3+<number-1>_2>'
  - '即时声明权重节点测试: <weight::5::权重文本1_1::权重文本2>'
  - '即时声明papi节点测试: <papi::<papiString-1><papiString-2>>'
  - '即时声明JavaScript节点测试: <js::ExampleScript.js::main>'
  - '全局节点调用测试: <global-strings-1>'
  - '嵌套识别测试: <<strings-1>>'
  - '文本中小于号请添加反斜杠, 防止错误识别'
  - '形如: \<\<\<\>\>\>'
  - '请尽量避免使用即时声明节点'
  - "换行符测试\n换行符测试"
  # 物品附魔
  enchantments:
    ARROW_DAMAGE: 1
    ARROW_KNOCKBACK: 1
  # 物品隐藏标识
  hideflags:
  - HIDE_ATTRIBUTES
  - HIDE_DESTROYS
  # 物品颜色(适用于药水/皮革装备)
  color: 65535
  # 额外选项
  options:
    charge: 10
    color: GOLD
  # 物品NBT
  nbt:
    # NBT中也可以随机调用节点
    <strings::文本1_文本2_文本3_文本4>: 114514
    # 可以在NBT中编辑物品的原版属性
    AttributeModifiers:
    - Amount: 10
      AttributeName: minecraft:generic.max_health
      Operation: 0
      UUID:
      - 0
      - 31453
      - 0
      - 59664
      Name: generic.maxHealth
  # 引用的全局节点
  globalsections:
  # 这种直接填写文件名的方式可以直接调用文件内的全部全局节点
  # - ExampleSection.yml
  - global-strings-1
  - global-number-1
  # 物品私有节点
  sections:
    simple-1: <strings::text1_text2_text3>
    strings-1:
      type: strings
      values:
      - 测试文本1
      - 测试文本2
    number-1:
      type: number
      min: 1
      max: 2
      fixed: 3
    calculation-1:
      type: calculation
      formula: 1+2+3<number-1>+<number-1>
      min: 1
      max: 100
      fixed: 3
    weight-1:
      type: weight
      values:
      - 5::第一行
      - 1::第二行
    js-1:
      type: js
      path: ExampleScript.js::main
    papiString-1:
      type: strings
      values:
      - "player_"
    papiString-2:
      type: strings
      values:
      - "name"
ExampleItem2:
  material: STONE
ExampleItem3:
  material: STONE
ExampleItem4:
  material: STONE
  name: "&f%neigeitems_nbt_NeigeItems.id%"
  lore:
  - '&f物品使用次数: %neigeitems_charge%/%neigeitems_maxCharge%'
  options:
    charge: 10
    
# 一个测试模板
template1:
  material: IRON_SWORD
  lore:
  - "&e攻击伤害: &f<damage>"
  nbt:
    MMOITEMS_ATTACK_DAMAGE: (Double) <damage>
# 一个测试模板
template2:
  material: DIAMOND_SWORD

# 一个全局继承测试, 它继承了"template1"的所有内容
templateItem1:
  inherit: template1
  name: §f物品继承测试
  sections:
    damage: 100
# 一个部分继承测试, 它继承了"template1"的lore, 以及"template2"的material
templateItem2:
  inherit: 
    lore: template1
    material: template2
  name: §f物品继承测试
  sections:
    damage: 100
# 一个顺序继承测试, 它将按顺序进行节点继承. 先继承"template1"的所有内容，再继承"template2"的所有内容
templateItem3:
  inherit:
  - template1
  - template2
  name: §f物品继承测试
  sections:
    damage: 100'

inheritSectionTest:
  material: STONE
  lore:
  - <templateTest>
  - <inheritTest>
  - <inherit::templateTest>
  sections:
    templateTest: <strings::text1_text2_text3>
    inheritTest:
      type: inherit
      template: templateTest
actionTest:
  material: STONE
  name: <test>
  nbt:
    test1: "666"
    test2: 
      test3: "777"
    test4:
    - "888"
    - "999"
  sections:
    test: "yeah"
customSection:
  material: STONE
  lore:
    - '自定义节点测试: <test-1>'
    - '自定义节点测试: <test::test_test_test>'
  sections:
    test-1:
      type: test
      values:
        - test
        - test
        - test
        - test
eatTest:
  material: APPLE
eatTest2:
  material: APPLE
  options:
    charge: 10
dropTest:
  material: STONE
dropTest2:
  material: STONE
  options:
    charge: 3
ownerTest:
  material: STONE
  name: 你捡我啊
  options:
    # 通过/ni drop或击杀MM怪物掉落该物品, 该物品首次拾取只能由Neige完成
    # 你可以在此处填写%player_name%, 这样就是谁击杀就属于谁了
    # 首次拾取后将不再有掉落物归属效果
    # 服务器重启后效果重置(掉了, 关服了, 再次开服, 谁都能捡)
    owner: Neige
CustomAction:
  all:
  - "test"
itemTimeTest:
  material: STONE
  name: 限时物品-到期时间-<js::ItemTime.js::main_<itemtime>>
  options:
    itemtime: <itemtime>
  sections:
    itemtime: 60

```
## Scripts/ExampleScript.js

```
function main() {
    if (typeof this.player != "undefined") {
        return this.vars("<strings-1>") + this.player.getName()
    } else {
        return this.vars("<strings-1>")
    }
}

```
## ItemActions/ExampleAction.yml

```
# 物品ID
ExampleItem:
  # 消耗选项
  consume:
    # 冷却时间(单位是ms)
    cooldown: 3000
    # 冷却组, 同一冷却组的物品共享冷却时间
    group: test1
    # 每次消耗物品数量
    amount: 1
    # 左键行为是否消耗物品
    left: true
    # 右键行为是否消耗物品
    right: true
  # 左键执行指令
  left:
  # 后台执行
  - "console: say He's name is %player_name%"
  # 玩家执行
  - "command: say My name is %player_name%"
  # 右键执行指令
  right: 
  - "console: say He's name is %player_name%"
  - "command: say My name is %player_name%"
  # 左/右键都会执行的指令
  all: 
  - "console: say He's name is %player_name%"
  - "command: say My name is %player_name%"
ExampleItem2:
  consume:
    cooldown: 3000
    amount: 10
    left: true
    right: true
  all: 
  - "console: say He's name is %player_name%"
  - "command: say My name is %player_name%"
ExampleItem3:
  # 物品使用冷却
  cooldown: 3000
  # 冷却组, 同一冷却组的物品共享冷却时间
  group: test2
  all: 
  - "console: say He's name is %player_name%"
  - "command: say My name is %player_name%"
ExampleItem4:
  consume:
    cooldown: 3000
    amount: 1
    left: true
    right: true
  all: 
  - "console: say He's name is %player_name%"
  - "command: say My name is %player_name%"
actionTest:
  all: 
  - "console: say 名为test1的NBT的值为: <nbt::test1>"
  - "console: say 名为test2.test3的NBT的值为: <nbt::test2.test3>"
  - "console: say 名为test4.0的NBT的值为: <nbt::test4.0>"
  - "console: say 名为test4.1的NBT的值为: <nbt::test4.1>"
  - "console: say 名为test的节点的值为: <data::test>"
  - "console: say 随机数尝试: <number::0_10_2>"
eatTest:
  eat:
  - "giveFood: 5"
  - "giveHealth: 5"
eatTest2:
  consume:
    cooldown: 3000
    amount: 1
    eat: true
  eat:
  - "giveFood: 5"
  - "giveHealth: 5"
dropTest:
  drop:
  - "castSkill: SkillTest"
dropTest2:
  consume:
    cooldown: 3000
    amount: 1
    drop: true
  drop:
  - "castSkill: SkillTest"
CustomAction:
  material: STONE

```
## CustomSection/CustomSection.js

```
// 文件名不重要, 写成啥都行
// main函数会自动执行
function main() {
    // 导入相应的类, 这两行看不懂的话直接抄就行
    const SectionManager = Packages.pers.neige.neigeitems.manager.SectionManager.INSTANCE
    const CustomSection = Packages.pers.neige.neigeitems.section.impl.CustomSection
    const SectionUtils = Packages.pers.neige.neigeitems.utils.SectionUtils

    // 创建自定义节点
    const customSection = new CustomSection(
        // 节点id
        "test",
        /**
         * 用于私有节点解析
         * @param data ConfigurationSection 节点内容
         * @param cache HashMap<String, String>? 解析值缓存
         * @param player OfflinePlayer? 待解析玩家
         * @param sections ConfigurationSection? 节点池
         * @return 解析值
         */
        function(data, cache, player, sections) {
            if (data.contains("values")) {
                // SectionUtils.parseSection("待解析字符串", cache, player, sections)用于解析节点内容
                return SectionUtils.parseSection("<number::0_1_2>", cache, player, sections)
            }
            return null
        },
        /**
         * 用于即时节点解析
         * @param args List<String> 节点参数
         * @param cache HashMap<String, String>? 解析值缓存
         * @param player OfflinePlayer? 待解析玩家
         * @param sections ConfigurationSection? 节点池
         * @return 解析值
         */
        function(args, cache, player, sections) {
            return SectionUtils.parseSection("<number::0_1_2>", cache, player, sections)
        })
    // 节点注册
    SectionManager.loadParser(customSection)
}

```
## CustomActions/CustomAction.js

```
// 文件名不重要, 写成啥都行
// main函数会自动执行
function main() {
    // 导入相应的类, 这两行看不懂的话直接抄就行
    const ActionManager = Packages.pers.neige.neigeitems.manager.ActionManager.INSTANCE
    const SectionUtils = Packages.pers.neige.neigeitems.utils.SectionUtils

    // 插入新的自定义动作
    ActionManager.addAction(
        // 动作名称
        "test",
        // 动作内容(一般是异步调用的, 所以需要同步执行的内容需要自行同步)
        function(player, string) {
            // 调用动作
            ActionManager.runAction(player, "tell: 123")
            ActionManager.runAction(player, "tell: 456")
            player.sendMessage(SectionUtils.parseSection("<number::0_10_2>"))
            // 每个动作都一定要返回一个布尔量(true或false), 返回false相当于终止一连串动作的执行
            return true
        })
}

```
## ItemPacks/ExampleItemPack.yml

```
Example1:
  Items:
  # 支持解析即时声明节点
  # [物品ID] (数量(或随机最小数量-随机最大数量)) (生成概率) (是否反复随机) (指向数据)
  - ExampleItem 1-5 0.5
  - test
  FancyDrop:
    # 偏移量
    offset:
      # 横向偏移量(或随机最小偏移量-随机最大偏移量)
      x: 0.1
      # 纵向偏移量(或随机最小偏移量-随机最大偏移量)
      y: 0.8
    angle:
      # 抛射类型(round/random)
      type: round
Example2:
  Items:
  - <test>
  FancyDrop:
    offset:
      x: 0.1
      y: 0.8
    angle:
      type: round
  # 引用的全局节点
  globalsections:
  # 这种直接填写文件名的方式可以直接调用文件内的全部全局节点
  # - ExampleSection.yml
  - global-strings-1
  - global-number-1
  # 物品私有节点
  sections:
    test:
      type: strings
      values:
      - ExampleItem 5 1
      - ExampleItem 10 1
      
```
## Scripts/ItemTime.js

```
function main(time) {
    const date = new Date()
    date.setTime(date.getTime() + (Number(time) * 1000))
    return date.getFullYear() + "年" + (date.getMonth() + 1) + "月" + date.getDate() + "日" + date.getHours() + "时" + date.getMinutes() + "分" + date.getSeconds() + "秒"
}

```