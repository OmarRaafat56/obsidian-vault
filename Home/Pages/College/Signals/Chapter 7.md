[[Signals]]



---

# Frequency Analysis of Signals and Systems

## 1. Fourier Series
#fourier_series 

Given a **periodic signal** ( x(t) ), we can write:
$$
[
x(t) = \sum_{n=-\infty}^{\infty} d_n e^{j n \omega_0 t}
]
$$
where:

* $$( \omega_0 = \dfrac{2\pi}{T_0} )$$
* ( T_0 ) is the **fundamental period**

### Fourier Series Coefficients
#fourier_series 
$$
[
d_n = \frac{1}{T_0} \int_{-T_0/2}^{T_0/2} x(t) e^{-j n \omega_0 t} , dt
]
$$
---

## 2. Fourier Transform
#fourier_transform 

Given ( x(t) ) is **not periodic**, it can be considered periodic with
$$( T_0 \rightarrow \infty ).$$
$$
[
X(j\omega) = \lim_{T_0 \to \infty} \left( T_0 d_n \right)
]
$$
As $$( T_0 \to \infty )$$:

* $$( n\omega_0 \to \omega ) $$(continuous variable)

### Derivation
$$
[
X(j\omega) = \int_{-\infty}^{\infty} x(t) e^{-j\omega t} , dt
]
$$
$$
[
x(t) = \lim_{T_0 \to \infty} \sum_{n=-\infty}^{\infty} \frac{X(j\omega)}{T_0} e^{j n \omega_0 t}
]
$$
$$
[
= \lim_{T_0 \to \infty} \frac{1}{T_0} \sum_{n=-\infty}^{\infty} X(j\omega) e^{j n \omega_0 t}
]
$$
$$
[
= \lim_{T_0 \to \infty} \frac{\omega_0}{2\pi} \sum_{n=-\infty}^{\infty} X(j\omega) e^{j n \omega_0 t}
]
$$
$$
[
= \frac{1}{2\pi} \int_{-\infty}^{\infty} X(j\omega) e^{j\omega t} , d\omega
]
$$
---

### Fourier Transform Pair
#fourier_transform 

**Analysis Equation**
$$
[
X(j\omega) = \int_{-\infty}^{\infty} x(t) e^{-j\omega t} , dt
]
$$
**Synthesis Equation**
$$
[
x(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} X(j\omega) e^{j\omega t} , d\omega
]
$$
---

## Fourier Transform of Some Signals
#fourier_transform 

### 1. Delta Function
$$
[
\mathcal{F}{\delta(t)}
= \int_{-\infty}^{\infty} \delta(t) e^{-j\omega t} dt
= e^{-j\omega \cdot 0}
= 1
]
$$
---

### 2. Constant Function
$$
[
\mathcal{F}{1} = 2\pi \delta(\omega)
]
$$
---

### 3. Exponential with Unit Step
$$
[
\mathcal{F}{e^{-\alpha t} u(t)}
= \int_0^{\infty} e^{-(\alpha + j\omega)t} dt
]
$$
$$
[
= \left[ \frac{e^{-(\alpha + j\omega)t}}{-(\alpha + j\omega)} \right]_0^{\infty}
]
$$
If $$( \text{Re}{\alpha} > 0 ):$$
$$
[
\mathcal{F}{e^{-\alpha t} u(t)} = \frac{1}{\alpha + j\omega}
]
$$
If $$( \text{Re}{\alpha} < 0 )$$, the Fourier Transform **does not exist**.

---

### 4. Left-Sided Exponential
$$
[
\mathcal{F}{-e^{-\alpha t} u(-t)}
= -\int_{-\infty}^{0} e^{(\alpha + j\omega)t} dt
]
$$
* If$$ ( \text{Re}{\alpha} < 0 ):$$
$$
[
\mathcal{F}{-e^{-\alpha t} u(-t)} = \frac{1}{\alpha + j\omega}
]
$$
* If$$ ( \text{Re}{\alpha} > 0 ):$$
$$
[
\mathcal{F}{-e^{-\alpha t} u(-t)} = \frac{1}{-\alpha + j\omega}
]
$$
---

### 5. Unit Step Function
$$
[
\mathcal{F}{u(t)} = \frac{1}{j\omega} + \pi \delta(\omega)
]
$$
---

### 6. Sign Function
$$
[
\mathcal{F}{\text{sgn}(t)} = \frac{2}{j\omega}
]
$$
---

## Properties of the Fourier Transform
#fourier_transform 

### 1. Linearity
$$
[
\mathcal{F}{\alpha_1 x_1(t) + \alpha_2 x_2(t)}
= \alpha_1 X_1(j\omega) + \alpha_2 X_2(j\omega)
]
$$
---

### 2. Time Shift
$$
[
\mathcal{F}{x(t - t_0)}
= \int_{-\infty}^{\infty} x(t - t_0) e^{-j\omega t} dt
]
$$
Let:
$$
[
t' = t - t_0
]
$$
Then:
$$
[
\mathcal{F}{x(t - t_0)}
= e^{-j\omega t_0} X(j\omega)
]
$$
---


## 3. Frequency Shift / Modulation Property
$$
[
\mathcal{F}{x(t)e^{j\omega_0 t}}
;\longleftrightarrow;
X\big(j(\omega - \omega_0)\big)
]
$$
### Modulation by a Cosine
$$
[
\cos(\omega_0 t) = \frac{1}{2}\left(e^{j\omega_0 t} + e^{-j\omega_0 t}\right)
]
$$
$$
[
\mathcal{F}{x(t)\cos(\omega_0 t)}
= \frac{1}{2} X\big(j(\omega - \omega_0)\big)

* \frac{1}{2} X\big(j(\omega + \omega_0)\big)
  ]
$$
---

## 4. Filtration Property

### (Convolution in the Time Domain)

### Time-Domain Convolution
$$
[
y(t) = x(t) * h(t)
= \int_{-\infty}^{\infty} x(\tau) h(t - \tau) , d\tau
]
$$
### Fourier Transform of Convolution
#fourier_transform 
$$
[
\mathcal{F}{x(t) * h(t)}
= \int_{-\infty}^{\infty} (x(t) * h(t)) e^{-j\omega t} dt
]
$$
$$
[
= \int_{-\infty}^{\infty} \int_{-\infty}^{\infty}
x(\tau) h(t - \tau) e^{-j\omega t}
, d\tau , dt
]
$$
$$
[
= \int_{-\infty}^{\infty} x(\tau) e^{-j\omega \tau} d\tau
\int_{-\infty}^{\infty} h(t) e^{-j\omega t} dt
]
$$
$$
[
= X(j\omega) , H(j\omega)
]
$$
---

### Interpretation

* $$( H(j\omega) )$$ **modifies the spectrum** of ( x(t) )
* Effects of $$( H(j\omega) ):$$

  1. Changes **magnitude**
  2. Changes **phase**
$$
[
H(j\omega) ;\text{is called the *frequency response* of the LTI system}
]
$$
---

