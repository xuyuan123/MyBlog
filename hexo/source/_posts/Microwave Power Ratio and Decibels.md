---

title: Microwave Power Ratio and Decibels
date: 2016-03-10 10:32:35
author: XuYuan
categories: Microwave
tags: [分贝, Microwave]

---

在微波系统中常常用分贝来表示系统中两个功率之比，这样的好处是可以很容易的计算通过一系列元件后的功率损耗或者增益，每一级的损耗或增益因子的相乘可以用分贝表示的增益或损耗的相加来计算。

<!--more-->

# 分贝（dB）的定义：

$$dB=10\lg{\frac{P_1}{P_2}}$$

> 功率比为2等效于3dB
> 功率比为0.1等效于-10dB

- 可以得到功率比与分贝之间的关系：
$$\frac{P_1}{P_2}=10^{\frac{dB}{10}} $$
- 由功率与电压的关系：$P_1={V_1^2}/{R_1}$，$P_2={V_2^2}/{R_2}$，可进一步得到分贝与电压比的关系：
$$dB=20\lg{\frac{V_1}{V_2} \sqrt{\frac{R_2}{R_1}}}$$
- 当负载电阻$R_1=R_2$时：
$$\frac{V_1}{V_2}=10^{\frac{dB}{20}}$$

# 功率（W）与dBm之间的关系

- 假定$P_2$为参考功率：$P_2=1mW$，$P_1$的功率可以用dBm表示：
$$dBm=10\lg{\frac{P_1}{1mW}}$$

	- 1mW 对应 0dBm
	- 1W 对应 30dBm
	- 0.1mW 对应 -10dBm
