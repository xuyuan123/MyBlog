---
title: Matlab connect Vector Network Analyzer E5071C with GPIB
date: 2017-04-5 15:10:35
author: XuYuan
comments: true
toc: true
categories: matlab
tags: [matlab E5071 GPIB]

---

这篇文章讲述了如何通过MATLAB用GPIB线连接到网络分析仪E5071C，并通过MATLAB采集网络分析仪上的S参数的数据。也可以利用MATLAB获取网络分析仪上的设置的各项参数，同时也能利用MATLAB对网络分析仪的巨大部分参数进行设置。所有的MATLAB的源代码已经上传在[我的GitHub仓库][1]里了，有需要的可以去下载，这里只简单介绍如何使用这些函数。

<!--more-->

### 1. 写在最前面
在用MATLAB控制网络分析仪之前，首先应该打开网络分析仪，设置其GPIB号，并将GPIB线与电脑相连接。
接下来最重要的一步就是要让MATLAB连接到你的网络分析仪。
```@matlab
VNA = VNA_connect('GPIB0::6::INSTR');
```
这个connect函数只有一个输入变量，为网络分析仪的GPIB号。connect函数的输出变量VNA为对应网络分析仪的一个类。后面所有的操作都必须要保证你的MATLAB工作区变量中有VNA这个变量。

### 2. 网络分析仪常见操作的实现
经常使用网络分析仪的可能会经常使用到某些功能，绝大部分功能都是可以通过MATLAB直接控制的。这里给出了大部分网络分析仪功能的MATLAB实现的函数。

- 设置或获取网络分析仪的power:
```@matlab
results = VNA_SweepPower(VNA,-40);  % 设置网分当前的power为 -40dBm；
results = VNA_SweepPower(VNA);  % 获取网分当前的power；
```
- 设置或获取start frequency：
```@matlab
results = VNA_SweepSart(VNA,5e9);  % 设置网分当前的start frequency 为5GHz；
results = VNA_SweepSart(VNA);  % 获取网分当前的start frequency；
```
- 设置或获取stop frequency：
```@matlab
results = VNA_SweepStop(VNA,15e9);  % 设置网分当前的stop frequency 为15GHz；
results = VNA_SweepStop(VNA);  % 获取网分当前的stop frequency；
```
- 设置或获取center frequency：
```@matlab
results = VNA_SweepCenter(VNA,8e9);  % 设置网分当前的center frequency 为8GHz；
results = VNA_SweepCenter(VNA);  % 获取网分当前的center frequency；
```
- 设置或获取span:
```@matlab
results = VNA_SweepSpan(VNA,3e9);  % 设置网分当前的span 为3GHz；
results = VNA_SweepSpan(VNA);  % 获取网分当前的span；
```
- 设置或获取网分当前测量类型：
```@matlab
results = VNA_MeasType(VNA,sparameter);  % 设置网分当前的测量类型，其中第二个参数可以是{'S11', 'S12', 'S21', 'S22'}中的任意一个；
results = VNA_MeasType(VNA);  % 获取网分当前的测量类型；
```
- 设置或获取网分当前测量类型：
```@matlab
results = VNA_DataFormat(VNA,foamat);  % 设置网分当前的数据类型，其中第二个参数可以是{'MLOG', 'PHAS', 'REAL', 'IMAG'}中的任意一个，分别对应大小，相位，实部和虚部；
results = VNA_DataFormat(VNA);  % 获取网分当前的数据类型；
```
- 设置网分restart average：
```@matlab
VNA_AvegRestart(VNA);  % 设置网分restart average
```
- 设置网分当前图形auto scale：
```@matlab
VNA_AutoScale(VNA);  % 设置网分当前图形auto scale;
```
- 其他的常用的网分控制函数：
```@matlab
results = VNA_RfoutputStates(VNA); % 获取当前网分的Rf output的状态；
results = VNA_RfoutputStates(VNA,states); % 设置网分的Rf output打开或关闭，states可以是{'ON', 'OFF'}中的任意一个；
results = VNA_AvegCount(VNA); % 获取当前网分的average factor；
results = VNA_AvegCount(VNA,counts); % 设置当前网分的average factor为counts；
results = VNA_AvegStates(VNA); % 获取当前网分的average状态是否打开；
results = VNA_AvegStates(VNA,states); % 设置网分的average状态为打开或关闭，states可以是{'ON', 'OFF'}中的任意一个；
```

### 3. MATLAB采集网分上的数据
在第二部分常见的这些网分操作的基础上，我们可以直接利用MATLAB采集网分上的数据。
```@matlab
results = VNA_GetCurrentCurve(VNA,savefilename,'170405');
```
该函数自动采集当前网分上显示的图形，并保存该数据到本地电脑的'D:/data/170405/'文件夹下，以savefilename命名的文件。其中第三个参数可以不写，默认为今天的日期。
当然也可以采集特定S参数，特定数据格式的网分数据。
```@malab
results = VNA_GetSparameters(VNA,savefilename,datestring,Sparameter,format);
```
其中format可以不写，默认为'MLOG'; Sparameter 也可以不写，默认为'S21'; datestring 也可以不写，默认为今天的日期。
也可以直接将4个S参数都采集下来，用下面的这个函数：
```@matlab
results = VNA_Get4Sparameters(VNA,savefilename,datestring,format);
```
后面两个参数为默认参数，和上面的一样。这个函数直接将四个S参数全部采集下来并画在一张图上保存在本地电脑上。

在这些函数的基础上可以进一步定制更多的功能。比如说改变power采集网分的S参数数据，或者是改变另外一个设备Yoko的电压，采集网分的S参数， 等等。。。

### 4. Summary
这篇文章简单总结了利用MATLAB控制网络分析仪E5071的基本的函数功能，能够实现绝大部分的数据采集工作。并且能够在此基础上定制更多的功能。目前这些代码也并非是非常的完善，可能也会存在很多问题，基本上没有任何错误和异常的处理操作，所以感兴趣的朋友可以联系我共同完善这些代码。
所有的MATLAB源代码都已经上传在[我的GitHub仓库][2]里，欢迎下载使用。MATLAB源代码编写过程中参考了[E5071官方的说明文档][3]。


  [1]: https://github.com/xuyuan123/matlab_VNA
  [2]: https://github.com/xuyuan123/matlab_VNA
  [3]: http://ena.support.keysight.com/e5071c/manuals/webhelp/eng/