---
header-includes: |
            \usepackage{cancel}
            \usepackage{steinmetz}
            \usepackage{derivative}
            \usepackage{mathtools}
            \usepackage{siunitx}
            \DeclareMathOperator{\sinc}{sinc}
            \DeclareMathOperator{\rect}{rect}
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
        1. \begin{gather*}
            E[y(t)] = E[x(t)\otimes h(t)]= E[\int_{-\infty}^{\infty} h(\alpha)\cdot x(t-\alpha) \,d\alpha] = \\
            \int_{-\infty}^{\infty} h(\alpha) \ E[x(t-\alpha)] \,d\alpha = m_{X} \int_{-\infty}^{\infty} h(\alpha) \,d\alpha = m_{X} \ H(0) = \text{ costante}
            \end{gather*}
        2. \begin{gather*}
            R_{yy}(t_{1},t_{2}) \left\{ \begin{array}{lcl}
            t_{1} &=t \\
            t_{2} &=t + \tau \to \tau = t_{2}-t_{1}
            \end{array} \right. \to \text{ cambio di variabile} \\
            R_{yy}(t, t + \tau)= E[y(t)\cdot y(t+\tau)] = E\Big[\int_{-\infty}^{\infty} h)\alpha \ x(t-\alpha)\,d\,\alpha \ \int_{-\infty}^{\infty}h(\beta) \ x(t+\tau -\beta) d\,\beta\Big]\\
            E\Big[\int_{-\infty}^{\infty}\int_{-\infty}^{\infty} h(\alpha) \ h(\beta) \ x(t-\alpha) x(t+\tau -\beta) \,d\alpha \,d\beta \Big]= \\
            \int_{-\infty}^{\infty}\int_{-\infty}^{\infty} h(\alpha) \ h(\beta) \ E \Big[x(t-\alpha) x(t+\tau -\beta) \Big] \,d\alpha \,d\beta \\
            \int_{-\infty}^{\infty}\int_{-\infty}^{\infty} h(\alpha) \ h(\beta) \ R_{xx}(\tau -\beta +\alpha) \,d\alpha \,d\beta \to R_{yy}(t, t+\tau) = R_{yy(\tau)}
            \end{gather*}
        
        Quindi il processo $y(t)$ è WSS.

## Segnali a tempo discreto aperiodici

2. Trasformata di Fourier per sequenze (definizione, periodo 1, denormalizzazione);

    Data la sequenza *aperiodica* $x[n]$ **discreta**:
    \begin{gather*}
    \overline{X}(f) = \sum_{n=-\infty}^{\infty}x[n]\ e^{-j2\pi nfT} \longrightarrow f=F\cdot F_{c} = \frac{F}{T} = \si{\hertz}
    \\
    = \sum_{n=-\infty}^{\infty}x[n] \ e^{j2\pi nF}
    \end{gather*}
    $\overline{X}(f)$ è **completamente nota** se conosco il suo andamento in un intervallo delle frequenze *normalizzate* di ampiezza unitaria:  $\underbrace{F\in [-\frac{1}{2}; \frac{1}{2}]}_{\text{Intervallo base}}$

    - Periodica di periodo $1$:
    \begin{gather*}
    \overline{X}(F+1) = \sum_{n=-\infty}^{\infty} x[n] \ e^{-j2\pi n(F+1)} = \\
    \sum_{n=-\infty}^{\infty} x[n] e^{-j2\pi nF}\underbrace{\cancel{e^{-j2\pi n}}}_{=1 \text{ (n intero)}} = \\
    \sum_{n=-\infty}^{\infty} x[n] e^{-j2\pi nF} = \overline{X}(F)
    \end{gather*}

    - *Denormalizzazione*:
    
    Necessaria in quanto se la sequenza $x[n]$ deriva da un'operazione di campionamento. la frequenza normalizzata **non permette** di stabilire un legame con la frequenza (espressa in \si{\Hz})
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
    \begin{gather*}
    \overline{X}(f) \triangleq \sum_{m=-\infty}^{\infty} x[m] \ e^{-j2\pi m fT} \to \text{ moltiplico e divido per osc.ni complesse alla frequenza } f \text{ e integro}\\
    \int_{-\frac{1}{2T}}^{\frac{1}{2T}} \overline{X}(f) \ e^{j2\pi n fT} \,df = \int_{-\frac{1}{2T}}^{\frac{1}{2T}} \sum_{m=-\infty}^{\infty} x[m] \ e^{-j2\pi m fT} \ e^{j2\pi n fT} \,df = \\
    \sum_{m=-\infty}^{\infty} x[m] \int_{-\frac{1}{2T}}^{\frac{1}{2T}} e^{-j2\pi (m-n)fT}\,df
    \end{gather*}

### Teoremi
4. Teorema di Linearità;
5. Teorema del Ritardo;
6. Teorema della Modulazione;
7. Teorema della Somma di Convoluzione;
    
    Sia $s[n]$ la sequenza discreta
8. Teorema del Prodotto;
9. Teorema dell'Incremento;
10. Teorema della Sequenza Somma.

### Campionamento:
11. Teorema del campionamento (Solo definizione);
12. Relazione tra TCF e TFS.

## Segnali a tempo discreto aperiodici
13. Trasformata discreta di Fourier (definizione);
14. La trasformata di una sequenza periodica è essa stessa periodica (stesso periodo);
15. La relazione di sintesi di una TDF discende da quella di analisi;

### Proprietà:
16. Proprietà di Linearità;
17. Proprietà di Traslazione Circolare;
18. Proprietà di Traslazione In Frequenza;
19. Proprietà di Inversione Temporale;
20. Simmetria per sequenze reali (pari e dispari);
21. Teorema di Parseval per sequenze;
22. Teorema del Prodotto;
23. Teorema della Convoluzione (+ relazioni tra convoluzione lineare e circolare).

### Generale:
24. Fast Fourier Transform (FFT).

## Sistemi monodimensionali a tempo discreto 

### Proprietà dei sistemi;
26. SLS a tempo discreto: risposta impulsiva.

### Proprietà:
27. Sistemi a cascata e in parallelo;
28. Risposta in frequenza;
29. Filtri a tempo discreto.

## Quantizzazione
30. Formule e definizioni (passo, dinamica D, bit B, fattore di scala A...);
31. Tipologie di quantizzatori (midrise, midtread, arrotondamento e troncamento);
32. Errore di quantizzazione;
33. Modello dell’errore di quantizzazione;
34. Definizione Signal To Noise Ratio (SNR) e formule.
