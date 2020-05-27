# Kill All

<b>/cmi killall</b> 让你可以提供条件来清除当前加载的实体  
默认情况下，具有自定义名字的实体不会被清除  
船或矿车中的实体将被忽略  
可以提供范围来实现只清除附近的实体  
<b>-monsters</b> 会清除所有怪物类型的实体。一般包括僵尸，小白，凋零等  
<b>-pets</b> 将包括任何可以驯服的实体，例如马和狼
<b>-npc</b> 将包括具有CPC元数据的实体，通常指Citizens之类的插件的产物  
<b>-animals</b> 删除动物类型的实体，例如猪或牛  
<b>-ambient</b> 蝙蝠等实体  
<b>-named</b> 自定义名字的任何实体  
<b>[mobType]</b> 可以通过定义怪物类型来只删除对应类型的怪物  
<b>-f</b> 将怪物，宠物，npc，傀儡，动物，环境，车辆等组合到一起  
<b>-lightning</b> 在实体被清除的地方降下闪电  
<b>-list</b> 打印出适当类别的实体

例子：
<b>/cmi killall</b> - 清除所有怪物
<b>/cmi killall 60</b> - 清除以你为中心60个方块内的怪物
<b>/cmi killall zombie</b> - 清除所有僵尸
<b>/cmi killall zombie skeleton</b> - 清除所有僵尸和小白
<b>/cmi killall -list</b> 列出所有实体
<b>/cmi killall -monsters -lightning</b> - 移除所有怪物，并在每个实体被移除的地方降下一道闪电
