# Contentpackage
用于定义内容包中含有的数据，例如物品、文本、贴图等。通常用于编写Mod核心文件`filelist.xml`。  

源代码：https://github.com/Regalis11/Barotrauma/blob/master/Barotrauma/BarotraumaShared/SharedSource/ContentPackage.cs  

属性|含义
-|-
name|Mod的名称，名称必须和filelist所在的文件夹同名
path|filelist相对于游戏根目录的路径，参考游戏自带的`ExampleMod`
corepackage|定义该Mod是否为核心包，例如官方的Vanilla内容包就是一个核心包
||因为XML数据的结构是统一的，Vanilla也可以看作是官方出的Mod。核心包只能有一个，并且对包含的内容有强制要求（见`ContentType`），而Mod可以有多个。
gameversion|定义内容包兼容的版本，版本不能向前兼容。例如15.0版本可以打开14.9的Mod，相反则不可以
steamworkshopid|创意工坊的id，用于校验当前用户是否订阅了某个Mod，本地测试无需填写
installtime|下载次数，用于游戏内工坊页面的展示，本地测试无需填写

## ContentType
用于定义内容包可以包含的数据的类型，例如物品、文本、贴图等，都是有效的类型。  

||标记X的文件类型表示有以下所述的要求|
-|-
MD5|表示这些类型的文件会进行MD5校验，意味着多人房间中每位玩家必须使用同样的文件。
Core|表示核心包必须包含这些类型的文件才能生效。

元素|含义|MD5|Core
-|-|-|-
None|未指定类型，通常用途定义物品贴图，音效等其他文件用到的内容
Submarine|潜艇`.sub`
Jobs|定义游戏内所有职业的文件，包括NPC使用的隐藏职业，如VIP|X|X
Item|物品文件，如`Tool.xml`|X|X
ItemAssembly|物品组件（物品组件指的是ItemAssemblies文件夹下包含的文件）
Character|生物的定义文件，如`Human.xml`|X|X
Structure|定义游戏内使用的装饰类物品，如潜艇墙面的贴图|X|
Outpost|前哨站`.sub`|X|
OutpostModule|前哨战模块`.sub`，用于地图生成的一个模块|X|
OutpostConfig|用于生成前哨站布局的参数|X|
BeaconStation|信标`.sub`|X|X
NPCSets|NPC的类型以及变种，如海盗船长有海盗船长和海盗王两种|X|
Factions|定义游戏内出现的阵营|X|X
Text|翻译文本，参考`Barotrauma\Content\Texts`下的各个文件夹||X
ServerExecutable|||X
LocationTypes|定义游戏内地图里出现的地点类型，如城市，自然群落等|X|X
MapGenerationParameters|用于生成大地图的参数|X|X
LevelGenerationParameters|用于生成巡回关卡的参数|X|X
CaveGenerationParameters|用于生成巡回内洞穴的参数|X|X
LevelObjectPrefabs||X|
RandomEvents|定义随机事件的文件，如`randomevents.xml`（刷怪表）和`OutpostEvents.xml`||X
Missions|定义游戏内可以接到的任务|X|X
BackgroundCreaturePrefabs|
Sounds|游戏里各类音效的定义文件，如BGM，碰撞音效等
RuinConfig|用于生成遗迹布局的参数|X|X
Particles|粒子特效的定义文件
Decals|
NPCConversations|NPC对话所使用的文本，和Text类似，每种语言有自己的文件
Afflictions|定义游戏内生物可以获得的各种buff，debuff|X|X
Tutorials|游戏内置的教程所用的定义文件
UIStyle|定义游戏内各种物品的交互界面，如文件定义了导航台按钮的布局||X
TraitorMissions|叛徒任务，用于多人的内鬼模式
EventManagerSettings|用于定义游戏各难度，事件刷新的参数等||X
Orders|定义游戏中人物所使用的所有命令，如操作反应堆，维修机械等|X|X
SkillSettings|定义游戏中人物进行各种操作可以获得的经验值，如定义治疗队友一次可以获得多少经验值
Wreck|沉船`.sub`|X|X
Corpses|尸体，用于沉船的随机生成，定义了尸体携带的物品等|X|X
WreckAIConfig|沉船AI逻辑|X|X
UpgradeModules|定义游戏中潜艇可以购买的升级项|X|X
MapCreature|定义游戏中丘脑的参数|X|
EnemySubmarine|海盗潜艇`.sub`|X|X
Talents|定义游戏中各种天赋的具体效果|X|X
TalentTrees|定义游戏中各大职业的天赋树
