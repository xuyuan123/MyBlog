---
title: Attenuator
date: 2016-03-8 11:50:35
author: XuYuan
categories: Microwave
tags: [Microwave, Instrument]
mathjax: true
toc: false
comments: true

---

An attenuator is an electronic device that reduces the power of a signal without appreciably distorting its waveform.
An attenuator is effectively the opposite of an amplifer. While an amplifer provides gain, an attenuator provides loss.

<!--more-->

Widly used is the matching T type attenuator. Its circuit model is as follows.

<div style="text-align:center" markdown="1">
![matching T type attenuator model][1]


Calculate the matching T type attenuator.
The matching input impendance $Z\_{in}$ and output impendance $Z\_{out}$ must satisfy
$$Z\_{in}=R\_1+R\_3//(R\_2+Z\_{out})$$
$$Z\_{out}=R\_2+R\_3//(R\_1+Z\_{in})$$
$$\frac{V\_{in}}{Z\_{in}}R\_3//(R\_2+Z\_{out})=\frac{V\_{out}}{Z\_{out}}(R\_2+Z\_{out})$$
From Solving the above three equations, we can get
$$R\_1=\frac{Z\_{in}Z\_{out}-2Z\_{in}Z\_{out}\alpha+Z\_{in}^2\alpha^2}{Z\_{out}-Z\_{in}\alpha^2}$$
$$R\_2=\frac{Z\_{out}^2-2Z\_{in}Z\_{out}\alpha+Z\_{in}Z\_{out}\alpha^2}{Z\_{out}-Z\_{in}\alpha^2}$$
$$R\_3=\frac{2Z\_{in}Z\_{out}\alpha}{Z\_{out}-Z\_{in}\alpha^2}$$
where the $\alpha=\frac{V\_{out}}{V\_{in}}$.

In general situation, the input and output impendance $Z\_{in}$ and $Z\_{out}$ are the same and both equal to $50\Omega$. The T type attenuator is also the balanced one. Therefore, we could simplify the above equations as follows.
$$R\_1=R\_2=Z\_{in}\frac{1-\alpha}{1+\alpha}$$
$$R\_3=Z\_{in}\frac{2\alpha}{1-\alpha^2}$$

Usually, the attenuation is described in dB, that is to say $\kappa=-20\log{\frac{V\_{out}}{V\_{in}}}=-20\log{\alpha}$ dB.
Then we can get the voltage loss ratio is $\alpha=\frac{V\_{out}}{V\_{in}}=10^{-\frac{\kappa}{20}}$

Therefore, from the attenuation and input and output impendance, we can caculate the internal resistance.

--------------------------
**SUMMARY:**
An attenuator with 50 $\Omega$ impedance match:
1. The resistance of the T type attenuator satisfy:
$$ R\_1=R\_2=\frac{1-10^{-\frac{dB}{20}}}{1+10^{-\frac{dB}{20}}}\times 50\Omega $$
$$ R\_3=\frac{2\times 10^{-\frac{dB}{20}}}{1-10^{-\frac{dB}{10}}} $$
2. The output-input power ratio:
$$\frac{P\_{out}}{P\_{in}}=10^{-\frac{dB}{10}}$$
3. The output-input voltage ratio:
$$\frac{V\_{out}}{V\_{in}}=10^{-\frac{dB}{20}}$$

---------------------------------

For example:

|Attenuation|$R\_1=R\_2$|$R\_3$|Voltage Ratio|Power Ratio|
|:----------:|:---------:|:-----:|:-----:|:-----:|
|5dB|14.006$\Omega$|82.241$\Omega$|0.562|0.316|
|10dB|25.972$\Omega$|35.136$\Omega$|0.316|0.1|
|20dB|40.909$\Omega$|10.101$\Omega$|0.1|0.01|
|50dB|49.685$\Omega$|0.316$\Omega$|0.032|0.001|


You can find more informations from the website [CHEMANDY ELECTRONICS][2] and [Wikipedia of attenuator][3]

  [1]: http://www.electronics-tutorials.ws/attenuators/attn22.gif
  [2]: http://chemandy.com/calculators/matching-t-attenuator-calculator.htm
  [3]: http://en.wikipedia.org/wiki/Attenuator_%28electronics%29