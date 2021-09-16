# Barotrauma 潜渊症 源代码笔记
收集整理潜渊症的源代码与相关XML元素的含义，方便制作Mod。  

## 有用的链接
潜渊症源代码：https://github.com/Regalis11/Barotrauma  

官方Mod教程：  
内容包 https://barotraumagame.com/wiki/Content_Packages  
生物编辑 https://barotraumagame.com/wiki/Content_Packages/Creation  
目前官方教程比较简单，因此本仓库也计划更新教程和更多的范例。

## 参与编辑
如果你不会使用Github，也欢迎你到讨论版（Discussions），直接上传txt文件，我会帮你整合到笔记里。  

## 教程
### XML基础
XML指可扩展标记语言，在游戏中用来传输和存储数据。XML和做网站用的HTML很像，都是层层嵌套的。因此需要格外注意开头和结尾，这是最常出现的错误，不能忘了收尾。  
XML由若干个元素组成，元素中可以有定义各种功能参数的属性比如下面这个：  
`<Item identifier="steel" />`  
这行代码能够生成一个钢筋，这就是一个典型的带有属性的元素。另外，注意开头`<`和结尾`/>`的格式。  
除了这种单行的写法，复杂的物品也可能在元素内包括若干个子元素，如下面这个：

    <Deconstruct time="10">
        <Item identifier="steel" />
    </Deconstruct>
这段代码定义了某个物品分解需要10秒钟，并分解得到一个钢筋。

### 通过范例学习
游戏内的很多物品本身就是由XML编写的，具体可以在`Barotrauma\Content`中找到，其中`Items`文件夹下就定义了游戏内的各种道具，如武器和工具等。

---

**下面是各类元素的解释**
## Item
创建物品，通常和下列其他元素配合使用  
包括各种定义物品各种功能的元素和属性  

源代码：https://github.com/Regalis11/Barotrauma/blob/master/Barotrauma/BarotraumaShared/SharedSource/Items/ItemPrefab.cs

### RequiredSkill
职业技能  
驾驶（helm），机械维修（Mechanical），电气工程（electrical），医疗（medical），武器操作（weapons）  

属性|含义  
-|-  
identifier|定义需要哪种职业的技能  
level|数值，技能的等级  

### RequiredItem
需要的物品，条件逻辑  

属性|含义
-|-
identifier|定义需要的物品
amount|需要物品的数量，不写则默认为1个
minCondition|
maxCondition|
useCondition|

## Status Effect: type
源代码：https://github.com/Regalis11/Barotrauma/blob/master/Barotrauma/BarotraumaShared/SharedSource/Enums.cs

属性|含义  
-|-  
Always|条件一直成立（一直有效）  
OnPicked|捡起来的那一刻  
OnUse, OnSecondaryUse|使用时，按住右键鼠标（左手或右手手持，如瞄准）  
OnWearing|穿戴，装备在身体槽位里（非物品栏）  
OnContaining, OnContained|保存状态（放在物品栏，柜子或工具袋里等）  
OnNotContained|非保存状态（如仍在地上）  
OnActive|左右鼠标同时按下  
OnFailure|使用失败（和技能有关，如维修接线盒被电）  
OnBroken|耐久为零（condition）
OnFire, InWater, NotInWater|着火，泡水，没有遇水  
OnImpact|受到冲击  
OnEating|
OnDamaged| 
OnSevered|
OnProduceSpawned|
OnOpen, OnClose|舱门，电器等实体的开关状态
OnDeath = OnBroken|两种状态意思相同，表示耐久为零

## Conditional: condition  
源代码：https://github.com/Regalis11/Barotrauma/blob/master/Barotrauma/BarotraumaShared/SharedSource/StatusEffects/StatusEffect.cs

### OperatorType
属性|含义  
-|-  
e, eq, equals|Equals，等于  
ne, neq, notequals, !, !e, !eq, !equals|NotEquals，不等于  
lt, lessthan|LessThan，小于
lte, lteq, lessthanequals|LessThanEquals，小于等于
gt, greaterthan|GreaterThan，大于
gte, gteq, greaterthanequals|GreaterThanEquals，大于等于
|None
