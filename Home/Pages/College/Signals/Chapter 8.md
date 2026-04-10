[[Signals]]

---

## Previously Covered

### Fourier Transform
#fourier_transform 

* **x(t)**: signal in the time domain
* **X(jω)**: signal in the frequency domain

**Analysis equation:**
$$
[
X(j\omega) = \int_{-\infty}^{\infty} x(t)e^{-j\omega t},dt
]
$$
**Synthesis equation:**
$$
[
x(t) = \frac{1}{2\pi}\int_{-\infty}^{\infty} X(j\omega)e^{j\omega t},d\omega
]
$$
---

## Fourier Transforms of Basic Signals
#fourier_transform 

| x(t)                     | X(jω)                                        |
| ------------------------ | -------------------------------------------- |
| δ(t)                     | 1                                            |
| 1                        | $$(2\pi \delta(\omega))$$                    |
| u(t)                     | $$(\frac{1}{j\omega} + \pi\delta(\omega))$$  |
| sgn(t)                   | $$(\frac{2}{j\omega})$$                      |
| $$(e^{\alpha t}u(t))$$   | $$(\frac{1}{-\alpha + j\omega}), Re{α} < 0$$ |
| $$(-e^{\alpha t}u(-t))$$ | $$(\frac{1}{-\alpha + j\omega}), Re{α} > 0$$ |

---

## 4. AM Modulator
$$
[
x_{AM}(t) = x(t)\cos(\omega_0 t)
]
$$
$$
[
= x(t)\cdot \frac{1}{2}\left(e^{j\omega_0 t} + e^{-j\omega_0 t}\right)
]
$$
$$
[
X_{AM}(j\omega) = \frac{1}{2}\left[X(j(\omega-\omega_0)) + X(j(\omega+\omega_0))\right]
]
$$
---

## 5. Derivative in Time Domain
#derivative 
$$
\mathcal{F}\left\{\dot{x}(t)\right\} = j\omega X(j\omega)
$$

---

## 6. Integration in Time Domain
#integration 
$$
\mathcal{F}\left\{\int_{-\infty}^{t} x(\tau)\, d\tau \right\}
= \frac{1}{j\omega} X(j\omega) + \pi x(0)\delta(\omega)
$$

### Proof of Fourier Transform of (u(t))
#fourier_transform 

We know:
$$
[
u(t) = \int_{-\infty}^{t}\delta(\tau),d\tau
]
$$
$$
[
\mathcal{F}{u(t)}
= \frac{1}{j\omega}(1) + \pi(1)\delta(\omega)
= \frac{1}{j\omega} + \pi\delta(\omega)
]
$$
---

## 7. Multiplication by *t* in Time Domain
$$
[
\mathcal{F}{t,x(t)} = j\frac{d}{d\omega}X(j\omega)
]
$$
### Proof
$$
[
X(j\omega) = \int_{-\infty}^{\infty} x(t)e^{-j\omega t},dt
]
$$
$$
[
\frac{d}{d\omega}X(j\omega)
= \int_{-\infty}^{\infty} x(t)(-jt)e^{-j\omega t},dt
]
$$
$$
[
= -j\int_{-\infty}^{\infty} t,x(t)e^{-j\omega t},dt
]
$$
$$
[
\Rightarrow \mathcal{F}{t,x(t)} = j\frac{d}{d\omega}X(j\omega)
]
$$
---

## 8. Convolution in Frequency Domain
$$
[
\mathcal{F}{x(t)y(t)}
= \frac{1}{2\pi}\int_{-\infty}^{\infty}X(j\sigma)Y(j(\omega-\sigma)),d\sigma
]
$$
---

## 9. Scaling in Time
$$
[
\mathcal{F}{x(\alpha t)} = \frac{1}{|\alpha|}X\left(j\frac{\omega}{\alpha}\right)
]
$$
### 9.5 Special Case (Time Reversal)
$$
[
\mathcal{F}{x(-t)} = X(-j\omega)
]
$$
---

## 11. Symmetry Properties

### Conjugate Symmetric (Even)
$$
[
x(t) = x^*(-t)
]
$$
> Remember: ((3 + j4)^* = 3 - j4)

### Conjugate Antisymmetric (Odd)
$$
[
x(t) = -x^*(-t)
]
$$
---

### Additional Properties

* Fourier transform of a **pure real** signal is **conjugate symmetric**

  * Magnitude is **even**
  * Phase is **odd**

* Fourier transform of a **pure imaginary** signal is **conjugate antisymmetric**
$$
[
x(t)\ \text{pure imaginary} \Rightarrow X(j\omega) = -X^*(-j\omega)
]
$$
---

### Even and Odd Functions

* Fourier transform of an **even** function is **pure real**

**Example:**
$$
[
\mathcal{F}{\cos(\omega_0 t)}
= \pi\left[\delta(\omega-\omega_0) + \delta(\omega+\omega_0)\right]
]
$$
* Fourier transform of an **odd** function is **pure imaginary**

**Example:**
$$
[
\mathcal{F}{\sin(\omega_0 t)}
= \frac{1}{2j}\left[\delta(\omega-\omega_0) - \delta(\omega+\omega_0)\right]
]
$$
---

## Inverse Fourier Transform
#fourier_transform 

We usually use **properties of Fourier transforms of simple functions** and **partial fractions**.

### Example 1

**Given:**
$$
[
X(j\omega) = \frac{1}{3 + j\omega}
]
$$
**Find:** (x(t))

**Solution:**
$$
[
x(t) = e^{-3t}u(t)
]
$$
---

### Example 2

**Given:**
$$
[
X(j\omega) = \frac{1}{-5 + j\omega}
]
$$
**Find:** (x(t))

**Solution:**
$$
[
x(t) = -e^{5t}u(-t)
]
$$
---

### Partial Fraction Examples

* Example and solution: 
![[Screenshot_20251228_020450_Drive.jpg]]

* Another example and solution: 
*![[Screenshot_20251228_015927_Drive.jpg]]

---

