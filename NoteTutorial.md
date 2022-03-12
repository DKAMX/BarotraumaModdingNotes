# 教程
在开始之前我们需要知道制作Mod涉及到对XML的编辑，虽然电脑自带的记事本程序就可以进行编辑，但是一个好的编辑器会带有语法感知，能够将XML的结构用不同颜色标记出来，非常方便。  
这里推荐**Visual Studio Code**和**Notepad++**，两款都是体积很小的编辑器。

## 如何开始  
有些人刚接触这个做Mod，无从下手。首先要知道的是Mod文件保存在`Barotrauma\Mods`，打开此文件夹，会有一个ExampleMod，这个是官方准备的一个结构简单的Mod。  
游戏中的Mod都由一个`filelist.xml`和若干其他`.xml`文件以及音频图片素材组成（如果这是一个非常复杂的Mod），另外`.sub`是潜艇的文件后缀名。  
其中，`filelist.xml`定义了这个Mod包含的所有文件的路径，游戏加载Mod只会以该文件内定义的路径为准，所以做完Mod，不要忘了完善filelist。

## XML基础
XML指可扩展标记语言，在游戏中用来传输和存储数据。XML和做网站用的HTML很像，都是层层嵌套的。因此需要格外注意开头和结尾，这是最常出现的错误，不能忘了收尾。  
XML由若干个元素组成，**元素**中可以有定义各种功能**参数**的属性比如下面这个：  
`<Item identifier="steel" />`  
这行代码能够生成一个钢筋，其中identifier就是这个元素的属性，而双引号中的steel则是这个属性的值，这就是一个典型的带有属性的元素。  
另外，注意开头`<`和结尾`/>`的格式。  
除了这种单行的写法，复杂的物品也可能在元素内包括若干个子元素，如下面这个：

    <Deconstruct time="10">
        <Item identifier="steel" />
    </Deconstruct>

注意开头`<Deconstruct>`和结尾`</Deconstruct>`的格式。这段代码定义了某个物品分解需要10秒钟，并分解得到一个钢筋。  
如果你想系统的学习XML可以前往菜鸟教程：https://www.runoob.com/xml/xml-tutorial.html  

## 通过范例学习
游戏内的很多物品本身就是由XML编写的，具体可以在`Barotrauma\Content`中找到，其中`Items`文件夹下就定义了游戏内的各种道具，如武器和工具等。
