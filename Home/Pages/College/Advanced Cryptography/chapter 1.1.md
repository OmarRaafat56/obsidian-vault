[[Advanced Cryptography]]

## Chapter 8 – Public-Key Cryptosystems Based on the Discrete Logarithm Problem

*From:* **Understanding Cryptography – Christof Paar & Jan Pelzl**

---

# 1. Diffie–Hellman Key Exchange (DHKE)

### Overview

* Proposed in **1976**.
* Invented by **Whitfield Diffie** and **Martin Hellman**.
* Used in many protocols:

  * SSH
  * TLS
  * IPSec
* **Purpose:** Securely establish a shared secret over an insecure channel.
* **Important:**

  * DHKE is **not encryption**.
  * It is **only a key exchange protocol**.

---

# 2. Diffie–Hellman Setup

Public parameters:

1. Choose a large prime **p**
2. Choose a generator **α** such that
   ( \alpha \in {2,3,...,p-2} )
3. Publish **p** and **α**

These are called **domain parameters**.

---

# 3. Diffie–Hellman Key Exchange Process

### Alice

1. Choose private key
 $$  ( a \in {1,...,p-1} ) $$

2. Compute public key

$$
A = \alpha^a \mod p
$$

---

### Bob

1. Choose private key


$$b \in {1,...,p-1}$$


2. Compute public key


$$B = \alpha^b \mod p$$


---

### Exchange Public Keys

* Alice sends **A**
* Bob sends **B**

---

### Compute Shared Secret

Alice:


$$k_{AB} = B^a \mod p$$


Bob:


$$k_{AB} = A^b \mod p$$


Both obtain the same key:


$$k_{AB} = \alpha^{ab} \mod p$$


This shared key can then be used for symmetric encryption (e.g., AES).

---

# 4. Example of DHKE

Parameters:

* ( p = 29 )
* ( \alpha = 2 )

Private keys:

* Alice: ( a = 5 )
* Bob: ( b = 12 )

Public keys:


$$A = 2^5 \mod 29 = 3$$



$$B = 2^{12} \mod 29 = 7$$


Shared key:


$$k = 7^5 \mod 29 = 16$$



$$k = 3^{12} \mod 29 = 16$$


Shared secret = **16**

---

# 5. Discrete Logarithm Problem (DLP)

Given:

* A cyclic group ( Z_p^* )
* Generator ( \alpha )
* Value ( \beta )

Find:


$$x \text{ such that } \alpha^x \equiv \beta \mod p$$


This is written as:


$$x = \log_{\alpha}(\beta) \mod p$$


Example:


$$5^x \equiv 41 \mod 47$$


Find **x**.

---

# 6. Generalized Discrete Logarithm Problem

For a cyclic group **G**:


$$\beta = \alpha^x$$


Find **x**.

Where:

* ( \alpha ) = generator
* ( \beta ) = group element
* ( x ) = discrete logarithm

---

# 7. Groups Used for DLP Cryptography

Common groups:

1. **Multiplicative group (Z_p^*)**
   Used in:

   * Diffie–Hellman
   * ElGamal
   * DSA

2. **Elliptic Curve Groups**

3. **Galois Fields (GF(2^m))**

4. **Hyperelliptic Curves**

Most practical systems use:

* **Prime fields**
* **Elliptic curves**

---

# 8. Algorithms for Solving DLP

### Generic Algorithms

Work in any cyclic group:

* Brute Force
* Baby-Step Giant-Step (Shanks)
* Pollard’s Rho
* Pohlig–Hellman

---

### Non-Generic Algorithms

Work only for specific groups (especially (Z_p)):

* **Index Calculus Method**

---

### Important Note

Elliptic curves **cannot use index calculus**, making them more secure with **shorter keys**.

---

# 9. Records for Solving DLP (Prime Fields)

| Decimal Digits | Bit Length | Year |
| -------------- | ---------- | ---- |
| 58             | 193        | 1991 |
| 68             | 216        | 1996 |
| 85             | 282        | 1998 |
| 100            | 332        | 1999 |
| 120            | 399        | 2001 |
| 135            | 448        | 2006 |
| 160            | 532        | 2007 |

---

# 10. Security of Diffie–Hellman

Attacker knows:

* (p, \alpha)
* (A = \alpha^a \mod p)
* (B = \alpha^b \mod p)

Attacker wants:


$$k_{AB} = \alpha^{ab} \mod p$$


This is called the **Diffie–Hellman Problem (DHP)**.

To solve it, attacker would need to solve:


$$a = \log_\alpha(A)$$


Which is the **Discrete Logarithm Problem**.

---

### Security Recommendation

Choose:


$$p > 2^{1024}$$


Typical modern recommendations:

* **2048-bit prime** for stronger security.

---

# 11. ElGamal Encryption Scheme

Proposed by **Taher Elgamal (1985)**.

Based on:

* Discrete Logarithm Problem
* Diffie–Hellman Problem

It extends DHKE to **actual encryption**.

---

# 12. ElGamal Key Generation

Bob:

1. Choose private key


$$d \in {2,...,p-2}$$


2. Compute public key


$$\beta = \alpha^d \mod p$$


Public key:


$$(p,\alpha,\beta)$$


---

# 13. ElGamal Encryption

Alice:

1. Choose random number


$$i$$


2. Compute ephemeral key


$$k_E = \alpha^i \mod p$$


3. Compute masking key


$$k_M = \beta^i \mod p$$


4. Encrypt message (x):


$$y = x \cdot k_M \mod p$$


Ciphertext:


$$(k_E, y)$$


---

# 14. ElGamal Decryption

Bob:

1. Compute masking key


$$k_M = k_E^d \mod p$$


2. Recover message


$$x = y \cdot k_M^{-1} \mod p$$


---

# 15. Computational Cost

### Encryption

* 2 modular exponentiations
* 1 modular multiplication

### Decryption

* 1 modular exponentiation
* 1 modular inverse

Efficient implementations use:

* **Square-and-Multiply algorithm**

---

# 16. Security Considerations

### Passive Attack

Attacker observes:

* (p, \alpha, \beta)
* (k_E)
* (y)

Recovering the message requires solving **DLP**.

---

### Active Attack

Possible if:

* Public keys are **not authenticated**
* Same **ephemeral key is reused**

---

# 17. Key Takeaways

* **Diffie–Hellman** is a fundamental key exchange protocol.
* Security relies on the **Discrete Logarithm Problem**.
* Use **large primes (≥1024 bits)**.
* **2048 bits recommended** for long-term security.
* **ElGamal** extends DHKE for encryption.
* ElGamal is **probabilistic**:

  * Same plaintext → different ciphertexts.

---

# Tags

#cryptography
#public_key_cryptography
#diffie_hellman
#discrete_logarithm_problem
#elgamal
#asymmetric_crypto
#cyclic_groups
#modular_arithmetic
#key_exchange
#information_security
