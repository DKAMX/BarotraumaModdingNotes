# Barotrauma 潜渊症 源代码笔记
收集整理潜渊症的源代码与相关XML参数的含义，方便制作Mod

## 参与编辑
如果你不会使用Github，也欢迎你到讨论版（Discussions），直接上传txt文件，我会帮你整合到笔记里。  

## Status Effect: ActionType
源代码：Barotrauma/BarotraumaShared/SharedSource/Enums.cs  

参数|含义  
-|-  
Always | 条件一直成立（一直有效）  
OnPicked | 捡起来的那一刻  
OnUse, OnSecondaryUse | 使用时，按住右键鼠标（左手或右手手持，如瞄准）  
OnWearing | 穿戴，装备在身体槽位里（非物品栏）  
OnContaining, OnContained | 保存状态（放在物品栏，柜子或工具袋里等）  
OnNotContained | 非保存状态（如仍在地上）  
OnActive | 左右鼠标同时按下  
OnFailure | 使用失败（和技能有关，如维修接线盒被电）  
OnBroken | 耐久为零（condition）
OnFire, InWater, NotInWater | 着火，泡水，没有遇水  
OnImpact | 受到冲击  
OnEating 
OnDamaged 
OnSevered 
OnProduceSpawned 
OnOpen, OnClose | 舱门，电器等实体的开关状态
OnDeath = OnBroken | 两种状态意思相同，表示耐久为零

## Conditional: condition  
源代码：Barotrauma/BarotraumaShared/SharedSource/StatusEffects/PropertyConditional.cs  

### OperatorType
参数|含义  
-|-  
e, eq, equals | Equals，等于  
ne, neq, notequals, !, !e, !eq, !equals | NotEquals，不等于  
lt, lessthan | LessThan，小于
lte, lessthanequals | LessThanEquals，小于等于
gt, greaterthan| GreaterThan，大于
gte, greaterthanequals | GreaterThanEquals，大于等于
| None
