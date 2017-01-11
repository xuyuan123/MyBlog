---
title: Quantization of linear and non-linear LC circuits
date: 2017-01-10 12:56:47
comments: true
toc: true
mathjax: true
author: XuYuan
categories: circuit
tag: [quantum, circuit]
---

When designing a quantum circuit, it's important to find the Hamiltonian and quantize it to obtain the energy levels. This blog introduce the general method to derive the Hamiltonian of linear and non-linear LC circuits and quantize the Hamiltonian.

<!--more-->

## 1.Single linear LC resonator
A general linear LC circuit is shown in figure 1. 
![Figure1: linear LC circuit][1]
We use the node varible $\Phi$ as the generalized coordinate. Then the voltage across the capacitor is $V=\frac{d\Phi}{dt}=\dot{\Phi}$
- capacitor potential energy: $U=\frac{1}{2}C\dot{\Phi}^2$
- inductor kinetic energy: $T=\frac{1}{2L}\Phi^2$

Therefore, the Lagrangian function of the LC circuit is :
$$ L = U-T = \frac{1}{2}C\dot{\Phi}^2 - \frac{1}{2L}\Phi^2$$
The conjugate momentum is defined: $Q \equiv \frac{\partial L}{\partial \dot{\Phi}} = C\dot{\Phi}$, and the commutation relationship between the coordinate and momentum is: $[\Phi,Q]=i\hbar$
Therefore, the Hamiltonian of the LC circuit is :
$$H = Q\dot{\Phi} - L=\frac{1}{2C}Q^2 + \frac{1}{2L}\Phi^2$$
Define the creation and annihilation operator of the LC circuit:
$$a^{\dagger} = -i \frac{1}{\sqrt{2C\hbar\omega}}Q + \frac{1}{\sqrt{2L\hbar\omega}}\Phi$$

$$a = i \frac{1}{\sqrt{2C\hbar\omega}}Q + \frac{1}{\sqrt{2L\hbar\omega}}\Phi$$
Here, we define the resonate frequency: $\omega=\frac{1}{\sqrt{LC}}$
The commutation relation between the creation and annihilation operator is : $[a,a^{\dagger}]=1$

Therefore, the Hamiltonian of the LC circuit can be quantized into this form:

$$H = \frac{\hbar\omega}{2}\left( a^{\dagger}a + aa^{\dagger} \right) = \hbar \omega \left( a^{\dagger} a + \frac{1}{2} \right)$$

The generalized coordinate and conjugate momentum can be expressed by the creation and annihilation operator:

$$\Phi = \Phi_{ZPF} \left( a^{\dagger} + a \right)$$

$$Q = iQ_{ZPF} \left( a^{\dagger} - a \right)$$

$$\Phi_{ZPF}=\sqrt{\frac{L\hbar\omega}{2}}=\sqrt{\frac{\hbar Z}{2}}$$

$$Q_{ZPF}=\sqrt{\frac{C\hbar\omega}{2}}=\sqrt{\frac{\hbar }{2Z}}$$

Here, the characteristic impedance is $Z=\sqrt{\frac{L}{C}}$
These formulars are very important in the following sections.

---

## 2.Two capacitance coupled linear LC circuit
In many cases, we will deal with two or more LC circuit coupled together. In this section, we will talk about two linear LC circuit capacitance coupled together, which is shown in figure 2. 
![Figure2: two capacitance coupled linear LC circuit][2]
Following the method described above, we can easily write the Lagrangian function of the coupled LC circuit:
$$\begin{align} L 
&= \frac{1}{2} C_1 \dot{\Phi_1}^2 +\frac{1}{2} C_2 \dot{\Phi_2}^2 +\frac{1}{2}C_0 \left\(\dot{\Phi_1}-\dot{\Phi_2}\right\)^2 - \frac{1}{2L_1}\Phi_1^2 - \frac{1}{2L_2}\Phi_2^2\\\\
&= \frac{1}{2}\dot{\Phi}^T C \dot{\Phi} -  \frac{1}{2}{\Phi}^T L^{-1} \Phi \\\\
\end{align}$$
Here, the matrix representation of $\Phi$, $C$ and $L^{-1}$ is:
$$ \Phi =
\begin{pmatrix}
\Phi_1 \\\\ \Phi_2 
\end{pmatrix}$$

$$C = 
\begin{pmatrix}
C_1+C_0 & -C_0 \\\\  -C_0 & C_2+C_0   
\end{pmatrix}$$

$$L^{-1}=
\begin{pmatrix}
\frac{1}{L_1} & 0 \\\\ 0 & \frac{1}{L_2}
\end{pmatrix}
$$

The conjugate momentum of the two resonance mode are defined: $Q_1 \equiv \frac{\partial L}{\partial \dot{\Phi_1}} $ and $Q_2 \equiv \frac{\partial L}{\partial \dot{\Phi_2}} $
Therefore, the Hamiltonian of the two coupled LC circuit is:
$$\begin{align}
H&=Q_1 \dot{\Phi_1} + Q_2 \dot{\Phi_2} - L
\\\\ &= \frac{1}{2}Q^T C^{-1} Q +  \frac{1}{2}\Phi^T L^{-1} \Phi
\end{align}$$

Here, 
$$C^{-1}=\frac{1}{C_1C_2+C_1C_0+C_2C_0} 
\begin{pmatrix}
C_2+C_0 & C_0 \\\\ C_0 & C_1+C_0 
\end{pmatrix}$$

Define some usefull constants:

$$C\_{1 \Sigma } = C\_1 + C\_{2s}$$

$$C\_{2 \Sigma } = C\_2 + C\_{1s}$$

$$\frac{1}{C\_{1s}} = \frac{1}{C\_0}+\frac{1}{C\_1}$$

$$\frac{1}{C\_{2s}} = \frac{1}{C\_0}+\frac{1}{C\_2}$$

The inverse matrix $C^{-1}$ can be simplied as:
$$C^{-1}= 
\begin{pmatrix}
\frac{1}{C\_{1 \Sigma }} & \frac{\beta}{C\_{2 \Sigma }} \\\\  \frac{\beta}{C\_{2 \Sigma }} & \frac{1}{C\_{2 \Sigma }}
\end{pmatrix}$$

Here, $\beta = \frac{C_0}{C_0 + C_1}$

Therefore, the Hamiltonian of the circuit is:

$$\begin{align}
H&=\frac{1}{2C\_{1 \Sigma}} Q\_1^2 + \frac{1}{2 L_1} \Phi\_1^2 + \frac{1}{2 C\_{2 \Sigma}} Q\_2^2 + \frac{1}{2 L\_2} \Phi\_2^2 + \frac{\beta}{C\_{2 \Sigma}} Q\_1 Q\_2   \\\\
&=H_0 + V
\end{align}$$
Here, 
$$H\_0 = \frac{1}{2C\_{1 \Sigma}} Q\_1^2 + \frac{1}{2L\_1} \Phi\_1^2 + \frac{1}{2C\_{2 \Sigma}} Q\_2^2 + \frac{1}{2L\_2} \Phi_2^2$$

$$V = \frac{\beta}{C\_{2 \Sigma}}Q\_1Q\_2$$

Define the resonance frequency of the two mode: $\omega\_1 = \frac{1}{L\_1 C\_{1 \Sigma}}$ and $\omega\_2 = \frac{1}{L\_2 C\_{2 \Sigma}}$; the caracteristic impedance of the two mode: $Z\_1 = \sqrt{\frac{L\_1}{C\_{1 \Sigma}}}$ and $Z\_2 = \sqrt{\frac{L\_2}{C\_{2 \Sigma}}}$.

We can also use the creation and annihilation operators of the two resonator modes to quantize the Hamiltonian.

$$\Phi\_1 = \Phi\_{ZPF1} \left( a\_1^{\dagger} + a\_1 \right)$$

$$Q\_1 = iQ\_{ZPF1} \left( a\_1^{\dagger} - a\_1 \right)$$

Here, $\Phi\_{ZPF1}=\sqrt{\frac{\hbar Z\_1}{2}}$ and $Q\_{ZPF1}=\sqrt{\frac{\hbar }{2 Z\_1}}$

In the same way, for the second mode:

$$\Phi\_2 = \Phi\_{ZPF2} \left( a\_2^{\dagger} + a\_2 \right)$$

$$Q\_2 = iQ\_{ZPF2} \left( a\_2^{\dagger} - a\_2 \right)$$

Here, $\Phi\_{ZPF2}=\sqrt{\frac{\hbar Z\_2}{2}}$ and $Q\_{ZPF2}=\sqrt{\frac{\hbar }{2 Z\_2}}$

Then, we could quantize the Hamiltonian $H\_0$ finally.

$$H\_0 = \hbar \omega\_1 \left( a\_1^{\dagger} a\_1 + \frac{1}{2} \right) + \hbar \omega\_2 \left( a\_2^{\dagger} a\_2 + \frac{1}{2} \right) $$

The coupling term $V$ can be expressed: 
$$V = -\frac{\beta Q\_{ZPF1}Q\_{ZPF2}}{C\_{2\Sigma}} \left( a\_1^{\dagger} - a\_1 \right) \left( a\_2^{\dagger} - a\_2 \right) =-\frac{\beta \hbar}{2C\_{2\Sigma}\sqrt{Z\_1Z\_2}} \left( a\_1^{\dagger} - a\_1 \right) \left( a\_2^{\dagger} - a\_2 \right) $$

---

## 3.Two inductance coupled linear LC circuit
How about the two LC resonators are coupled by an inductor? we then talk about how to deal with tihs plobem. Figure 3 shows the two LC resonators coupled by an inductor.
![Figure3: two inductance coupled linear LC circuit][3]
The method is similar to what I have described in the first two sections. First I will give the simple Lagrangian function directly.
$$\begin{align}
L &=  \frac{1}{2}C\_1\dot{\Phi\_1}^2 +\frac{1}{2}C\_2\dot{\Phi\_2}^2 - \frac{1}{2L\_1}\Phi\_1^2 - \frac{1}{2L\_2}\Phi\_1^2 - \frac{1}{2L\_0}\left( \Phi\_1 - \Phi\_2 +\Phi\_0 \right)^2
\\\\&= \frac{1}{2}\dot{\Phi}^T C \dot{\Phi} -  \frac{1}{2}{\Phi}^T L^{-1} \Phi
\end{align}$$
Here, $\Phi\_0$ is the external flux across the loop, $\Phi\_1$ and $\Phi\_2$ are the two node variables. For simplisity, we have ignored the external flux $\Phi\_0$ in the following analysis. the $\Phi$, $C$ and $L^{-1}$ are expressed in matrix representation.
$$ \Phi =
\begin{pmatrix}
\Phi\_1 \\\\ \Phi\_2 
\end{pmatrix}$$
$$C = 
\begin{pmatrix}
C\_1 & 0 \\\\  0 & C\_2   
\end{pmatrix}$$
$$L^{-1}=
\begin{pmatrix}
\frac{1}{L\_1}+\frac{1}{L\_0} & \frac{1}{L\_0} \\\\ \frac{1}{L\_0} & \frac{1}{L\_2}+\frac{1}{L\_0}
\end{pmatrix}
$$
We can define $\frac{1}{L\_{1\Sigma}}=\frac{1}{L\_1}+\frac{1}{L\_0}$ and $\frac{1}{L\_{2\Sigma}}=\frac{1}{L\_2}+\frac{1}{L\_0}$, then simplify the $L^{-1}$ matrix.
$$L^{-1}=
\begin{pmatrix}
\frac{1}{L\_{1\Sigma}} & \frac{1}{L\_0} \\\\ \frac{1}{L\_0} & \frac{1}{L\_{2\Sigma}}
\end{pmatrix}
$$
The conjugate momentum of the two node variables are defined: $Q\_1 \equiv \frac{\partial L}{\partial \dot{\Phi\_1}} $ and $Q\_2 \equiv \frac{\partial L}{\partial \dot{\Phi\_2}} $
From the above analysis, we can easily get the Hamiltonian of this LC circuit.
$$\begin{align}
H&=Q\_1 \dot{\Phi\_1} + Q\_2 \dot{\Phi\_2} - L
\\\\ &= \frac{1}{2}Q^T C^{-1} Q +  \frac{1}{2}{\Phi}^T L^{-1} {\Phi}
\end{align}$$
Here, the matrix representation of $Q$ and $C^{-1}$ are represented as:
$$ Q =
\begin{pmatrix}
Q\_1 \\\\ Q\_2 
\end{pmatrix}$$
$$C^{-1} = 
\begin{pmatrix}
\frac{1}{C\_1} & 0 \\\\  0 & \frac{1}{C\_2}   
\end{pmatrix}
$$
Finally, we can ge the Hamiltonian:
$$\begin{align}
H&=\frac{1}{2C\_1}Q\_1^2 + \frac{1}{2L\_{1\Sigma}}\Phi\_1^2+\frac{1}{2C\_2}Q\_2^2 + \frac{1}{2L\_{2\Sigma}}\Phi\_2^2+\frac{1}{L\_0}\Phi\_1 \Phi\_2
\\\\&=H\_0 + V
\end{align}$$
Here, $$H\_0 = \frac{1}{2C\_1}Q\_1^2 + \frac{1}{2L\_{1\Sigma}}\Phi\_1^2+\frac{1}{2C\_2}Q\_2^2 + \frac{1}{2L\_{2\Sigma}}\Phi\_2^2$$
$$V = \frac{1}{L\_0}\Phi\_1 \Phi\_2$$
We use the same method as before to quantize the Hamiltonian.
Define the resonance frequency of the two mode: $\omega\_1 = \frac{1}{\sqrt{L\_{1\Sigma} C\_{1}}}$ and $\omega\_2 = \frac{1}{\sqrt{L\_{2\Sigma} C\_2}}$; the caracteristic impedance of the two mode: $Z\_1 = \sqrt{\frac{L\_{1\Sigma}}{C\_1}}$ and $Z\_2 = \sqrt{\frac{L\_{2\Sigma}}{C\_2}}$.
We can also use the creation and annihilation operators of the two resonator modes to quantize the Hamiltonian.
$$\Phi\_1 = \Phi\_{ZPF1} \left( a\_1^{\dagger} + a\_1 \right)$$
$$Q\_1 = iQ\_{ZPF1} \left( a\_1^{\dagger} - a\_1 \right)$$
Here, $\Phi\_{ZPF1}=\sqrt{\frac{\hbar Z\_1}{2}}$ and $Q\_{ZPF1}=\sqrt{\frac{\hbar }{2 Z\_1}}$
In the same way, for the second mode:
$$\Phi\_2 = \Phi\_{ZPF2} \left( a\_2^{\dagger} + a\_2 \right)$$
$$Q\_2 = iQ\_{ZPF2} \left( a\_2^{\dagger} - a\_2 \right)$$
Here, $\Phi\_{ZPF2}=\sqrt{\frac{\hbar Z\_2}{2}}$ and $Q\_{ZPF2}=\sqrt{\frac{\hbar}{2 Z\_2}}$
Then, we could quantize the Hamiltonian $H\_0$ finally.
$$H\_0 = \hbar \omega\_1 \left( a\_1^{\dagger} a\_1 + \frac{1}{2} \right) + \hbar \omega\_2 \left( a\_2^{\dagger} a\_2 + \frac{1}{2} \right) $$
The coupling term $V$ can be expressed: 
$$V = \frac{\hbar}{2L\_0 \sqrt{Z\_1 Z\_2}}\left( a\_1^{\dagger} + a\_1 \right)\left( a\_2^{\dagger} + a\_2 \right) $$

---

## 4.Single non-linear LC circuit
Usually, we want to specifily drive the two energy levels in the resonator energy levels and find it's difficult because the linear resonator has equaly energy levels and each two of them have the same transition frequency.Therefore, we want have a non-equaly energy levels system. Then we will need to utilize the non-linear LC circuit elements.
The only non-liner LC circuit element is the Josephson junction, which serves as a non-linear inductor. The energy stored in this non-linear inductor can be expressed as:
$$H\_L = - E\_J \cos{\varphi}$$
Here, $E\_J$ is the Josephson energy of the Josephson junction. $\varphi =2\pi \frac{\Phi}{\varphi\_0}$ is the phase across the junction. $\Phi$ is the node flux variable. $\varphi\_0=\frac{h}{2e}$ is the flux quantum.
The non-linear circuit is shown in figure 4.
![Figure4: cooper pair box circuit][4]
Here, the large buffer capacitance $C\_B$ provides a random quantum fluctuation voltage across the island of the junction. $C\_g$ is the coupling capacitance that couples the junction island to the environment.
Then we will write the Lagrangian function of this cooper pair box circuit:
$$\begin{align}
L &=  \frac{1}{2}C\_J\dot{\Phi\_1}^2 +\frac{1}{2}C\_B\dot{\Phi\_2}^2 +\frac{1}{2}C\_g(\dot{\Phi\_1}-\dot{\Phi\_2})^2 + E\_J \cos{\varphi}
\\\\ &= \frac{1}{2}\dot{\Phi}^T C \dot{\Phi}  + E\_J \cos{\varphi}
\end{align}$$
Here, $\Phi$ and $C$ are represented as matrix:
$$ \Phi =
\begin{pmatrix}
\Phi\_1 \\\\ \Phi\_2 
\end{pmatrix}$$
$$C = 
\begin{pmatrix}
C\_g+ C\_J & -C\_g \\\\  -C\_g & C\_g+C\_B   
\end{pmatrix}$$
and $\varphi$ is the phase angle across the Josephson junction, and $\varphi = 2\pi \frac{\Phi\_1}{\varphi\_0}$, $\varphi\_0=\frac{h}{2e}$ is the flux quantum.
With the same method of the linear LC circuit, we also define the conjugate momentum of the two mode: $Q\_1 \equiv \frac{\partial L}{\partial \dot{\Phi\_1}} $ and $Q\_2 \equiv \frac{\partial L}{\partial \dot{\Phi\_2}} $
Then we can easily write the Hamiltonian of the cooper pair box:
$$\begin{align}
H&=Q\_1 \dot{\Phi\_1} + Q\_2 \dot{\Phi\_2} - L
\\\\ &= \frac{1}{2}Q^T C^{-1} Q - E\_J \cos{\varphi}
\end{align}$$
Here, $$C^{-1}=\frac{1}{C\_gC\_B+C\_gC\_J+C\_BC\_J} \begin{pmatrix} C\_g+C\_B & C\_g \\\\ C\_g & C\_g+C\_J \end{pmatrix}$$
We also define some usefull constants:
$$C\_{1\Sigma} = C\_J + C\_{2s}$$
$$C\_{2\Sigma} = C\_B + C\_{1s}$$
$$\frac{1}{C\_{1s}} = \frac{1}{C\_g}+\frac{1}{C\_J}$$
$$\frac{1}{C\_{2s}} = \frac{1}{C\_g}+\frac{1}{C\_B}$$
The inverse matrix $C^{-1}$ can be simplied as:
$$C^{-1}= \begin{pmatrix} \frac{1}{C\_{1\Sigma}} & \frac{\beta}{C\_{2\Sigma}} \\\\ \frac{\beta}{C\_{2\Sigma}} & \frac{1}{C\_{2\Sigma}} \end{pmatrix}$$
Here, $\beta = \frac{C\_g}{C\_g + C\_J}$
Then the Hamiltonian of the cooper pair box can be simplified as:
$$\begin{align}
H&=\frac{1}{2C\_{1\Sigma}}Q\_1^2 +\frac{1}{2C\_{2\Sigma}}Q\_2^2 +\frac{\beta}{C\_{2\Sigma}}Q\_1Q\_2 - E\_J \cos{\varphi}
\\\\&=\frac{1}{2C\_{1\Sigma}}Q\_1^2 + \beta V\_B Q\_1 + \frac{1}{2} C\_{2\Sigma} V\_B^2 - E\_J \cos{\varphi}
\\\\&=4E\_C \left( n^2 -2n\_g n \right) - E\_J \cos{\varphi} + \frac{1}{2} C\_{2\Sigma} V\_B^2
\\\\&=4E\_C \left( n -n\_g  \right)^2 - E\_J \cos{\varphi} + \frac{1}{2}\frac{C\_{1\Sigma}C\_{2\Sigma}}{C\_g + C\_J}  V\_B^2
\\\\& \approx 4E\_C  n^2 + \frac{E\_J}{2} \varphi^2 - \frac{E\_J}{24} \varphi^4
\\\\& = H\_0 +V
\end{align}$$
Here, we have defined some usefull variables:$V\_B = \frac{Q\_2}{C\_{2\Sigma}}$, $E\_C=\frac{e^2}{2C\_{1\Sigma}}$, $n\_g=-\beta\frac{C\_{1\Sigma V\_B}}{2e} \approx - \frac{C\_g V\_B}{2e}$.
The two conjugate operators are defined: $n = \frac{Q\_1}{2e}$, $\varphi = 2\pi \frac{\Phi\_1}{\varphi\_0}$. 
$$\begin{align}
H\_0 &= 4E\_C n^2 + \frac{E\_J}{2} \varphi^2
\\\\&=\frac{Q\_1^2}{2C\_{1\Sigma}} + \frac{\Phi\_1^2}{2L\_J}
\end{align}$$
$$V = - \frac{E\_J}{24} \varphi^4$$
Here, we have ignor all the constant terms in the Hamiltonian. And we defined $L\_J = \frac{\varphi\_0^2}{4\pi^2 E\_J}=\frac{\hbar^2}{4e^2 E\_J}$
Using the quantization method as before,we can also define the resonance frequency: $\omega\_1 = \frac{1}{\sqrt{L\_J C\_{1\Sigma}}}=\frac{\sqrt{8E\_J E\_C}}{\hbar}$  and the caracteristic impedance: $Z\_1 = \sqrt{\frac{L\_J}{C\_{1\Sigma}}}=\frac{\hbar}{2e^2}\sqrt{\frac{2E\_C}{E\_J}}$.
We use the creation and annihilation operators of the two resonator modes to quantize the cooper pair box Hamiltonian.
$$\Phi\_1 = \Phi\_{ZPF1} \left( a\_1^{\dagger} + a\_1 \right)$$
$$Q\_1 = iQ\_{ZPF1} \left( a\_1^{\dagger} - a\_1 \right)$$
Here, $\Phi\_{ZPF1}=\sqrt{\frac{\hbar Z\_1}{2}}$ and $Q\_{ZPF1}=\sqrt{\frac{\hbar}{2 Z\_1}}$
Finally, the quantized Hamiltonian $H\_0$ and $V$ can be written as:
$$H\_0 = \hbar \omega\_1 \left( a\_1^{\dagger} a\_1 + \frac{1}{2} \right)  $$
$$\begin{align}
V &= -\frac{E\_C}{12} \left( a\_1^{\dagger} + a\_1 \right)^4
\\\\&\approx -\frac{E\_C}{2} \left( a\_1^{\dagger}a\_1^{\dagger} a\_1 a\_1 + 2 a\_1^{\dagger} a\_1 \right)
\end{align}$$
Here, we have ignored some terms that don't sastify the principle of conservation of energy.
Finally we combined the two terms toghter and ignore the constant terms in the Hamiltonian. The final quantized Hamiltonian of the cooper pair box is:
$$\begin{align}
H &= H\_0 + V
\\\\&= \left( \hbar \omega\_1 -E\_C \right)a\_1^{\dagger} a\_1 -\frac{E\_C}{2}a\_1^{\dagger}a\_1^{\dagger} a\_1 a\_1 
\\\\&= \hbar \tilde{\omega}\_1 a\_1^{\dagger} a\_1 -\frac{E\_C}{2}a\_1^{\dagger}a\_1^{\dagger}a\_1 a\_1 
\end{align}$$
Here, the modified resonance frequency is: $\tilde{\omega}\_1 = \omega\_1 - E\_C/ \hbar = \frac{\sqrt{8E\_J E\_C} - E\_C}{\hbar}$
The eigenenergy of the Hamiltonian if:
$$E\_n = \hbar \tilde{\omega}\_1 n -\frac{E\_C}{2} n^2 $$
Therefore, the transition frequency of $0 \rightarrow 1 $ and $1 \rightarrow 2 $ are: 
$$\omega\_{01} = E\_1 - E\_0 = \hbar \tilde{\omega}\_1 -\frac{E\_C}{2} $$
$$\omega\_{12} = E\_2 - E\_1 = \hbar \tilde{\omega}\_1 -\frac{3E\_C}{2} $$
Therefore, the anharmonicity of the cooper pair box is:
$$\alpha \equiv \omega\_{12} - \omega\_{01} = -E\_C$$

The cooper pair box can be considered as a two level qubit when we only consider the first two levels of the cooper pair box energy levels because of its enough large anharmonicity.
The method of truncating the n-level system to 2-level system can be found in another blog. Here, I only give the final results.
The final Hamiltonian of the cooper pair box when truncted into 2-level system is:
$$\begin{align}
H &= \hbar \tilde{\omega}\_1 a\_1^{\dagger} a\_1 -\frac{E\_C}{2}a\_1^{\dagger}a\_1^{\dagger}a\_1 a\_1
\\\\& \approx \frac{\hbar \tilde{\omega}\_1}{2} \sigma\_z
\end{align}$$

---

## 5.Cooper pair box qubit capacitance coupled to a linear LC resonator

Then we will deal with the situation of coupling a linear LC resonator to a Cooper pair box qubit. figure 5 shows the coupled system circuit.
![Figure5: cooper pair box qubit capacitance coupled to a resonator][5]
We also follows the steps above. First, we write the Lagrangian function:
$$\begin{align}
L &=  \frac{1}{2}C\_J\dot{\Phi\_1}^2 +\frac{1}{2}C\_B\dot{\Phi\_2}^2 +\frac{1}{2}C\_g(\dot{\Phi\_1}-\dot{\Phi\_2})^2 + E\_J \cos{\varphi} - \frac{1}{2L\_B} \Phi\_2^2
\\\\ &= \frac{1}{2}\dot{\Phi}^T C \dot{\Phi}  + E\_J \cos{\varphi} - \frac{1}{2L\_B} \Phi\_2^2
\end{align}$$
Here, $\Phi$ and $C$ are represented as matrix:
$$ \Phi =
\begin{pmatrix}
\Phi\_1 \\\\ \Phi\_2 
\end{pmatrix}$$
$$C = 
\begin{pmatrix}
C\_g+ C\_J & -C\_g \\\\  -C\_g & C\_g+C\_B   
\end{pmatrix}$$
and $\varphi$ is the phase angle across the Josephson junction, and $\varphi = 2\pi \frac{\Phi\_1}{\varphi\_0}$, $\varphi\_0=\frac{h}{2e}$ is the flux quantum.
With the same method of the linear LC circuit, we also define the conjugate momentum of the two mode: $Q\_1 \equiv \frac{\partial L}{\partial \dot{\Phi\_1}} $ and $Q\_2 \equiv \frac{\partial L}{\partial \dot{\Phi\_2}} $
Then we can easily write the Hamiltonian of the cooper pair box:
$$\begin{align}
H&=Q\_1 \dot{\Phi\_1} + Q\_2 \dot{\Phi\_2} - L
\\\\ &= \frac{1}{2}Q^T C^{-1} Q - E\_J \cos{\varphi} + \frac{1}{2L\_B} \Phi\_2^2
\end{align}$$
Here, $$C^{-1}=\frac{1}{C\_gC\_B+C\_gC\_J+C\_BC\_J} \begin{pmatrix} C\_g+C\_B & C\_g \\\\ C\_g & C\_g+C\_J \end{pmatrix}$$
We also define some usefull constants:
$$C\_{1\Sigma} = C\_J + C\_{2s}$$
$$C\_{2\Sigma} = C\_B + C\_{1s}$$
$$\frac{1}{C\_{1s}} = \frac{1}{C\_g}+\frac{1}{C\_J}$$
$$\frac{1}{C\_{2s}} = \frac{1}{C\_g}+\frac{1}{C\_B}$$
The inverse matrix $C^{-1}$ can be simplied as:
$$C^{-1}= \begin{pmatrix} \frac{1}{C\_{1\Sigma}} & \frac{\beta}{C\_{2\Sigma}} \\\\ \frac{\beta}{C\_{2\Sigma}} & \frac{1}{C\_{2\Sigma}} \end{pmatrix}$$
Here, $\beta = \frac{C\_g}{C\_g + C\_J}$
The final Hamiltonian of the coupled system can be written as:
$$\begin{align}
H&= \frac{Q\_1^2}{2C\_{1\Sigma}} - E\_J \cos{\varphi} + \frac{Q\_2^2}{2C\_{2\Sigma}} + \frac{\Phi\_2^2}{2L\_B} + \frac{\beta}{C\_{2\Sigma}}Q\_1Q\_2
\\\\&=H\_1 + H\_2 + H\_{12}
\end{align}$$
Here, $H\_1$, $H\_2$ and $H\_{12}$ are represented as the Cooper pair box mode, resonator mode and their coupling mode.

$$\begin{align}
H\_1&= \frac{Q\_1^2}{2C\_{1\Sigma}} - E\_J \cos{\varphi} 
\\\\&= \hbar \tilde{\omega}\_1 a\_1^{\dagger} a\_1 -\frac{E\_C}{2}a\_1^{\dagger}a\_1^{\dagger}a\_1 a\_1 
\end{align}$$
Here, $\tilde{\omega}\_1 =  \frac{\sqrt{8E\_J E\_C} - E\_C}{\hbar}$, $E\_C=\frac{e^2}{2C\_{1\Sigma}}$, $Q\_1 = iQ\_{ZPF1} \left( a\_1^{\dagger} - a\_1 \right)$, $Q\_{ZPF1}=\sqrt{\frac{\hbar}{2 Z\_1}}$, $Z\_1=\frac{\hbar}{2e^2}\sqrt{\frac{2E\_C}{E\_J}}$.
$$\begin{align}
H\_2&= \frac{Q\_2^2}{2C\_{2\Sigma}} + \frac{\Phi\_2^2}{2L\_B}
\\\\& \approx \hbar \omega\_2  a\_2^{\dagger} a\_2 
\end{align}$$
Here, $\omega\_2 = \frac{1}{\sqrt{L\_B C\_{2\Sigma}}}$,  $Q\_2 = iQ\_{ZPF2} \left( a\_2^{\dagger} - a\_2 \right)$, $Q\_{ZPF2}=\sqrt{\frac{\hbar}{2 Z\_2}}$, $Z\_2 = \sqrt{\frac{L\_B}{C\_{2\Sigma}}}$.
$$\begin{align}
H\_{12}&= \frac{\beta}{C\_{2\Sigma}}Q\_1Q\_2
\\\\& = -\frac{\hbar \beta \sqrt{Z\_1 Z\_2}}{2 C\_{2\Sigma}} \left(a\_1^{\dagger} - a\_1 \right) \left(a\_2^{\dagger} - a\_2 \right) 
\\\\& = -\hbar g \left(a\_1^{\dagger} - a\_1 \right) \left(a\_2^{\dagger} - a\_2 \right) 
\\\\& \approx \hbar g \left(a\_1^{\dagger} a\_2 + a\_1 a\_2^{\dagger} \right)
\end{align}$$
Here, we have defined a coupling strength parameter: $g = \frac{\beta \sqrt{Z\_1 Z\_2}}{2 C\_{2\Sigma}}$
Combaining these terms together, we can obtain the whole Halmitonian of the Cooper pair qubit coupled to a resonator system:
$$H = \hbar \tilde{\omega}\_1 a\_1^{\dagger} a\_1 -\frac{E\_C}{2}a\_1^{\dagger}a\_1^{\dagger}a\_1 a\_1 +  \hbar \omega\_2  a\_2^{\dagger} a\_2 + \hbar g \left(a\_1^{\dagger} a\_2 + a\_1 a\_2^{\dagger} \right)$$
Under the condition of large detuning which is the so-called dispersive regime, we can derive the disperive coupling by a unitary transformaton: $U = e^{\eta}$, here $\eta = \frac{g}{\Delta} \left( a\_1^{\dagger} a\_2 - a\_1 a\_2^{\dagger} \right)$, detuning $\Delta = \tilde{\omega}\_1 - \omega\_2$
Therefore, the Hamiltonian after the transformation is:
$$\begin{align} \tilde{H} &= UHU^{\dagger} = e^{\eta} H e^{-\eta}
\\\\&=H + \left[ \eta, H \right] + \frac{1}{2} \left[ \eta, \left[ \eta, H \right] \right]
\\\\&=H\_0 + V + \left[ \eta, H\_0 \right] +\left[ \eta, V \right] + \frac{1}{2} \left[ \eta, \left[ \eta, H\_0 \right] \right]
\\\\&=H\_0 + V + \left( -V + T \right) + \left[ \eta, V \right] + \frac{1}{2}\left[ \eta, -V+T \right]
\\\\&=H\_0 + T +  \frac{1}{2}\left[ \eta, V \right] + \frac{1}{2}\left[ \eta, T \right]
\end{align}$$
In the above expression, we have defined:
$$H\_0 = \hbar \tilde{\omega}\_1 a\_1^{\dagger} a\_1 -\frac{E\_C}{2}a\_1^{\dagger}a\_1^{\dagger}a\_1 a\_1 +  \hbar \omega\_2  a\_2^{\dagger} a\_2$$
$$V = \hbar g \left(a\_1^{\dagger} a\_2 + a\_1 a\_2^{\dagger} \right)$$
and $\left[ \eta, H\_0 \right] = -V + T= -V + \frac{gE\_C}{\Delta} \left( a\_1^{\dagger} a\_1^{\dagger} a\_1 a\_2 + a\_1^{\dagger} a\_1 a\_1 a\_2^{\dagger}\right)$
Finally, we can obtain the Hamiltonian after transformation:
$$\begin{align} \tilde{H} & \approx \hbar \left( \tilde{\omega}\_1 + \frac{g^2}{\Delta} \right) a\_1^{\dagger} a\_1 - \frac{E\_C}{2} \left( 1-\frac{2g^2}{\Delta^2} \right) a\_1^{\dagger}a\_1^{\dagger}a\_1 a\_1 + \hbar \left( \omega\_2 - \frac{g^2}{\Delta} \right) a\_2^{\dagger} a\_2 -\frac{2g^2 E\_C}{\Delta^2} a\_1^{\dagger} a\_1 a\_2^{\dagger} a\_2
\\\\&= \hbar \omega\_1' a\_1^{\dagger} a\_1 +\frac{\alpha}{2}a\_1^{\dagger}a\_1^{\dagger}a\_1 a\_1 +  \hbar \omega\_2'  a\_2^{\dagger} a\_2 + \hbar \chi a\_1^{\dagger} a\_1 a\_2^{\dagger} a\_2
\end{align}$$
Here, the modified frequency are: $\omega\_1' = \tilde{\omega}\_1 + \frac{g^2}{\Delta}$, and $\omega\_2' =\omega\_2 - \frac{g^2}{\Delta} $. The qubit anharmonicity is $\alpha = - E\_C\left( 1-\frac{2g^2}{\Delta^2} \right)$. The dispersive coupling strength is $\chi = -\frac{2g^2 E\_C}{\hbar \Delta^2}$

Then ,I will truncate the n-level Cooper pair box mode into a 2-level qubit mode and finally get the Hamiltonian of the 2-level system coupled to a linear resonator:
$$H = \frac{\hbar \tilde{\omega}\_1}{2} \sigma\_z +  \hbar \omega\_2  a\_2^{\dagger} a\_2 + \hbar g \left(\sigma^{+} a\_2 + \sigma^{-} a\_2^{\dagger} \right)$$
This is the so-called "Jaynes Cumming Hamiltonian".
The first term describes the qubit mode with qubit frequency $\tilde{\omega}\_1$. The second term describe the resonator mode with resonance frequency $\omega\_2$. The last term describe their coupling with a coupling strength $g$.
In the same war, we can also perform a unitary transformation to find the dispersive Hamiltonian. We choose the unitary transformation: $U = e^{\eta}$, here $\eta = \frac{g}{\Delta} \left( \sigma^{+} a\_2 - \sigma^{-} a\_2^{\dagger} \right)$, detuning $\Delta = \tilde{\omega}\_1 - \omega\_2$.
Finally, we will obtain the Hamiltonian after the unitary transformation:
$$\begin{align} \tilde{H} & \approx \hbar \left( \tilde{\omega}\_1 + \frac{g^2}{\Delta} \right) \frac{\sigma\_z}{2}   + \hbar  \omega\_2  a\_2^{\dagger} a\_2 +\frac{\hbar g^2}{\Delta} \sigma\_z a\_2^{\dagger} a\_2
\\\\&= \hbar \omega\_1' \frac{\sigma\_z}{2}  +  \hbar \omega\_2  a\_2^{\dagger} a\_2 + \hbar \chi \sigma\_z a\_2^{\dagger} a\_2
\end{align}$$
Here, the modified qubit frequency is: $\omega\_1' = \tilde{\omega}\_1 + \frac{g^2}{\Delta}$. And the dispersive coupling strength is : $\chi = \frac{ g^2}{\Delta}$

---

## 6.Two capacitance coupled cooper pair box qubits
From now on, we have only talked about one cooper pair box qubit coupled to a resonator. In this section, I will try to deal with two cooper pair box qubits capacitance coupled together, which is shown in figure6.
![Figure6: Two capacitance coupled cooper pair box qubits][6]
The analysis method is same as the above sections and I leave it as an exercise to enhance the method I have described above.

---

## 7.Josephson ring modulator
Finally, I want to show a more complex circuit called Josephson ring modulator (JRM) circuit which consists of four identical Josephson junctions. The circuit is shown in figure 7.
![Figure7: Josephson ring modulator circuit][7]

To be continued......


  [1]: http://7xroek.com1.z0.glb.clouddn.com/linear_LC.png
  [2]: http://7xroek.com1.z0.glb.clouddn.com/capacitance_coupled_linear_LC.png
  [3]: http://7xroek.com1.z0.glb.clouddn.com/inductance_coupled_circuit.jpg
  [4]: http://7xroek.com1.z0.glb.clouddn.com/cooper_pair_box_circuit.png
  [5]: http://7xroek.com1.z0.glb.clouddn.com/JC_circuit.png
  [6]: http://7xroek.com1.z0.glb.clouddn.com/coupled_qubits.png
  [7]: http://7xroek.com1.z0.glb.clouddn.com/JRM_circuit.png
