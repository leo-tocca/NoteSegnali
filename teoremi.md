---
header-includes: |
            \usepackage{cancel}
            \usepackage{steinmetz}
            \usepackage{derivative}
            \usepackage{mathtools}
            \usepackage{siunitx}
            \DeclareMathOperator{\sinc}{sinc}
            \DeclareMathOperator{\rect}{rect}
            \DeclareMathOperator{\tfs}{TFS}
            \newcommand{\dft}{\operatorname{DFT}}
            \newcommand{\tf}[1]{\text{T}\Big[ #1 \Big]}
            \newcommand{\Abs}[1]{\Big| #1 \Big|}
            \newcommand{\ov}[1]{\overline{#1}}
            \usepackage{geometry}
				\geometry{
					a4paper,
					total={170mm,257mm},
					left=20mm,
					top=20mm,
				}
---
# Lista teoremi Teoria dei Segnali

## Introduzione
1. $x(t)$ segnale periodico di periodo $T_0$ e ha potenza media su un intervallo finita, allora ha $\bar{P}$ finita e calcolabile sul periodo:
    
    Per definizione $\bar{P}= \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} |x(t)|^{2} \,dt$. Scegliamo come periodo $NT_0$, in quanto se $N\to \infty$ vale come $T\to \infty$.

    Quindi $\displaystyle \lim_{N \to \infty} \frac{1}{NT_0} \int_{-\frac{NT_0}{2}}^{\frac{NT_0}{2}} |x(t)|^{2} \,dt$ equivale a $N$ integrali cui si aggiunge un $T_0$ ogni volta:

    $$
    \displaystyle \lim_{N \to \infty} \frac{1}{\cancel{N}T_0} \cdot \cancel{N} \Big \{ \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} |x(t)|^{2} \,dt \} = \bar{P} = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} |x(t)|^{2} \,dt
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
    = A_0 + \sum_{k=1}^{\infty} A_{k} e^{j(2\pi kf_{0}t + \theta_{k})}  + \sum_{k=1}^{\infty} A_{k} e^{-j(2\pi kf_{0}t + \theta_{K})} \to \text{ separo le due esponenziali}
    $$
    $$
    = x_0 + \sum_{k=1}^{\infty} A_{k} e^{j\theta_{k}} e^{j2\pi kf_{0}t}  + \sum_{k=1}^{\infty} A_{k} e^{-j\theta_{k}} e^{-j2\pi kf_{0}t}  \to \text{ raggruppo le sommatorie e} k \text{ diventa }-k
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
    \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t)e^{-j2\pi kf_{0}t} \,dt = \sum_{k=-\infty}^{\infty} X_k  \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} e^{j2\pi (k-n)f_{0}t} \,dt
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
    
    N-esimo termine della serie di Fourier
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

    I coefficienti $X_k$ sono generalmente quantità complesse del tipo 
    \begin{gather*}
    X_k = |X_{k}|e^{j\phase{X_{k}}}
    \end{gather*}
    $X_{k}$può essere rappresentata tramite spettro di ampiezza e spettro di fase, discreti (esiste solo in corrispondenza delle armoniche $k$)
    $$
    X_k = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi kf_{0}t} \,dt
    $$
    Analizziamone il coniugato $X^{*}_{k}$:
    $$
    X_k^{*} = \Big(\frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi kf_{0}t} \,dt \Big)^{*} = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t)^{*} e^{+j2\pi kf_{0}t} \,dt = \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi (-k)f_{0}t} \,dt
    $$
    È da notare come $x(t)^{*}=x(t)$, dal momento che il segnale $x(t)$ è reale.

    Quindi $X_{k}^{*}=X_{-k}$: i coefficienti $X_k$ di un segnale *reale* **godono di simmetria hermitiana**, ossia hanno *lo stesso modulo e fase opposta*
    $$
    X_{-k}=X_{k}^{*} \Longleftrightarrow \left\{ \begin{array}{cl}
    |X_k|=|X_{-k}| \ \text{ stesso modulo}  \\
    \phase{X_{k}} = -\phase{X_{-k}} \ \text{ fase opposta}
    \end{array} \right.
    $$
    In definitiva per un segnale reale:
    - lo spettro d'ampiezza è **simmetrico** rispetto a $k \to$ pari
    - lo spettro di fase è **antisimmetrico** rispetto a $k \to$ dispari

    <!--- (TODO: controllare appunti Agata) --->
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
        \begin{gather*}
        X_{-k} = \frac{1}{T_0} \int_{\frac{T_0}{2}}^{-\frac{T_0}{2}} x(-\alpha) e^{-j2\pi (\cancel{-}(\cancel{-}\alpha)) kf_{0}} -\,d\alpha = -\frac{1}{T_0} \int_{\frac{T_0}{2}}^{-\frac{T_0}{2}} x(\alpha) e^{-j2\pi\alpha kf_{0}} \,d\alpha =
        \\ 
        \frac{1}{T_0} \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(\alpha) e^{-j2\pi\alpha kf_{0}} \,d\alpha = X_k
        \end{gather*}
        dato che il segnale $\in \mathbb{R}$ lo possiamo rappresentare come (perché essendo reale ha fase nulla?):
        $$
        x(t) = X_{0} + 2\sum_{k=1}^{\infty}X_{k}\cos(2\pi kf_{0}t)
        $$
        Dimostrazione:
        $$
        x(t) = \sum_{k=-\infty}^{\infty} X_{k} e^{j2\pi kf_{0}t} = X_{0} + \sum_{k=1}^{\infty} X_{k} e^{j2\pi kf_{0}t} + \sum_{k=-\infty}^{-1} X_{k} e^{j2\pi kf_{0}t} =
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
        \begin{gather*}
        X_k = \frac{1}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi kf_{0}t} \,dt = \\
        \frac{1}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} \underbrace{x(t)}_{pari}\cdot\underbrace{\cos{(2\pi kf_{0}t)}}_{pari} \,dt - \frac{j}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} \underbrace{x(t)}_{pari}\cdot\underbrace{\sin{(2\pi kf_{0}t)}}_{dispari}\,dt=
        \\
        \frac{2}{T_0} \int_{0}^{\frac{T_0}{2}} x(t)\cdot\cos{(2\pi kf_{0}t)} \,dt - 0
        \end{gather*}
        Integrale di una funzione pari su un intervallo simmetrico.

    * se $x(t)$ è **dispari**, allora anche i coefficienti $X_k$ saranno dispari. Inoltre, dato che $x(t)\in\mathbb{R}$, $X_k$ sarà un **immaginario puro**, ed 
        $$
        x(t)=2j \sum_{k=1}^{\infty} X_{k} \sin{(2\pi k f_{0}t)} \text{ e } X_k=-\frac{2j}{T_0}\int_{0}^{\frac{T_0}{2}}x(t)\sin(2\pi kf_0 t) \,dt
        $$
        Dimostrazione:

        * Dato che $x(t)\in\mathbb{R}$, $X_k$, allora vale $X_{-k} = -X_{k} = X_{k}^{*} \Rightarrow X_{k}^{*}=-X_k$, quindi è un immaginario puro!
        * Per $X_k$:
        $$
        X_k = \frac{1}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x(t) e^{-j2\pi kf_{0}t} \,dt =
        $$
        \begin{gather*}
        \frac{1}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} \underbrace{x(t)}_{\text{dispari}}\cdot\underbrace{\cos(2\pi kf_{0}t)}_{\text{pari}} \,dt - \frac{j}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} \underbrace{x(t)}_{\text{dispari}}\cdot\underbrace{\sin(2\pi kf_{0}t)}_{\text{dispari}}\,dt=
        \\
        -\frac{2j}{T_0} \int_{0}^{\frac{T_0}{2}} x(t)\cdot\sin{(2\pi kf_{0}t)} \,dt 
        \end{gather*}

    * **Note varie**
        
        * Se $x(t)$ è pari i suoi coefficienti $X_k$ sono reali e lo spettro di fase vale $0$ o $\pm \pi$; mentre se $x(t)$ è dispari i suoi coefficienti $X_k$ sono immaginari puri e lo spettro di ampiezza non viene toccato: un segnale dispari è solo "spostato" nel tempo.
        * È da notare come la diversa velocità di un segnale dipenda dal suo andamento temporale: le variazioni brusche comportano la presenza di **armoniche**[^1] con $k$ più elevato per rappresentare la velocimento alta(?):
            * più il segnale è regolare meno armoniche sono necessarie per "ricreare" il segnale
                * $\frac{1}{k} \to$ funzioni discontinue: dente di sega ideale, onda quadra, onda quadra "antisimmetrica", rect
                * $\frac{1}{k^2} \to$ funzioni continue a derivata discontinua: onda triangolare.
[^1]: TODO: definire meglio armoniche

## Segnali aperiodici a tempo continuo
### Trasformata continua di Fourier

> Una funzione non periodica, definita tra $-\infty$ e $\infty$, può essere rappresentata come **somma** di **infinite armoniche semplici** di ampiezza *infinitesima* e di frequenza variabile con continuità tra $-\infty$ e $\infty$

9. Dal segnale periodico al segnale aperiodico...
     
    Partiamo dall'impulso rettangolare *aperiodico* $\rect{\frac{t}{T}}$:
    \begin{gather*}
    x(t) = \rect{\frac{t}{T}} \to x_{p}(t) = \sum \rect(\frac{t-nT_0}{T}) \text{ treno di impulsi rettangolari}
    \end{gather*}
    possiamo vedere $x(t)$ come caso limite di $x_p(t)$ con periodo $T_0 \to \infty$
    $$
    x(t) = \lim_{T_0 \to \infty} x_{p}(t)
    $$
    1. la frequenza diventa infinitesima $(f_0 = \frac{1}{T_0})$
    2. si riduce la *distanza tra le armoniche*, ossia si **infittisce** lo spettro;
    3. $X_k=\frac{1}{T_0}\int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} x_p(t) \ e^{-j2\pi kf_0 t}\,dt$, l'ampiezza assume valori *sempre più piccoli*

    Usiamo il coefficiente *modificato* $X(f_0 k) = T_0 X_k$ per ovviare il problema. Riscriviamo $x_p(t)$ e $X_k$\
    \begin{gather*}
    x_{p}(t) = \sum_{k=-\infty}^{\infty}X(kf_0)\ e^{j2\pi kf_0 t} \cdot f_0 \to x(t) = \underbrace{\int_{-\infty}^{\infty}X(f)\ e^{j2\pi ft}\,df}_{\text{integrale di Fourier}}
    \end{gather*}
    Le armoniche si *infittiscono talmente tanto* da non essere più distinte ma **continue**.

    \begin{gather*}
    X(kf_0) = T_0 \ X_k = \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}}  x_{p}(t) \ e^{-j2\pi kf_0 t}\,dt \to \underbrace{X(f) = \int_{-\infty}^{\infty}x(t)\ e^{j2\pi ft}\,dt}_{\text{trasformata continua di Fourier}}
    \end{gather*}

    $X(f)$ è una **funzione complessa della variabile continua $f$**, quindi è di spettro continuo.

    - Nota: **differenze tra segnali continui periodici e aperiodici**:
        * un segnale *periodico* è rappresentato da componenti sinusoidali a frequenze in relazione **armonica** (multipli di $f_0$, frequenza *fondamentale* e ad ampiezza finita).
        * un segnale *aperiodico* è rappresentato con componenti sinusoidali di ampiezza *infinitesima* $|X(f)|\,df$ e frequenza $f$ variabile con continuità su $\mathbb{R}$; è un segnale
        periodico di periodo illimitato con $f_0$ infinitesimo. Le armoniche discrete *degenerano* nell'insieme continuo.

10. Criteri di esistenza per la trasformata continua di Fourier (TCF)
    1. $X(f)$ esiste se il segnale $x(t)$ ha energia finita (condizione "sufficiente")!
    2. Criteri di Dirichlet:
        1.  la funzione deve essere assolutamente sommabile: $\displaystyle \int_{-\infty}^{\infty} |x(t)| dt < +\infty$
        2.  se in qualunque intervallo finito $t_1 < t < t_2$ è continua o presenta un numero finito di discontinuità di prima specie
        3.  se in qualunque intervallo finito $t_1 < t < t_2$ la funzione ha un numero finito di massimi e minimi.

    Allora $x(t)$ è rappresentabile come TCF e 
    $$
    x(t) = \int_{-\infty}^{\infty}X(f)\ e^{j2\pi ft} \,df =  \left\{ \begin{array}{cl}
    x(t) \ \text{ se continua}  \\
    \frac{x(t_{0}^{+})-x(t_{0}^{-})}{2}\ \text{ se discontinua}
    \end{array} \right.
    $$

    
11. Simmetria Hermitiana della trasformata continua di Fourier

    Possiamo rappresentare $X(f)$ in forma rettangolare:
    $$
    X(f) = Re(f) + Im(f) = \int_{-\infty}^\infty x(t) \cos(2\pi ft) \,dt - j\int_{-\infty}^\infty x(t) \sin(2\pi ft) \,dt
    $$
    $$
    \underbrace{Re(f)=Re(-f)}_{\text{pari}} \text{ e } \underbrace{Im(f)=-Im(-f)}_{\text{dispari}} \Longrightarrow X(f)=X^{*}(-f) \text{ simmetria hermitiana}
    $$
    infatti $X(f)=Re(f)+jIm(f)=Re(-f)+jIm(f)=X^{*}(-f)$
    - lo spettro di ampiezza è quindi *pari* a quello di fase dispari.
12. Parità e disparità:
    - se un segnale è *reale e pari*
    $$
    X(f) = \int_{-\infty}^\infty x(t) \cos(2\pi ft) \,df=
    \left\{ \begin{array}{cl}
    Re(f) = 2\int_{0}^\infty x(t) \cos(2\pi ft) \,dt \\
    Im(f) = 0
    \end{array} \right.
    $$
    $\to X(f) = Re(f) \to X(f)=X(-f)$ è reale e pari
    - se un segnale è *dispari e reale*
    $$
    X(f) = - \int_{-\infty}^\infty x(t) \sin(2\pi ft) \,dt=
    \left\{ \begin{array}{cl}
    Re(f) = 0 \\
    Im(f) = -2\int_{0}^\infty x(t) \sin(2\pi ft) 
    \end{array} \right.
    $$
    $\to X(f)=jIm(f) \to X(f)=-X(f)$ è immaginaria pura e dispari

#### Proprietà della trasformata continua

13. **Linearità**
    
    Dati due segnali $x_1(t)$ e $x_2(t)$ con le loro trasformate continue di Fourier $X_1(f)$ e $X_2(f)$, allora se:
    $$
    x(t) = ax_1(t) + bx_2(t) \Longleftrightarrow X(f)=aX_1(f)+bX_2(f)
    $$
    con $a,b$ costanti, $X_1(f)=\text{TCF}[x_1(t)]$ e $X_2(f)=\text{TCF}[x_2(t)]$
    * Dimostrazione:
        $$
        X(f)= \int_{-\infty}^{\infty}x(t)\ e^{-j2\pi ft}\,dt = \int_{-\infty}^{\infty}(ax_1(t) + bx_2(t)) \ e^{-j2\pi ft}\,dt
        $$
        ma sappiamo che l'integrale è *lineare*, quindi
        $$
        = a\int_{-\infty}^{\infty}x_1(t)\ e^{-j2\pi ft}\,dt + b\int_{-\infty}^{\infty}x_2(t)\ e^{-j2\pi ft}\,dt = aX_1(f)+bX_2(f)
        $$

14. **Dualità**
    
    se $x(t)\Longleftrightarrow X(f)$, allora $X(t)\Longleftrightarrow x(-f)$:

    Se la trasformata continua di Fourier passa ad essere un *segnale nel tempo*, allora $x(-f)$ è la sua trasformata di Fourier. Abbiamo quindi una corrispondenza biunivoca tra la funzione e la sua trasformata.
    * Esempio:
        $$
        \rect(\frac{t}{T})\Longleftrightarrow\sinc(fT)
        $$
        Ma se nel tempo ho un segnale $\sinc(bT)$ qual è la sua trasformata?

        $T\sinc(Tt) \Longleftrightarrow \rect({-\frac{f}{T}})$ da cui $\sinc(Bt)\Longleftrightarrow \frac{1}{B}\rect(\frac{t}{B})$, dove $B$ indica la banda.
    * Dimostrazione:
        $$
        x(t) =\int_{-\infty}^{\infty}X(f)\ e^{j2\pi ft} \,df \to x(f) = \int_{-\infty}^{\infty}X(t)\ e^{j2\pi ft} \,dt 
        $$
        con uno scambio di variabili $t$ con $f$. Quindi:
        $$
        x(-f)=\int_{-\infty}^{\infty}<S-Del>Xx(t)\ e^{-j2\pi ft} \,dt 
        $$
        Da qui deriviamo che $x(-f)$ è la trasformata di $X(t)$

15. **Ritardo**
    
    Sia $X(f)=\text{TCF}[x(t)]$: la trasformata di Fourier di $x(t)$ ritardato nel tempo di una quantità $t_0$ è pari a:
    $$
    x(t-t_0) \Longleftrightarrow X(f) \ e^{-j2\pi ft_0}
    $$

    - Dimostrazione:

    Applichiamo a $x(t-t_0)$ la definizione di TCF
    $$
    x(t-t_0) \Longleftrightarrow \int_{-\infty}^{\infty} x(t-t_0) \ e^{-j2\pi ft} \,dt = \text{ sostituiamo } \Big\{\alpha = t-t_0 \to t=\alpha +t_0, \,dt = \,d\alpha
    $$
    $$
    x(t-t_0) \Longleftrightarrow \int_{-\infty}^{\infty} x(\alpha) e^{-j2\pi (\alpha +t_0)f} \,d\alpha = e^{-j2\pi ft_0} \int_{-\infty}^{\infty} x(\alpha)\ e^{-j2\pi f\alpha} =  e^{-j2\pi ft_0} \ X(f) 
    $$
    - Esempio:
    $$
    A\rect(\frac{t-\frac{T}{2}}{T}) \Longleftrightarrow AT\sinc(fT)e^{-j\cancel{2}\pi f\frac{T}{\cancel{2}}}
    $$

    Se $y(t)=x(t-t_0) \Rightarrow Y(f) = X(f) \ e^{-j2 pi ft_0} \Rightarrow$ Un ritardo modifica lo spettro di **fase** ma *non cambia* il suo spettro di ampiezza, in quanto quest'ultimo di indica quali componenti sinusoidali sono necessarie per comporre la forma del segnale, mentre lo spettro di fase mi dice con quale *angolo* iniziale devono "partire" le sinusoidi.

    Quindi se il segnale si sposta nel tempo, allora le sinusoidi hanno angoli iniziali diversi, ma sono le stesse.
    \begin{gather*}
    |Y(f)| = |X(f)|\cdot |e^{-j2\pi ft_0}| = |X(f)| \\
    \phase{Y(f)} = \phase{X(f) \ e^{-j2 pi ft_0}} = \phase{X(f)} + \phase{e^{-j2 pi ft_0}} = \underbrace{\phase{X(f)} - \overbrace{2\pi ft_0}^{=0}}_{\text{\underline{NON} è una traslazione!}}
    \end{gather*}
16. **Cambiamento di scala**

    Si consideri $y(t)=x(\alpha t)$, effettuando un *cambiamento della scala temporale*:
    $$
    \begin{array}{cl}
    |\alpha | > 1 \ \to \text{ compressione della scala dei tempi} \to \text{ l'evoluzione è "accelerata"}\\
    |\alpha | < 1 \ \to \text{ dilatazione della scala dei tempi} \to \text{ l'evoluzione è "rallentata"}\\
    \alpha  < 0 \ \to \text{ inversione della scala dei tempi}
    \end{array} 
    $$
    Inoltre vale:
    $$
    x(\alpha t) \Longleftrightarrow \frac{1}{|\alpha |} X(\frac{f}{\alpha})
    $$
    - Dimostrazione:
    $$
    \cdot \ \ \underline{\alpha > 0} \Rightarrow x(\alpha t) \Longleftrightarrow \int_{-\infty}^{\infty} x(\alpha t) e^{-j2\pi ft} \,dt \text{, ponendo } z=\alpha t \to t = \frac{z}{\alpha}, \,dz = \alpha \,dt \to \,dt = \frac{\,dz}{\alpha} 
    $$
    $$
    \Rightarrow x(\alpha t) \Longleftrightarrow \int_{-\infty}^{\infty} \frac{x(z) e^{-j2\pi f \frac{z}{\alpha}}}{\alpha} \,dz = \frac{1}{\alpha}\int_{-\infty}^{\infty} x(z) e^{-j2\pi f \frac{z}{\alpha}} \,dz = \frac{1}{\alpha} X(\frac{f}{\alpha})
    $$
    $$
    \cdot \ \ \underline{\alpha < 0} \Rightarrow x(\alpha t) \Longleftrightarrow \int_{\infty}^{-\infty} \frac{x(z) e^{-j2\pi f \frac{z}{\alpha}}}{\alpha} \,dz = -\frac{1}{\alpha}\int_{-\infty}^{\infty} x(z) e^{-j2\pi f \frac{z}{\alpha}} \,dz = -\frac{1}{\alpha} X(\frac{f}{\alpha})
    $$
    È da notare come l'inversione dell'integrale nel secondo caso l'abbiamo quando $t \to -\infty, \ z \to +\infty$. Inoltre abbiamo sostituito $z=-\alpha t$.

    Quindi una *dilatazione* nel tempo corrisponde ad una *compressione* in frequenza, e **viceversa**

17. **Modulazione**

    Dato un segnale $x(t)$ e la sua trasformata $X(f)$ allora
    $$
    x(t)\cos(2\pi f_{0}t) \Longleftrightarrow \frac{X(f-f_0)+X(f+f_0)}{2}
    $$
    dove $X(f-f_0)$ e $X(f+f_0)$ sono rispettivamente la replica centrata in $f_0$ e la replica centrata in $-f_0$.

    - Dimostrazione:
    \begin{gather*}
    \text{TCF}[x(t)\cos(2\pi f_{0}t)] = \int_{-\infty}^{\infty} x(t)\cos(2\pi f_{0}t)  e^{-j2\pi ft} \,dt = 
    \\
    = \frac{1}{2} \int_{-\infty}^{\infty} x(t) [e^{-j2\pi f_0 t}+ e^{-j2\pi f_0 t}]e^{-j2\pi ft} \,dt =\\ \frac{1}{2}\Big[\int_{-\infty}^{\infty}x(t)  e^{-j2\pi (f-f_0)t}\,dt + \int_{-\infty}^{\infty}x(t)  e^{-j2\pi (f+f_0)t}\,dt  \Big] =
    \\
    \frac{X(f-f_0)+X(f+f_0)}{2}
    \end{gather*}
    Corollario: $x(t)e^{j2\pi f_{0}t} \Longleftrightarrow X(f-f_0) \to$ *traslazione in frequenza*

18. **Derivazione**

    Se $x(t) \to X(f)$, allora:
    $$
    \odv{}{t} x(t) \Longleftrightarrow j2\pi f \cdot X(f) = Y(f)
    $$
    Una derivata nel tempo è una *moltiplicazione* in frequenza.

    - Dimostrazione:

    Deriviamo entrambi i lati di $x(t)$:
    \begin{gather*}
    \odv{}{t}x(t) = \odv{}{t} \int_{-\infty}^{\infty} X(f) e^{j2\pi ft} \,df = \int_{-\infty}^{\infty}\odv{}{t} \Big [X(f) e^{j2\pi ft} \Big ] \,df = \int_{-\infty}^{\infty} X(f) \odv{}{t}e^{j2\pi ft} \,df = 
    \\
    \int_{-\infty}^{\infty} X(f) (2\pi f) e^{j2\pi ft} \,df \Longrightarrow \text{TCF}\Big[\odv{x(t)}{t}\Big] = j2\pi f X(f)
    \end{gather*}

    Il teorema della derivazione *modifica gli spettri*
    \begin{gather*}
    |Y(f)| = 2\pi f |X(f)| \\ \phase{Y(f)} = \phase{X(f)} + \text{sgn}(f)\frac{\pi}{2}
    \end{gather*}
    Aumenta proporzionalmente l'ampiezza, esaltando le altre frequenze, e sfasando di $\pm \frac{\pi}{2}$
    
19. **Integrazione** (deriva dal teorema di derivazione)

    Dato un segnale $x(t) \Longleftrightarrow X(f)$ e un segnale $y(t) = \int_{-\infty}^{t} x(\alpha) \,d\alpha$, allora vale
    $$
    \int_{-\infty}^{t}  x(\alpha) \,d\alpha \Longleftrightarrow \frac{X(f)}{j2\pi f}
    $$
    - Dimostrazione:

    Segue dal teorema di derivazione e richiede che $X(0)=0$, al fine di evitare che per $f\to 0$, il rapporto tenda ad infinito.
    \begin{gather*}
    X(0)= 0 \longleftrightarrow X(0)=\underbrace{\int_{-\infty}^{\infty}x(t) \ e^{0}\,dt}_{\text{sottende area} \textbf{ nulla}} \longleftrightarrow y(\infty) = \int_{-\infty}^{\infty} x(t)\,dt = X(0) \to 0 \\ y(t) = \int_{-\infty}^{t} x(\alpha) \,d\alpha \Rightarrow x(t) \odv{}{t}y(t) \Rightarrow X(f)=j2\pi f\cdot Y(f) \Rightarrow Y(f) = \frac{X(f)}{j2\pi f}
    \end{gather*}
    Anche l'integrale nel tempo si trasforma in un'operazione algebrica in frequenza: in questo caso però vengono esaltate le componenti a **bassa** frequenza nello spettro del segnale, mentre le alte vengono attenuate; la fase varia sempre di $\pm \frac{\pi}{2}$
    \begin{gather*}
    |Y(f)| = \frac{|X(f)|}{2\pi f} \\ \phase{Y(f)} = \phase{X(f)} + \text{sgn}(f)\frac{\pi}{2}
    \end{gather*}
    Da questo teorema deriva la relazione $A \text{tri}(\frac{t}{T})\Longleftrightarrow AT\sinc^{2}(fT); \ A\rect (\frac{t}{T})\Longleftrightarrow AT\sinc (fT)$

20. **Prodotto**: è il duale della convoluzione

    Partendo da due segnali $x(t)$ e $y(t)$
    $$
    z(t)=x(t)\cdot y(t) \Longleftrightarrow X(f) \otimes Y(f)
    $$
    - Dimostrazione:
    \begin{gather*}
    \Rightarrow Z(f) =  \int_{-\infty}^{\infty}x(t)\ y(t)\ e^{-j2\pi ft}\,dt = \int_{t=-\infty}^{\infty} \Big[ \int_{\nu = -\infty}^{\infty} X(\nu) e^{-j2\pi \nu t} \,d\nu \Big ] y(t)\ e^{-j2\pi ft}\,dt= \\ 
    \int_{\nu=-\infty}^{\infty} X(\nu) \Big[ \int_{t = -\infty}^{\infty}  y(t)\ e^{-j2\pi (f-\nu)t}\,dt \Big ] \,d\nu =  \int_{\nu = -\infty}^{\infty} X(\nu) Y(f-\nu) \,d\nu =
    \\ X(f) \otimes Y(f)
    \end{gather*}
    Quindi:
    $$
    \underset{PRODOTTO}{x(t) \ y(t)} \Longleftrightarrow \underset{CONVOLUZIONE}{X(f)\otimes Y(f)} \to \text{ la convoluzione è \textit{commutativa}}
    $$
    Nota Bene: $\nu$ è __nu__!

21. **_Convoluzione_**

    Dati due segnali $x(t)$ e $y(t)$ sappiamo che:
    $$
    z(t) = x(t) \otimes y(t) \Longleftrightarrow X(f) \ Y(f)
    $$
    - Dimostrazione:

        Partiamo sempre dalla definizione di TCF:
    \begin{gather*}
    z(t) = x(t) \otimes y(t) = \int_{-\infty}^{\infty} x(\alpha) y(t-\alpha) \,d\alpha \Longleftrightarrow Z(f) = \int_{-\infty}^{\infty} z(t) \ e^{-j2\pi ft} \,dt = \\  \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \Big [ x(\alpha) y(t -\alpha) \,d\alpha  \Big] e^{-j2\pi f(t-\alpha+\alpha)} \,dt =\\
    \int_{\alpha=-\infty}^{\infty} x(\alpha) \underbrace{\Big [\int_{t=-\infty}^{\infty}y(t-\alpha)e^{-j2\pi f(t-\alpha)}\,dt \Big ]}_{Y(f)}  e^{-j2\pi f\alpha} \,d\alpha = \\ \int_{\alpha=-\infty}^{\infty} x(\alpha) \ Y(f) \ e^{-j2\pi f\alpha}\,d\alpha = X(f) \ Y(f)
    \end{gather*}
    - Nota bene:
        - la convoluzione ha proprietà commutativa, associativa e distributiva.


## Trasformata di Fourier generalizzata

22. Teorema d'integrazione **completo**:

    Vogliamo rimuovere il vincolo (o ipotesi) $X(0)$ che è alla base dell'applicabilità del teorema d'integrazione "incompleto": ciò viene realizzato utilizzando la delta di Dirac.

    Il teorema completo afferma che:
    $$
    y(t) = \int_{-\infty}^{t} x(\alpha)\,d\alpha \Longleftrightarrow Y(f) = \frac{X(f)}{j2\pi f} + \frac{\delta(f)}{2}\cdot X(0)  
    $$
    Il nuovo termine rende conto dell’eventuale valor medio diverso da zero del segnale!.
    
    - Dimostrazione:

        Essendo:
        \begin{gather*}
        x(t)\otimes u(t) = \int_{-\infty}^{\infty} x(\alpha) \ u(t-\alpha)\,d\alpha = \int_{-\infty}^{t} x(\alpha)\,d\alpha
        \\
        u(t) = \frac{1}{2}\text{sgn}(t)+\frac{1}{2}
        \end{gather*}
        abbiamo che per la convoluzione $x(t)\otimes u(t)\Longleftrightarrow X(f)U(f)$:
        $$
        X(f)\ U(f)=X(f)\Big[\frac{1}{j2\pi f}+\frac{\delta(f)}{2}\Big] = \frac{X(f)}{j2\pi f}+ \frac{X(0)}{2}\delta(f)
        $$
        Questo perché $\text{TCF}(u(t))=U(f)=\frac{1}{j2\pi f}+\frac{1}{2}\delta (f)$; l’ultimo termine scompare per segnali ad area nulla: rende conto dell'eventuale valor medio diverso da zero del segnale, ed è un termine correttivo che rappresenta la funzione impulsiva.

23. Teorema della modulazione, alternativa:
    
    - Dimostrazione:

        per il teorema del prodotto, 
        \begin{gather*}
        x(t)\cos(2\pi f_{0}t) \Longleftrightarrow X(f) \otimes \Big[ \frac{\delta(f-f_0)+\delta(f+f_0)}{2} \Big] = \\ X(f) \otimes \frac{\delta(f-f_0)}{2} + X(f) \otimes  \frac{\delta(f+f_0)}{2} \\
        \to X(f)\otimes \delta(f-f_0) = \int_{\mathbb{R}}X(\alpha) \delta(f-f_0 -\alpha)\,d\alpha = \int_{\mathbb{R}}X(\alpha) \delta(\alpha) -(f-f_0)\,d\alpha = X(f-f_0) \\
        x(t)\cos(2\pi f_0 t) \Longleftrightarrow \frac{X(f-f_0)+X(f+f_0)}{2}
        \end{gather*}
        
## Periodicizzazione

24. Prima formula della somma di Poisson:

    Come rendere un segnale *aperiodico* $x(t)$ **periodico** di periodo $T_0$. Partiamo da $y(t)=\sum_{n=-\infty}^{\infty} = x(t-nT_0)$
    relazione nel tempo tra periodico e aperiodico
    \begin{gather*}
    \to Y_k = \frac{1}{T_0} = \int_{-\frac{T}{2}}^{\frac{T}{2}} y(t) \ e^{-j2 \pi kf_{0}t} \,dt = \frac{1}{T_0} = \int_{-\frac{T}{2}}^{\frac{T}{2}} \sum_{n=-\infty}^{\infty} x(t-nT_0) e^{-j2\pi kf_{0}t} \,dt \\
    \sum_{n=-\infty}^{\infty}\frac{1}{T_0} \int_{-\frac{T}{2}}^{\frac{T}{2}} x(t-nT_0)e^{-j2\pi kf_{0}t} \,dt = \ \ \ \text{ sostituiamo } \left\{ \begin{array}{cl} \alpha = t-t_0 \\ t = \alpha -t_0 \\ \,d\alpha = \,dt \end{array}\right.  \\
    \frac{1}{T_0} \sum_{n=-\infty}^{\infty}\frac{1}{T_0} \int_{-\frac{T}{2}-nT_0}^{\frac{T}{2}-nT_0} x(\alpha) \ e^{-j2\pi kf_{0}(\alpha +nT_0)} \,d\alpha = \\
    \frac{1}{T_0} \sum_{n=-\infty}^{\infty}\frac{1}{T_0} \int_{-\frac{T}{2}-nT_0}^{\frac{T}{2}-nT_0} x(\alpha) e^{-j2\pi kf_{0}\alpha} \cdot \underbrace{e^{-j2\pi k\cancel{f_0}n\cancel{T_0}}}_{\text{multiplo di }2\pi \to e^{0}} \,d\alpha= \\
    \frac{1}{T_0} \sum_{n=-\infty}^{\infty}\frac{1}{T_0} \int_{-\frac{T}{2}-nT_0}^{\frac{T}{2}-nT_0} x(\alpha) \ e^{-j2\pi kf_{0}\alpha} \,d\alpha =
    \frac{1}{T_0} \int_{-\infty}^{\infty}x(\alpha) \ e^{-j2\pi kf_{0}\alpha}\,d\alpha = \underbrace{\frac{1}{T_0}X(kf_0)}_{\text{campionamento in frequenza}}
    \end{gather*}
    Si ottiene una relazione detta **campionamento in frequenza**. I coefficienti della serie di Fourier del segnale periodico $y(t)$ sono, a meno del fattore $\frac{1}{T_0}$, i campioni della TCF del *segnale base* $x(t)$ presi in corrispondenza delle frequenze armoniche $kf_0$
    \begin{gather*}
    \to \sum_{n=-\infty}^{\infty}x(t-nT_0) = \sum_{k=-\infty}^{\infty} \frac{1}{T_0} X(\frac{k}{T_0})\ e^{+j2\pi kt f_0}
    \end{gather*}

25. Seconda formula della somma di Poisson

    Applichiamo alla prima formula di Poisson il teorema della dualità:
    \begin{gather*}
    X(t) \longleftrightarrow x(-f) \\
    x(t) \longleftrightarrow X(f)
    \end{gather*}
    \begin{gather*}
    \sum_{n=-\infty}^{\infty}x(t-nT_0) = \sum_{k=-\infty}^{\infty} \frac{1}{T_0} X(\frac{k}{T_0})\ e^{+\frac{j2\pi kt}{T_0}} \\
    \sum_{n=-\infty}^{\infty}X(t-nT_0) = \sum_{k=-\infty}^{\infty} \frac{1}{T_0}(x(-\frac{k}{T_0}))\ e^{+\frac{j2\pi kt}{T_0}} \\
    \Rightarrow \sum_{n=-\infty}^{\infty}X(t-nT_0) = \sum_{k=-\infty}^{\infty} \frac{1}{T_0} x(\frac{k}{T_0})\ e^{-\frac{j2\pi kt}{T_0}} \text{ cambio di segno all'indice k} \\
    \to T = \frac{1}{T_0} \Rightarrow \sum_{n=-\infty}^{\infty}X(t-\frac{n}{T}) = T\sum_{k=-\infty}^{\infty} \frac{1}{T_0} x(kT)\ e^{-j2\pi ktT}
    \end{gather*}
    Adesso, dal punto di vista puramente formale, cambiano nome da $t$ in $f$, otteniamo un'espressione, otteniamo un'espressione *duale* rispetto alla prima formula di Poisson
    $$
    \sum_{n=-\infty}^{\infty}x(nT)e^{-j2\pi fT} = \frac{1}{T}\sum_{k=-\infty}^{\infty}X(f-\frac{k}{T})
    $$


## Sistemi
26. Teorema di Parseval:

Dato un segnale $x(t)$ e la sua energia $E_{x}=\int_{-\infty}^{\infty} |x(t)|^2 \,dt < +\infty$ (energia finita), possiamo esprimere l'energia $E_x$ *anche in frequenza*:
\begin{gather*}
E_{x}=\int_{-\infty}^{\infty} |x(t)|^2 \,dt = \int_{-\infty}^{\infty} x(t) \ x^{\ast} \,dt = \int_{-\infty}^{\infty} x(t) \Big[ \int_{-\infty}^{\infty} X^{*}(f) e^{-j2\pi ft} \,df \Big] \,dt \\
\int_{f=-\infty}^{\infty} X^{\star}(f) \Big [\int_{t=-\infty}^{\infty} x(t) e^{-j2\pi ft} \,dt\Big ] \,df = \int_{-\infty}^{\infty} X^{*}(f) = \int_{-\infty}^{\infty} |X(f)|^{2} \,df
\end{gather*}
$E_x$ è l'energia totale, deriva da $p_x = |x(t)|^2$ potenza istantanea integrata o da $|X(f)|^2$ detta **densità spettrale** $E_x(f)$ integrata.

27. Teorema di Wiener-Khinchin

Siamo la densità spettrale di potenza:
$$
P_x = \lim_{T\to \infty} \frac{1}{T}\int_{-\infty}^{\infty} x(t) \,dt 
$$
e la funzione *densità spettrale di potenza*
$$
S_x(f) \triangleq \lim_{T\to \infty} \frac{E_{x_T}(f)}{T} =\lim_{T\to\infty} \frac{|x(t)|^2}{T} 
$$
con $E_{x_T}(f)$ densità di energia del segnale *troncato* nell'intervallo $[-\frac{T}{2}; \frac{T}{2}]$ 

Definiamo **funzione di autocorrelazione** $R_x(\tau)= \int_{-\infty}^{\infty}x(\tau)x(t-\tau)\,dt$ ossia il segnale moltiplicato per una sua replica *ritardata*. Indica "quanto il segnale somiglia alla sua replica ritardata": 
più $x(t)$ è compatta meno somiglierà e meno varrà $R_x(\tau)$

Il teorema afferma che la densità spettrale di energia di un segnale coincide con la trasformata di Fourier della funzione di autocorrelazione del segnale stesso:

\begin{gather*}
E_x(f)= \int_{-\infty}^{\infty}R_{x}(\tau) e^{-j2\pi ft}\,d\tau \underbrace{=}_{R_x(\tau) \text{ è pari})} 2\int_{0}^{\infty} \cos(2\pi f\tau)R_x(\tau) \,d\tau
\end{gather*}

- Dimostrazione:

Partiamo dalla definizione di autocorrelazione:

\begin{gather*}
R_{x} (\tau) = \int_{-\infty}^{\infty} x(\alpha) x(\alpha -t) \,d\alpha = \int_{-\infty}^{\infty} x(\alpha)x(-(t-\alpha)) \,d\alpha = x(\tau) \otimes x(-\tau) = \\
R_{x} (\tau) =  x(\tau) \otimes x(-\tau) \Longleftrightarrow X(f) \ X(-f) = X(f) \ X^{*}(-f) = |X(f)|^{2} = E_x(f)
\end{gather*}

\newpage

# Secondo Parziale

## Processi aleatori analogici

1. Un processo aleatorio $X(t)$ filtrato da un SLS è all'uscita un nuovo processo $Y(t)$ WSS.
    
    Per far sì che accada il processo $y(t)$ deve avere:
    1. Media costante;
    2. L'autocorrelazione funzione solo di $\tau$
    - Dimostrazione:
        1. \begin{align*}
            E[y(t)]&= E[x(t)\otimes h(t)]= E\Big[\int_{-\infty}^{\infty} h(\alpha)\cdot x(t-\alpha) \,d\alpha\Big] =
            =\int_{-\infty}^{\infty} h(\alpha) \ E[x(t-\alpha)] \,d\alpha \\ &= m_{X} \int_{-\infty}^{\infty} h(\alpha) \,d\alpha = m_{X} \ H(0) =  \text{ costante}
            \end{align*}
        2. \begin{align*}
            R_{yy}(t_{1},t_{2}) &= \left\{ \begin{array}{lcl}
            t_{1} =t \\
            t_{2} = t + \tau \to \tau &= t_{2}-t_{1}
            \end{array} \right. \to \text{ cambio di variabile} \\
            R_{yy}(t, t + \tau) &= E[y(t)\cdot y(t+\tau)] = E\Big[\int_{-\infty}^{\infty} h(\alpha) \ x(t-\alpha)\,d\,\alpha \ \int_{-\infty}^{\infty}h(\beta) \ x(t+\tau -\beta) d\,\beta\Big]\\
            &=E\Big[\int_{-\infty}^{\infty}\int_{-\infty}^{\infty} h(\alpha) \ h(\beta) \ x(t-\alpha) x(t+\tau -\beta) \,d\alpha \,d\beta \Big]= \\
            &=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty} h(\alpha) \ h(\beta) \ E \Big[x(t-\alpha) x(t+\tau -\beta) \Big] \,d\alpha \,d\beta \\
            &=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty} h(\alpha) \ h(\beta) \ R_{xx}(\tau -\beta +\alpha) \,d\alpha \,d\beta \\&\to R_{yy}(t, t+\tau) = R_{yy(\tau)}
            \end{align*}
        
        Quindi il processo $y(t)$ è WSS.

## Segnali a tempo discreto aperiodici

2. Trasformata di Fourier per sequenze (definizione, periodo 1, denormalizzazione);

    Data la sequenza *aperiodica* $x[n]$ **discreta**:
    \begin{align*}
    \overline{X}(f) &= \sum_{n=-\infty}^{\infty}x[n]\ e^{-j2\pi nfT} = \longrightarrow f=F\cdot F_{c} = \frac{F}{T} = \si{\hertz} \longrightarrow
    = \sum_{n=-\infty}^{\infty}x[n] \ e^{j2\pi nF}
    \end{align*}
    $\overline{X}(f)$ è **completamente nota** se conosco il suo andamento in un intervallo delle frequenze *normalizzate* di ampiezza unitaria:  $\underbrace{F\in [-\frac{1}{2}; \frac{1}{2}]}_{\text{Intervallo base}}$

    - Periodica di periodo $1$:
    \begin{align*}
    \overline{X}(F+1) &= \sum_{n=-\infty}^{\infty} x[n] \ e^{-j2\pi n(F+1)} =
    \sum_{n=-\infty}^{\infty} x[n] e^{-j2\pi nF}\underbrace{\cancel{e^{-j2\pi n}}}_{=1 \text{ (n intero)}} =
    =\sum_{n=-\infty}^{\infty} x[n] e^{-j2\pi nF} = \\ &= \overline{X}(F)
    \end{align*}

    - *Denormalizzazione*:
    
    Necessaria in quanto se la sequenza $x[n]$ deriva da un'operazione di campionamento, la frequenza normalizzata **non permette** di stabilire un legame con la frequenza (espressa in \si{\Hz})
    delle componenti nella trasformata del segnale analogico di partenza.

    Se $T$ è il periodo di campionamento, $\Rightarrow f \triangleq \frac{F}{T} = F \cdot f_{c}$ in \si{\hertz}. Sostituendo ottengo $F=fT$ in \si{\Hz}
    \begin{gather*}
    \text{TFS}\Big[X[n]\Big] = \overline{X}(f) \triangleq \sum_{n=-\infty}^{\infty} x[n] e^{-j2\pi nfT}
    \end{gather*}
    $f$ continua in $\Big[ -\frac{1}{2T}; \frac{1}{2T} \Big] \to \overline{X}(f)$ continua. Posso introdurre il *modulo* $\overline{A}(f)=|\overline{X}(f)|$ e lo *spettro di fase* $\overline{\theta}(f)= \phase{\overline{X}(f)}$.

    $X(f)$ è periodica di periodo pari a $f_c =\frac{1}{T} \Rightarrow \overline{X}(f+\frac{1}{T})= \sum x[n]e^{-j2\pi nFT} \cdot \underbrace{\cancel{e^{2\pi n \frac{1}{T}T}}}_{=1}=\overline{X}(f)$
3. Relazione tra definizione di antitrasformata e trasformata; Criterio di convergenza per TFS (solo definizione).
    
    $$
    x[n] = \text{ITFS}\Big [ \overline{X}(f) \Big] = T \int_{-\frac{1}{2T}}^{\frac{1}{2T}} \overline{X}(f) \ e^{j2\pi n ft} \,df
    $$
    - Dimostrazione:
    \begin{align*}
    \overline{X}(f) &\triangleq \sum_{m=-\infty}^{\infty} x[m] \ e^{-j2\pi m fT} \to \text{ moltiplico e divido per osc.ni complesse alla frequenza } f \text{ e integro}\\
    & =\int_{-\frac{1}{2T}}^{\frac{1}{2T}} \overline{X}(f) \ e^{j2\pi n fT} \,df = \int_{-\frac{1}{2T}}^{\frac{1}{2T}} \sum_{m=-\infty}^{\infty} x[m] \ e^{-j2\pi m fT} \ e^{j2\pi n fT} \,df = \\
    & =\sum_{m=-\infty}^{\infty} x[m] \int_{-\frac{1}{2T}}^{\frac{1}{2T}} e^{-j2\pi (m-n)fT}\,df \\
    &\text{Studiamo } \int_{-\frac{1}{2T}}^{\frac{1}{2T}} e^{-j2\pi (m-n)fT}\,df \longrightarrow
    \left\{ \begin{array}{cl}
    \frac{1}{T} & : \ m=n \to \int_{-\frac{1}{2T}}^{\frac{1}{2T}} 1\cdot \,df = \frac{1}{T} \\
    0 & : \ m \neq n \to m-n=k \to \int_{-\frac{1}{2T}}^{\frac{1}{2T}} e^{-j2\pi kfT} = 0
    \end{array} \right. \\    
    &\Rightarrow \text{ Riprendo la sommatoria } \int_{-\frac{1}{2T}}^{\frac{1}{2T}} \overline{X}(f) \ e^{-j2\pi nfT} \,df = \sum_{m=-\infty}^{\infty}
    x[m] \int_{-\frac{1}{2T}}^{\frac{1}{2T}} e^{-j2\pi(m-n)fT}\,df = \frac{1}{T}x[n] \\
    & \Rightarrow x[n] = T \int_{-\frac{1}{2T}}^{\frac{1}{2T}}\overline{X}(f)\ e^{j2\pi nfT}
    \end{align*}
    Nota bene: nell'ultima sommatoria ho tutti elementi pari a $0$, tranne il caso $m=n \to \frac{1}{T}$
    - Criterio di convergenza:
    \begin{gather*}
    \sum_{n=-\infty}^{\infty} \Big|x[n]\Big| < +\infty \Rightarrow \exists \text{ TFS}
    \end{gather*}
    Un criterio di convergenza per l'esistenza della trasformata è la **assoluta sommabilità** della frequenza.

### Teoremi
4. Teorema di Linearità;
    $$
    x[n]=ax_1[n]+bx_2[n] \Rightarrow \overline{X}(f) = a\overline{X_1}(f)+b\overline{X_2}(f)
    $$    
5. Teorema del Ritardo;

    Sia $x[n]$ una sequenza.
    $$
    x[n-k] \Longleftrightarrow \overline{X}(f) \cdot e^{-j2\pi kfT}
    $$
    - Dimostrazione:
    \begin{align*}
    \tfs[x[n-k]]& = \sum_{m=-\infty}^{\infty}x[n-k] \ e^{-j2\pi nfT} = \sum_{m=-\infty}^{\infty} x[m] \ e^{-j2\pi(m+k)fT} = e^{-j2\pi kfT}\sum_{m=-\infty}^{\infty}x[m] \ e^{-j2\pi mfT} =\\&=\overline{X}(f)e^{-j2\pi kfT}
    \end{align*}
6. Teorema della Modulazione;
    $$
    x[n]\cdot e^{-j2\pi nf_{0}t} \Longleftrightarrow \overline{X}(f-f_{0})
    $$
    - Dimostrazione:
    \begin{gather*}
    \tfs\Big[x[n]e^{j2\pi nf_{0}t}\Big] = \sum_{n=-\infty}^{\infty} x[n] \ e^{-j2\pi nfT} \cdot e^{j2\pi nf_{0}T}= \sum_{n=-\infty}^{\infty} x[n] \ e^{-j2\pi n(f-f_0)T} = \overline{X}(f-f_0)
    \end{gather*}
7. Teorema della Somma di Convoluzione;
    
    Sia $s[n]$ la sequenza discreta *somma di convoluzione* tra le sequenze aperiodiche $x[n]$ e $y[n]$.
    $$
    s[n]= x[n]\otimes y[n] = \sum_{k=-\infty}^{\infty} x[k]\ y[n-k] = \sum_{k=-\infty}^{\infty} y[k] \ x[n-k]
    $$
    Gode delle stesse proprietà del caso continuo.
    $$
    \Rightarrow \overline{S}(f) = \overline{X}(f) \cdot \overline{Y}(f)
    $$
    - Dimostrazione:
    \begin{align*}
    \overline{S}(f) &= \sum_{n=-\infty}^{\infty} \sum_{k=-\infty}^{\infty} x[k]\ y[n-k] e^{-j2\pi nfT} = \sum_{k=-\infty}^{\infty} x[k] \underbrace{\sum_{n=-\infty}^{\infty}y[n-k]\ e^{-j2\pi nfT}}_{\text{ritardo}}= \\
    &= \sum_{n=-\infty}^{\infty} x[k] \overline{Y}(f) \ e^{-j2\pi kfT} = \overline{Y}(f)  \sum_{n=-\infty}^{\infty} \ x[k]  e^{-j2\pi kfT} =\overline{Y}(f) \ \overline{X}(f)
    \end{align*}
8. Teorema del Prodotto;
    $$
    p[n]=x[n]\cdot y[n] \Longleftrightarrow \overline{P}(f) = \overline{X}(f) \otimes \overline{Y}(f)
    $$
    - Dimostrazione:
    \begin{align*}
     \overline{P}(f)&=\sum_{n=-\infty}^{\infty} p[n] \ e^{-j2\pi nfT} =  \sum_{n=-\infty}^{\infty} x[n] \ y[n] \ e^{-j2\pi nfT} = \sum_{n=-\infty}^{\infty}
     \underbrace{\Big[T\int_{-\frac{1}{2T}}^{\frac{1}{2T}} \overline{X}(\nu)\ e^{j2\pi n\nu T} \,d\nu\Big]}_{\text{antitrasformata di }\overline{X}(f)} y[n] \ e^{-j2\pi nfT} = \\
     &= T \int_{-\frac{1}{2T}}^{\frac{1}{2T}} \overline{X}(\nu)  \underbrace{\sum_{n=-\infty}^{\infty} y[n] \ e^{-j2\pi n(f-\nu)T}}_{\text{dalla modulazione }\to \overline{Y}(f-\nu)} \,d\nu=
     T \int_{-\frac{1}{2T}}^{\frac{1}{2T}} \overline{X}(\nu) \overline{Y}(f-\nu)\,d\nu  \\
    &\Rightarrow \overline{P}(f) = T \int_{-\frac{1}{2T}}^{\frac{1}{2T}} \overline{X}(\nu) \overline{Y}(f-\nu)\,d\nu
    \end{align*}
    Questa è la **convoluzione ciclica o periodica**. Calcolato su un singolo periodo e il risultato è diviso per l'ampiezza del periodo $\frac{1}{T}$
9. Teorema dell'Incremento;
    $$
    \odv{X(t)}{t}\Big|_{t=nT} \cong \frac{x(nT)-x(nT-T)}{T} = \frac{x[n]-x[n-1]}{T}, \text{ con } x[n] \triangleq x(nT)  
    $$
    Si introduce l'operatore **incremento** $\Delta x[n] \triangleq x[n] - x[n-1]$ \newline
    Usando il *teorema del ritardo*:
    $$
    \Delta x[n] \Longleftrightarrow \overline{X}(f) - \overline{X}(f)\ e^{-j2\pi fT} = \overline{X}(f) \ (1-e^{-j2\pi fT})
    $$
    È l'analogo del teorema di derivazione.
10. Teorema della Sequenza Somma.

    Consideriamo la sequenza somma $\displaystyle y[n]=\sum_{k=-\infty}^{n}x[k]$. Dal teorema dell'incremento otteniamo la sua trasformata in sequenza:
    $$
    \overline{Y}(f) = \frac{\overline{X}(f)}{1-e^{-j2\pi fT}}
    $$
    purché $\overline{X}(0) = 0$.
    - Dimostrazione:
    \begin{gather*}
    z[n] = \Delta y[n] \Longleftrightarrow \overline{Z}(f)=\overline{Y}(f)[1-e^{-j2\pi fT}] \text{ dal teorema dell'incremento} \\
    \text{però } \Delta y[n] = y[n] - y[n-1] = \sum_{k=-\infty}^{n} x[k] - \sum_{k=-\infty}^{n-1}x[k] = x[n] \\
    \text{quindi } \overline{X}(f) = \overline{Y}(f)[1-e^{-j2\pi fT}] \to \overline{Y}(f) = \frac{\overline{X}(f)}{1-e^{-j2\pi fT}}
    \end{gather*}

### Campionamento:
11. Teorema del campionamento ("risultato" dell'interpolazione cardinale);

    Un segnale il cui spettro è *limitato* nella banda $B$ può essere ricostruito a partire dai propri campioni, **purché** $f_c \leq 2B$
    
    $p(t)$ è un impulso "diverso" per generalizzare l'operazione d'interpolazione, anche al fine di evitare le discontinuità che lo stesso impulso $p(t)$ introduce nell'interpolazione a mantenimento.
    \begin{align*}
    \hat{x}(t)&= \sum_{n=-\infty}^{\infty} x[n] \ p(t-nT), \ \text{scegliendo } p(t)= \sinc\Big(\frac{f}{T}\Big) \Rightarrow P(f)=T\rect (fT) \\ 
    \hat{X}(f)&= P(f) \ \overline{X}(f) = \cancel{T}\rect \Big(\frac{f}{\frac{1}{T}}\Big)\frac{1}{\cancel{T}}\cdot  \sum_{k=-\infty}^{+\infty} X\Big(f-\frac{k}{T}\Big)= X(f) \\
   &\boxed{\begin{array}{cl}
  \text{ricampionando il segnale}
  \\
   \text{interpolato al generico istante } t=kT
  \end{array}}&
  \\
    \hat{x}(kT) &=\sum_{n=-\infty}^{+\infty} x(nT) \ \sinc\Big(\frac{kT-nT}{T}\Big), \text{ ma } \sinc(k-n)=
    \left\{ \begin{array}{cl}
    0 & n\neq k \\
    1 & k=n
    \end{array} 
    \right. \\
    &\text{Quindi: } \hat{x}(kT)=\sum_{n=-\infty}^{+\infty}x[n] \ \underbrace{\delta[k-n]}_{1\text{ sse }n=k}= x[k] = x(kT)
    \end{align*}
    Il segnale di partenza coincide con il segnale interpolato.
12. Relazione tra TCF e TFS.
    \begin{align*}
    \underset{\text{discreto}}{x[n]}=\underset{\text{continuo}}{x(nT)} \Longleftrightarrow \underset{\text{discreto}}{\overline{X}(f)} = \underset{\text{continuo}}{X(f)}
    \end{align*}
    \begin{align*}
    \overline{X}(f) &\triangleq \sum_{n=-\infty}^{\infty} x[n] \ e^{-j2\pi nfT} = \sum_{n=-\infty}^{\infty} x(nT) \ e^{-j2\pi nfT}=
    \boxed{\text{Sapendo che: } x(nT)=\int_{-\infty}^{\infty}X(\alpha) e^{j2\pi\alpha nT}\,d\alpha} \\
    &= \sum_{n=-\infty}^{\infty} \int_{-\infty}^{\infty} X(\alpha) \ e^{-j2\pi \alpha nT} \,d\alpha \cdot e^{-j2\pi nfT}
    = \int_{-\infty}^{\infty} X(\alpha) \sum_{n=-\infty}^{\infty} e^{-j2\pi n(f-\alpha)T} \,d\alpha
    \end{align*}
    ma il segnale *pettine di Dirac* è esprimibile in serie di Fourier con coefficienti pari a $\frac{1}{T}$:
    $$
    \displaystyle
    \boxed{\displaystyle
    \begin{array}{c} \displaystyle
    \sum_{n=-\infty}^{\infty} \delta(t-nT) = \frac{1}{T} \sum_{k=-\infty}^{\infty} e^{\frac{j2\pi kt}{T}} \\
    \text{Trasformata di Fourier} \updownarrow \\ \displaystyle
    \sum_{n=-\infty}^{\infty} e^{-j2\pi nfT} = \frac{1}{T}\sum_{n=-\infty}^{\infty} \delta(f-\frac{k}{T})
    \end{array}
    }
    $$
    \begin{align*}
    &\int_{-\infty}^{\infty}X(\alpha) \frac{1}{T} \sum_{k=-\infty}^{\infty} \delta(f-\alpha -\frac{k}{T})\,d\alpha = \frac{1}{T}\sum_{k=-\infty}^{\infty} \int_{-\infty}^{\infty}X(\alpha) \delta(f-\alpha -\frac{k}{T})\,d\alpha = \\
    &=\delta \text{ è pari } = \frac{1}{T}\sum_{k=-\infty}^{\infty} \int_{-\infty}^{\infty}X(\alpha) \delta\Big(\alpha -(f- \frac{k}{T})\Big)\,d\alpha = \text{ prodotto tra } X(\alpha) \text{ e Dirac centrato in } f -\frac{k}{T} \\
    &=\text{per la proprietà campionatrice della delta di Dirac } \longrightarrow \overline{X}(f) = \frac{1}{T}\sum_{n=-\infty}^{\infty}X(f-\frac{k}{T})
    \end{align*}

## Segnali a tempo discreto periodici
13. Trasformata discreta di Fourier (definizione);

    Supponiamo $x[n]$ periodica di periodo $N_0$ 
    $$
    \underset{\text{antitrasformata discreta di Fourier}}{x[n]=\frac{1}{N_0}\sum_{k=0}^{N_0 -1}\overline{X}_{k} \ e^{j\frac{2\pi kn}{N_0}}}; \
    \underset{\text{Trasformata discreta di Fourier}} {\overline{X}_k = \sum_{n=0}^{N_0 -1} x[n] \ e^{-j \frac{2\pi kn}{N_0}}}
    $$
14. La trasformata di una sequenza periodica è essa stessa periodica (stesso periodo $N_0$);
    \begin{gather*}
    \overline{X}_{k+N_0} = \sum_{n=0}^{N_0 -1} x[n] e^{-j2\pi(k+N_0)\frac{n}{N_0}} = \sum_{n=0}^{N_0 -1} x[n] e^{-j2\pi k\frac{n}{N_0}} \ e^{-j2\pi n} = \overline{X}_k
    \end{gather*}
    
15. La relazione di sintesi di una TDF discende da quella di analisi;
    \begin{align*}
    x[n] &= \sum_{k=0}^{N_0 -1} \overline{X}_k \ e^{j2\pi k \frac{n}{N_0}} \Rightarrow \overline{X}_k = \sum_{n=0}^{N_0 -1} x[n] e^{-j\frac{2\pi nk}{N_0}} \\
    &\text{Moltiplichiamo per } e^{-j \frac{2\pi nm}{N_0}} \text{ con } 0\leq m \leq N_0 - 1 \text{ ed effettuiamo una somma sul periodo} \\
    &=\sum_{n=0}^{N_0 -1} x[n] e^{-j2\pi m\frac{n}{N_0}} = \sum_{n=0}^{N_0 -1} \sum_{k=0}^{N_0 -1}\overline{X}_k e^{-j2\pi n\frac{(k-m)}{N_0}} = \sum_{k=0}^{N_0 -1}\overline{X}_k \sum_{n=0}^{N_0 -1} e^{-j2\pi n\frac{(k-m)}{N_0}} = N_0 \overline{X}_k \\
    &\Rightarrow \overline{X}_k = \frac{1}{N_0}\sum_{n=0}^{N_0 -1} x[n] \ e^{-j2\pi\frac{k}{N_0}}
    \end{align*}

### Proprietà:

Notazione: $\dft_{N_0}\Big\{x[n]\Big\} = \overline{X}_k, \text{ con } 0\leq n, k \leq N_0 -1$

16. Proprietà di Linearità;
    $$
    \dft_{N_0}\Big\{ax[n]+by[n]\Big\} = a\overline{X}_k + b\overline{Y}_k
    $$
17. Proprietà di Traslazione Circolare;
    $$
    \dft_{N_0}\Big\{ x[n-n_0] \Big\} = \overline{X}_k \ e^{-\frac{j2\pi kn_0}{N_0}}
    $$
    - Dimostrazione:
    \begin{align*}
    \dft_{N_0}\Big\{ x[n-n_0] \Big\} &= \sum_{n=0}^{N_0 -1} x[n-n_0] \ e^{-j2\pi\frac{n}{N_0}k} =
    \boxed{
    \begin{array}{cl}
    \text{cambio di variabile} \\
    p  = n - n_0 \\
    n  = p + n_0
    \end{array}} \\
    &= \sum_{p=-n_0}^{N_0 - 1 - n_0} x[p] \ e^{-j\frac{2\pi}{N_0}(p+n_0)} = \sum_{p=-n_0}^{N_0 - 1 - n_0} x[p] \ e^{-j\frac{2\pi}{N_0}kp} \ e^{-j\frac{2\pi}{N_0}n_0}=\\
    &= e^{-j\frac{2\pi}{N_0}kn_0} \sum_{p=-n_0}^{N_0 - 1 - n_0} x[p] \ e^{-j\frac{2\pi}{N_0}kp} = e^{-j\frac{2\pi}{N_0}kn_0} \sum_{p=0}^{N_0 - 1} x[p] \ e^{-j\frac{2\pi}{N_0}kp} \\
    &\dft_{N_0}\Big\{ x[n-n_0] \Big\} = e^{-j\frac{2\pi kn_0}{N_0}} \cdot \overline{X}_k &
    \end{align*}
    Si dice traslazione **circolare** in quanto, osservando la periodicità della sequenza originale e di quella traslata,
    è possibile notare come i campioni che "escono" a destra dell'intervallo rientrano alla sinistra dell'intervallo stesso.
18. Proprietà di Traslazione In Frequenza;
    $$
    \dft_{N_0}\Big\{ x[n] \ e^{-j\frac{2\pi k_0 n}{N_0}} \Big\} = \overline{X}_{k-k_0}
    $$
19. Proprietà di Inversione Temporale;
    \begin{gather*}
    \dft_{N_0}\Big\{ x[-n] \Big\} = \overline{X}_{-k} = \overline{X}_{N_0 - k} 
    \end{gather*}
    - Dimostrazione:
    \begin{align*}
    \dft_{N_0}\Big\{ x[-n] \Big\} &= \sum_{n=0}^{N_0 -1} x[-n] \ e^{-j\frac{2\pi}{N_0}kn} = \sum_{n=0}^{N_0 -1} x[N_0 -n] \ e^{-j\frac{2\pi}{N_0}kn} =
    \boxed{
    \begin{array}{cl}
    \text{cambio di variabile} \\
    p  = N_0 - n \\
    n  = N_0 - p
    \end{array}}\\
    &= \sum_{p=1}^{N_0} x[p] \ e^{-j\frac{2\pi}{N_0}k(N_0 -p)} = \underbrace{e^{-j2\pi k}}_{=1} \ \sum_{p=0}^{N_0 -1} x[p] \ e^{-j\frac{2\pi}{N_0}(-k)(-k)p} = \overline{X}_{-k} = \overline{X}_{N_0 - k}
    \end{align*}
    dove nel primo passaggio, abbiamo usato la periodicità della sequenza x[n] e
    nel penultimo passaggio, per cambiare gli indici della sommatoria, abbiamo
    usato le proprietà di periodicità della sequenza e della funzione esponenziale,
    come già visto.
20. Proprietà di coniugazione;
    $$
    \dft_{N_0}\Big\{ x^{*}[n] \Big\} = \overline{X}^{*}_{-k} = \overline{X}^{*}_{N_0 - k}
    $$
21. Simmetria per sequenze reali (pari e dispari);
    
    Per una sequenza reale $x[n]$ abbiamo:
    $$
    \dft_{N_0}\Big\{ x[n] \Big\} = \dft_{N_0}\Big\{x^{*}[n] \Big\} \to \overline{X}_k = \overline{X}^{*}_{-k} = \overline{X}^{*}_{N_0 -k}
    $$
    da cui derivano le proprietà di simmetria per il modulo e per la fase:
    \begin{gather*}
    \Big|\overline{X}_k \Big| = \Big| \overline{X}_{N_0 - k} \Big| \\
    \phase{\overline{X}_k} = -\phase{\overline{X}_{-k}}
    \end{gather*}
    Tali relazioni implicano che il modulo della sequenza $X[k]$ è simmetrico rispetto al valore $k = \frac{N}{2}$, mentre la fase è antisimmetrica rispetto a tale valore.
    - per sequenze di lunghezza **pari**, il centro di simmetria coincide con un campione della sequenza;
    - per sequenze di lunghezza **dispari**, invece, il centro di simmetria coincide con un punto equidistante tra due campioni.
22. Teorema di Parseval per sequenze;
    \begin{gather*}
    \left\{ \begin{array}{cl} \displaystyle
    \sum_{n=0}^{N_0 -1} x[n] \ y^{*}[n] = \frac{1}{N_0} \sum_{k=0}^{N_0 -1}\overline{X}_k \ \overline{Y}^{*}_{k} \\
    \displaystyle\sum_{n=0}^{N_0 -1} \Big|x[n]\Big|^{2} = \frac{1}{N_0} \sum_{k=0}^{N_0 -1} \Big|\overline{X}_{k}\Big|^{2}
    \end{array} \right.
    \end{gather*}
    - Dimostrazione:
    \begin{gather*}
    \sum_{n=0}^{N_0 -1} x[n] \ y^{*}[n] =\sum_{n=0}^{N_0 -1}\overline{X}_k \ \Big(\frac{1}{N_0}\sum_{k=0}^{N_0 - 1}\overline{Y}_k \ e^{j\frac{2\pi kn}{N_0}}\Big)^{*} 
    = \frac{1}{N_0} \sum_{k=0}^{N_0 -1} \overline{Y}_k \sum_{n=0}^{N_0 -1 }x[n] \ e^{-j\frac{2\pi kn}{N_0}} = \frac{1}{N_0} \sum_{k=0}^{N_0 -1} \overline{X}_k \ \overline{Y}^{*}_k
    \end{gather*}
        - Ponendo $x[n]=y[n]$ si ottiene la seconda relazione.
23. Teorema del Prodotto;

    Consideriamo adesso la sequenza (periodica) $p[n]$ data dal *prodotto* fra la sequenza $x[n]$ e la sequenza $y[n]$ entrambe periodiche di periodo $N_0$
    $$
    p[n] =x[n] \ y[n]
    $$
    e calcoliamone la trasformata discreta di Fourier:
    \begin{align*}
    \overline{P}_k &= \sum_{n=0}^{N_0 - 1} p[n] \ e^{-j2\pi\frac{nk}{N_0}} = \sum_{n=0}^{N_0 - 1}x[n] \ y[n] e^{-j2\pi\frac{nk}{N_0}}
    = \sum_{n=0}^{N_0 -1}\frac{1}{N_0}\sum_{m=0}^{N_0 -1}\overline{X}_m \ e^{j2\pi\frac{nm}{N_0}}\cdot y[n] \ e^{-j2\pi\frac{nk}{N_0}}
    \end{align*}
    Dove $x[n]$ è stata scomposta in serie discreta di Fourier. Inoltre è stata utilizzata una variabile "muta" $m$ nell'antitrasformata per non creare ambiguità con la 
    variabile $k$, da cui dipende la trasformata.
    \begin{align*}
    &= \frac{1}{N_0} \sum_{n=0}^{N_0 -1}\sum_{m=0}^{N_0 -1} \overline{X}_m \ e^{j2\pi \frac{nm}{N_0}} \cdot y[n] e^{-j2\pi\frac{nk}{N_0}}
    \end{align*}
    Invertendo l'ordine delle sommatorie otteniamo:
    \begin{align*}
    \overline{P}_k &= \sum_{m=0}^{N_0 -1} \overline{X}_m \frac{1}{N_0}\sum_{n=0}^{N_0 -1} y[n] \ e^{-j2\pi{\frac{n(k-m)}{N_0}}} = \frac{1}{N_0}\sum_{m=0}^{N_0 -1}\overline{X}_m \ \overline{Y}_{k-m}= \\ 
    &= \frac{1}{N_0}\cdot \overline{X}_k \otimes \overline{Y}_k
    \end{align*}
    La convoluzione tra le due trasformate discrete è una somma di convoluzione **ciclica** tra le due sequenze periodiche $\overline{X}_k$ e $\overline{Y}_k$ in ambito *frequenziale*. In conclusione:
    \begin{align*}
    p[n] = x[n] \ y[n] \Longleftrightarrow \overline{P}_k = \frac{1}{N_0}\cdot \overline{X}_k \otimes \overline{Y}_k
    \end{align*}
24. Teorema della Convoluzione (+ relazioni tra convoluzione lineare e circolare).
    
    Consideriamo ora la sequenza $z[n]$ come somma di convoluzione ciclica o circolare tra le due sequenze $x[n]$ e $y[n]$, periodiche di periodo $N_0$
    $$
    z[n] = x[n] \otimes y[n] = \sum_{m=0}^{N_0 -1}x[m] \ y[n-m] = \sum_{m=0}^{N_0 -1}y[m] \ x[n-m]
    $$
    La somma di convoluzione gode di tutte le proprietà citate per la somma di convoluzione tra sequenze periodiche. \newline
    Calcoliamo la trasformata discreta di $z[n]$:
    \begin{align*}
    \overline{Z}_k &= \sum_{n=0}^{N_0 -1} z[n] \ e^{-j2\pi{\frac{nk}{N_0}}} = \sum_{n=0}^{N_0 -1} \sum_{m=0}^{N_0 -1} x[m] \ y[n-m] e^{-j2\pi{\frac{nk}{N_0}}} = 
    \sum_{m=0}^{N_0 -1} x[m] \sum_{n=0}^{N_0 -1} y[n-m] e^{-j2\pi\frac{nk}{N_0}} = \\
    &= \sum_{m=0}^{N_0 -1} x[m] \ \overline{Y}_k \ e^{-j2\pi\frac{mk}{N_0}} = \overline{Y}_k \sum_{m=0}^{N_0 -1} x[m] \ e^{-j2\pi\frac{mk}{N_0}}= \\
    &= \overline{X}_k \cdot \overline{Y}_k
    \end{align*}
    Quindi:
    $$
    x[n]\otimes y[n] \Longleftrightarrow \overline{X}_k \cdot \overline{Y}_k
    $$
    - Relazioni tra convoluzione lineare e circolare (per due sequenze di lunghezza finita):

        Siano $x[n]$ e $h[n]$ due sequenze di lunghezza $L$ e $M$: il "supporto" sul quale le sequenze hanno campioni *non nulli* è $[0, L-1]$ e $[0, M-1]$.
        - La convoluzione *lineare* è ottenuta dalla relazione:
        $$
        y_{l}[n] = x[n] * h[n] = \sum_{k=-\infty}^{\infty} x[k] \ h[n-k]
        $$
        dove le sequenze sono considerate **aperiodiche** e $y_l[n]$ ha una lunghezza *finita* e pari a $L+M-1$ campioni, considerando il "supporto" dove le sequenze
        hanno campioni non nulli. Vi è quindi una *sovrapposizione* tra campioni non nulli delle due sequenze in $[0, L+M-2]$
        - La convoluzione *circolare* invece, a causa della diversa lunghezza delle due sequenze, richiede di fissare un **periodo comune** $N$, per eseguire l'**estensione 
        periodica** delle sequenze: l'unico vincolo da porre diventa quindi $N \geq \text{max}(L,M)$, appendendo quindi in fondo alle sequenze un numero di zeri (pari a $N-L$
        o $N-M$) prima di estendere periodicamente le due sequenze. La convoluzione circolare è data da:
        $$
        y_{c}[n] = x[n] \otimes h[n] =\sum_{k=0}^{N-1}x[k] \ h[n-k]
        $$

### Generale:
25. Fast Fourier Transform (FFT).

    Supponiamo di avere in memoria un numero $N_0$ di valori della sequenza periodica $x[n]$ e calcoliamone numericamente la trasformata discreta:
    $$
    \overline{X}_k = \sum_{n=0}^{N_0 -1} \  e^{-j\frac{1\pi kn}{N_0}} =\Big\{ x[0]\cdot e^{-j0}+x[1]\cdot e^{j\frac{2\pi k}{N_0}}+x[2]\cdot e^{-j\frac{2\pi 2k}{N_0}} + \cdots + x[N_0 -1]\cdot e^{-j\frac{2\pi(N_0 -1)k}{N_0}}\Big\}
    $$
    Vogliamo quindi determinare il numero di *operazioni necessarie* sia per la trasformata che per l'antitrasformata (ignorando il fattore di scala $\frac{1}{N_0}$):
    $$
    x[n] = \overline{X}_0 \cdot e^{j0}+\overline{X}_1\cdot e^{j\frac{2\pi k}{N_0}}+\overline{X}_2\cdot e^{j\frac{2\pi 2k}{N_0}} + \cdots + \overline{X}_{N_0 -1}\cdot e^{j\frac{2\pi(N_0 -1)k}{N_0}}
    $$
    Supponiamo quindi di avere valori *complessi* $z=a+jb$, ma **precalcolati**, ovvero già in memoria. Per il calcolo di un *singolo campione* $X[k]$ è necessario eseguire $N_0$ moltiplicazioni complesse
    e $N_0 -1$ addizioni complesse, le quali sono tradotte dai calcolatori in operazioni nel campo reale, eseguendole tra le parti reali e immaginari dei numeri complessi coinvolti:
    - per eseguire un’addizione complessa è necessario eseguire 2 addizioni reali: $(a + jb) + (c + jd) = (a + c) + j(b + d)$
    - per eseguire una moltiplicazione complessa è necessario eseguire 4 moltiplicazioni reali e 2 addizioni reali, $(a + jb) · (c + jd) = (ac - bd) + j(ad + bc)$.

    Quindi per un singolo campione $X[k]$ sono necessarie $N_0$ moltiplicazioni complesse e $N_0 -1$ somme complesse. Inoltre, per ogni valore di $k$ sono necessarie
    $8N_0 -2$ operazioni reali, e dato che la sequenza è composta da $N_0$ valori la complessità diventa **quadratica**:
    $$
    (8N_0 -2)N_0 = 8N_{0}^{2} -2N_0 \approx 8N_{0}^2
    $$
    Per velocizzare i calcoli è stato quindi introdotto l'algoritmo **Fast Fourier Transform** o FFT, il quale viene applicato se *$N_0$ è una potenza del $2 \to N_0 = 2^{M}$*
    \begin{align*}
    \overline{X}_k &= \sum_{m=0}^{\frac{N_0}{2}-1} x[2m]\ e^{-j\frac{2\pi(2m)k}{N_0}} + \sum_{m=0}^{\frac{N_0}{2}-1} x[2m+1] \ e^{-j\frac{2\pi(2m-1)k}{N_0}}= \\
    & = \overbrace{\sum_{m=0}^{\frac{N_0}{2}-1} x[2m]\ e^{-j\frac{2\pi mk}{\frac{N_0}{2}}}}^{\overline{P}_k}+e^{-j\frac{2\pi k}{\frac{N_0}{2}}} + \overbrace{\sum_{m=0}^{\frac{N_0}{2}-1} x[2m+1] \ e^{-j\frac{2\pi mk}{\frac{N_0}{2}}}}^{\overline{D}_k}
    \end{align*}
    con $k= 0, \dots , N_0 -1$. $\overline{P}_k$ è la trasformata ottenuta dai $\frac{N_0}{2}$ campioni di *indice pari* di $x[n]$, mentre $\overline{D}_k$ indica la trasformata
    della sequenza ottenuta dai $\frac{N_0}{2}$ campioni di *indice dispari* Questa scomposizione è ricorsiva dell'ordine, in quanto la trasformata di ordine $N_0$ è espressa come combinazione lineare
    di due trasformate di ordine $\frac{N_0}{2}$: questo concetto può essere esteso al numero di operazioni $N_{FFT}$:
    $$
    N_{FFT}(N_0)=N_{FFT}(\frac{N_0}{2})+N_{FFT}(\frac{N_0}{2})+6N_0 + 2N_0
    $$
    tenendo conto che per ogni $k$ (dei coefficienti dispari) è necessario moltiplicare $D_k$ per un esponenziale complesso (precalcolato, 6 operazioni reali) e poi sommare con $P_k$ (2 operazioni reali).

    Il procedimento viene poi ripetuto ricorsivamente. Infine, iterando la formula:
    $$
    N_{FFT}(N_0) = 6N_0 + 8N_0\log_2 N_0 \approx 8N_0 \log_2 N_0
    $$
    la complessità risulta **logaritmica**! Ad esempio, con $N_0=1024$
    $$
    \frac{N_{TDF}(N_0)}{N_{FFT}(N_0)} = \frac{8N_{0}^{\cancel{2}}}{\cancel{8N_0}\log_2 N_0} = \frac{N_0}{\log_2 N_0} \approx 100
    $$
    Il vantaggio conseguito dall'utilizzo di FFT al posto della trasformata classica aumenta al crescere di $N_0$
 
## Sistemi monodimensionali a tempo discreto 

$$
y[n] = \text{T}\Big[x[m], n\Big] = \text{T}\Big[x[n] \Big]
$$

### Proprietà dei sistemi;
26. SLS a tempo discreto: risposta impulsiva.
    $$
    h[n] = \tf{\delta[n]}
    $$
    Nota $h[n]$:
    \begin{align*}
    y[n] &= \tf{x[n]} = \tf{\sum_{k=-\infty}^{\infty}x[k] \ \delta[n-k]} = \text{per la linearità} \\
    &= \sum_{k=-\infty}^{\infty}x[k] \tf{\delta[n-k]} = \text{per la stazionarietà: } \to
    \left \{\begin{array}{cl}
    \tf{\delta[n-k]}=h[n-k]
    \end{array}\right. \\
    &= \sum_{k=-\infty}^{\infty}x[k] \ h[n-k] = x[n] \otimes h[n]
    \end{align*}
    Quindi l'uscita è una *somma di convoluzione* tra la sequenza in ingresso e la risposta impulsiva del sistema stesso!
    
    Un sistema lineare e stazionario (SLS) può essere:
    - FIR (Finite Impulse Response) se la sua risposta impulsiva è costituita da un **numero finito di campioni**;
    - IIR (Infinite Impulse Response) se la sua risposta impulsiva è costituita da un numero **infinito** di campioni.

    È possibile dimostrare come la *condizione necessaria e sufficiente* per la stabilità in senso BIBO di un SLS è l'**'assoluta sommabilità**
    della sua risposta impulsiva:
    $$
    \sum_{k=-\infty}^{\infty} \Abs{h[k]} < \infty
    $$
    Da ciò deriviamo che
    - i sistemi FIR sono stabili: la sommatoria diventa una somma *finita* di quantità *limitate*;
    - mentre i sistemi IIR non lo sono sempre. Diventa necessario controllare la validità della seguente condizione:
        - **sequenza causale**:

            un SLS è causale se e solo se la sua risposta impulsiva è una sequenza causale, cioè:
            $$
            h[n] = 0 \text{ se } n<0, \text{ ovvero } h[n] = h[n] \ u[n] 
            $$

### Proprietà:
27. Sistemi a cascata e in parallelo;
    
    - In un sistema a **cascata** l'ordine degli stessi può essere variato senza alterare l'uscita:
        \begin{align*}
        h[n] = h_{1}[n] \otimes h_{2}[n] \to y[n] = x[n] \otimes \Big(h_{1}[n] \otimes h_{2}[n] \Big)
        \end{align*}
        Questo per la proprietà commutativa del prodotto di concoluzione discreta.
    - Due sistemi **in parallelo**:
        \begin{align*}
        h[n] = h_{1}[n] + h_{2}[n] \to y[n] = x[n] \otimes \Big[ h_{1}[n] + h_{2}[n] \Big]
        \end{align*}

28. Risposta in frequenza;

    1. La risposta in frequenza di un SLS a tempo discreto è la **trasformata di Fourier** della risposta impulsiva $h[n]$ del sistema stesso
        $$
        \overline{H}(f) = \sum_{n=-\infty}^{\infty} h[n] \ e^{-j2\pi nfT}
        $$
    2. Inoltre $\overline{H}(f)$ è pari al rapporto tra le trasformate $\overline{Y}(f)$ e $\ov{X}(f)$ rispettivamente
        della sequenza in uscita $y[n]$ e in ingresso $x[n]$:
        $$
        \ov{H}(f)=\frac{\ov{Y}(f)}{\ov{X}(f)}
        $$
    3. La risposta in frequenza è data dal rapporto fra la sequenza di uscita y[n] e quella di ingresso x[n] quando x[n] è una oscillazione complessa alla frequenza f:
        $$
        \ov{H}(f) = \frac{y[n]}{x[n]}\Bigg|_{x[n]=e^{j2\pi nfT}}
        $$
    È possibile inoltre definire, data la risposta in frequenza $\ov{H}(f)$, la *risposta in ampiezza* $\ov{A}(f)=|\ov{H}(f)|$, la quale determina
    la **selettività** di un SLS e la sua *risposta in fase* $\ov{\theta}(f)=\phase{\ov{H}(f)}$

29. Filtri a tempo discreto.

    La **condizione di non distorsione** viene riformulata come segue:
    $$
    y[n]=Kx[n-n_0]
    $$
    $K$ ed $n_0$ rappresentano rispettivamente il guadagno ed il ritardo del sistema. Nel dominio della frequenza, questa condizione si traduce nei due seguenti requisiti per la risposta in ampiezza e la risposta in fase:
    $$
    \ov{A}(f) = K, \ \ \ov{\theta}(f)=-2\pi fn_{0}T
    $$
    È sufficiente che queste condizioni siano verificate nell'ambito della banda del segnale per garantire assenza di distorsioni

    Le caratteristiche di selettività di un filtro a tempo discreto con risposta in frequenza (che è una funzione periodica di periodo 1/T) sono determinate dall'andamento della sua
    risposta in ampiezza in un solo periodo della funzione (as esempio $\Big[-\frac{1}{2T}, \frac{1}{2T}\Big]$).

    Le basse frequenze sono sempre prossime alla frequenza nulla, mentre le alte sono comunque prossime al limite superiore dell'intervallo, ovvero $\frac{1}{2T}$:
    - **passa basso**
        \begin{align*}
        h_{\text{LP}}[n] &= 2BT \sinc(2nBT) \Longleftrightarrow \ov{H}_{\text{LP}} = \frac{1}{T}\sum_{k=-\infty}^{\infty} T \cdot \operatorname{rect}\left(\frac{f-\frac{k}{T}}{2 B}\right)
        \end{align*}
    - **passa alto**
        \begin{align*}
        h_{\text{HP}}[n] = \delta[n] -2BT\sinc(2nBT) \Longleftrightarrow \ov{H}_{\text{HP}}(f) = 1- \ov{H}_{\text{LP}}(f) 
        \end{align*}
    I filtri ideali **non sono causali!**    

## Quantizzazione (per alcune di queste domande guardare quesiti)
30. Formule e definizioni (passo, dinamica D, bit B, fattore di scala A...);

    L’operazione di quantizzazione rende **discreta** l’ampiezza dei campioni associando loro
    un valore di ampiezza scelto da un insieme finito di possibili livelli (livelli di quantizzazione)
    $$
    \hat{x} = \text{Q}\Big[x(nT)\Big]
    $$
    La quantizzazione è un'operazione *lossy*, in quanto essendo un'operazione irreversibile, una volta quantizzato il segnale l'informazione originale
    non potrà essere più recuperata, commettendo un errore
    $$
    e(nt)=\hat{x}(nT)-x(nT)
    $$
    Per effettuare l'operazione di quantizzazione dividiamo l’intervallo di variazione di ampiezza dei suoi campioni in intervalli di quantizzazione contigui $(x_i, x_{i+1})$,
    dove gli estremi rappresentano le *soglie* di quantizzazione. 

    L'operazione quindi consiste nel **selezionare l'intervallo più corretto per ogni campione** $x(nt)$ e associare al suo interno un valore $\hat{x}_i$ detto *livello* dell'intervallo selezionato.
    
    - "Definizioni":
        - **Passo**: indicato con $\Delta$, rappresenta la distanza tra livelli di quantizzazione.
        - **bit**: indicato con $B$, serve a determinare il numero di possibili livelli di quantizzazione, rappresentati con notazione binaria, pari a $2^{B}$
        - **dinamica**: indicata con $D$ rappresenta l'ampiezza dell'intervallo di valori che i livelli di quantizzazione riescono a coprire.
    
    - Quantizzatori uniformi
        
        Ottenuti imponendo una distanza costante tra le soglie e i livelli ($\Delta$ costante).

        Per avere una *buona rappresentazione del segnale*, la dinamica $D \approx$ **intervallo variazione ampiezza dei campioni**!
        $$
        D > X_{\text{max}}-X_{\text{min}}
        $$
        In un processo *aleatorio gaussiano*, i cui campioni seguono la distribuzione di probabilità Gaussiana (quindi con un intervallo di variazione *illimitato*),
        si rende necessario ipotizzare un intervallo di variazione dei campi **finito** e di dimensione tale da rendere *minima* la probabilità che esca da tale intervallo
        (**overflow**). Considerando il caso di valor medio *nullo*:
        \begin{align*}
        E\Big[f(x)\Big]=0 &\to \text{gli intervalli sono: }
        \left\{\begin{array}{cl}
        [-3\Delta, 3\Delta] & \approx 95,45 \% \\ \relax 
        [-4\Delta, 4\Delta] & \approx 99,73 \%
        \end{array} \right. \to \Delta > 8\sigma
        \end{align*}

        Per far sì che il passo non sia né eccessivamente grande (livelli di quantizzazione usati molto minori rispetto a quelli a disposizione), né troppo piccolo (commessi
        errori rilevanti (di overflow), quando si quantizzano campioni al di fuori della dinamica del quantizzatore) $\Delta, D, B$ sono legati secondo:
        $$
        \Delta=\frac{D}{2^B}
        $$

31. Tipologie di quantizzatori (midrise, midtread, arrotondamento e troncamento);

    Vedi risposte 33, 34 quesiti

32. Errore di quantizzazione e modello;

    L'errore di quantizzazione può essere visto come una sequenza che *si somma* (modello additivo) al segnale campionato:
    $$
    e(nT)=\hat{x}(nt)-x(nT) \Rightarrow \hat{x}(nT) = e(nT)+x(nT)
    $$
    Modelliamo quindi $e(nT)$ come un processo aleatorio, indicandolo come **rumore di quantizzazione** e con le seguenti ipotesi:
    1. $e(nT)$ sia un processo stazionario in senso lato: quindi media,
        potenza e varianza *costanti* e non dipendono da n;
    2.   che la densità di probabilità di $e(nT)$ sia di tipo
        **uniforme**, permettendo di valutare tali costanti distinguendo i casi di quantizzazione per troncamento e per arrotondamento: \\
        densità probabilità errore quantizzazione:
        \begin{align*}
        P_e(e)= \left\{
        \begin{array}{ll}
        \frac{1}{\Delta}& -\frac{\Delta}{2}<e\leq\frac{\Delta}{2}\\
        0 & \text{altrove}
        \end{array}\right. \to E\Big[e(nT)\Big]= 0 = E\Big[e^{2}(nT)\Big] = \frac{\Delta^{2}}{12}
        \end{align*}
    3.   $\{e(nT)\}$ incorrelato con processo $\{x(nT)\}$;
    4.   I campioni del processo $\{e(nT)\}$ sono **incorrelati** tra loro;

    Per la quantizzazione con troncamento si ha:
    \begin{align*}
    E\Big[e(nT)\ e\Big((n+m)T\Big)\Big]=\left\{\begin{array}{ll}E[e^2(nT)]=\frac{\Delta^2}{3}&m=0\\
    \\E[e(nT)]E\Big[e\Big((n+m)T\Big)\Big]=\frac{\Delta}{2}\cdot\frac{\Delta}{2} =\frac{\Delta^2}{4}&m\neq0,\end{array}\right.
    \end{align*}
    mentre per la quantizzazione con arrotondamento abbiamo
    \begin{align*}
    E\Big[e(nT)e\Big((n+m)T\Big)\Big]=\left\{\begin{array}{ll}E[e^2(nT)]=\sigma_e^2=\frac{\Delta^2}{12}&m=0\\\\0&m\ne0.\end{array}\right.
    \end{align*}
    In questo caso, l'errore di quantizzazione è un **processo bianco**.

33. Definizione Signal To Noise Ratio (SNR) e formule.

    È il rapporto tra la *potenza del segnale* e la *potenza dell'errore di quantizzazione*:
    $$
    \text{SNR}_q = \frac{S}{\sigma^2_e}
    $$
    Ciò vale con l'ipotesi di un quantizzatore che utilizzi l'arrotondamento. $S$ rappresenta la potenza del segnale (è necessario conoscerla oltre ai 
    parametri del quantizzatore)...  e $\Delta=\frac{D}{2^{B}}$:
    $$
    \text{SNR}_{q}=\frac{S}{\sigma_e^2}=\frac{S}{\frac{1}{12}\Delta^2}=\frac{S}{\frac{1}{12}(\frac{D}{2^B})^2}=\frac{12\cdot S\cdot2^{2B}}{D^2}
    $$
    Esprimendo $\text{SNR}_{q}$ in scala logaritmica
    \begin{align*}
    SNR_{\mathrm{qdB}} &=10\log_{10}SNR_{\mathrm{q}}=10\log_{10}\left(\frac{12\cdot S\cdot2^{2B}}{D^{2}}\right) \\
    &=(20 \log_{10}2)B+10\log_{\mathbf{1}0}\left(\frac{12S}{D^2}\right) \\
    &\approx6.02B+10\log_{10}\left(\frac{12S}{D^2}\right)\ \mathrm{dB}. 
    \end{align*}
