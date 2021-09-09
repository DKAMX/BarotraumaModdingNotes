# Barotrauma 潜渊症 源代码笔记
收集整理潜渊症的源代码与相关XML参数的含义，方便制作Mod

## 参与编辑
如果你不会使用Github，也欢迎你到讨论版（Discussions），直接上传txt文件，我会帮你整合到笔记里。  

## Status Effect enum: ActionType
源代码：Barotrauma/BarotraumaShared/SharedSource/Enums.cs  

Always，一直  
OnPicked，捡起来的那一刻  
OnUse, OnSecondaryUse，使用时，按住右键鼠标（左手或右手手持，如瞄准）  
OnWearing，穿戴，装备在身体槽位里（非物品栏）  
OnContaining, OnContained，保存状态（放在物品栏，柜子或工具袋里等）  
OnNotContained，非保存状态（如仍在地上）  
OnActive，左右鼠标同时按下  
OnFailure, OnBroken,  
OnFire, InWater, NotInWater，着火，泡水，没有遇水  
OnImpact，收到冲击  
OnEating  
OnDamaged  
OnSevered  
OnProduceSpawned  
OnOpen, OnClose,  
OnDeath = OnBroken，两种状态意思相同，表示耐久为零（condition）  
