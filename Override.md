## Override
用于定义需要替换的元素块  
使用范例1：  

    <Override>
		<Item name="Potato Gun" identifier="harpoongun">
			内容代码省略...
		</Item>
	</Override>

这段代码会替换官方的鱼叉枪的名字（name）为Potato Gun，通过`identifier`来确定被替换的物品。  
此外，如果修改了内容代码或是添加了新的功能，原版物品也会有对应的改变。  

使用范例2：  
也许我们需要替换大量物品，可以在更高层级进行替换。  

    <Override>
        <Items>
            <Item name="" ...>
                ...
            </Item>
            内容代码省略...
        </Items>
    </Override>

这段代码会将`<Items></Items>`下包含的所有物品都进行替换，通过`identifier`来确定被替换的物品。  
