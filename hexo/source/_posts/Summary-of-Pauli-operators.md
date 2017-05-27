---
title: Summary of Pauli operatoes
date: 2017-01-5 15:10:35
comments: true
toc: true
mathjax: true
author: XuYuan
categories: quantum
tag: [quantum]
---

This article summaries the wildly used Pauli operators and its matrix representation. And I will give a summary of all the properties of the Pauli operators. Finally, I will exihibit the method to truncate the n-level system to a 2-level system.

<!--more-->

## Pauli operators
The basic three Pauli operators are: $\sigma\_x$, $\sigma\_y$ and $\sigma\_z$. In the following, I will show the commute relationship and anti-commute relationship between these Pauli operators.
$$\left[ \sigma\_x, \sigma\_y \right] = 2i \sigma\_z \quad ; \quad \left\\{ \sigma\_x, \sigma\_y \right\\} =0$$
$$\left[ \sigma\_y, \sigma\_z \right] = 2i \sigma\_x \quad ; \quad \left\\{ \sigma\_y, \sigma\_z \right\\} =0$$
$$\left[ \sigma\_z, \sigma\_x \right] = 2i \sigma\_y \quad ; \quad \left\\{ \sigma\_z, \sigma\_x \right\\} =0$$
$$\sigma\_x \sigma\_y = i \sigma\_z \quad ; \quad  \sigma\_x^2 =1$$
$$\sigma\_y \sigma\_z = i \sigma\_x \quad ; \quad  \sigma\_y^2 =1$$
$$\sigma\_z \sigma\_x = i \sigma\_y \quad ; \quad  \sigma\_z^2 =1$$
$$\sigma^2 = \sigma\_x^2 + \sigma\_y^2 + \sigma\_z^2 =3$$
Define another two Pauli operators:
$$\sigma\_{+} = \frac{1}{2}\left(  \sigma\_x +i \sigma\_y \right)$$
$$\sigma\_{-} = \frac{1}{2}\left(  \sigma\_x -i \sigma\_y \right)$$
Then we will get more commute and anti-commute relationships between the creation and annihilation Pauli operations.
$$\left[ \sigma\_{+}, \sigma\_{-} \right] =  \sigma\_z \quad ; \quad \left\\{ \sigma\_{+}, \sigma\_{-} \right\\} =1$$
$$\left[ \sigma\_{+}, \sigma\_{x} \right] =  \sigma\_z \quad ; \quad \left\\{ \sigma\_{+}, \sigma\_{x} \right\\} =1$$
$$\left[ \sigma\_{+}, \sigma\_{y} \right] = i \sigma\_z \quad ; \quad \left\\{ \sigma\_{+}, \sigma\_{y} \right\\} =1$$
$$\left[ \sigma\_{+}, \sigma\_{z} \right] =  -2 \sigma\_{+} \quad ; \quad \left\\{ \sigma\_{+}, \sigma\_{z} \right\\} =0$$
$$\left[ \sigma\_{-}, \sigma\_{x} \right] = - \sigma\_z \quad ; \quad \left\\{ \sigma\_{-}, \sigma\_{x} \right\\} =1$$
$$\left[ \sigma\_{-}, \sigma\_{y} \right] = i \sigma\_z \quad ; \quad \left\\{ \sigma\_{-}, \sigma\_{y} \right\\} =1$$
$$\left[ \sigma\_{-}, \sigma\_{z} \right] = 2 \sigma\_{-} \quad ; \quad \left\\{ \sigma\_{-}, \sigma\_{z} \right\\} =0$$

---

## Pauli matrixes
Because $\sigma\_z$ and $\sigma^2$ are commuted $\left[ \sigma\_z, \sigma^2 \right]$=0, we can choose common representation of these two operators.
$$\sigma\_z \left|z^{+} \right> = \left|z^{+} \right>$$
$$\sigma\_z \left|z^{-} \right> = - \left|z^{-} \right>$$
$$\sigma^2 \left|z^{+} \right> =3 \left|z^{+} \right>$$
$$\sigma^2 \left|z^{-} \right> =3 \left|z^{-} \right>$$
Therefore, we can write the matrix representation of all these Pauli operators:
$$\sigma\_x=\begin{pmatrix}
0 & 1 \\\\ 1 & 0
\end{pmatrix}$$
$$\sigma\_y=\begin{pmatrix}
0 & -i \\\\ i & 0
\end{pmatrix}$$
$$\sigma\_z=\begin{pmatrix}
1 & 0 \\\\ 0 & -1
\end{pmatrix}$$
$$\sigma\_{+}=\begin{pmatrix}
0 & 1 \\\\ 0 & 0
\end{pmatrix}$$
$$\sigma\_{-}=\begin{pmatrix}
0 & 0 \\\\ 1 & 0
\end{pmatrix}$$
The two eigenstates of $\sigma\_z$ are:
$$\left| z^{+} \right> = \begin{pmatrix}
1 \\\\ 0 \end{pmatrix} \quad; \quad \left| z^{-} \right> = \begin{pmatrix}
0 \\\\ 1 \end{pmatrix}$$
These two states conresponds to the spin up and spin down states or excited state and ground state. I show the relationship between these conversional notation:
$$\left| z^{+} \right> \Longleftrightarrow \left| \uparrow \right> \Longleftrightarrow \left| 0 \right> \Longleftrightarrow \left| e \right>$$
$$\left| z^{-} \right> \Longleftrightarrow \left| \downarrow \right> \Longleftrightarrow \left| 1 \right> \Longleftrightarrow \left| g \right>$$
In the following, I will use the $\left| e \right>$ and $\left| g \right>$ to represent the spin up and spin down states.
Then, we will find some relationships:
$$\sigma\_x \left| e \right> = \left| g \right> \quad; \quad \sigma\_x \left| g \right> = \left| e \right>$$
$$\sigma\_y \left| e \right> =i \left| g \right> \quad; \quad \sigma\_y \left| g \right> = -i\left| e \right>$$
$$\sigma\_z \left| e \right> = \left| e \right> \quad; \quad \sigma\_z \left| g \right> =- \left| g \right>$$
$$\sigma\_{+} \left| e \right> = 0 \quad; \quad \sigma\_{+} \left| g \right> = \left| e \right>$$
$$\sigma\_{-} \left| e \right> = \left| g \right> \quad; \quad \sigma\_{-} \left| g \right> = 0$$
Therefore, we can re-write the Pauli operators by the two egienstates:
$$\sigma\_x = \left| e \right> \left< g \right| + \left| g \right> \left< e \right|$$
$$\sigma\_y = -i \left| e \right> \left< g \right| + i \left| g \right> \left< e \right|$$
$$\sigma\_z = \left| e \right> \left< e \right| - \left| g \right> \left< g \right|$$
$$\sigma\_{+} = \left| e \right> \left< g \right| $$
$$\sigma\_{-} = \left| g \right> \left< e \right| $$

---

## n-level system truncate to 2-level system
For a n-level system, we have the creation and annihilation operators $a^{\dagger}$ and $a$ for the Fock states. When only considering the first two energy levels $\left| 0 \right>$ and $\left| 1 \right>$, we have some relations:
$$a \left| 0 \right> = 0 $$
$$a \left| 1 \right> = \left| 0 \right> $$
$$a^{\dagger} \left| 0 \right> = \left| 1 \right> $$
$$a^{\dagger} \left| 1 \right> = 0 $$

When comparing with the creation and annihilation operators $\sigma\_{+}$ and $\sigma\_{-}$, we will find their conresponding relationships:
$$a \quad \Longleftrightarrow \quad \sigma\_{-}$$
$$a^{\dagger} \quad \Longleftrightarrow \quad \sigma\_{+}$$
Therfore, for a linear harmonic resonator can be simplified as a 2-level system:
$$\begin{align}
H &= \hbar \omega \left( a^{\dagger} a + \frac{1}{2} \right)
\\\\&=\hbar \omega \left( \sigma\_{+} \sigma\_{-} + \frac{1}{2} \right)
\\\\&=\hbar \omega \left( \frac{1+\sigma\_z}{2} + \frac{1}{2} \right)
\\\\& \approx \frac{\hbar \omega }{2} \sigma\_z
\end{align}$$

---

## Summary
This article summaries the properties of all the Pauli operators and exihibits the conresponding relation between a truncated n-level system and a 2-level system.
