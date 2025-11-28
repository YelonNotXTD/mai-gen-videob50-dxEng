# 导入国际服/日服B50的相关说明

> 基于[MMBL](https://myjian.github.io/mai-tools/)工具导出数据的B5和AP50读取正在测试中，如遇问题还请在QQ群(994702414)内反馈！

## 快速使用

a. 进入您所在服务器maimai DX NET的Rating对象乐曲页面，复制HTML源代码备用
或
b. 进入[DXrating](https://dxrating.net/rating)网站导入数据并导出B50的JSON文件，复制文件中的内容备用
或
c. 使用[MMBL](https://myjian.github.io/mai-tools/)工具导出您的全部成绩，复制备用

按照应用页面引导操作，注意在应用内导入B50时选择`导入B50数据源代码`并粘贴。之后根据您导入的类型选择对应的读取按钮。

### A. 从maimai DX NET(官网)获取B50数据的HTML源代码

1. 打开[国际服Maimai DX NET](https://maimaidx-eng.com/maimai-mobile/home/ratingTargetMusic/)或[日服Maimai DX NET](https://maimaidx.jp/maimai-mobile/home/ratingTargetMusic/)并进入Rating对象乐曲页面。

> 日服maimai DX NET的rating对象乐曲页面属于SEGA的付费项目，价格为330円/月。

2. 等待页面加载完毕后，按`Ctrl + U` 或 右键>>点击`查看网页源代码`（这个选项卡的名称可能因浏览器不同而有些许差别）。在新打开或跳转至的页面中，全选复制所有内容备用。

### B. 从DXrating网站获取B50数据的JSON源代码

1. 打开[DXrating](https://dxrating.net/rating)，可以在网页中部右侧找到`IMPORT`、`EXPORT`等按钮。点击`IMPORT`并选择`Import from offical maimai NET...`，然后根据弹窗说明完成数据导入。

2. 导入完毕后，注意页面中央的maimai logo处选择正确的区服。然后点击`EXPORT`并选择`Export JSON (Only B50 records)`，浏览器会下载一个名字形如`dxrating.export-{导出时间}.json`的文件，复制其中的内容备用。
   
   - 打不开Json文件？您可能需要在弹出的打开方式窗口中选择`记事本`，或右键点击`以记事本打开`，或将其后缀改为`.txt`等类似方式。如果都不适用，还请搜索`如何打开Json文件`。

   - 以此法获取的数据可能由于[DXrating](https://dxrating.net/rating)的数据更新缓慢导致部分曲目不正确，或大版本更新前后的B15版本不正确。

### C. 通过[MMBL](https://myjian.github.io/mai-tools/)工具导出官网成绩（支持AP50！）

前往[MMBL](https://myjian.github.io/mai-tools/)官网，按照其中指引使用该工具。使用该工具在官网导出您的全部分数并复制，注意在导出分数时应包括所有可选的条目，尤其是谱面定数（Chart Constant）。

## 如何使用获取的源代码

在通过上述操作获取根据一种数据后，请按照[使用说明](../README.md/#使用说明)的步骤继续使用。在应用内获取B50时，选择`从多种数据源导入B50（国际服/日服）`，确定您的数据源类型并将复制的内容粘贴到指定输入框内，最后点击`从粘贴内容创建新存档`。

## 插件特性

- 使用保存的`Rating对象乐曲`网页作为B50信息的读取源，替代国服使用的水鱼查分器获取B50；

- 也可以使用[DXrating](https://dxrating.net/)网站导出的B50 Json文件作为数据源。

## 开发状态与计划

- [x] 歌曲列表文件的自动更新同步（来自主分支v0.6~1.0的数据库更新）；

- [x] 改变成绩的获取来源，以获取DX score、FC等级、FS等级；（NEW: MMBL导出的数据若包含，则可以自动录入。）

- [x] 支持其他数据源的AP50。（NEW: MMBL数据源允许用户筛选AP50！）

## 常见问题

- 读取HTML时，报错`Error: HTML screw (type = "XXXXXX") not found.`

请检查查看源代码的网页是否是DX Rating对象乐曲界面。在乐曲加载完毕之前操作也可能导致这个问题。
> 自v0.4.1版本起已经支持**日服**Rating对象乐曲界面的读取，但功能可能不稳定。如果您导入**日服**数据出现了这个问题，请联系开发者。

- 生成B50图片时，报错`list index out of range`

该问题的大概率诱因是您的B50包含某个歌曲数据库未收录的白谱，您可以在自定义修改成绩页面手动更正。

- B50定数显示不正确？
  
对于官网HTML/Dxrating JSON导入，这可能是因为歌曲数据库未同步导致的。您可以手动修改正确的定数或联系开发者更新数据库。
对于MMBL导入，请确认输出分数时是否包含了谱面定数（Chart Constant）。如果依旧错误，则是MMBL数据库的问题。

> 以下是较为古老版本可能预见的问题

- 显示`已找到谱面视频的缓存`，但是不是正确的谱面确认视频

如果显示的缓存视频名称结构为`-XX-Y-DX.mp4`，例如`-39-3-DX.mp4`，说明这是上一次下载视频时有缺少内部id的曲目并留下了缓存视频。
您可以删除对应文件或修改其名称，然后尝试重新下载。

- 下载视频后许多谱面都指向同一个`None-3-DX.mp4`（或相似的以None开头的名称）

这是一个在`v0.3.3`版本的常见问题，原因是太新的曲目并没有一个内部id，请更新到更新版本。

## 引用

[maimaiDX-songs](https://github.com/Becods/maimaiDX-songs) 更新更热的歌曲数据库

[DXrating](https://dxrating.net/) 第三方maimai曲库和B50处理网页

[MMBL]