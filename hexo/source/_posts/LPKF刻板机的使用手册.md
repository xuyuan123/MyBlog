
---
title: LPKF刻板机的使用手册
date: 2016-05-31 16:06:35
author: XuYuan
categories: manual
tags: [刻板机, manual]

---

刻板机主要是采用高精度的机械加工来进行PCB电路板的刻制，精度高，可控性好，比传统的腐蚀法制电路板有很多优势。LPKF是德国的一家刻板机公司，是目前比较流行的刻板机。本文介绍了LPKF S63型号的刻板机的简单的使用说明。

<!--more-->

## Gerber文件生成
1. PCB 设计常用的设计软件有[Altium Designer](http://www.altium.com.cn/)， 使用AD设计出来的PCB文件的后缀名为`.pcbdoc`，我们需要将该文件转成Gerber文件再传给LPKF刻板机进行加工制作。
2. 使用Altium Designer 软件打开`.pcbdoc`文件，选择**file/fabrication output/gerber files**， 弹出Gerber setup对话框。
3. 在general标签页中，选择单位为：**inch**；精度为：**2：5**；
4. 在layer标签页中，Plot Layers选择Used On； Mirror Layers选择All Off；
5. 在Advanced标签页中，选择suppress leading zero； reference to relative origin; 
6. 设置完成后，点击OK，即可在`.pcbdoc`对应文件夹下生成每个layer对应的gerber文件。
7. 生成孔文件。还是打开`.pcbdoc`文件，选择**file/fabrication output/NC drill files**， 弹出NC drill setup对话框。
8. 在option标签页中选择和之前相同的设置，点击OK确定。在弹出的Import Drill Date 对话框中设置单位与前面设置相同。点击OK即可生成孔文件。

-----
Gerber 文件后缀名与相应layer的对照表：


|文件|layer|
|:--:|:--:|
|.GTO|Top Overlay|
|.GBO|Bottom Overlay|
|.GKO|Keepout layer|
|.GTL|Top layer|
|.GBL|Bottoim layer|
|.TXT|钻孔文件|

## 文件导入

1. 打开刻板机电源。
2. 打开电脑端软件CircuitPro，电脑自动识别并连接到仪器。
3. 在菜单栏选择`File`$\Longrightarrow$`New`，在出现的模板文件里选择DoubleSided ProConduct.cbf，点击OK。
4. 在菜单栏选择`File`$\Longrightarrow$`Import`，在弹出的对话框中，选择之前生成的几个Gerber文件，重点是：**.GTL(TopLayer)**, **.GBL(BottomLayer)**, **.TXT(drill plated)**, **.GKO(Board Outline)**这四个文件。
5. 根据文件后缀名与层的对应关系，在Layer/Template中将每个文件分配到对应的层上面。

## 设置剥铜区域和靶标，并进行计算

1. 设置剥铜区域。在菜单栏选择`Insert`$\Longrightarrow$`Rubout area`$\Longrightarrow$`Rubout top`，然后在图中由两点创建一个矩形的剥铜区域。创建完成后点击CLOSE。
2. 设置靶标。在菜单栏选择`Insert`$\Longrightarrow$`Fiducial`$\Longrightarrow$`Fiducial...`，在PCB板子四周点上四个点，即创建了四个靶标，创建完成后点击CLOSE。
3. 开始计算切割路径。在菜单栏选择`Toolpath`$\Longrightarrow$`Technology Dialog`，在Insulate绝缘设置中选择4/4,全部剥铜，在Coutour Routing切割轮廓中选择3/6，表示轮廓切割时横向留两个断点。在Drills的Show Details中不勾选Create marking drills，不勾选Pockets。点击Start开始计算，计算完成之后直接Close即可。

## 装配刀具

1. 在菜单栏选择`Edit`$\Longrightarrow$`Tool Magazine`，打开刀具配置对话框。
2. 在对话框右侧会显示本次切割所需要的刀具，有红色`X`表示的是当前刀具架上没有该刀，需要往刀具架上添加该刀。
3. 在对话空右侧对应刀位的下拉框中选择需要添加的刀具的类型大小，并手动打开仪器盖子，在该刀具位置添加相对应的刀具，注意两者一定要相一致。

## 开始切割加工

1. 在Processing标签页中，Operate项目下拉框中选择Process All，点击绿色三角符号开始运行，请注意每一步的提示信息。所有的步骤在Toolpath标签页中的Phase中显示，其中前面带小三角符号的表示该步骤需要某一刀具进行加工，展开该项即可看到该步骤详情。
2. 也可以一步一步执行，一般建议这样操作。现在Toolpath标签页中的Phase中选择要执行的步骤（一般需要执行的步骤前面会有一个小三角符号，展开该项即可看到这一步骤所需要的刀具信息），选中该步骤之后再切换回Processing标签页，在Operate项目中点击绿色三角符号开始执行当前步骤。
3. 一般进行切割时首先要先打靶标，然后先背面刻Bottom层，将板子翻转180度，再在正面刻top层。每一步刻板过程中都会有提示是否识别靶标，尽量每一步都选择识别靶标，以防不同层刻制时出现错位。
4. 如果要进行孔金属化，那么孔一般最后打。在所有正反面图形以及轮廓都铣完和切割完之后，需要在正反面贴上一张薄膜，然后再进行打孔。打完孔之后在膜上面涂上银浆，然后将银浆从孔里面吸到下表面，实现将孔金属化将双层板两面导通。然后再将电路板放入高温烘烤半个小时，温度设为300摄氏度。烘烤烘烤完成之后揭掉表面的薄膜，再超声清洗一下，电路板即制作完成了。
