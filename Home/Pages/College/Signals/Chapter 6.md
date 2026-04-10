  [[Signals]]





---

# Frequency Analysis of Signals and Systems

## 1. Orthogonality of Signals
#orthogonal 

Two signals ( x(t) ) and ( y(t) ) are **orthogonal** if their inner product is zero:
$$
[
\langle x(t), y(t) \rangle = 0
]
$$
This occurs when ( x(t) ) is perpendicular to ( y(t) ).

### Inner Product (Aperiodic Signals)
#inner_product 
$$
[
\langle x(t), y(t) \rangle = \int_{-\infty}^{\infty} x(t),y(t),dt
]
$$
### Inner Product (Periodic Signals)
#inner_product 

For #periodic signals with period ( T ):
$$
[
\int_{-T/2}^{T/2} x(t),y(t),dt = 0
]
$$
---

## 2. Orthogonality of Sinusoids
#orthogonal 

Let:
$$
[
x(t) = \sin(m\omega t), \quad y(t) = \sin(n\omega t)
]
$$
Using the trigonometric identity:
#trigonometry 
$$
[
\sin a \sin b = \frac{1}{2}[\cos(a-b) - \cos(a+b)]
]
$$
$$
[
\sin(m\omega t)\sin(n\omega t)
= \frac{1}{2}\left[\cos((m-n)\omega t) - \cos((m+n)\omega t)\right]
]
$$
### Results
$$
 ( \sin(m\omega t) ) $$ 
* is #orthogonal to:
$$ ( \sin(n\omega t) ) when ( m \neq n )
$$
___
$$
( \sin(m\omega t) )$$ 
* is #orthogonal to:
$$ ( \cos(n\omega t) )
$$
---

$$
( \cos(m\omega t) ) $$
* is #orthogonal to:
$$( \cos(n\omega t) ) when ( m \neq n )
$$
---

$$
( e^{jm\omega t} ) $$
is #orthogonal to:

$$( e^{-jn\omega t} ) when ( m \neq n )
$$
### Proof Example (Sine–Cosine Orthogonality)

Using identities:
$$
[
\sin(a+b) = \sin a \cos b + \cos a \sin b
]
$$
$$
[
\sin(a-b) = \sin a \cos b - \cos a \sin b
]
$$
$$
[
\sin a \cos b = \frac{1}{2}[\sin(a+b) + \sin(a-b)]
]
$$
$$
[
\sin(m\omega t)\cos(n\omega t)
= \frac{1}{2}\left[\sin((m+n)\omega t) + \sin((m-n)\omega t)\right]
]
$$
The integral over one period is zero.

---

## Fourier Series
#fourier_series 

Any #periodic signal can be expanded in terms of sinusoids with frequencies:
$$
[
0, \omega, 2\omega, \dots, k\omega, \dots
]
$$
where ( \omega ) is the **fundamental frequency**.

---

## 1. Rectangular (Trigonometric) Form
#trigonometry 

If ( x(t) ) is #periodic with period ( T ):
$$
[
x(t) = a_0 + \sum_{n=1}^{\infty} a_n \cos(n\omega t)
+ \sum_{n=1}^{\infty} b_n \sin(n\omega t)
]
$$
### Coefficients
$$
[
a_0 = \frac{1}{T} \int_{-T/2}^{T/2} x(t),dt
]
$$
$$
[
a_n = \frac{2}{T} \int_{-T/2}^{T/2} x(t)\cos(n\omega t),dt
]
$$
$$
[
b_n = \frac{2}{T} \int_{-T/2}^{T/2} x(t)\sin(n\omega t),dt
]
$$
### Useful Identities
$$
[
\cos^2 a = \frac{1}{2}(1 + \cos 2a)
]
$$
$$
[
\sin^2 a = \frac{1}{2}(1 - \cos 2a)
]
$$
---

## Compact (Amplitude–Phase) Form
$$
[
a_n \cos(n\omega t) + b_n \sin(n\omega t)
= c_n \cos(n\omega t + \phi_n)
]
$$
Where:
$$
[
c_n = \sqrt{a_n^2 + b_n^2}
]
$$
$$
[
\phi_n = -\tan^{-1}\left(\frac{b_n}{a_n}\right)
]
$$
### Compact Fourier Series
#fourier_series 
$$
[
x(t) = \sum_{n=0}^{\infty} c_n \cos(n\omega t + \phi_n)
]
$$
---

## 3. Exponential Form
$$
[
x(t) = \sum_{n=-\infty}^{\infty} d_n e^{jn\omega t}
]
$$
### Coefficients
$$
[
d_n = \frac{1}{T} \int_{-T/2}^{T/2} x(t)e^{-jn\omega t},dt
]
$$
### Proof Sketch
$$
[
\frac{1}{T} \int_{-T/2}^{T/2}
\left[\sum_{m=-\infty}^{\infty} d_m e^{jm\omega t}\right]
e^{-jn\omega t} dt
]
$$

___


