# Item
创建物品，通常和下列其他元素配合使用，包括各种定义物品各种功能的元素和属性。在以下元素中出现的一些属性也可以直接作为`<Item />`的属性内使用。  

源代码：https://github.com/Regalis11/Barotrauma/blob/master/Barotrauma/BarotraumaShared/SharedSource/Items/ItemPrefab.cs

## RequiredSkill
需要的职业技能，条件逻辑  
原版游戏有5种职业技能分别对应一下5个identifier：  
驾驶（helm），机械维修（Mechanical），电气工程（electrical），医疗（medical），武器操作（weapons）  

属性|含义  
-|-  
identifier|定义需要哪种职业的技能  
level|数值，技能的等级  

## RequiredItem
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

### RelationType: type
type属性的参数

参数|含义
-|-
None|无明确特殊关系
Contained|需要的物品保存在当前物品内
Equipped|装备在手上
Picked|保存在物品栏里
Container|

## Deconstruct
定义该物品可以被分解

属性|含义
-|-
time|分解需要的时间，单位：秒
chooserandom|是否随机选择分解生成的物品（true/false）（参考物品：废料），物品的随机概率由Item属性`commonness`决定
amount|分解生成物品的数量

### DeconstructItem
有一些Item的属性适用于Deconstruct

属性|含义
-|-
outcondition|分解生成物品的耐久
copycondition|是否设置生成物品的耐久为被分解物品的耐久（true/false）（如，分解一个用了50%的弹药箱会获得50%的铅）
commonness|该物品生成的概率（0-1）

## IdCard
定义该物品具有ID卡的元素，例如打开舱门和保险柜，会读取一个含有IdCard属性的物品的Tags。理论上如果你的其他物品也具有该属性和对应的权限Tag，同样可以用来开门。  
由于ID卡本质上只有开门这一种功能，没有太大的修改意义，主要还是对Tags进行修改，IdCard内部的属性保持默认即可。

属性|含义
-|-
slots|可以装备的槽位，通常是`“Card，Any”`，可以装备在物品栏和人物卡槽里
