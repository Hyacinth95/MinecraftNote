# 任务计划

schedule.yml文件的作用是在特定的时间或指定的时间间隔执行重复命令。可以用来发广播或执行一些预设任务，例如重启服务器或者在满足特定条件时触发命令  

支持CMI和  PlaceHolderAPI占位符

可以用到的设置：  

Enabled: (true/false)只有设置为true的计划会自动启用。记住/cmi schedule [计划名]将会触发该计划，即时已经设置为false(禁用)

任务计划可以有两种类型：1.以固定的时间间隔（以秒为单位） 2.在特定的时间执行

Dalay: (数字) 定义每个动作之间要等待多长时间，600表示10分钟执行一次动作

PerformOn: 定义要执行命令的特定时间。应该定义时间的单位和值
可以有：Month,Day,Hour,Minute,Second这几种单位，后面跟数字格式，使用24小时格式  
例如  
``` yml
PerformOn:
  FirstTimeFrame:
    Hour: 4
  SecondTimeFrame:
    Hour: 22
    Minute: 30
```
这会将命令设置为在凌晨04:00和22:30执行。是在线人数较少时，控制服务器备份的好方法。

Day: [dayOfMonth/weekday] 你可以设置每月的第几天（几号），如Day: 5，也可以设置为Day: Sunday这样的星期几，会自动在每个星期天执行计划任务

Repeat: (true/false) 如果设置为false，则任务只会执行一次，否则，将每隔一段时间或在特定的时间重复一次

MinPlayers: (数量) 如果没有足够的玩家在线，则在任务启动的那一刻就跳过计划任务

MaxPlayers: (数量) 如果玩家数量超过这个值，则跳过任务

FeedBack: (true/false) 如果设置为false，则在没有足够的玩家执行此任务的情况下不会在控制台中反馈消息

Commands: 时间正确时要执行的命令列表。这里用到了[专用命令](http://www.zrips.net/cmi/commands/specialized/)

[randomPlayer]占位符可用于获取没有cmi.scheduler.exclude权限节点的随机在线玩家名称。这可用于在特定的时间为随机玩家提供奖励。例如：– cmi give [randomPlayer] diamond %rand/1-5% 将会给一名在线的随机玩家1到5个钻石

[allPlayers]占位符可用于对所有玩家执行命令。例如：– cmi heal [allPlayers] 将会治愈所有在线玩家

``` yml
# 每10分钟保存一次地图
saveMaps:
  Enabled: false
  Delay: 600
  Repeat: true
  Commands:
  - save-all
# 每天18点的时候，如果在线人数超过两位则随机给一位在线玩家1到5个钻石
GiveDiamonds:
  Enabled: false
  MinPlayers: 3
  Repeat: true
  PerformOn:
    1:
      Hour: 18  
  Commands:
  - cmi give [randomPlayer] diamond %rand/1-5%
  - msg! [randomPlayer] &eYou just got diamonds!
# 在3:59:30停止服务器，并在此之前发出30秒警告和一些重复消息
StopServer:
  Enabled: false
  PerformOn:
    1:
      Hour: 3
      Minute: 59
      Second: 30
  Commands:
  - actionbar! &eServer will stop in &630 &esec!
  - delay! 5
  - actionbar! &eServer will stop in &625 &esec!
  - delay! 5
  - actionbar! &eServer will stop in &620 &esec!
  - delay! 5
  - actionbar! &eServer will stop in &615 &esec!
  - delay! 5
  - actionbar! &eServer will stop in &610 &esec!
  - delay! 5
  - actionbar! &eServer will stop in &65 &esec!
  - delay! 1
  - actionbar! &eServer will stop in &64 &esec!
  - delay! 1
  - actionbar! &eServer will stop in &63 &esec!
  - delay! 1
  - actionbar! &eServer will stop in &62 &esec!
  - delay! 1
  - actionbar! &eServer will stop in &61 &esec!
  - delay! 1
  - kickall! &eServer will be back online soon!
  - delay! 1
  - stop
# 包含所有设置的示例任务
AllInOneJustExample:
  Enabled: false
  MinPlayers: 3
  MaxPlayers: 10
  Delay: 600
  Repeat: true
  PerformOn:
    1:
      Month: 12 
      Day: Monday    
      Hour: 18    
      Minute: 36
      Second: 15   
    2: 
      Hour: 18
  Commands:
  - cmi give [randomPlayer] diamond %rand/1-5%
  - msg! [randomPlayer] &eYou just got diamonds!
  - broadcast! &e[randomPlayer] just got some stuff! 
  - delay! 1
  - actionbar! &eServer will stop in &61 &esec!
  - kickall! &eServer will be back online soon!
// Shows random message from the list every 10 minutes
Announcer:
  Enabled: false
  MinPlayers: 1
  Delay: 600
  Repeat: true
  Randomize: true
  Commands:
  - broadcast! &eRules can be found at &e/rules
  - broadcast! &eKits can be accesed with &e/kits
  - broadcast! &eIf you need help, ask staff
  - broadcast! &eAdvertisement of other servers will be punished
```