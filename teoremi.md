---
header-includes: |
            \usepackage{cancel}
            \usepackage{steinmetz}
---
# Lista teoremi Teoria dei Segnali

## Introduzione
1. $x(t)$ segnale periodico di periodo $T_0$ e ha potenza media su un intervallo finita, allora ha $\bar{P}$ finita e calcolabile sul periodo:
    
    Per definizione $\bar{P}= \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} |x(t)|^{2} \,dt$. Scegliamo come periodo $NT_0$, in quanto se $N\to \infty$ vale come $T\to \infty$.

    Quindi $\displaystyle \lim_{N \to \infty} \frac{1}{NT_0} \int_{-\frac{NT_0}{2}}^{\frac{NT_0}{2}} |x(t)|^{2} \,dt$ equivale a $N$ integrali cui si aggiunge un $T_0$ ogni volta:

    $$
    \displaystyle \lim_{N \to \infty} \frac{1}{\cancel{N}T_0} \cdot \cancel{N} \{ \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} |x(t)|^{2} \,dt \} = \bar{P} = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} |x(t)|^{2} \,dt
    $$

## Segnali periodici a tempo continuo
### Serie di Fourier
2. Da forma polare a complessa (o rettangolare)

    la forma polare della serie di Fourier è data da:
    $$
    x(t) = A_0 + 2 \sum_{k=1}^{\infty} A_{k} \cos (2\pi kf_{0}t + \theta_{K})
    $$
    $$
    = A_0 + \cancel{2} \sum_{k=1}^{\infty} A_{k} \frac{e^{j(2\pi kf_{0}t + \theta_{K})}+e^{-j(2\pi kf_{0}t + \theta_{K})}}{\cancel{2}} \to \text{ uso formula di Eulero per il coseno}
    $$
    $$
    = A_0 + \sum_{k=1}^{\infty} A_{k} e^{j2\pi kf_{0}t + \theta_{K}}  + \sum_{k=1}^{\infty} A_{k} e^{-j2\pi kf_{0}t + \theta_{K}} \to \text{ separo le due esponenziali}
    $$
    $$
    = x_0 + \sum_{k=1}^{\infty} A_{k} e^{j\theta_{k}} e^{j2\pi kf_{0}t}  + \sum_{k=1}^{\infty} A_{k} e^{-j\theta_{k}} e^{-j2\pi kf_{0}t}  \to \text{ raggruppo le sommatorie}
    $$
    $$
    = x_0 + \sum_{k=1}^{\infty} X_k e^{j2\pi kf_{0}t}  + \sum_{k=1}^{\infty} X_k e^{-j2\pi kf_{0}t}
    $$
    $$
    \Rightarrow x(t) = \sum_{k=-\infty}^{\infty} X_k \ e^{j2\pi kf_{0}t} \text{ forma complessa della serie di Fourier}
    $$

3. Come si calcolano i coefficienti $X_n$?
    
    Partendo dalla forma complessa, moltiplico a destra e a sinistra per $e^{-j2\pi kf_{0}t}$, integrando sul periodo $T_0$.
    $$
    \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t)e^{-j2\pi kf_{0}t} \,dt = \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} \sum_{k=-\infty}^{\infty} X_k \ e^{j2\pi kf_{0}t}  e^{-j2\pi nf_{0}t} \,dt
    $$
    Porto fuori la sommatoria e raccolgo $e$: per ipotesi la serie converge.
    $$
    \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t)e^{-j2\pi kf_{0}t} \,dt = \sum_{k=-\infty}^{\infty} X_k  \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} e^{j2\pi (k-n)f_{0}t} 
    $$
    L'integrale al secondo membro viene calcolato per $k\neq n$
    $$
    \to \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} e^{j2\pi (k-n)f_{0}t} = \frac{e^{j2\pi (k-n)f_{0}t}}{j2\pi (k-n)f_{0}} \Big|_{-\frac{T_0}{2}}^{\frac{T_0}{2}}=
    $$
    $$
    \frac{e^{j\cancel{2}\pi (k-n)\cancel{f_{0}}\frac{\cancel{T_0}}{\cancel{2}}} - e^{-j\cancel{2}\pi (k-n)\cancel{f_{0}}\frac{\cancel{T_0}}{\cancel{2}}}}{2j \cdot \pi (k-n)f_{0}} \to \text{ uso formula di Eulero per il seno}
    $$
    $$
    \frac{\sin (\pi (k-n))}{\pi (k-n)f_{0}} = \left\{ \begin{array}{cl}
    k=n\to T_0  \\
    k\neq n \to 0
    \end{array} \right.
    \to \text{ sostituiamo questo risultato}
    $$
    $$
    \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t)e^{-j2\pi nf_{0}t} \,dt = X_{n}T_{0} \Rightarrow X_{n} = \frac{1}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t)e^{-j2\pi nf_{0}t} \,dt 
    $$

4. Forma rettangolare dalla forma polare
    $$
    x(t) = A_{0} + 2 \sum_{k=1}^{\infty} A_{k} \cos(2\pi k f_{0}t + \theta_{k})
    $$
    usiamo la formula di addizione $\cos(\alpha + \beta) = \cos\alpha\cos\beta - \sin\alpha\sin\beta$
    $$
    x(t) = A_{0} + 2 \sum_{k=1}^{\infty} (A_{k}(\cos(2\pi k f_{0})\cos({\theta_k}) - \sin(2\pi k f_{0})\sin({\theta_k})))
    $$
    $$
    x(t) = a_{0} + 2 \sum_{k=1}^{\infty} [a_{k} \cos(2\pi k f_{0}) - b_{k}\sin(2\pi k f_{0})]
    $$
    sapendo che $a_{0} = A_{0}, \ a_{k} = A_{k}\cos(\theta_k), \ b_{k} = B_{k}\sin(\theta_k)$.

    Abbiamo quindi ottenuto la forma rettangolare della serie di Fourier, dove si nota che un segnale *periodico* $x(t)$ può essere espresso tramite una **somma di seni e coseni**.

    Il coefficiente $X_n$ può essere espresso anche come:
    $$
    X_k = \frac{1}{T_0} \int_{[T_0]} x(t) (\cos(2\pi kf_{0}t) - j\sin(2\pi kf_{0}t))
    $$
    $$
    X_k = a_k +jb_k = A_k \cos(\theta_k) + jA_k\sin(\theta_k) = A_k e^{j\theta_k}
    $$

5. Criterio di Dirichlet (per $x(t)$ periodico):

    È una serie di condizioni che se incontrate sono sufficienti per poter sviluppare un dato segnale $x(t)$ in serie di Fourier:
    * $x(t)$ deve essere *assolutamente integrabile sul periodo*: ovvero $(\int_{[T_0]}|x(t)| \,dt < \infty)$
    * $x(t)$ deve essere *continua* (o avere un numero *finito* di discontinuità di prima specie)
    * $x(t)$ deve essere *derivabile sul periodo* $T_0$, escluso al più un numero finito di punti, dove comunque esiste **finita** sia la derivata destra che la derivata sinistra
        - quest'ultima ipotesi è equivalente a: $x(t)$ presenta un numero finito di massimi e minimi nel periodo
    La serie **converge** al valore assunto da $x(t)$ dove *continua* e alla semisomma dei limiti sinistro e destro se discontinua.

### Spettro di un segnale periodico e reale
#### Proprietà
6. Simmetria Hermitiana dello spettro reale:

    I coefficienti $X_k$ sono generalmente quantità complesse del tipo $X_k = |X_{k}|e^{j\phase{X_{k}}}$: $X_{k}$ può essere rappresentata tramite spettro di ampiezza e spettro di fase, discreti (esiste solo in corrispondenza delle armoniche k)
    $$
    X_k = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi kf_{0}t} \,dt
    $$
    Analizziamone il coniugato $X^{*}_{k}$:
    $$
    X_k^{*} = \Big(\frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi kf_{0}t} \,dt \Big)^{*} = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t)^{*} e^{+j2\pi kf_{0}t} \,dt = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi (-k)f_{0}t} \,dt
    $$
    È da notare come $x(t)^{*}=x(t)$, dal momento che il segnale $x(t)$ è reale.

    Quindi $X_{k}^{*}=X_{-k}$: i coefficienti $X_k$ di un segnale *reale* sono **simmetrici hermitiani**, ossia hanno *lo stesso modulo e fase opposta*
    $$
    X_{-k}=X_{k}^{*} \Longleftrightarrow \left\{ \begin{array}{cl}
    |X_k|=|X_{-k}| \ \text{ stesso modulo}  \\
    \phase{X_{k}} = -\phase{X_{-k}} \ \text{ fase opposta}
    \end{array} \right.
    $$
    In definitiva per un segnale reale:
        - lo spettro d'ampiezza è **simmetrico** rispetto a $k \to$ pari
        - lo spettro di fase è **antisimmetrico** rispetto a $k \to$ dispari

    TODO: controllare appunti Agata

7. Linearità dello spettro reale:

    Se $x(t)$ e $y(t)$ sono due segnali con periodo $T_0$ *reali* allora vale:
    $$
    z(t)=ax(t)+by(t) \Longleftrightarrow Z_{k} = aX_{k} + bY_{k}
    $$
    Somma di *oscillazioni* alle (o con?) le stesse frequenze dei segnali $x(t)$ e $y(t)$.
    $$
    Z_{k} = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} z(t) e^{-j2\pi kf_{0}t} \,dt = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} (ax(t)+by(t)) e^{-j2\pi kf_{0}t} \,dt 
    $$
    $$
    = \frac{a}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi kf_{0}t} \,dt + \frac{b}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} y(t) e^{-j2\pi kf_{0}t} \,dt = aX_{k}+bY_{k}
    $$

8. Parità e disparità del segnale

    * Se $x(t)$ è **pari**, allora il coefficiente $X_{k} = X_{-k}$; se il segnale è anche **reale** vale $X_{k}=X_{-k}=X^{*}_{k} \Longleftrightarrow X_k \in \mathbb{R}$. 
        
        $X_k = X_{-k}$ (con un cambio di variabile $\alpha=-t \to \,dt=-\,d\alpha$).
        $$
        X_{k} = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi kf_{0}t} \,dt \Longleftrightarrow X_{-k} = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi (-k)f_{0}t} \,dt 
        $$
        Utilizziamo il cambio di variabile
        $$
        X_{-k} = \frac{1}{T_0} \int_{\frac{T_0}{2}}^{-\frac{T_0}{2}} x(-\alpha) e^{-j2\pi (\cancel{-}(\cancel{-}\alpha)) kf_{0}} -\,d\alpha = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(\alpha) e^{-j2\pi\alpha kf_{0}} \,d\alpha =
        $$
        $$
        -\frac{1}{T_0} \int_{\frac{T_0}{2}}^{-\frac{T_0}{2}} x(\alpha) e^{-j2\pi\alpha kf_{0}} \,d\alpha = X_k
        $$
        dato che il segnale $\in \mathbb{R}$ lo possiamo rappresentare come (perché essendo reale ha fase nulla?):
        $$
        x(t) = X_{0} + 2\sum_{k=1}^{\infty}X_{k}\cos(2\pi kf_{0}t)
        $$
        Dimostrazione:
        $$
        x(t) = \sum_{k=-\infty}^{\infty} X_{k} e^{j2\pi kf_{0}t} = X_{0} + \sum_{k=1}^{\infty} X_{k} e^{j2\pi kf_{0}t} + \sum_{k=-1}^{\infty} X_{k} e^{j2\pi kf_{0}t} =
        $$
        $$
        = X_{0} + \sum_{k=1}^{\infty} X_{k} e^{j2\pi kf_{0}t} + \sum_{k=1}^{\infty} X_{-k} e^{-j2\pi kf_{0}t} =
        $$
        $$
        = X_{0} + \sum_{k=1}^{\infty} X_{k} e^{j2\pi kf_{0}t} + \sum_{k=1}^{\infty} X_{k} e^{-j2\pi kf_{0}t} =
        $$
        $$
        = X_{0} + 2 \sum_{k=1}^{\infty} X_{k} \frac{e^{j2\pi kf_{0}t}+ e^{-j2\pi kf_{0}t}}{2} = X_{0} + 2 \sum_{k=1}^{\infty} X_{k} \cos{(2\pi k f_{0}t)}
        $$
        Da ciò deduco che un segnale reale e pari è esprimibile in serie di soli *coseni* (i quali sono a loro volta pari).

        Possiamo inoltre scrivere i coefficienti $X_k$ in modo semplificato, data la *parità* del segnale:
        $$
        X_k = \frac{1}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi kf_{0}t} \,dt = \frac{1}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} \underset{pari}{x(t)}\cdot\underset{pari}{\cos{(2\pi kf_{0}t)}} \,dt - \frac{j}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} \underset{pari}{x(t)}\cdot\underset{dispari}{\sin{(2\pi kf_{0}t)}}\,dt=
        $$
        $$
        \frac{2}{T_0} \int_{0}^{\frac{T_0}{2}} x(t)\cdot\cos{(2\pi kf_{0}t)} \,dt - 0
        $$

    * se $x(t)$ è **dispari**, allora anche i coefficienti $X_k$ saranno dispari. Inoltre, dato che $x(t)\in\mathbb{R}$, $X_k$ sarà un **immaginario puro**, ed 
        $$
        x(t)=2j \sum_{k=1}^{\infty} X_{k} \sin{(2\pi k f_{0}t)} \text{ e } X_k=-\frac{2j}{T_0}\int_{0}^{\frac{T_0}{2}}x(t)\sin(2\pi kf_0 t) \,dt
        $$
        Dimostrazione:

        * Dato che $x(t)\in\mathbb{R}$, $X_k$, allora vale $X_{-k} = -X_{k} = X_{k}^{*} \Rightarrow X_{k}^{*}=-X_k$, quindi è un immaginario puro!
        * Per $X_k$:
        $$
        X_k = \frac{1}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi kf_{0}t} \,dt = \frac{1}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} \underset{dispari}{x(t)}\cdot\underset{pari}{\cos{(2\pi kf_{0}t)}} \,dt - \frac{j}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} \underset{dispari}{x(t)}\cdot\underset{dispari}{\sin{(2\pi kf_{0}t)}}\,dt=
        $$
        $$
        -\frac{j}{T_0} \int_{0}^{\frac{T_0}{2}} x(t)\cdot\sin{(2\pi kf_{0}t)} \,dt 
        $$

    * **Note varie**
        
        Se $x(t)$ è pari i suoi coefficienti $X_k$ sono reali e lo spettro di fase vale $0$ o $\pm \pi$; mentre se $x(t)$ è dispari i suoi coefficienti $X_k$ sono immaginari puri e lo spettro di ampiezza non viene toccato: un segnale dispari è solo "spostato" nel tempo.

