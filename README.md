# Barotrauma 潜渊症 源代码笔记
收集整理潜渊症的源代码与相关XML元素的含义，方便制作Mod。  

## 有用的链接
潜渊症源代码：https://github.com/Regalis11/Barotrauma  

官方Mod教程  
内容包：https://barotraumagame.com/wiki/Content_Packages  
生物编辑：https://barotraumagame.com/wiki/Content_Packages/Creation  
~~目前官方教程比较简单，因此本仓库也计划更新教程和更多的范例。~~  

有趣的是官方实际上在Steam创意工坊发布了Mod相关的指南，内容丰富，这也对我的笔记整理大有帮助。  
Mod参考：https://steamcommunity.com/sharedfiles/filedetails/?id=2181462640  
但是要注意的是官方的参考是2020年发布的，并未进行更新，现在的游戏新增了很多元素和属性，这就需要我们继续研究和完善了。

## 参与编辑
如果你不会使用Github，也欢迎你到讨论版（Discussions），直接上传txt文件，我会帮你整合到笔记里。  

当前目标：
1. 汉化官方的Mod参考
2. Items相关元素
3. StatusEffects相关元素

## 教程
在开始之前我们需要知道制作mod涉及到对XML的编辑，虽然电脑自带的记事本程序就可以进行编辑，但是一个好的编辑器会带有语法感知，能够将XML的结构用不同颜色标记出来，非常方便。  
这里推荐**Visual Studio Code**和**Notepad++**，两款都是体积很小的编辑器。

### 如何开始  
有些人刚接触这个做mod，无从下手。首先要知道的是Mod文件保存在`Barotrauma\Mods`，打开此文件夹，会有一个ExampleMod，这个是官方准备的一个结构简单的mod。  
游戏中的Mod都由一个`filelist.xml`和若干其他`.xml`文件以及音频图片素材组成（如果这是一个非常复杂的mod），另外`.sub`是潜艇的文件后缀名。  
其中，`filelist.xml`定义了这个mod包含的所有文件的路径，游戏加载mod只会以该文件内定义的路径为准，所以做完mod，不要忘了完善filelist。

### XML基础
XML指可扩展标记语言，在游戏中用来传输和存储数据。XML和做网站用的HTML很像，都是层层嵌套的。因此需要格外注意开头和结尾，这是最常出现的错误，不能忘了收尾。  
XML由若干个元素组成，元素中可以有定义各种功能参数的属性比如下面这个：  
`<Item identifier="steel" />`  
这行代码能够生成一个钢筋，这就是一个典型的带有属性的元素。另外，注意开头`<`和结尾`/>`的格式。  
除了这种单行的写法，复杂的物品也可能在元素内包括若干个子元素，如下面这个：

    <Deconstruct time="10">
        <Item identifier="steel" />
    </Deconstruct>

注意开头`<Deconstruct>`和结尾`</Deconstruct>`的格式。这段代码定义了某个物品分解需要10秒钟，并分解得到一个钢筋。

### 通过范例学习
游戏内的很多物品本身就是由XML编写的，具体可以在`Barotrauma\Content`中找到，其中`Items`文件夹下就定义了游戏内的各种道具，如武器和工具等。

---

**下面是各类元素的解释**
## Item
创建物品，通常和下列其他元素配合使用，包括各种定义物品各种功能的元素和属性。在以下元素中出现的一些属性也可以直接作为`<Item />`的属性内使用。  

源代码：https://github.com/Regalis11/Barotrauma/blob/master/Barotrauma/BarotraumaShared/SharedSource/Items/ItemPrefab.cs

### RequiredSkill
需要的职业技能，条件逻辑  
原版游戏有5种职业技能分别对应一下5个identifier：  
驾驶（helm），机械维修（Mechanical），电气工程（electrical），医疗（medical），武器操作（weapons）  

属性|含义  
-|-  
identifier|定义需要哪种职业的技能  
level|数值，技能的等级  

### RequiredItem
需要的物品，条件逻辑  

属性|含义
-|-
item|定义需要的物品，使用物品item属性查找
identifier|定义需要的物品，使用物品的identifier属性查找
type|定义需要物品的和当前实体的状态关系，如加工台要求物品必须是摆在加工台内（Contained）
optional|
amount|需要物品的数量，不写则默认为1个
mincondition|物品耐久低于或等于最小状态会被忽略
maxcondition|物品耐久大于最大状态会被忽略
usecondition|bool
ignoreineditor|
excludebroken|

#### RelationType: type
type属性的参数

参数|含义
-|-
None|无明确特殊关系
Contained|需要的物品保存在当前物品内
Equipped|装备在手上
Picked|保存在物品栏里
Container|

### Deconstruct
定义该物品可以被分解

属性|含义
-|-
time|分解需要的时间，单位：秒
chooserandom|是否随机选择分解生成的物品（true/false）（参考物品：废料），物品的随机概率由Item属性`commonness`决定
amount|分解生成物品的数量

#### DeconstructItem
有一些Item的属性适用于Deconstruct

属性|含义
-|-
outcondition|分解生成物品的耐久
copycondition|是否设置生成物品的耐久为被分解物品的耐久（true/false）（如，分解一个用了50%的弹药箱会获得50%的铅）
commonness|该物品生成的概率（0-1）

### IdCard
定义该物品具有ID卡的元素，例如打开舱门和保险柜，会读取一个含有IdCard属性的物品的Tags。理论上如果你的其他物品也具有该属性和对应的权限Tag，同样可以用来开门。  
由于ID卡本质上只有开门这一种功能，没有太大的修改意义，主要还是对Tags进行修改，IdCard内部的属性保持默认即可。

属性|含义
-|-
slots|可以装备的槽位，通常是`“Card，Any”`，可以装备在物品栏和人物卡槽里

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
OnActive|手持物品时  
OnFailure|使用失败（和技能有关，如维修接线盒被电）  
OnBroken|耐久为零（condition = 0）
OnFire, InWater, NotInWater|着火，泡水，没有遇水  
OnImpact|受到冲击  
OnEating|
OnDamaged| 
OnSevered|
OnProduceSpawned|
OnOpen, OnClose|舱门，电器等实体的开关状态
OnDeath|与`OnBroken`意思相同，表示耐久为零

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
||None

## EventManagerSettings
专门用于设置游戏中事件难度的元素  

游戏文件：Barotrauma\Content\EventManagerSettings.xml  

元素|含义
-|-
Easy|简单
Medium|中等
Hard|困难
Hellish|地狱

属性|含义
-|-
Identifier|
Name|
DefaultEventThreshold|默认事件阈值，事件阈值决定了触发新的随机事件需要小于多少密度（intensity）。阈值可能会随事件增长，但在触发新的事件后会重置为默认值。
EventThresholdIncrease|每秒事件阈值的增长量，即使当前的危机仍未解决也会使事件触发，例如：潜艇在海床上搁浅了
EventCooldown|事件冷却，触发新事件的最小时间间隔
MinLevelDifficulty|最小难度等级，大于该值采用该难度等级
MaxLevelDifficulty|最大难度等级，小于该值采用该难度等级
||适配难度的控制条，4个难度等级对应不同的难度百分比，例如：官方默认10%是简单难度
FreezeDurationWhenCrewAway|船员离开时冻结时间，超过50%的非电脑玩家在潜艇外时（出海作业）额外事件不会触发的时间