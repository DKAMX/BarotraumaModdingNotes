# EventManagerSettings
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
DefaultEventThreshold|默认事件阈值，事件阈值决定了触发新的随机事件需要小于多少密度（intensity）。阈值可能会随事件增长，但在触发新的事件后会重置为默认值
EventThresholdIncrease|每秒事件阈值的增长量，即使当前的危机仍未解决也会使事件触发，例如：潜艇在海床上搁浅了
EventCooldown|事件冷却，触发新事件的最小时间间隔
MinLevelDifficulty|最小难度等级，大于该值采用该难度等级
MaxLevelDifficulty|最大难度等级，小于该值采用该难度等级
||适配难度的控制条，4个难度等级对应不同的难度百分比，例如：官方默认10%是简单难度
FreezeDurationWhenCrewAway|船员离开时冻结时间，超过50%的非电脑玩家在潜艇外时（出海作业）额外事件不会触发的时间