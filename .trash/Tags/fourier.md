

## #fourier_series 

A Fourier series is a way to represent a periodic function as an infinite sum of sines and cosines (or complex exponentials). It shows that complicated periodic signals can be built from simple waves.


---

**Basic idea**

If a function  is periodic with period , it can be written as:
$$
f(x) = \frac{a_0}{2}
+ \sum_{n=1}^{\infty}
\left( a_n \cos(nx) + b_n \sin(nx) \right)
$$
This is called the Fourier series of .


---

Fourier coefficients

The constants  tell us how much of each sine and cosine wave is needed:
$$
a_0 = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x)\,dx
$$
$$
a_n = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x)\cos(nx)\,dx
$$
$$
b_n = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x)\sin(nx)\,dx
$$

---

**Why it matters**

Fourier series are fundamental in:

* Physics (heat transfer, waves, vibrations)

* Engineering (signal processing, electrical circuits)

* Mathematics (solving differential equations)

* Data & audio compression


---

**Intuitive explanation**

Think of it like this:

Any periodic signal (even a square wave) can be broken into a sum of smooth sine and cosine waves each with different frequencies and amplitudes.

---

**Simple example**

A square wave can be written as:

$$
f(x) = \frac{4}{\pi}

\left(
\sin x + \frac{1}{3}\sin 3x + \frac{1}{5}\sin 5x + \cdots
\right)
$$
Even though a square wave has sharp corners, it can still be approximated using smooth sine waves.


---


