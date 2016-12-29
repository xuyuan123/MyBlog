---
title: Capacity Measurement with Lock-in Amplifier
comments: true
mathjax: true
date: 2016-05-01 09:41:37
author: XuYuan
categories: capacity measurement
tags: [capacity measurement]

---

Capacity is a difficult parameter to measure, especially for small capacities fabricated by trilayer nano-fabrication technology. This article provides a method to measure the small capacity by using a lock-in amplifier.
<!--more-->

## Measurement Scheme
The measurement circuit is shown below.
![the measurement circuit][1]

The reference sin signal comes from the lock-in amplifier and we use a reference resistance $R\_{ref}$. We put the unknown capacity $C\_x$ in parallel in the circuit. And the $U\_{out}$ signal comes into the lock-in amplifier signal in port.

We can calculate the output signal:
$$\begin{align}
&\frac{U\_{out}}{U\_{in}}=\frac{Z\_{out}}{Z\_{in}}=\frac{R\_0 ||\left( C\_0 +C\_x \right)}{R\_{ref} + R\_0 ||\left( C\_0 +C\_x \right) }\\\\
&=\frac{R\_0}{\left( R\_0+ R\_{ref}\right) +j\omega R\_0 R\_{ref}\left( C\_0 +C\_x \right) }\\\\
&=\frac{R\_0 \left[\left( R\_0+ R\_{ref}\right) +j\omega R\_0 R\_{ref}\left( C\_0 +C\_x \right)\right]}{\left( R\_0+ R\_{ref}\right) ^2 + \omega^2R\_0^2R\_{ref}^2 \left( C\_0 +C\_x \right)^2}\\\\
\end{align}$$

We can get the phase from the above equation:
$$\tan\theta=\frac{-\omega R\_0 R\_{ref}\left( C\_0 +C\_x \right)}{\left( R\_0+ R\_{ref}\right)}$$

Finally, we can get the relation between the unknown capacity $C\_x$ and the signal frequency $\omega$, the phase difference $\theta$:
$$C\_x=- \frac{\left( R\_0+ R\_{ref}\right)}{ R\_0 R\_{ref}}\times \frac{\tan \theta}{\omega} - C\_0$$

First, we can fixed the frequency at $\omega \_k$, and from measuring the phase $\theta$ to obtain the capacity $C\_x$:
when $C\_x=0$, we can get:
$$- \frac{\left( R\_0+ R\_{ref}\right)}{ R\_0 R\_{ref}}\times \frac{\tan \theta \_0}{\omega \_k} = C\_0$$
$$- \frac{\left( R\_0+ R\_{ref}\right)}{ \omega \_k R\_0 R\_{ref}} = \frac{C\_0}{\tan \theta \_0}$$
Finally, we can get:
$$C\_x=C\_0 \times \left( \frac{\tan \theta}{\tan \theta \_0}-1 \right) = \frac{C\_0}{\tan \theta\_0} \left( \tan \theta - \tan \theta\_0 \right)$$

Second, we fix the phase to $\theta \_k$ and from measuring the frequency $\omega$ to obtain the unknown capacity $C\_x$.
when $C\_x=0$, we can get:
$$- \frac{\left( R\_0+ R\_{ref}\right)}{ R\_0 R\_{ref}}\times \frac{\tan \theta \_k}{\omega _0} = C\_0$$
$$- \frac{\left( R\_0+ R\_{ref}\right)\tan \theta \_k }{ R\_0 R\_{ref}} = \omega _0 C\_0$$
Finally, we can get:
$$C\_x=C\_0 \times \left( \frac{\omega _0}{\omega }-1 \right) =\omega _0 C\_0 \left( \frac{1}{\omega}-\frac{1}{\omega\_0} \right)=f _0 C\_0 \left( \frac{1}{f}-\frac{1}{f\_0} \right)$$

From the above two equations, we can measure the capacities.
## Calibration Experiment
1. Fixed the frequency $f=200Hz$, and measure the phase $\theta$.
We use different capacities from 10pF to 680pF for the calibration experiment.the result shows in below figure.
![calibration_fixFreq][2]
From the fitting to the curve, we can get:
$$C\_x=-264.78 \times \left( \tan(\theta+1.6428) - \tan(\theta \_0 -1.6428) \right) pF$$

2. Fix the phase $\theta=-45°$, and measure the frequency.
The result for this situation is shown below:
![calibration_fixPhase][3]
From the fitting to the curve, we can get:
$$C\_x=53266 \times \left( \frac{1}{f+7.9213} -\frac{1}{f\_0 +7.9213} \right) pF$$


## Summary
1. Fix the frequency $f=200Hz$, and measure the background phase $\theta\_0$ and the phase $\theta$ corresponding to the unknow capacity $C\_x$.
 $$C\_x=-264.78 \times \left( \tan(\theta+1.6428) - \tan(\theta \_0 -1.6428) \right) pF$$

2. Fix the phase $\theta=-45°$, and measure the background frequency $f\_0$ and the frequency f corresponding to the unknown capacity $C\_x$.
$$C\_x=53266 \times \left( \frac{1}{f+7.9213} -\frac{1}{f\_0 +7.9213} \right) pF$$

3. Average the above two results to get the final capacity.

This method can be used to measure the capacities fabricated by trilayer nano-frbrication technology with the help of probe station.




  [1]: http://7xroek.com1.z0.glb.clouddn.com/capacity_measurement_circuit.png
  [2]: http://7xroek.com1.z0.glb.clouddn.com/calibration_fixFreq.png
  [3]: http://7xroek.com1.z0.glb.clouddn.com/calibration_fixPhase.png