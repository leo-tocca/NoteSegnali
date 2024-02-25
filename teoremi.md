# Lista teoremi Teoria dei Segnali

## Introduzione
1. $x(t)$ segnale periodico di periodo $T_0$ e ha potenza media su un intervallo finita, allora ha $\bar{P}$ finita e calcolabile sul periodo:
    
    Per definizione $\bar{P}= \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} |x(t)|^{2} \,dt$. Scegliamo come periodo $NT_0$, in quanto se $N\to \infty$ vale come $T\to \infty$.

    Quindi $\displaystyle \lim_{N \to \infty} \frac{1}{NT_0} \int_{-\frac{NT_0}{2}}^{\frac{NT_0}{2}} |x(t)|^{2} \,dt$ equivale a $N$ integrali cui si aggiunge un $T_0$ ogni volta:

    $\displaystyle \lim_{N \to \infty} \frac{1}{NT_0} \cdot N \{ \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} |x(t)|^{2} \,dt \} = \bar{P} = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} |x(t)|^{2} \,dt$

## Segnali periodici a tempo continuo
### Serie di Fourier
2. Da polare a complessa
    la forma polare della serie di Fourier è data da:
    $$
    x(t) = A_0 + 2 \sum_{k=1}^{\infty} A_{k} \cos (2\pi kf_{0}t + \theta_{K}) \\
    = A_0 + \cancel{2} \sum_{k=1}^{\infty} A_{k} \frac{e^{j(2\pi kf_{0}t + \theta_{K})}+e^{-j(2\pi kf_{0}t + \theta_{K})}}{\cancel{2}} \to \text{ uso formula di Eulero per il coseno} \\
    = A_0 + \sum_{k=1}^{\infty} A_{k} e^{j2\pi kf_{0}t + \theta_{K}}  + \sum_{k=1}^{\infty} A_{k} e^{-j2\pi kf_{0}t + \theta_{K}} \to \text{ separo le due esponenziali} \\
    = x_0 + \sum_{k=1}^{\infty} A_{k} e^{j\theta_{k}} e^{j2\pi kf_{0}t}  + \sum_{k=1}^{\infty} A_{k} e^{-j\theta_{k}} e^{-j2\pi kf_{0}t}  \to \text{ raggruppo le sommatorie} \\
    = x_0 + \sum_{k=1}^{\infty} X_k e^{j2\pi kf_{0}t}  + \sum_{k=1}^{\infty} X_k e^{-j2\pi kf_{0}t} \\
    \Rightarrow x(t) = \sum_{k=1}^{\infty} X_k e^{j2\pi kf_{0}t} \text{ forma complessa della serie di Fourier}
    $$
3. Come si calcolano i coefficienti $X_n$?

