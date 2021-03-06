# 动态告示牌

此功能让你拥有一个文字可以根据配置更新的告示牌。它可以为看到它的人显示个性化的文字或者为每个人单独显示特定文本。

在示例中你可以通过添加适当的占位符来显示玩家余额，显示玩家当前拿着的物品价格等等。

不局限于你可以显示的内容，并且可以有超过4行的内容，会自动滚动显示所有内容。

想创建动态告示牌，首先要在地上放置一个告示牌。告示牌的内容不重要，甚至可以放一个空告示牌。

接下来，指针对着告示牌并输入<b>/cmi dsign new testSign</b>之类的内容。

你会发现周围出现粒子效果，这表示玩家在哪个区域内出现会更新告示牌。因此，站在粒子效果外的玩家不会在服务器上造成不必要的负载，因为当玩家看不到文字时，不需要更新。

执行第一个命令后，你会接收到聊天消息，看起来像这个样子

让我们为这个告示牌添加一些行。在此示例中，让它显示你手中物品的价值。就跟你在gif中看到的一样。

单击[+]符号，然后输入第一行

```
%cmi_iteminhand_realname%
```

这是CMI的占位符，用于显示玩家当前手持物品的名称。按下回车，接下来再输入两行

```
%cmi_iteminhand_amount%
&7Worth: %cmi_iteminhand_worth%
```

最终结果就像这样

默认情况下，告示牌会5秒更新一次。因此，让我们把它修改成更适合此功能的间隔

点击<打开菜单>你会打开一个新的窗口。找到一个标着更新间隔的按钮，并将其修改为1秒。

就这样。告示牌已将创建好，它将为每个人自动更新。

还有就是你可以将告示牌设置为非私人的，这样就不会为每个人而是为满足特定信息的人更新告示牌。如果你只是想向玩家显示普通的信息（例如在线人数），这是一种更好的方法。

你也可以修改告示牌更新的范围，可以设置为更宽或者更窄，并且在不需要告示牌时避免更新。如果不需要则使用默认值，但是可以修改总是好的。

gif的最后一个功能来自于[交互式命令](https://www.zrips.net/cmi/commands/interactive-commands/)