# Fractional-and-Volterra-processes-for-Fourier-pricing

This project explores the evolution of option pricing models, starting from the classical Black-Scholes framework and moving to stochastic volatility models, specifically Heston and Volterra-Heston (rough Heston).

---

## 1. Limitations of the Black-Scholes Model

The Black-Scholes (BS) model is a cornerstone of financial mathematics, providing closed-form solutions for European option pricing. It assumes:

- Constant volatility over time.
- Log-normal distribution of asset prices.
- No jumps in prices.

**Limitations observed in real markets:**

- **Volatility smiles and skews:** Market-implied volatilities vary across strikes and maturities, contrary to the constant volatility assumption.  
- **Short-term options:** BS often misprices options with very short maturities.  
- **Volatility clustering:** Real market volatility exhibits persistence and roughness that BS cannot capture.  

These limitations motivated the development of **stochastic volatility models**.

---

## 2. The Heston Model

The **classical Heston model** introduces stochastic volatility:

$$
dS_t = S_t \sqrt{V_t} \, dB_t, \quad d\langle W, B\rangle_t = \rho \, dt, \quad S_0=1
$$

$$
dV_t = (\theta - \lambda V_t) \, dt + \eta \sqrt{V_t} \, dW_t, \quad V_0 \geq 0
$$

where:

- $S_t$ is the asset price.  
- $V_t$ is the instantaneous variance.  
- $\lambda$ is the speed of mean reversion.  
- $\theta$ is the long-term variance level.  
- $\eta$ is the volatility of variance (vol of vol).  
- $\rho$ is the correlation between the asset and its variance.

**Advantages:**

- Captures **volatility smiles and skews** for medium and long maturities.  
- Provides **stochastic volatility**, allowing more realistic modeling of market dynamics.  

**Limitations:**

- Fails to reproduce the **steep short-term skew** observed in real markets.  
- Volatility paths are still relatively smooth compared to empirical “rough volatility” data.  

---

## 3. The Volterra-Heston (Rough Heston) Model

The **Volterra-Heston model** generalizes Heston by introducing **memory effects and rough volatility**:

$$
\begin{align*}
dS_t &= S_t \sqrt{V_t} \, dB_t, \quad S_0=1,\\
V_t &= V_0 + \int_0^t K_{\epsilon}(t-s) \Big( (\theta - \lambda V_s) \, ds + \eta \sqrt{V_s} \, dW_s \Big),
\end{align*}
$$

with the kernel:

$$
K_{\epsilon}(t) = (t + \epsilon)^{H-1/2}, \quad 0 < H < 1/2
$$

- Introduces **rough paths** for volatility to better match empirical data.  
- Captures **short-term steep skew**, **volatility clustering**, and **power-law decay** of ATM volatility.  
- Provides a **more realistic term structure** of implied volatility across maturities.

---

## 4. Conclusion

- **Black-Scholes:** simple, closed-form, but unrealistic for short-term or skewed markets.  
- **Heston:** stochastic volatility, good for medium/long maturities, but smooth paths limit short-term accuracy.  
- **Volterra-Heston:** rough volatility, steep short-term skew, realistic term structure of implied volatility.  

This project implements simulations and examples to visualize the differences between these models.
