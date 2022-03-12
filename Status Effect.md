# Status Effect
源代码：  

https://github.com/Regalis11/Barotrauma/blob/master/Barotrauma/BarotraumaShared/SharedSource/StatusEffects/StatusEffect.cs  

https://github.com/Regalis11/Barotrauma/blob/master/Barotrauma/BarotraumaShared/SharedSource/Enums.cs

### ActionType

属性|含义  
-|-  
Always|条件一直成立（一直有效）  
OnPicked|捡起来的那一刻  
OnUse|物品使用时
OnSecondaryUse|
OnWearing|穿戴，装备在身体槽位里（非物品栏）  
OnContaining|
OnContained|保存状态（放在物品栏，柜子或工具袋里等）  
OnNotContained|非保存状态（如仍在地上）  
OnActive|激活状态（如手持物品时，获得某种Buff时）  
OnSuccess|
OnFailure|使用失败（和技能有关，如维修接线盒被电）  
OnBroken|耐久为零（condition = 0）
OnFire, InWater, NotInWater|着火，泡水，没有遇水  
OnImpact|受到冲击  
OnEating|
OnDamaged|
OnSevered|
OnProduceSpawned|
OnOpen, OnClose|舱门，电器等实体的开关状态
OnSpawn|
OnAbility|技能生效时（如助手的回光返照，生效时回满活力值）
OnDeath|与`OnBroken`意思相同，表示耐久为零

## Conditional: condition  
源代码：  

https://github.com/Regalis11/Barotrauma/blob/master/Barotrauma/BarotraumaShared/SharedSource/StatusEffects/PropertyConditional.cs

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