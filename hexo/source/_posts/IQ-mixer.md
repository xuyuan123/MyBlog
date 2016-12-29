---
title: IQ mixer
comments: true
toc: false
mathjax: true
date: 2016-03-27 19:41:37
author: XuYuan
categories: Microwave
tags: [Microwave Instrument]

---

Mixers are widly used to shift signals from one frequency to another. IQ mixer is a kind of mixer which consits of two mixers. This article talks about the caculation of the IQ mixer.
<!--more-->

IQ mixers address the problem of maximizing information transmission in a limited bandwidth by allowing the user to modulate both the in-phase and quadrature components of a carrier simultaneously, doubling the information density

The folowing picture is the ideal frequency mixer symbol.
![ideal frequency mixer symbol][1]
The Input Signal ,Local Osicillator and Output Single satisfy the relation: $$Output Signal=InputSignal * LocalOscillator$$
The IQ mixer consists of two frequency mixers which can be seen from the following picture.
![IQ mixer model][2]

For ideal sistuation, the input signals and output signal are:
**LO signal:** $\cos(\omega t)$
**I signal:** $C\cos(\omega_0 t)$
**Q signal:** $D\sin(\omega_0 t)$     $(D=C)$
**RF signal:** $C\cos(\omega t)\cos(\omega_0 t) + D\sin(\omega t)\sin(\omega_0 t)=C\cos(\omega-\omega_0)t$

Therefore, the RF output signal only has the frequency $\omega-\omega_0$ term.

However, for practise situation, the output signal will have other frequency term because the amplitude and phase are not ideal.
The actually output RF signal is 
**RF Signal:** $AC(\cos(\omega t)+M)\cos(\omega_0 t) + BD\sin(\omega t+\phi_0)\sin(\omega_0 t)$
Then we can see the output signal will contain three frequency terms, that is $\omega$, $\omega-\omega_0$, and $\omega+\omega_0$
We need to change the IQ signal to make the output frequency only $\omega-\omega_0$ remained.

- First change the $M=0$, the output will not have the $\omega$ term.
- Change the IQ signal amplitude ratio to make $AC=BD$, and change the IQ signal relative phase to $-\phi_0$, then we can eliminate the $\omega+\omega_0$ term.

When satisfied the above two conditions, the output signal is 
$$\begin{align}
&AC\cos(\omega t)\cos(\omega_0 t) + BD\sin(\omega t+\phi_0)\sin(\omega_0 t-\phi_0)\\\\
&=AC\left[ \frac{1}{2}\left(\cos(\omega-\omega_0)t+\cos(\omega+\omega_0)\right) +\frac{1}{2}\left(\cos((\omega-\omega_0)t+2\phi_0)-\cos(\omega+\omega_0)t \right)\right]\\\\
&=\frac{AC}{2}\left[\cos(\omega-\omega_0)t+\cos((\omega-\omega_0)t+2\phi_0) \right]\\\\
&=AC\cos((\omega-\omega_0)t+\phi_0)\cos(\phi_0)\\\\
\end{align}$$

Finally, there only remains the $\omega-\omega_0$ frequency term.

You can find more information about [IQ Mixer][3] in this website.

-----
**SUMMARY:**
1. Change the offset to make the $M=0$ and lower the leakage;
2. Change the IQscale to satisfy $AC=BD$;
3. Change the Phasedelay to make the IQ signal relative phase to $-\phi_0$

  [1]: http://upload.wikimedia.org/wikipedia/commons/thumb/0/05/IdealMixer.svg/512px-IdealMixer.svg.png
  [2]: http://www.markimicrowave.com/Assets/ProductImages/Mixers/Image_Reject_and_Single_Sideband/IQ_Block_Diagram.png
  [3]: http://www.markimicrowave.com/blog/2013/06/iq-image-reject-and-single-sideband-mixers/