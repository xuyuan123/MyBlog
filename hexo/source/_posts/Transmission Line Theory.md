---

title: Transmission Line Theory of 《Microwave Engineering》
date: 2016-03-9 08:32:35
author: XuYuan
categories: Microwave
tags: [Transmission line, Microwave]

---

传输线理论是微波工程中的一个很重要的基本知识，它把微波的场分析理论和基本电路理论联系了起来。本文介绍传输线理论的基本知识框架。

<!--more-->

# 传输线的集总元件模型
- 微波的波长在3m到3mm之间，对应的频率为300MHz到300GHz之间。
- 电路理论假定网络的物理尺寸比电波长小很多，电压的幅值和相位在整个电路中不发生变化；
- 传输线尺度与电波长量级相当，为分布参量网络，电压或电流的幅值和相位都可能发生变化。
- 等效模型：无穷小长度$\delta z$的一段传输线等效为一个集总元件电路，对应的集总元件参数为：

> $R$：两导体单位长度的串联电阻，$\Omega /m$。来源于两导体的有限电导率。
> $L$：两导体单位长度的串联电感，$H/m$。两导体的总自感。
> $G$：单位长度的并联电导，$S/m$。来源于两导体间填充材料的介电损耗。
> $C$：单位长度的并联电容，$F/m$。来源于两导体的紧密贴近。

![传输线理论的等效电路模型][1]

- 利用基尔霍夫电压定律和电流定律可得：
$$v(z,t)-R\Delta zi(z,t)-L\Delta z\frac{\partial i(z,t)}{\partial t}-v(z+\Delta z,t)=0$$
$$i(z,t)-G\Delta zv(z+\Delta z,t)-C\Delta z\frac{\partial v(z+\Delta z,t)}{\partial t}-i(z+\Delta z,t)=0$$
- 由上面两式可得到**传输线方程**（电报方程）：
$$\frac{\partial v(z,t)}{\partial t}=-Ri(z,t)-L\frac{\partial i(z,t)}{\partial t}$$
$$\frac{\partial i(z,t)}{\partial t}=-Gv(z,t)-C\frac{\partial v(z,t)}{\partial t}$$
- 对于简谐稳态，具有余弦型含时分量。上面两式可简化为：
$$\frac{dV(z)}{dz}=-(R+j\omega L)I(z)$$
$$\frac{dI(z)}{dz}=-(G+j\omega C)V(z)$$

# 传输线上的波传播

- 联立上面关于$V(z)$和$I(z)$的方程可得：
$$\frac{d^2V(z)}{dz^2}-\gamma^2V(z)=0$$
$$\frac{d^2I(z)}{dz^2}-\gamma^2I(z)=0$$
其中$\gamma=\alpha+j\beta=\sqrt{(R+j\omega L)(G+j\omega C)}$为复传播常数。
- 由上面两个方程可以求得其行波解：
$$V(z)=V_0^+e^{-\gamma z}+V_0^-e^{\gamma z}$$
$$I(z)=I_0^+e^{-\gamma z}+I_0^-e^{\gamma z}$$
- $e^{-\gamma z}$代表沿$+z$方向传播的波，$e^{\gamma z}$代表沿$-z$方向传播的波。
- 根据$I(z)$和$V(z)$之间的关系可得：
$$I(z)=\frac{\gamma}{R+j\omega L}\left[V_0^+e^{-\gamma z}-V_0^-e^{\gamma z} \right]$$
- 定义**特征阻抗**$Z_0$：
$$Z_0=\frac{R+j\omega L}{\gamma}=\sqrt{\frac{R+j\omega L}{G+J\omega C}}$$
- 特征阻抗联系了传输线上的电压和电流。
$$\frac{V_0^+}{I_0^+}=Z_0=\frac{-V_0^-}{I_0^-}$$
- 对应电流可以表示为：
$$I(z)=\frac{V_0^+}{Z_0}e^{-\gamma z}-\frac{V_0^-}{Z_0}e^{\gamma z}$$
- 进一步时域形式的电压波形可表示为：
$$v(z,t)=\left|V_0^+ \right|\cos(\omega t-\beta z+\phi^+)e^{-\alpha z}+\left|V_0^- \right|\cos(\omega t+\beta z+\phi^-)e^{\alpha z}$$

- 传输线上波长：$\lambda=\frac{2\pi}{\beta}$
- 相速为：$v_p=\frac{\omega}{\beta}=\lambda f$

# 无耗传输线

- 对于一般传输线而言，损耗都比较小，可以忽略。也就是说：$R=G=0$
$$\gamma=\alpha+j\beta=j\omega\sqrt{LC}$$
$$\beta=\omega\sqrt{LC}$$
$$\alpha=0$$

- 特征阻抗为：
$$Z_0=\sqrt{\frac{L}{C}}$$

- 无耗传输线的电压和电流为：
$$V(z)=V_0^+e^{-j\beta z}+V_0^-e^{j\beta z}$$
$$I(z)=\frac{V_0^+}{Z_0}e^{-j \beta z}-\frac{V_0^-}{Z_0}e^{j \beta z}$$ 

- 波长：$\lambda=\frac{2\pi}{\beta}=\frac{2\pi}{\omega \sqrt{LC}}$
- 相速：$v_p=\frac{\omega}{\beta}=\frac{1}{\sqrt{LC}}$

# 端接负载的无耗传输线

![端接负载的无耗传输线][2]

- 由上面$z$处的电压和电流公式，可以得到$z=0$处的电压和电流，以及它们与负载阻抗之间的关系：
$$Z_L=\frac{V(0)}{I(0)}=\frac{V_0^+ + V_0^-}{V_0^+ -V_0^-} Z_0$$

- 由上面公式可以反解出$V_0^-$
$$V_0^-=\frac{Z_L-Z_0}{Z_L+Z_0} V_0^+ $$

- 定义**电压反射系数：**$\Gamma$，表示入射电压波的振幅与反射电压波的振幅之比。
$$\Gamma=\frac{Z_L-Z_0}{Z_L+Z_0}$$

- 将$\Gamma$代入无耗传输线的的电压和电流公式中可得：
$$V(z)=V_0^+ \left[ e^{-j\beta z}+\Gamma e^{j\beta z} \right]$$
$$I(z)=\frac{V_0^+}{Z_0}\left[ e^{-j \beta z}-\Gamma e^{j \beta z} \right]$$ 

- 当负载阻抗$Z_L$等于传输线的特征阻抗$Z_0$时，电压反射系数$\Gamma =0$，此时只有入射波，没有反射波。这样的负载称为**匹配负载**。

- 考虑传输线上$z$处的时间平均功率流：
$$P\_{avg}=\frac{1}{2} Re \left[ V(z) I(z)^\* \right] = \frac{1}{2} \frac{\left| V\_0^+ \right| ^2}{Z\_0} Re  \left[ 1 - \Gamma^\* e^{-2j \beta z } + \Gamma e^{2j\beta z} -\left| \Gamma \right|^2 \right] \\
=  \frac{1}{2} \frac{\left| V\_0^+ \right|^2}{Z_0} \left(1-\left| \Gamma \right|^2 \right)$$

	+ 负载匹配时，$\Gamma =0$，传送到负载的功率最大；
	+ 负载阻抗远大于传输线本征阻抗时，$\Gamma =1$，没有功率传到负载。
	
- 定义回波损耗（return loss）:（以dB为单位）
$$RL=-20\lg{\left| \Gamma \right| } dB$$
	- 匹配负载（$\Gamma=0$）具有$\infty$ dB 的回波损耗（无反射功率）；
	- 全反射（$\left| \Gamma \right|=1$）具有0 dB的回波损耗（所有的入射功率都被反射回来了）。
	
- 传输线上电压幅值随距离$z$的变化：
$$\left| V(z) \right| = \left| V_0^+ \right| \left| 1+\Gamma e^{2j\beta z} \right|= \left| V_0^+ \right| \left| 1+\Gamma e^{-2j\beta l} \right| = \left| V_0^+ \right| \left| 1+\left| \Gamma \right| e^{j(\theta-2 \beta z)} \right|$$

	- 其中$l=-z$, $\theta$是反射系数的相位（$\Gamma = \left| \Gamma \right| e^{j \theta}$）。
	- 电压幅值随传输线的距离$z$的变化而周期性震荡变化。
	- 当相位项$e^{j(\theta-2\beta l)}=1$时，电压幅值出现最大值：$$V_{max} =\left| V_0^+ \right| (1+\left| \Gamma \right| ) $$
	- 当相位项$e^{j(\theta-2\beta l)}=-1$时，电压幅值出现最大值：$$V_{min} =\left| V_0^+ \right| (1-\left| \Gamma \right| ) $$
	- 定义**电压驻波比**：$$ SWR=\frac{V\_{max}}{V\_{min}} = \frac{1+\left| \Gamma \right|}{1-\left| \Gamma \right|} $$
		- 电压驻波比SWR为实数，且$1 \le SWR \le  \infty $ 
		- $SWR =1 $ 对应负载匹配。
	- 相邻两个电压最大值（或最小值）之间的距离为：$l={2\pi}/{2 \beta}=\lambda /2$
	
- 传输线上$z=-l$处的反射系数可以表示为：$$\Gamma (l) = \frac{V_0^- e^{-j\beta l}}{V_0^+ e^{j\beta l}} = \Gamma (0) e^{-2j\beta l} $$
	- 其中：$\Gamma (0)$是$z=0$ 处的反射系数。

- 在传输线上距离负载$z=-l$距离处，朝负载看去的输入阻抗为：$$Z_{in} = \frac{V(-l)}{I(-l)} = \frac{V_0^+ \left[ e^{j\beta l}+\Gamma e^{-j\beta l} \right]}{V_0^+ \left[ e^{j \beta l}-\Gamma e^{-j \beta l} \right]} Z_0 $$
- 将反射系数$\Gamma $的表达式代入上式，进一步可以得到**传输线的阻抗方程**：
$$Z_{in} =Z_0 \frac{Z_L + jZ_0 \tan{\beta l} }{Z_0 + jZ_L \tan{\beta l} } $$

## 负载短路的无耗传输线

![负载短路的无耗传输线模型][3]
- 负载短路：$Z_L=0$；
- 短路负载的反射系数：$\Gamma=-1$；
- 短路负载的驻波比为无穷大；
- 短路负载传输线上的电压和电流为：
$$V(z)=V_0^+ \left[ e^{-j \beta z}- e^{j \beta z} \right] = -2jV_0^+ \sin{\beta z} $$
$$I(z)=\frac{V_0^+}{Z_0} \left[ e^{-j \beta z}+ e^{j \beta z} \right] =\frac{2V_0^+}{Z_0} \cos{\beta z} $$

- 在$z=-l$处的输入阻抗为：$$Z_{in} =\frac{V(-l)}{I(-l)}= jZ_0 \tan{\beta l} $$
	- 当$l=0$时， $Z_{in}=0$；
	- 当$l={\lambda}/{4}$时， $Z_{in}=\infty $；


## 负载开路的无耗传输线

![负载开路的无耗传输线模型][4]
- 负载开路：$Z_L=\infty$；
- 开路负载的反射系数：$\Gamma=1$；
- 开路负载的驻波比也为无穷大；
- 开路负载传输线上的电压和电流为：
$$V(z)=V_0^+ \left[ e^{-j \beta z}+ e^{j \beta z} \right] = 2V_0^+ \cos{\beta z} $$
$$I(z)=\frac{V_0^+}{Z_0} \left[ e^{-j \beta z}- e^{j \beta z} \right] =\frac{-2jV_0^+}{Z_0} \sin{\beta z} $$

- 在$z=-l$处的输入阻抗为：$$Z_{in} =\frac{V(-l)}{I(-l)}= -jZ_0 \cot{\beta l} $$


## 具有特定长度的端接传输线

- 对于$l=\lambda /2$的传输线，输入阻抗为：$$Z_{in}= Z_L$$
	- 半波长（或半波长的整数倍）的传输线不变换负载阻抗，与自身的特征阻抗无关。
	
- 对于$l=\lambda /4$（或者是$l=\lambda /4+n \lambda /2 , n=0,1,2,3...$）的传输线，输入阻抗为：$$Z_{in}=\frac{Z_0^2}{Z_L}$$
	- 这种传输线称为**四分之一波长变换器**;
	- 它具有以倒数的方式变换负载阻抗的作用；
	- 它依赖传输线的特征阻抗。

## 具有不同特征阻抗的传输线的串接

- 考虑特征阻抗为$Z_0$的传输线连接到一个具有不同特征阻抗$Z_1$的传输线上，假定负载线无穷长。
![具有不同特征阻抗的传输线的串接][5]

- 由连接处看到的输入阻抗为$Z_1$，反射系数为：$$\Gamma= \frac{Z_1-Z_0}{Z_1+Z_0}$$

- $z<0$处的电压为：$$V(z)= V_0^+ \left( e^{-j \beta z}+\Gamma e^{j \beta z} \right), z<0 $$
- $z>0$处的电压为：$$V(z) =V_0^+ T  e^{-j \beta z} , z>0 $$
	- 其中$T$为传输系数。

- 使上面两个公式的电压值在$z=0$处相等，则可以得到传输系数为：
$$T=1+\Gamma=1+ \frac{Z_1-Z_0}{Z_1+Z_0} = \frac{2Z_1}{Z_1+Z_0} $$

- 电路中两点之间的传输系数常常用dB表示为**插入损耗**：$$IL=-20 \lg{\left| T \right|} dB$$




  [1]: http://www.dannex.se/theory/pict/image188.gif
  [2]: http://7xroek.com1.z0.glb.clouddn.com/microwave20160309172635.png
  [3]: http://7xroek.com1.z0.glb.clouddn.com/microwave20160310143358.png
  [4]: http://7xroek.com1.z0.glb.clouddn.com/microwaveQQ20160310144058.png
  [5]: http://7xroek.com1.z0.glb.clouddn.com/microwave20160310153522.png