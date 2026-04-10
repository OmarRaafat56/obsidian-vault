[[Signals]]

___

## Sampling

### Ideal Sampling

> **Ideal sampling:** the clock is an impulse train.
$$
[
p_T(t) = \sum_{n=-\infty}^{\infty} \delta(t - nT)
]
$$
The sampled signal is:
$$
[
x_s(t) = x(t)p_T(t)
]
$$
$$
[
x_s(t) = x(t)\sum_{n=-\infty}^{\infty}\delta(t-nT)
= \sum_{n=-\infty}^{\infty}x(nT)\delta(t-nT)
]
$$
---

### Fourier Transform of the Sampled Signal
#fourier_transform 
Taking the Fourier transform of both sides:
$$
[
X_s(j\Omega) = \sum_{n=-\infty}^{\infty} x(nT)e^{-j\Omega nT}
]
$$
Define:

* $$(\omega = \Omega T)$$
* $$(\omega)$$: discrete-time radian frequency (rad)
* $$(\Omega)$$: continuous-time radian frequency (rad/s)

Then:
$$
[
X(e^{j\omega}) = \sum_{n=-\infty}^{\infty} x[n]e^{-j\omega n}
]
$$
This is the **Discrete-Time Fourier Transform (DTFT)**.

---

## DTFT Properties
#fourier_transform 
### 1. Periodicity

The DTFT is **periodic with period (2\pi)**.

**Proof:**
$$
[
X(e^{j(\omega+2\pi)}) = \sum_{n=-\infty}^{\infty}x[n]e^{-j(\omega+2\pi)n}
]
$$
$$
[
= \sum_{n=-\infty}^{\infty}x[n]e^{-j\omega n}e^{-j2\pi n}
]
$$
$$
[
= \sum_{n=-\infty}^{\infty}x[n]e^{-j\omega n}
= X(e^{j\omega})
]
$$
> The standard DTFT is defined over ([-\pi, \pi]).

---

### Aliasing and Nyquist Rate

To prevent aliasing (overlap between spectral replicas):
$$
[
\Omega_s \ge 2\Omega_m
]
$$
* **Nyquist sampling rate:** $$(2\Omega_m)$$

---

### 2. Linearity
$$
[
\text{DTFT}{\alpha_1 x_1[n] + \alpha_2 x_2[n]}
= \alpha_1 X_1(e^{j\omega}) + \alpha_2 X_2(e^{j\omega})
]
$$
---

### 3. Time Shift
$$
[
\text{DTFT}{x[n-k]} = e^{-j\omega k}X(e^{j\omega})
]
$$
---

### 4. Convolution in Time Domain
$$
[
\text{DTFT}{x[n] * h[n]} = X(e^{j\omega})H(e^{j\omega})
]
$$
---

### 5. Frequency Shift
$$
[
\text{DTFT}{x[n]e^{j\omega_0 n}}
= X(e^{j(\omega-\omega_0)})
]
$$
---

### 6. Multiplication by (n)
$$
[
X(e^{j\omega}) = \sum_{n=-\infty}^{\infty}x[n]e^{-j\omega n}
]
$$
$$
[
\frac{d}{d\omega}X(e^{j\omega})
= \sum_{n=-\infty}^{\infty}(-jn)x[n]e^{-j\omega n}
]
$$
$$
[
\text{DTFT}{n x[n]} = j\frac{d}{d\omega}X(e^{j\omega})
]
$$
> Multiplication by (n) in time ↔ differentiation in frequency.

---

## DTFT of Simple Signals

### 1. Unit Impulse
$$
[
\text{DTFT}{\delta[n]}
= \sum_{n=-\infty}^{\infty}\delta[n]e^{-j\omega n}
= 1
]
$$
---

### 2. Constant Signal
$$
[
\text{DTFT}{1}
= 2\pi\sum_{k=-\infty}^{\infty}\delta(\omega - 2\pi k)
]
$$
---

### 3. Sign Function
$$
[
\text{DTFT}{\text{sgn}[n]}
= \frac{2}{1 - e^{-j\omega}}
]
$$
---

### 4. Unit Step
$$
[
\text{DTFT}{u[n]}
= \frac{1}{1 - e^{-j\omega}}

* \pi\sum_{k=-\infty}^{\infty}\delta(\omega - 2\pi k)
  ]
$$
---

### 5. Exponential (Right-Sided)
$$
[
\text{DTFT}{a^n u[n]}
= \sum_{n=0}^{\infty}a^n e^{-j\omega n}
]
$$
This is a geometric series.

**Convergence condition:**
$$
[
|a| < 1
]
$$
$$
[
\Rightarrow \text{DTFT}{a^n u[n]}
= \frac{1}{1 - ae^{-j\omega}}
]
$$
---

### 6. Exponential (Left-Sided)
$$
[
\text{DTFT}{-a^n u[-n-1]}
= -\sum_{n=-\infty}^{-1}a^n e^{-j\omega n}
]
$$
Convergence condition:
$$
[
|a| > 1
]
$$
$$
[
\text{DTFT}{-a^n u[-n-1]}
= \frac{1}{1 - ae^{-j\omega}}
]
$$
---

## Inverse DTFT
$$
[
x[n] = \frac{1}{2\pi}
\int_{-\pi}^{\pi}X(e^{j\omega})e^{j\omega n},d\omega
]
$$
> Usually solved using DTFT properties, partial fractions, and known transforms.

---

## Examples

### Example 1

**Given:**
$$
[
X(e^{j\omega}) = \frac{1}{1 + 4e^{-j\omega}}
]
$$
**Find:** (x[n])

**Solution:**
$$
[
x[n] = -(-4)^n u[-n-1]
]
$$
---

### Example 2

**Given:**
$$
[
X(e^{j\omega}) = \frac{1}{1 - 0.2e^{-j\omega}}
]
$$
**Find:** (x[n])

**Solution:**
$$
[
x[n] = (0.2)^n u[n]
]
$$
---

### Example 3

**Given:**
$$
[
X(e^{j\omega}) = \frac{1}{2}(e^{j\omega} + e^{-j\omega}) = \cos\omega
]
$$
**Solution:**
$$
[
x[n] = \frac{1}{2}\big[\delta[n+1] + \delta[n-1]\big]
]
$$
---

## System Example Using DTFT

**Given:**
$$
[
x[n] = (0.2)^n u[n]
]
$$
$$
[
h[n] = (0.5)^n u[n]
]
$$
Find the output (y[n]).

---

### Solution
$$
[
X(e^{j\omega}) = \frac{1}{1 - 0.2e^{-j\omega}}
]
$$
$$
[
H(e^{j\omega}) = \frac{1}{1 - 0.5e^{-j\omega}}
]
$$
$$
[
Y(e^{j\omega})
= \frac{1}{(1 - 0.2e^{-j\omega})(1 - 0.5e^{-j\omega})}
]
$$
Using partial fractions:
$$
[
Y(e^{j\omega})
= \frac{A}{1 - 0.2e^{-j\omega}}

* \frac{B}{1 - 0.5e^{-j\omega}}
  ]
$$
$$
[
A = -\frac{2}{3}, \quad B = \frac{5}{3}
]
$$
Final result:
$$
[
y[n] = -\frac{2}{3}(0.2)^n u[n]

* \frac{5}{3}(0.5)^n u[n]
  ]
$$
---

#fourier_transform #fourier_series #DTFT #nyquist-rate #inverse-DTFT 