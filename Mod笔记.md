# Barotrauma 潜渊症 源代码笔记
by DKAMX

## Status Effect enum: ActionType
源代码：Barotrauma/BarotraumaShared/SharedSource/Enums.cs  

Always，一直  
OnPicked，捡起来的那一刻  
OnUse, OnSecondaryUse，捡起来的那一刻，按住右键（左手或右手手持）  
OnWearing，准备在身体槽位里（非物品栏）  
OnContaining, OnContained，保存状态（放在物品栏，柜子或工具袋里等）  
OnNotContained，非保存状态（如仍在地上）  
OnActive, OnFailure, OnBroken,  
OnFire, InWater, NotInWater，着火，泡水，没有遇水  
OnImpact，收到冲击  
OnEating  
OnDamaged  
OnSevered  
OnProduceSpawned,  
OnOpen, OnClose,  
OnDeath = OnBroken，两种状态意思相同，表示耐久为零（condition）  