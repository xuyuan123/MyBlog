---

title: Transmission Line Input-Output Theory
date: 2016-04-06 15:10:35
author: XuYuan
categories: Microwave
tags: [Microwave]
mathjax: true
toc: false
comments: true

---

Transmission line input-output theory is very important in microwave transmission line category. Here give some usefull equations for calculation of the input and output power.
<!--more-->

The transmission input-output theory is used to describe the microwave cavity. The input power is $P\_{in}$. The output power of the cavity is $P\_{out}$. They satisfy the following equation:
$$\left| S\_{21} \right|^2 = \frac{P\_{out}}{P\_{in}} = \frac{4\kappa \_{in} \kappa \_{out}}{\kappa^2} = \frac{4Q\_{tot}^2}{Q\_{in}Q\_{out}}$$

$$P\_{out} = n \hbar \omega \kappa \_{out} = \frac{n\hbar \omega^2}{Q \_{out}}$$

$$P\_{in}= \frac{4\hbar \omega \kappa^2}{4\kappa \_{in}}=\frac{n\hbar \omega^2 Q\_{in}}{4Q\_{tot}^2}$$

$$\kappa \_{tot}=\kappa \_{in}+\kappa \_{out} + \kappa \_{int} $$

$$Q\_{tot}=\frac{\omega}{\kappa \_{tot}} $$

$$Q\_{in}=\frac{\omega}{\kappa \_{in}} $$

$$Q\_{out}=\frac{\omega}{\kappa \_{out}} $$

$$Q\_{int}=\frac{\omega}{\kappa \_{int}} $$

$$\frac{1}{Q\_{tot}}= \frac{1}{Q\_{in}}+ \frac{1}{Q\_{out}}+ \frac{1}{Q\_{int}}$$

$\kappa\_{tot}$ describes the microwave photon decay from the cavity. It consits of three parts: 

+ $\kappa\_{in}$, the photons decay from the input port;
+ $\kappa\_{out}$, the photons decay from the output port;
+ $\kappa\_{int}$, the photons decay in the cavity because of the cavity loss.