# 专用命令

专用命令的用法  
用于：Ranks, Scheduler, Portals, EventCommands, Interactive Commands, Kits 和 custom alias.  
- 只能使用一个动作变量，否则将使用最后一个  
- 如果命令包含<b>[playerName]</b>会尽量使用目标玩家的名字，不能在计划任务中使用，因为插件不知道要使用哪个玩家
- 如果命令以<b>msg!</b>开头并且后面带有玩家名，如果该玩家在线的话会发送一条简单的消息给该玩家。例如：**msg! Zrips Hello!**
- 如果命令以<b>broadcast!</b>开头则消息会发送到服务器上的每个人，以没有任何前缀的简单方式
- 如果命令以<b>actionbar!</b>开头则所有玩家都会收到后面定义的动作条消息
- 如果命令以<b>title!</b>开头则所有玩家都会收到后面定义的标题消息
- 如果命令以<b>subtitle!</b>开头则所有玩家都会收到后面定义的子标题消息
- 如果命令以<b>kickall!</b>开头则所有玩家都会被踢出服务器并且提示后面的消息，在重启服务器之前很有用
- 如果命令以<b>asPlayer!</b>开头则会以玩家的身份执行原始命令
- 如果命令以<b>asConsole!</b>开头则会以控制台的身份执行命令，在自定义别名的时候可以用到，当没有指定特定玩家的时候默认以控制台执行
- 如果命令以<b>asFakeOp!</b>开头则会以op身份执行命令。与asConsole有一点点不同，因为你不会接收到任何反馈信息，并且服务器会像真实玩家一样处理命令。这不会像直接在游戏里执行那样，而是作为完全不同的伪op玩家执行。
- 如果命令以<b>cooldown:[timeInSec]!</b>开头则该行或后面的行（如果有）将在使用前具有冷却时间。示例：cooldown:5! cmi heal [playerName]将会治愈玩家，但是只能5秒使用一次，如果5秒内再次使用不会有任何事发生
- 如果命令以<b>perm:[permissionNode]!</b>开头则只有当玩家具有此权限节点才会执行命令。但是如果插件不知道谁是目标玩家时不会起作用
- 如果命令以<b> moneycost:[amount]!</b>开头，如果玩家有足够的钱，命令就会被执行
- 如果命令以<b>hasmoney:[amount]!</b>开头会检查玩家是否有足够的钱，满足条件则继续执行，不满足则停止
- 如果命令以<b>expcost:[amount]!</b>开头并且玩家有足够的经验则会执行
- 如果命令以<b>hasexp:[amount]!</b>开头会检查玩家是否有足够的经验，满足条件则继续执行，不满足则停止
- 如果命令以<b>item:[itemdata](-amount)!</b>开头，如果玩家有足够的物品，则执行命令。例：**item:stone:1-12!** 需要12个花岗岩才会执行命令
- 如果命令以<b>hasitem:[itemdata](-amount)!</b>开头，如果玩家有足够的物品，则执行命令。不会取走物品
- 如果命令以<b>ifonline:[playerName]!</b>开头，如果玩家在线，命令将执行。固定的名字或[playerName]取决于你想要的结果
- 如果命令以<b>ifoffline:[playerName]!</b>开头，如果玩家离线，命令将执行。固定的名字或[playerName]取决于你想要的结果
- 如果命令以<b>ifempty:[hand/offhand/quickbar/armor/inv/subinv]!</b>开头，如果玩家该类型的容器为空则执行命令。Subinv是具有27个空位，打开背包时除去快捷栏的上方3行位置。使用inv类型时，将检查玩家背包的每个物品。可以为quickbar/maininv/subinv类型定义额外的值，例如maininv-5将要求你的主背包内有5个空位，而subinv-10将要求子背包中有10个空位，而quickbar-3将要求快捷栏有3个空位。使用示例：ifempty:maininv-3?! 
- 如果命令以<b>votes:[amount]!</b>开头，如果玩家有足够的票数，命令将会执行
- 插入一行<b>delay! 5</b>将在5秒之后执行后续命令. 这允许你创建示例任务中那样的重启服务器倒计时
    ``` yml
    - cmi launch [playerName]
    - delay! 2
    - cmi launch [playerName]
    ```
- [randomPlayer]占位符可用于获取没有<b>cmi.scheduler.exclude</b>权限节点的随机在线玩家名称。这可用于在特定的时间为随机玩家提供奖励。例如：<b>cmi give [randomPlayer] diamond %rand/1-5%</b>将会给一名在线的随机玩家1到5个钻石
- 如果命令以<b>allPlayers!</b>开头，将在所有在线玩家上执行命令。[allPlayers]应该用于在需要的地方插入玩家名字。例如：<b>allPlayers! cmi heal [allPlayers]</b>将会治愈服务器在线的所有玩家
- 支持<b>PlaceHolderAPI</b>变量
