# Fractional-and-Volterra-processes-for-Fourier-pricing

This project explores the evolution of option pricing models, from the classical Black-Scholes framework to more advanced stochastic volatility models, namely Heston and Volterra-Heston (rough Heston).

---

## **1. Limitations of the Black-Scholes Model**

The Black-Scholes (BS) model is a cornerstone of financial mathematics, providing a closed-form solution for European option pricing. It assumes:

- Constant volatility over time.
- Log-normal distribution of asset prices.
- No jumps in prices.

**Limitations observed in real markets:**

- **Volatility smiles and skews:** Market-implied volatilities vary across strikes and maturities, contrary to the constant volatility assumption.  
- **Short-term options:** BS often misprices options with very short maturities.  
- **Volatility clustering:** Real market volatility exhibits persistence and roughness that BS cannot capture.  

These limitations motivated the development of **stochastic volatility models**.

---

## **2. Introduction to the Heston Model**

The **Heston model** introduces stochastic volatility:

\begin{align*}
	dS_t &=S_t \sqrt{V_t} dB_t, \quad d\langle W, B\rangle_t = \rho dt \\
	dV_t &= (\theta-\kappa V_t)dt + \eta \sqrt{V_t} dW_t, \quad V_0 \geq 0, S_0=1
\end{align*}


where:

- $S_t$ is the asset price.  
- \(V_t\) is the instantaneous variance.  
- \(\kappa\) is the speed of mean reversion, \(\theta\) is the long-term variance.  
- \(\sigma\) is the volatility of variance (vol of vol).  
- \(\rho\) is the correlation between the asset and its variance.

**Advantages:**

- Captures **volatility smiles and skews**, especially for medium and long maturities.  
- Provides **stochastic volatility**, allowing more realistic modeling of market dynamics.  

**Limitations:**

- Fails to reproduce the **steep short-term skew** observed in real markets.  
- Volatility paths are still relatively smooth, unlike empirical "rough volatility" data.  

---

## **3. Introduction to the Volterra-Heston (Rough Heston) Model**

The **Volterra-Heston** model generalizes the Heston model by introducing **memory effects and rough volatility**:

\[
V_t = V_0 + \int_0^t K(t-s) \big( \kappa (\theta - V_s) ds + \sigma \sqrt{V_s} dW_s^V \big)
\]

- \(K(t-s)\) is a kernel (often \(t^{\alpha-1}\), \(0 < \alpha < 1\)) that induces rough paths.  
- Captures the **empirical roughness** and **short-term irregularities** of market volatility.  

**Advantages:**

- Fits **short-term implied volatility skews** more accurately than Heston.  
- Models **volatility clustering and power-law decay** of ATM volatility across maturities.  
- Provides a more **realistic term structure of volatility**.  

---

## **Conclusion**

- **Black-Scholes:** simple, closed-form, but unrealistic for short-term or skewed markets.  
- **Heston:** stochastic volatility, good for medium/long maturities, but smooth paths limit short-term accuracy.  
- **Volterra-Heston:** captures rough volatility, steep short-term skew, and realistic term structure.  
