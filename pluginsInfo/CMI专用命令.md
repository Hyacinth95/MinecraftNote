# 专用命令

专用命令的用法  
用于：Ranks, Scheduler, Portals, EventCommands, Interactive Commands, Kits 和 custom alias.  
- 只能使用一个动作变量，否则将使用最后一个  
- 如果命令包含<b>[playerName]</b>会尽量使用目标玩家的名字，不能在计划任务中使用，因为插件不知道要使用哪个玩家
- 如果命令以<b>msg!</b>开头并且后面带有玩家名，如果该玩家在线的话会发送一条简单的消息给该玩家。例如：**msg! Zrips Hello!**
- 如果命令以<b>broadcast!</b>开头则消息会发送到服务器上的每个人，以没有任何前缀的简单方式
- 如果命令以<b>actionbar!</b>开头则所有玩家的动作栏都会显示后面的消息
- 
