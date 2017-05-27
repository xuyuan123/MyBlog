---
title: Black Box Quantization
date: 2017-01-20 10:19:31
comments: true
toc: true
mathjax: true
author: XuYuan
categories: quantum
tags: [quantum]

---

This article introduces the method called "Black Box Quantization (BBQ)" to deal with complex LC circuits. The basic reference of this article is [Simon's paper][1]. For simplicity, I just show 2 simple cases to illustrate the general priciple of the BBQ method.

<!--more-->

---

## Introduction
In my previous article ["Quantization of linear and non-linear LC circuits"][2], we have learned the method to quantize a simple linear and non-linear LC circuit. However, a typical circuit always consitsing of many capacitors and inductors is more complex than a simple LC circuit. Generally, we consider this complex linear LC circuit as a black box. The following figure shows a complex linear LC circuit which is considered as a linear black box. This linear black box is usually coupled to a non-linear element. In the following figure, the gray background indicates the linear black box.
![Complex LC circuit][3]

In the following two parts, we illustrate the black box quantization method in two simple situations. One is "one qubit coupled to two resonator modes", another is "two qubits coupled to one resonator mode".

---

## One qubit coupled to two resonator modes
The LC circuit we will deal with is shown in the following figure. 
![Qubit coupled to two cavities][4]
For the non-linear element Josephson junction, it can be considered as a non-linear inductor. The Hamiltonian of the non-linear inductor can be expressed as:
$$H\_{inductor} = -E\_J \cos\varphi = -E\_J \left( 1 - \frac{1}{2!} \varphi^2 + \frac{1}{4!} \varphi^4 - \frac{1}{6!} \varphi^6 + ... \right)$$

The non-linear part of the Josephson junction can be obtained by removing the linear part of the inductor Hamiltonian.
$$V = H\_{inductor} + E\_J \left( 1 - \frac{1}{2!} \varphi^2 \right) = -E\_J \left(  \frac{1}{4!} \varphi^4 - \frac{1}{6!} \varphi^6 + ... \right)$$

The linear part of the inductor Hamiltonian and other linear inductors and capacitors form the black box, which is equivalent to a series of LC resonators. Then the circuit can be simplified as non-linear Josephson junction coupled to a linear black box, which is shown in the following figure.
![Qubit\_BBQ][5]
The gray background indicates the linear black box. The impedence of the black box can be expressed as:
$$\begin{align}
Z &= j\omega L\_1 //\frac{1}{j\omega C\_1} + j\omega L\_2 //\frac{1}{j\omega C\_2} + j\omega L\_3 //\frac{1}{j\omega C\_3}
\\\\&= \frac{1}{j\omega C\_1 + \frac{1}{j\omega L\_1}} + \frac{1}{j\omega C\_2 + \frac{1}{j\omega L\_2}} + \frac{1}{j\omega C\_3 + \frac{1}{j\omega L\_3}}
\\\\&= \frac{Z\_1}{j \left( \frac{\omega}{\omega\_1}-\frac{\omega\_1}{\omega} \right)} + \frac{Z\_2}{j \left( \frac{\omega}{\omega\_2}-\frac{\omega\_2}{\omega} \right)} + \frac{Z\_3}{j \left( \frac{\omega}{\omega\_3}-\frac{\omega\_3}{\omega} \right)}
\end{align}$$
Here, we have defined the resonance frequencies are: $\omega\_1 = \frac{1}{L\_1 C\_1}$, $\omega\_2 = \frac{1}{L\_2 C\_2}$ and $\omega\_3 = \frac{1}{L\_3 C\_3}$. The characteristic impedances are: $Z\_1 = \sqrt{\frac{L\_1}{C\_1}}$, $Z\_2 = \sqrt{\frac{L\_2}{C\_2}}$ and $Z\_3 = \sqrt{\frac{L\_3}{C\_3}}$.

Then the admittance of the black box can be expressed as:
$$Y = Z^{-1} = j \left( \frac{Z\_1}{ \frac{\omega}{\omega\_1}-\frac{\omega\_1}{\omega} } + \frac{Z\_2}{\frac{\omega}{\omega\_2}-\frac{\omega\_2}{\omega} } + \frac{Z\_3}{ \frac{\omega}{\omega\_3}-\frac{\omega\_3}{\omega} } \right)^{-1}$$

Then from zero points of the imaginary of the admittance $ImY = 0$, we can obtain the three resonance frequencies: $\omega = \omega\_1$, $\omega = \omega\_2$ and $\omega = \omega\_3$.

We can also derive the expression of the derivative of the imaginary admittance and find this derivative at the three resonance frequencies.
When $\omega = \omega\_1$:

$$\left( ImY \right)'\_{\omega\_1} = \frac{2}{\omega\_1 Z\_1} \quad \Longrightarrow \quad Z\_1 = \frac{2}{\omega\_1 \left( ImY \right)'\_{\omega\_1} } $$

When $\omega = \omega\_2$:

$$\left(ImY \right)'\_{\omega\_2} = \frac{2}{\omega\_2 Z\_2} \quad \Longrightarrow \quad Z\_2 = \frac{2}{\omega\_2 \left(ImY \right)'\_{\omega\_2}} $$

When $\omega = \omega\_3$:

$$\left(ImY \right)'\_{\omega\_3} = \frac{2}{\omega\_3 Z\_3} \quad \Longrightarrow \quad Z\_3 = \frac{2}{\omega\_3 \left(ImY \right)'\_{\omega\_3}} $$

Therefore, we can see that a positive slope of the imaginary admittance can always be obtained at each zero point.

For a specific model, we use High Frequency Structural Simulator (HFSS) software to obtain the admittance of the linear black box seen from the two port. With the knowledge of the admittance of the black box, we can obtain the zero points of the imaginary admittance and its slope of at each zero points. These zero points are coresponding to the resonance frequencies of the black box. From the resonance frequencies and slopes, we can calculate the characteristic impedance of each mode.

After obtaining the resonance frequency and characteristic impedance of each mode, we can write the quantized Hamiltonian of the linear black box.

$$H\_{linear} = \hbar \omega\_1 a\_1^{\dagger} a\_1 + \hbar \omega\_2 a\_2^{\dagger} a\_2 + \hbar \omega\_3 a\_3^{\dagger} a\_3$$

Here, the $a\_1^{\dagger}$, $a\_1$,$a\_2^{\dagger}$, $a\_2$ and $a\_3^{\dagger}$, $a\_3$ are the creation and anhilation operator of the three modes.
The flux variable of each mode can also be expressed by the creation and anhilation operators.

$$\Phi\_1 = \Phi\_{ZPF1} \left( a\_1^{\dagger} + a\_1 \right)$$

$$\Phi\_2 = \Phi\_{ZPF2} \left( a\_2^{\dagger} + a\_2 \right)$$

$$\Phi\_3 = \Phi\_{ZPF3} \left( a\_3^{\dagger} + a\_3 \right)$$

Here, $\Phi\_{ZPF1} = \sqrt{\frac{\hbar Z\_1}{2}}$, $\Phi\_{ZPF2} = \sqrt{\frac{\hbar Z\_2}{2}}$ and $\Phi\_{ZPF3} = \sqrt{\frac{\hbar Z\_3}{2}}$

The phase difference of each mode can be expressed as:

$$\varphi\_1 = 2\pi \frac{\Phi\_1}{\varphi\_0} = 2\pi \frac{\Phi\_1}{h/2e} = \frac{2e}{\hbar} \Phi\_1$$

$$\varphi\_2 = 2\pi \frac{\Phi\_2}{\varphi\_0} = 2\pi \frac{\Phi\_2}{h/2e} = \frac{2e}{\hbar} \Phi\_2$$

$$\varphi\_3 = 2\pi \frac{\Phi\_3}{\varphi\_0} = 2\pi \frac{\Phi\_3}{h/2e} = \frac{2e}{\hbar} \Phi\_3$$

The phase difference across the non-linear Josephson junction can be expressed as:

$$\begin{align}
\varphi &= \varphi\_1 + \varphi\_2 + \varphi\_3 
\\\\&=\frac{2e}{\hbar} \left( \Phi\_1 + \Phi\_2 + \Phi\_3 \right) 
\\\\&=\frac{2e}{\hbar} \left[ \sqrt{\frac{\hbar Z\_1}{2}} \left( a\_1^{\dagger} + a\_1 \right) +  \sqrt{\frac{\hbar Z\_2}{2}} \left( a\_2^{\dagger} + a\_2 \right) + \sqrt{\frac{\hbar Z\_3}{2}} \left( a\_3^{\dagger} + a\_3 \right) \right] 
\end{align}$$

Therefore, the non-linear Hamiltonian of the Josephson junction can be expressed as:

$$\begin{align}
&H\_{non-linear} = V
\\\\&= -E\_J \left( \frac{1}{4!}\varphi^4 - \frac{1}{6!}\varphi^6 + \frac{1}{8!}\varphi^8 - \frac{1}{10!}\varphi^{10} + ... \right)
\end{align}$$

Finally, we can obtain the whole Hamiltonian of the system:
$$H\_{system} = H\_{linear} + H\_{non-linear}$$
After obtaning the whole Hamiltonian, we can diagonalize this Hamiltonian numerically and find its eigenenergies, from which we can obtain the resonance frequencies, self-Kerr, cross-Kerr terms and finally, we can acquire the coupling strength and anharmonicity of the qubit.

---

## Two qubits coupled to one resonator mode

Then we are gong to deal with a two qubits situation, which is shown in the following figure.
![cavity_2qubits][6]

We use the same method as before to move all the linear part into the black box, and only the two ports non-linear Josephson junctions remain. The equivalent circuit is shown below.
![cavity_2qubits_BBQ][7]

Here, we consider the port 1 as the reference port. We could obtain the impedance matrix from the HFSS for each resonance mode. That is to say, we can obtain $Z\_{11} \left(\omega \right)$, $Z\_{12} \left(\omega \right)$, $Z\_{21} \left(\omega \right)$ and $Z\_{22} \left(\omega \right)$ at each frequency point.

We use the method as before. We first calculate the admattance of the two port:
$$Y\_1(\omega) = Z\_{11} \left(\omega \right) ^{-1}$$
$$Y\_2(\omega) = Z\_{22} \left(\omega \right) ^{-1}$$
Find the zero points of the imaginary admattance $ImY\_1(\omega) =0$ or $ImY\_2(\omega) =0$, we can get the resonance frequency of each mode. $\omega = \omega\_1$, $\omega = \omega\_2$ and $\omega = \omega\_3$ . The zero root solutions of these two equations should be same. 
Therefore, we can obtain the linear Hamiltonian:
$$H\_{linear} = \hbar \omega\_1 a\_1^{\dagger} a\_1 +\hbar \omega\_2 a\_2^{\dagger} a\_2+\hbar \omega\_3 a\_3^{\dagger} a\_3$$

The characteristic impedance of the three modes can aslo be calculated:
$$Z\_1 = \frac{2}{\omega\_1 \left(ImY \right)'\_{\omega\_1}} $$
$$Z\_2 = \frac{2}{\omega\_2 \left(ImY \right)'\_{\omega\_2}} $$
$$Z\_3 = \frac{2}{\omega\_3 \left(ImY \right)'\_{\omega\_3}} $$

The phase difference across the reference Josephson junction port can be expressed as:
$$\begin{align}
\varphi1 &= \varphi\_1 + \varphi\_2 + \varphi\_3 
\\\\&=\frac{2e}{\hbar} \left( \Phi\_1 + \Phi\_2 + \Phi\_3 \right) 
\\\\&=\frac{2e}{\hbar} \left[ \Phi\_{ZPF1} \left( a\_1^{\dagger} + a\_1 \right) +  \Phi\_{ZPF2} \left( a\_2^{\dagger} + a\_2 \right) + \Phi\_{ZPF3} \left( a\_3^{\dagger} + a\_3 \right) \right] 
\end{align}$$

The second junction port can also be calculated:
$$\begin{align}
\varphi2 &= \frac{Z\_{21}(\omega\_1) }{Z\_{11}(\omega\_1)}\varphi\_1 + \frac{Z\_{21}(\omega\_2) }{Z\_{11}(\omega\_2)}\varphi\_2 + \frac{Z\_{21}(\omega\_3) }{Z\_{11}(\omega\_3)}\varphi\_3 
\\\\&=\frac{2e}{\hbar} \left( \frac{Z\_{21}(\omega\_1) }{Z\_{11}(\omega\_1)}\Phi\_1 + \frac{Z\_{21}(\omega\_2) }{Z\_{11}(\omega\_2)}\Phi\_2 + \frac{Z\_{21}(\omega\_3) }{Z\_{11}(\omega\_3)}\Phi\_3 \right) 
\\\\&=\frac{2e}{\hbar} \left[ \frac{Z\_{21}(\omega\_1) }{Z\_{11}(\omega\_1)} \Phi\_{ZPF1}\left( a\_1^{\dagger} + a\_1 \right) +  \frac{Z\_{21}(\omega\_2) }{Z\_{11}(\omega\_2)}\Phi\_{ZPF2} \left( a\_2^{\dagger} + a\_2 \right) + \frac{Z\_{21}(\omega\_3) }{Z\_{11}(\omega\_3)}\Phi\_{ZPF3} \left( a\_3^{\dagger} + a\_3 \right) \right] 
\end{align}$$
Here, $\Phi\_{ZPF1} = \sqrt{\frac{\hbar Z\_1}{2}}$, $\Phi\_{ZPF2} = \sqrt{\frac{\hbar Z\_2}{2}}$ and $\Phi\_{ZPF3} = \sqrt{\frac{\hbar Z\_3}{2}}$
Here, we define a matrix:
$$\phi\_{ZPF} =\frac{2e}{\hbar} \begin{pmatrix}
\Phi\_{ZPF1} & \Phi\_{ZPF2} & \Phi\_{ZPF3} \\ \frac{Z\_{21}(\omega\_1) }{Z\_{11}(\omega\_1)}\Phi\_{ZPF1} & \frac{Z\_{21}(\omega\_2) }{Z\_{11}(\omega\_2)}\Phi\_{ZPF2} & \frac{Z\_{21}(\omega\_3) }{Z\_{11}(\omega\_3)}\Phi\_{ZPF3}
\end{pmatrix}$$
$$a = \begin{pmatrix}
a\_1^{\dagger} + a\_1 \\\\ a\_2^{\dagger} + a\_2 \\\\ a\_3^{\dagger} + a\_3
\end{pmatrix}$$
Therefore, 
$$\varphi = \begin{pmatrix}
\varphi 1 \\\\ \varphi 2
\end{pmatrix}
=\phi\_{ZPF} \cdot a$$

We can define a function which expand the cos function and ignore the first two terms.
$$\begin{align}F(x) &= \cos(x) -(1 - \frac{1}{2!}x^2) 
\\\\ &= \frac{1}{4!}x^4 - \frac{1}{6!}x^6 + \frac{1}{8!}x^8 - \frac{1}{10!}x^{10} + ...\end{align}$$

Therefore, we can obtain the non-linear Hamiltonian:
$$H\_{non-linear} = -E\_{J1} F(\varphi 1) -E\_{J2} F(\varphi 2)$$
Finally, we can acquire the total Hamiltonian of the system:
$$H\_{system} = H\_{linear} + H\_{non-linear}$$



---

## Summary
This article summaries the method of black box quantization with two simple situations. The black box quantization 

---


  [1]: https://arxiv.org/pdf/1204.0587v1.pdf
  [2]: http://xuyuan.cf/2017/01/10/Quantization-of-linear-and-non-linear-LC-circuits/
  [3]: http://7xroek.com1.z0.glb.clouddn.com/complex_circuit.png
  [4]: http://7xroek.com1.z0.glb.clouddn.com/Qubit_2Cavity.png
  [5]: http://7xroek.com1.z0.glb.clouddn.com/Qubit_BBQ.png
  [6]: http://7xroek.com1.z0.glb.clouddn.com/cavity_2qubits.png
  [7]: http://7xroek.com1.z0.glb.clouddn.com/cavity_2qubits_BBQ.png