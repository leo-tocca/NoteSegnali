---
#title: "Dimostrazioni e quesiti per secondo parziale di Teoria dei Segnali"
#author:[Leonardo Toccafondi]
#date: 2024-04-18
header-includes: |
            \usepackage{cancel}
            \usepackage{steinmetz}
            \usepackage{derivative}
            \usepackage{mathtools}
            \usepackage{siunitx}
            \usepackage[italian]{babel}
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
...

## QUESITI
##### Processo WSS
1. Enunciare le proprietà che devono essere soddisfatte affinché un processo aleatorio sia stazionario in senso stretto [$^{**}$]
2. Enunciare le proprietà che devono essere soddisfatte affinché un processo aleatorio sia stazionario in senso lato
3. Elencare le proprietà che caratterizzano un processo aleatorio stazionario in senso lato (WSS).
4. Cos'è il rumore bianco?[$^{**}$]
5. Se $x(t)$ è un processo WSS in ingresso ad un sistema SLS con risposta impulsiva $h(t)$, il segnale $y(t)$ ottenuto in uscita è a sua volta un processo WSS?  [$^{**}$]

##### Trasformata di Fourier per una Sequenza
6. Che significato ha l'espansione della sequenza $x[n]$?  [$^{**}$]
7. Qual è la condizione sufficiente per l'esistenza della trasformata per sequenze?  [$^{**}$]
8. Cosa s'intende per denormalizzazione e a cosa serve?
9. Enunciare e spiegare il teorema dell'Incremento della TDF per sequenze reali
10. Enunciare e spiegare la condizione di convergenza della Trasformata di Fourier per sequenze (vedi n°6)
11. Sia $x[n] = cos(2\pi 0.1 n), \ n \in \mathbb{Z}$. Quale è la sua trasformata di Fourier per sequenze? Giustificare la risposta.
12. Se $x[n]$ ha trasformata di Fourier per sequenze $\overline{X}(F)$, quale sequenza $y[n]$ ha trasformata di Fourier $\overline{Y}(F) = \overline{X}(F - F_0)$? Giustificare la risposta.
13. Calcolare la trasformata di Fourier della sequenza $x[n]$ formata dall'impulso rettangolare discreto, cioè $x[n]= u[n]-u[n-N]$

###### Campionamento e interpolazione
14. Definizione teorema del campionamento e condizione di Nyquist [$^{**}$]
15. Cosa si intende per *aliasing*? Come si evita e perché va evitato. [$^{**}$]
16. Il segnale $x(t) = e^{-t} u(t)$ può essere campionato con assoluta assenza di aliasing? Giustificare la risposta.
17. Data una serie di campioni $x(nT)$ ottenuti campionando il segnale analogico di partenza $x(t)$, scrivere la relazione che lega il segnale ricostruito $\hat{x}(t)$ ai campioni $x(nT)$, nel caso di interpolazione lineare. 
18. Dato il segnale campionato $x_c(t)$ ottenuto campionando il segnale analogico di partenza $x(t)$, scrivere la relazione che lega lo spettro di $x_c(t)$ allo spettro di $x(t)$.
19. Differenza tra interpolazione a mantenimento, cardinale (e/o lineare) $^{**}$
20. Quali sono gli svantaggi e i vantaggi dell'interpolazione a mantenimento?  [$^{**}$]
21. Scrivere l'espressione del segnale interpolato in funzione dei valori della sequenza di campioni nel caso di Interpolazione a mantenimento

##### Trasformata di Fourier discreta
22. Che differenza troviamo tra una trasformata discreta ed una per sequenze [$^{**}$]
23. Da quanti campioni non nulli è composta la DFT a 20 campioni del segnale di durata finita $x[n] = cos^2(\frac{2\pi}{10}n)$, $n = 0, 1, . . . , 19$? Giustificare la risposta.
24. Scrivere i Teoremi del prodotto e della convoluzione della DFT
25. Enunciare e spiegare la Proprietà di Simmetria della TDF per sequenze reali
26. Scrivere la proprietà di traslazione in frequenza della DFT
27. Enunciare la proprietà di traslazione circolare della Trasformata Discreta di Fourier
28. Enunciare e spiegare la Proprietà di Simmetria della Trasformata Discreta di Fourier per sequenze reali
29. Sia data una sequenza finita $x[n]$, di lunghezza $N = 10$ campioni. Indicando con $X_{10}[k]$ e $X_{20}[k]$ le DFT di $x[n]$ calcolate, rispettivamente, con periodicità $L = 10$ e $L = 20$, quali campioni di $X_{20}[k]$ coincidono con campioni di $X_{10}[k]$? Giustificare la risposta.

##### Sistemi LTI discreti
30. Scrivere la risposta impulsiva di un sistema discreto che implementa una finestra mobile
31. Scrivere la risposta impulsiva di un sistema discreto che implementa un accumulatore o integratore numerico
32. Descrivere un filtro discreto a media mobile
33. Descrivere il filtro detto accumulatore o integratore numerico
34. Descrivere il filtro derivatore numerico o operatore
35. Giustificare la seguente affermazione: "Un sistema LTI è stabile se la sua funzione di trasferimento ha una regione di convergenza che include la circonferenza unitaria del piano z". $^*$.
36. Si supponga di voler usare un algoritmo di convoluzione veloce per eseguire il filtraggio di un segnale con un sistema LTI di tipo FIR, avente una risposta impulsiva lunga $N = 200$ campioni. Misurando la complessità in termini di moltiplicazioni reali per campione di uscita, è più conveniente usare (per il calcolo della convoluzione circolare) una FFT con periodicità $L = 2048$ oppure una con periodicità $L = 512$? Giustificare la risposta.
37. In uno schema di convoluzione veloce, quante moltiplicazioni reali per campione di uscita devono essere effettuate? Giustificare la risposta
38. Spiegare la differenza tra sistemi lineari e stazionari a tempo discreto di tipo FIR e di tipo IIR.

##### Quantizzazione
39. Spiegare la differenza tra un quantizzatore uniforme (a passo $\Delta$ e a $B$ bit) di tipo midtread e uno di tipo midrise
40. Dato un quantizzatore uniforme, scrivere le relazioni che permettono di trovare il valore quantizzato $\hat{x}(nT)$ a partire dal campione $x(nT)$ nel caso dell'operazione di arrotondamento e di troncamento
41. Enunciare le ipotesi che usualmente vengono assunte per il rumore di quantizzazione.
42. Giustificare la seguente affermazione: "Quantizzando un segnale sinusoidale di ampiezza unitaria con un convertitore analogico-digitale avente $B$ bit di quantizzazione e dinamica $[-1, 1]$ si ottiene un rapporto segnale-rumore 0 (espresso in $dB$) dato da $SNR \approx 6.02B + 1.76$".

##### Sistemi di comunicazione digitale
43. Spiegare il ruolo svolto dal codificatore di canale in un sistema di comunicazione digitale
44. Spiegare il ruolo svolto da un codificatore di sorgente nella catena di trasmissione digitale.
45. Spiegare il ruolo svolto da un modulatore digitale nella catena di trasmissione digitale.
46. Come ridurre gli effetti del rumore?
47. Descrivere gli schemi di base di modulazione digitale utilizzati in un sistema di comunicazione
48. Spiegare quali sono le tecniche multiplex utilizzate in un sistema di trasmissione digitale

## DIMOSTRAZIONI

1. Enunciare e dimostrare il Teorema del prodotto della TDF di una sequenza
2. Mostrare come la TDF di una sequenza ottenuta per campionamento si ricava come periodicizzazione della TDF del segnale di partenza [$^{**}$]
3. Enunciare e dimostrare la relazione che esiste tra la trasformata di Fourier di una sequenza $x[n]$ ottenuta per campionamento di un segnale continuo $x(t)$, e la Trasformata di Fourier di $x(t)$ stesso
4. Dimostrare che dalla relazione di antitrasformata discreta di Fourier discende la relazione di trasformata discreta di Fourier
5. Enunciare e dimostrare il Teorema della convoluzione della Trasformata discreta di Fourier
6. Enunciare e dimostrare il teorema di Parseval nella sua forma valida per sequenze aperiodiche e relative trasformate di Fourier per sequenze.
7. Dimostrare che, data una sequenza $x[n]$ di $N$ campioni, definendo la sequenza DFT mediante la formula
   
   $$
   \displaystyle
X[K] = \sum_{n=0}^{N-1} x[n] e^{-j \frac{2\pi}{N} kn}, \ \ \ k = 0, 1 , \dots, N-1
   $$
   
   allora la sequenza $x[n]$ è ricavabile da 
   $$
   \displaystyle
   x[n] = \frac{1}{N} \sum_{n=0}^{N-1} X[K] = e^{j \frac{2\pi}{N} kn}
 $$
   
8. Enunciare e dimostrare la relazione tra le trasformate di Fourier della sequenza somma $y[n]$ di una sequenza data $x[n]$, e la Trasformata di $x[n]$ stessa  [$^{***}$]
9. Enunciare e dimostrare la relazione che esiste tra la trasformata di Fourier di una sequenza $x[n]$ ottenuta per campionamento di un segnale continuo $x(t)$, e la Trasformata di Fourier di $x(t)$ stesso
10. Calcolare i parametri della densità di probabilità dell'ampiezza dell'errore di quantizzazione nei casi di arrotondamento e di troncamento
   
NOTA BENE: con [$^{**}$] si intendono domande aggiunte da me!
con [$^{***}$] si intende una domanda spostata dai quesiti alle dimostrazioni

\newpage

## RISPOSTE QUESITI

1.  Un processo aleatorio $x$ è detto stazionario se la sua *funzione di
    autocorrelazione* $R_{XX}(t_1, t_2) = E[X(t_1), X(t_2)]$ dipende
    solo dalla distanza (o *lag*) tra i campioni e **non** dai singoli
    istanti $t_1$ e $t_2$. - Un processo aleatorio è stazionario in
    senso stretto (SSS) se tutte le sue proprietà statistiche rimangono
    invariate nel tempo. Ovvero se la densità di probabilità rispetto ai
    singoli campioni, sia quella congiunta rispetto a più campioni non
    sono alterate da una transazione solidale nel tempo applicata agli
    indici dei campioni. Va verificato per tutti gli ordini i con
    $i= 0, \dots, \infty$
    $$
    f_x (x, t) = f_x(x, t+ \Delta t)$$
    $$
    f_x(x_1, x_2, t_1, t_2) = f_x(x_1, x_2, t_1 + \Delta t_1, t_2 + \Delta t_2)...
    $$

2.  Un processo aleatorio è stazionario in senso lato (WSS):

    -   la sua media e la sua varianza rimangono costanti nel tempo
        $\to E[x(t)] = m_x(t) = m_x$\
    -   la sua autocorrelazione dipende solo dallo scarto temporale e
        non dal tempo assoluto (funzione solo dello scarto $\tau$).
        $\to R_{xx}(t, t+\tau) = R_{xx}(\tau)$

3.  Le proprietà che caratterizzano un processo aleatorio WSS includono:

    -   $R_x(\tau) = R_x(-\tau) \to$ la funzione di autocorrelazione è
        una funzione pari

    -   $R_x(0)= E[X^2(t)] = P_x \geq 0 \to$ potenza costante

    -   $|R_x(\tau)| \leq R_x(0) \to$ la funzione di autocorrelazione ha
        il proprio massimo in $\tau = 0$

4.  Il rumore bianco è un tipo di segnale casuale che ha una potenza
    spettrale costante in tutto lo spettro di frequenze. Questo
    significa che tutte le frequenze sono presenti con la stessa
    intensità. Inoltre il rumore/processo bianco $w(t)$ ha campioni
    incorrelati

    -   $R_{ww}(\tau) = \frac{N_0}{2} \delta(\tau), \ \tau \neq 0$

    -   $E[w(t)] = 0$

    -   $S_{ww}(f) = \mathcal{F} \{\frac{N_0}{2}\} = \frac{N_0}{2} \to$''
        Potenza **infinita** $\to$ densità spettrale di potenza

    -   Nota: si chiama bianco in quanto possedendo nello spettro
        *tutte* componenti non nulle, si trova una similitudine con il
        colore bianco nello spettro dei colori

5.  Sapendo che $y(t) = x(t) \otimes h(t)$
    \begin{align*}
    E[y(t)] &= E[x(t)\otimes h(t)] = E[\int_{-\infty}^{\infty} h(\alpha)x(t - \alpha) d\alpha]
    = \int_{-\infty}^{\infty} h(\alpha)E[x(t - \alpha)] d\alpha =
       m_x \int_{-\infty}^{\infty} h(\alpha) d\alpha =\\&= m_x \cdot H(0)
    \\ R_y(t_1, t_2) &= E[y(t_1), y(t_2)] \to R_y(t, t-\tau) =
      E[y(t)y(t-\tau)] \to R_y(\tau) = R_x(\tau) \otimes (\tau) h(\tau) h(-\tau)=
    \ S_y(\tau) \\ &= S_x(f) \cdot H(f) \cdot H(-f) = S_x(f) \cdot H(f) \cdot H^*(-f) = S_x(f) \cdot |H(f)|^2
    \end{align*}
    Quindi è nuovamente un processo WSS

##### Risposte tdf sequenze aperiodiche

6.  Il segnale $x[n]$ viene espresso mediante la somma di molti termini
    $X(f)$ i quali, al variare della frequenza $\overline{X}(F)$ hanno
    un peso diverso (in ampiezza e in fase). A differenza di un segnale
    analogico, per esprimere una sequenza in ambito frequenziale sono
    **sufficienti** le sole componenti con frequenze comprese tra
    $[\frac{-1}{2T}, \frac{1}{2T}]$ (ciò è giustificato dalla
    periodicità della trasformata di Fourier per sequenze)

7.  La condizione sufficiente per l'esistenza della trasformata per
    sequenze è che la sequenza sia ***assolutamente sommabile***, ovvero
    la somma dei valori assoluti dei suoi elementi sia finita.
    $$\displaystyle \sum_{n=-\infty}^{\infty} |x[n]| < + \infty \to |X(f)| < +\infty$$
    $$|\overline{X}(f)| = |\sum_{n=-\infty}^{\infty} x[n] e^{-j2\pi nfT}| \leq \sum_{n=-\infty}^{\infty} | x[n] e^{-j2\pi nfT}| \leq 
      \sum_{n=-\infty}^{\infty} |x[n]|$$

8.  La denormalizzazione è necessaria quando la sequenza $x[n]$ deriva
    da un'operazione di campionamento: in questo caso la frequenza $F_0$
    $(= \frac{F}{F_c}$ dove $F$ è la frequenza e $F_c$ è la frequenza di
    campionamento$)$ non permette di stabilire un legame *immediato* con
    la frequenza espressa in Hz (e quindi **non** adimensionale) delle
    componenti nella trasformata del segnale analogico di partenza.
    Quindi se $T$ = al periodo di campionamento e
    $f=\frac{F}{T}=F\cdot F_c \to F=fT$ in Hz.

9. Il teorema dell'Incremento della Trasformata di Fourier per sequenze
    per sequenze reali afferma che l'incremento di una sequenza nel
    dominio del tempo corrisponde a una modulazione nel dominio della
    frequenza.

10. La condizione di convergenza della Trasformata di Fourier per
    sequenze è che la sequenza sia assolutamente sommabile, ovvero la
    somma dei valori assoluti dei suoi elementi sia finita.

11. Dagli appunti del Prof. Argenti (lezione 02/05/22):

    $x[n]=\cos(2\pi 0.1n)$ è un segnale sinusoidale di durata infinita alla
    frequenza normalizzata $F_0 = 0,1 = \frac{1}{10}, |F_0|<\frac{1}{2}$.
    È una sequenza **non** assolutamente sommabile, ma riusciamo ad ottenere la
    sua TFS mediante segnali impulsivi ($\delta$ di Dirac):
    \begin{align*}
    x[n] = \cos(2\pi 0.1n) \longleftrightarrow
    \ov{X}(f) &= \frac{1}{2}\Big[ \delta(F-F_0)+\delta(F+F_0) \Big] = \\
    &= \frac{1}{2}\Big[ \delta\Big(F-\frac{1}{10}\Big)+\delta\Big(F+\frac{1}{10}\Big) \Big] 
    \end{align*}
    Si può dimostrare utilizzando la trasformata *inversa*:
    \begin{align*}
    \int_{-\frac{1}{2}}^{\frac{1}{2}}\ov{X}(f) \ e^{j2\pi nF}\,df &=
    \int_{-\frac{1}{2}}^{\frac{1}{2}} \frac{1}{2}\Big[ \delta(F-F_0)+\delta(F+F_0) \Big] \ e^{j2\pi nF}\ \,df= \\
    &=\int_{-\frac{1}{2}}^{\frac{1}{2}} \frac{1}{2}\Big[ \delta\Big(F-\frac{1}{10}\Big)+\delta\Big(F+\frac{1}{10}\Big) \Big]\ e^{j2\pi nF}\ \,df= \\
    &=\frac{1}{2}(e^{j2\pi\frac{1}{10}} + e^{-j2\pi\frac{1}{10}})= \\
    &=\cos(\frac{2\pi n}{10}) = \cos(2\pi 0.1n)
    \end{align*}
    Nel caso generale in cui sia richiesta la TFS di un coseno $\cos(2\pi nf_0 T)$ è necessario utilizzare:
    $$
    \ov{X}(f) = \frac{1}{T}\sum_{n=-\infty}^{\infty}X\Big(f-\frac{k}{T}\Big)
    $$
    Dalla trasformata della sequenza costante, dal teorema del campionamento e dal teorema della modulazione:
    \begin{align*}
    e^{j2\pi nf_0 T} &\Leftrightarrow \frac{1}{T}\sum_{n=-\infty}^{\infty}\delta\Big(f-\frac{k}{T}\Big) \\
    \ov{X}(f) &= \frac{1}{2T}\Big[\sum_{k=-\infty}^{\infty}\delta\Big(f -f_0 -\frac{k}{T}\Big) + \sum_{k=-infty}^{\infty}\delta\Big(f+f_0 -\frac{k}{T}\Big) \Big]
    \end{align*}

12. Se $x[n]$ ha trasformata di Fourier per sequenze $X(F)$, allora la
    sequenza $y[n]$ con TDF $Y(F)=X(F-F_0)$ è data da
    $y[n]=x[n]e^{j2\pi F_0n}$. Questo è dovuto alla proprietà di
    traslazione in frequenza della trasformata di Fourier, che afferma
    che la traslazione di una funzione nel dominio della frequenza
    corrisponde a una modulazione esponenziale nel dominio del tempo.

13. La trasformata di Fourier della sequenza $x[n]=u[n]-u[n-N]$, dove
    $u[n]$ è la funzione gradino unitario, è data da:
    \begin{align*}
    \displaystyle \overline{X}(f) &= \sum_{n = -\infty}^{+\infty} (u[n]-u[n-N])e^{-2\pi nfT} = \sum_{n = 0}^{N-1}e^{-2\pi nfT} = \sum_{n = 0}^{N-1}(e^{-2\pi fT})^n = \\
    &\text{si applica la serie geometrica, con} \ q = e^{-j2\alpha}& \\
    &= \frac{1-e^{-2\pi N\alpha}}{1-e^{-2\pi \alpha}} = \frac{e^{j \alpha N}}{e^{\alpha}} \cdot \frac{e^{j\alpha N} - e^{-j\alpha N}}{e^{j\alpha } - e^{-j\alpha }} = e^{j \alpha (N-1)} \cdot \frac{sen(\alpha N)}{sen(\alpha)} = e^{-j\pi (N-1)fT} \cdot \frac{sen(N\pi fT)}{sen(\pi fT)}
    \end{align*}

##### Risposte campionamento e interpolazione

14. "Un segnale il cui spettro è **limitato** nella banda $B$ può essere
    ricostruito esattamente dai propri campioni, purché la frequenza di
    campionamento non sia inferiore a $2B$". La condizione di Nyquist:
    "Una volta fissata $B$ la frequenza di campionamento
    $f_c = \frac{1}{T} \geq 2B, \to T \leq \frac{1}{2B}$

15. L'aliasing è un effetto indesiderato che si verifica quando *non
    viene rispettata* la frequenza di Nyquist ($f_c < 2B$). Può essere
    evitato campionando il segnale a una frequenza almeno doppia della
    banda. L'aliasing va evitato perché introduce
    distorsioni nel segnale ricostruito dal momento che le repliche, a
    causa della loro sovrapposizione si sommano, rendendo impossibile
    una ricostruzione **fedele** del segnale originale .

16. Il segnale $x(t)=e^{-t}u(t)$ può essere campionato senza aliasing
    solo se la frequenza di campionamento è infinita. Questo perché il
    segnale ha componenti di frequenza che si estendono all'infinito,
    quindi non esiste una frequenza di Nyquist finita che possa essere
    utilizzata per campionare il segnale senza aliasing.

17. $\displaystyle x(nT) = x[n] \text{ ottenuti da:} \ \hat{x}(t)= \sum_{n= -\infty}^{\infty} x[n] \cdot tri(\frac{t-nT}{T})= \sum_{n= -\infty}^{\infty}x[n] (1-\frac{|t|}{T})rect(\frac{t}{2T})$

18. $\overline{X}(f) = \frac{1}{T}\sum_{k=-\infty}^{\infty}X(f-\frac{k}{T})$

19. -   L'interpolazione a mantenimento, o interpolazione a gradino, è
        un metodo di interpolazione che mantiene l'n-esimo valore della
        sequenza $x[n]$ a partire dall'istante $nT$ fino a $nT+1$.
        Successivamente sarà mantenuto $x[n+1]$ e così via\
        $\hat{x}(t)=\sum_{n=-\infty}^{+\infty}x[n]\cdot p(t-nT)\text{, con } p(t)= rect(\frac{t-\frac{T}{2}}{T})$.

    -   L'interpolazione cardinale, o sinc, utilizza come impulso $p(t)$
        una funzione sinc per interpolare tra i campioni:
        $\to p(t)=sinc(\frac{t}{T}) \to \hat{x}(t)=\sum_{n=-\infty}^{+\infty} x[n]\cdot sinc(\frac{t-nT}{T})$.
        Rispetto alla interpolazione a mantenimento introduce meno
        discontinuità, ma nella realtà non è applicabile, dal momento
        che sono necessari un numero infinito di termini, dal fatto che
        non è **causale** e a causa della impossibilità di ricostruire
        un segnale rect in frequenza;

    -   L'interpolazione lineare utilizza un'impulso triangolare, in
        modo tale che la risultante sia una spezzata che unisce i
        vertici dei triangoli:
        $p(t) = tri(\frac{t}{T}) \to \hat{x}(t) = \sum_n x[n]tri(\frac{t-nT}{T})$

        -   L'interpolazione a mantenimento è la più semplice, ma può
            introdurre distorsioni significative. L'interpolazione
            cardinale può fornire risultati più accurati, ma è
            computazionalmente più intensiva.

20. L'interpolazione a mantenimento ha il vantaggio di essere semplice
    da implementare e computazionalmente efficiente. Tuttavia, il
    segnale interpolato **non è limitato in banda**: in questo modo sono
    introdotte delle componenti frequenziali non presenti nel segnale
    analogico $x(t)$. Derivano dalla presenza di repliche dello spettro
    del segnale a cavallo dei multipli delle frequenze di campionamento
    (sono dette *immagini*). Inoltre anche all'interno della cosiddetta
    banda "utile" (intervallo base $f \in[-\frac{1}{2T}, \frac{1}{2T}]$) il
    segnale $x(t)$ viene distorto in ampiezza (i due spettri sono legati
    dalla seguente relazione:
    $\hat{X}(f)=\frac{P(f)X(f)}{T}=X(f)sinc(fT)e^{-j\pi fT}$). Bisogna
    notare come sia possibile ridurre la presenza di immagini
    utilizzando un filtro "*anti-immagine*" all'uscita
    dell'interpolatore: corrisponde ad un filtro passa-basso di banda B,
    che elimina le immagini dallo spettro del segnale interpolato.

21. $\hat{x}(t)=\sum_{n=-\infty}^{+\infty}x[n]\cdot p(t-nT)\text{, con } p(t)= rect(\frac{t-\frac{T}{2}}{T})$

##### Risposte TDF discreta

22. La differenza tra una trasformata discreta e una per sequenze
    risiede nel fatto che la trasformata discreta è definita solo per un
    numero finito di punti, mentre la trasformata per sequenze può
    essere definita per sequenze infinite. Inoltre, la trasformata
    discreta assume che il segnale sia periodico, mentre la trasformata
    per sequenze non fa questa assunzione (?).

23. 
\begin{align*} 
x[n] &= \cos^2(\frac{2\pi n}{10}), \ n= 0, \cdots, 19 \\
x[n] &= \frac{1}{2}[1+\cos(2\frac{2\pi n}{10})] = \frac{1}{2} + \frac{1}{4}e^{\frac{j2\pi 4n}{20}} + \frac{1}{4}e^{\frac{-j2\pi 4n}{20}} \\
x[k] &= \frac{1}{2}\sum_{k=0}^{19} e^{\frac{-j2\pi kn}{20}} + \frac{1}{4}\sum_{k=0}^{19} e^{\frac{-j2\pi (k-4)n}{20}} +\frac{1}{4}\sum_{k=0}^{19} e^{\frac{-j2\pi (k+4)n}{20}} = x_1[k]+x_2[k]+x_3[k]
\end{align*}
$$
x_{1}[k] = \left\{ \begin{array}{cl}
\frac{1}{2} \cdot 20 = 10 & \text{per } m=0 \\
0 & \text{altrimenti}
\end{array} \right., \
x_{2}[k] = \left\{ \begin{array}{cl}
\frac{1}{4} \cdot 20 = 5& \text{per } m=4 \\
0 & \text{altrimenti}
\end{array} \right.,
$$
$$
x_{3}[k] = \left\{ \begin{array}{cl}
\frac{1}{4} \cdot 20 = 5& \text{per } m=16 \\
0 & \text{altrimenti}
\end{array} \right.,\
x[k] = \left\{ \begin{array}{cl}
10& \text{per } m=0 \\
5 & \text{per }m=4, 16\\
0 & \text{altrimenti}
\end{array} \right.
$$
   
24. Il Teorema del prodotto per la DFT afferma che la DFT del prodotto
    di due sequenze è uguale alla convoluzione circolare delle DFT delle
    due sequenze. Il Teorema della convoluzione per la DFT afferma che
    la DFT della convoluzione di due sequenze è uguale al prodotto delle
    DFT delle due sequenze.


25.  La Proprietà di Simmetria della Trasformata di Fourier per sequenze
    reali afferma che lo spettro di una sequenza reale è simmetrico
    rispetto all'origine. Questo significa che la parte positiva dello
    spettro è l'immagine speculare della parte negativa.


26. La proprietà di traslazione in frequenza della DFT afferma che la
    DFT di una sequenza moltiplicata per un'onda esponenziale complessa
    è uguale alla DFT della sequenza originale spostata in frequenza.

27. La proprietà di traslazione circolare della Trasformata Discreta di
    Fourier afferma che la DFT di una sequenza traslata circolarmente è
    uguale alla DFT della sequenza originale moltiplicata per un'onda
    esponenziale complessa.

28. Per una sequenza reale $x[n]$ abbiamo:
    $$
    \dft_{N_0}\Big\{ x[n] \Big\} = \dft_{N_0}\Big\{x^{*}[n] \Big\} \to \overline{X}_k = \overline{X}^{*}_{-k} = \overline{X}^{*}_{N_0 -k}
    $$
    da cui derivano le proprietà di simmetria per il modulo e per la fase:
    \begin{gather*}
    \Big|\overline{X}_k \Big| = \Big| \overline{X}_{N_0 - k} \Big| \\
    \phase{\overline{X}_k} = -\phase{\overline{X}_{-k}}
    \end{gather*}
    Tali relazioni implicano che il modulo della sequenza $X[k]$ è simmetrico rispetto al valore $k = \frac{N_0}{2}$, mentre la fase è antisimmetrica rispetto a tale valore.
    - per sequenze di lunghezza **pari**, il centro di simmetria coincide con un campione della sequenza;
    - per sequenze di lunghezza **dispari**, invece, il centro di simmetria coincide con un punto equidistante tra due campioni.

29. $x[n]$ sequenza di 10 campioni (per esempio posti ad 1) \newline
    $X_{10}[k] \rightarrow$ DFT con periodicità 10 \newline
    $X_{10}[k] \rightarrow$ DFT con periodicità 20 \newline
\begin{align*}
x_{10}[n]&=x[n], \quad 
x_{20}[n] = \begin{cases}x[n] & n=0,\dots,9 \\
0 & n=10,\dots,19\end{cases} \\
X_{10}[k]&=\sum_{n=0}^9 x[n]  \\
X_{20}[k]&=\sum_{n=0}^{19} x[n] \cdot e^{\frac{-j2\pi nk}{20}}= \\
& =\sum_{n=0}^9 x[n] e^{\frac{-j2\pi nk}{20}} \\
X_{20}[2k]&=\sum_{n=0}^9 x[n] e^{\frac{-2 \pi n \cdot \cancel{2}k}{\cancel{20}_{10}}} =
 =\sum_{n=0}^{9} x[n] e^{\frac{-j2\pi nk}{10}}= \\
& =X_{10}[K] \\
\end{align*}
    Quindi corrispondono i campioni **pari** delle sequenze!

##### Risposte sistemi

30. $h(n) = \frac{1}{N}(u[n]-u[n-N])$

31. Ha una risposta impulsiva uguale alla funzione gradino unitario, cioè $h(n) = u(n)$

32. Un filtro a media mobile prende in ingresso un numero $N$ di campioni della sequenza d'ingresso,
    calcolandone la media aritmetica degli ultimi $N$ valori, a partire dall'istante $n^{*}$ verso
    tempi decrescenti, producendo un valore $y[n^{*}]$ in uscita. Il nome media mobile deriva dalla 
    traslazione in avanti di un "passo", al fine di ottenere il valore $y[n^{*}+1]$ (la media viene
    ricalcolata!)

33. Il filtro accumulatore numerico è un sistema che somma di tutti i campioni arrivati al suo ingresso fino all’istante $n$.
    Ha un risposta impulsiva uguale alla funzione gradino unitario, cioè $h(n)=u(n)$. Quindi:
    \begin{align*}
    y[n] &=\sum_{k=-\infty}^{\infty}x[k] \ h[n-k] = \sum_{k=-\infty}^{\infty}x[k] \ u[n-k] = \\
    & =\sum_{k=-\infty}^{n}x[k] \\ &\ u[n-k] = 1 \text{ sse } n\geq k
    \end{align*}
    Il sistema è *instabile*, ma l'uscita non è sempre illimitata: ad esempio esistono ingressi limitati (ad esempio segnali sinusoidali)
    per i quali l'uscita sarà comunque limitata.

34. Il filtro derivatore numerico o operatore differenza, e opera la differenza tra due campioni adiacenti. La sua risposta impulsiva
    è pari a:
    \begin{align*}
    h[n] &= \delta[n] - \delta[n-1], \text{ oppure } h[n]= \delta[n+1]-\delta[n]& \\
    y[n] &= \sum_{k=-\infty}^{\infty}x[k] \ h[n-k] = x[n] - x[n-1], \ y[n] = \sum_{k=-\infty}^{\infty}x[k] \ h[n-k] = x[n+1] - x[n] 
    \end{align*}
    Il primo è causale, il secondo no!

35. Domanda sulla trasformata z, da non considerare

36. ~~In uno schema di convoluzione veloce, il numero di moltiplicazioni
    reali per campione di uscita dipende dalla lunghezza del segnale e
    dalla lunghezza della risposta impulsiva del sistema. In generale,
    la convoluzione veloce richiede meno moltiplicazioni rispetto alla
    convoluzione diretta, ma il numero esatto dipende dai dettagli
    dell'implementazione dell'algoritmo FFT utilizzato per calcolare la
    convoluzione(?).~~

37. 

38. Un sistema SLS FIR (Finite Impulse Response) ha la sua risposta impulsiva  costituita
    da un numero finito di campioni, mentre un sistema SLS è IIR (Infinite Impulse Response) se la sua risposta
    impulsiva è costituita da un numero infinito di campioni.

    Inoltre, condizione necessaria e sufficiente per la stabilità in senso
    BIBO di un SLS è la assoluta sommabilità della sua risposta impulsiva:
    $$
    \sum_{k=-\infty}^{\infty}\Big|h[k]\Big| < +\infty
    $$
    I sistemi di tipo IIR, invece, non sono sempre stabili: per essi, è necessario controllare la validità o meno della condizione:
    
    un SLS è causale se e solo se la sua risposta impulsiva è una sequenza causale:
    $$
    h[n] = 0 \text{ se } n < 0, \text{ ovvero } h[n] = h[n] \cdot u[n]
    $$


39. Un quantizzatore uniforme è ottenuto imponendo una distanza costante
    tra le soglie e i livelli di quantizzazione (quindi il *passo*
    $\Delta$ è costante
    $\to x_{i+1}-x_i=\Delta; \ \hat{x}_{i+1}-\hat{x}_i = \Delta$). Per
    quanto riguarda la "scelta" dei livelli di quantizzazione nei quantizzatori
    uniformi si distinguono i:

    -   Midtread: i livelli di quantizzazione si estendono su un
        intervallo approssimativamente *simmetrico*, dal momento che i
        livelli sono un numero *pari* ed è incluso lo 0
        $$
        \to \{\hat{x}_i : i=0,\_,2^B -1\}= \{-2^{B-1}\Delta,\cdots,-\Delta,0,\Delta,\cdots,(2^{B-1}-1)\Delta \}
        $$

    -   Midrise: in questo caso i livelli coprono un intervallo
        **esattamente simmetrico** rispetto all'origine, tuttavia il
        valore 0 **non** è compreso nell'insieme (il passo è $\Delta$ e
        parto da $\frac{\Delta}{2}$):
        $$
        \to \{\hat{x}_i : i=0,\_,2^B -1\}= \{-(2^{B-1}-\frac{1}{2})\Delta,\cdots,-\frac{\Delta}{2},\frac{\Delta}{2},\cdots,(2^{B-1}-\frac{1}{2})\Delta \}
        $$

40. In un quantizzatore uniforme, in base alla scelta della regola di
    associazione tra $x(nT)\leftrightarrow \hat{x}(nT)$ si può usare:

    -   arrotondamento: dove ad $x(nT)$ viene associato il livello
        $\hat{x}_i$ più vicino. Inoltre le soglie di quantizzazione
        risultano essere posizionate nel *punto medio* tra i due livelli
        di quantizzazione. La relazione che permette di trovare il
        valore quantizzato $\hat{x}(nT)$ a partire dal campione $x(nT)$
        è:
        $$
        \hat{x}(nT) = \{\hat{x}_i : i=arg \ min_k (|x(nT)=\hat{x}_k| \}
        $$
        L'errore è $0 \leq |e(nT)| \leq \frac{\Delta}{2}$

    -   troncamento: ad $x(nT)$ viene associato il livello $\hat{x}_i$
        più vicino tra tutti quelli minori o uguali a $x(nT)$. Le soglie
        di quantizzazione coincidono con i livelli di quantizzazione. La
        relazione che permette di trovare il valore quantizzato
        $\hat{x}(nT)$ a partire dal campione $x(nT)$:
        $$
        \hat{x}(nT) = \{\hat{x}_i : i=arg \ max_k (\hat{x}_k \text{ con } \hat{x}_k \leq x(nT)) \}
        $$
        L'errore è $0 \leq |e(nT)| < \Delta$

41. Il rumore di quantizzazione $e(nT)$ è l'errore introdotto dal
    processo di quantizzazione, modellato come processo
    aleatorio *additivo*: $\hat{x}(nT)=x(nT)+e(nT)$.
    Le ipotesi usualmente assunte per il rumore di quantizzazione sono:

    -   $e(nT)$ sia un processo stazionario in senso lato: quindi media,
        potenza e varianza *costanti* e non dipendono da n;

    -   che la densità di probabilità di $e(nT)$ sia di tipo
        **uniforme**, permettendo di valutare tali costanti.

    -   $\{e(nT)\}$ incorrelato con processo $\{x(nT)\}$

    -   I campioni del processo $\{e(nT)\}$ sono **incorrelati** tra
        loro


42. Dal momento che l'escursione (pari a due volte l'ampiezza della
    sinusoide fratto la dinamica del quantizzatore = $\frac{1}{\Delta}$)
    è pari ad $1$ (viene quindi occupata tutta la dinamica), la dinamica
    $D=2$ e la potenza sarà $S=\frac{1}{2}$ allora
    $\sigma^2_e = \frac{\Delta^2}{12}=\frac{1}{12} = \frac{4}{2^{2B}}=\frac{1}{3} 2^{-2B} \to SNR_q=\frac{S}{\sigma^2_e}=\frac{3}{2}2^{2B} \to SNR=6.02B+1.76dB$

##### Risposte sistemi digitali

43. Il codificatore di canale in un sistema di comunicazione digitale
    introduce (in modo *controllato*) una **ridondanza** nella sequenza
    di informazioni binarie. In questo modo il ricevitore può utilizzare
    questa ridondanza per **attenuare e/o correggere** gli effetti
    negativi dovuti al rumore o alle interferenze incontrate nella
    trasmissione del segnale, riducendo quindi la probabilità d'errore
    dei bit di "informazione". In questo modo viene aumentata
    l'affidabilità e migliorata la fedeltà del segnale. \newline
    Ci sono due strategie per impiegare i codici a controllo di errore:
        - rivelare gli errori, per poi richiedere una ritrasmissione
        - correggere gli errori, non richiedendo eventualmente una ritrasmissione
    Può essere implementata con una:

    -   codici a blocchi (n/k): 
        Il messaggio è diviso in blocchi di $k$ simboli, a cui vengono associate
        parole di codice formate da $n=k+q$ simboli. Si introducono quindi $q$ bit di
        ridondanza.
        - codice a ripetizione:
        consiste nel ripetere una cifra binaria per
        $m$ volte ($m>0$). Se viene riscontrato un errore vi è una
        decisione "a maggioranza" (se errori $\displaystyle < \frac{N}{2}$).
        Tuttavia vi è un numero elevato di bit da trasmettere.

        - codifica "non banale" (controllo di parità): vengono mappati $k$ bit (alla volta) di
        una sequenza di $n$ bit ($k<n$) andando a creare una **parola in
        codice**. Il suo funzionamento si basa su una combinazione di k 
        bit di dati e $(n-k$) bit di parità, che vengono calcolati in modo
        da rendere rilevabili e correggibili determinati tipi di errori.
        In questo caso vi è una ridondanza pari a $\frac{n}{k}$

44. Il codificatore di sorgente in un sistema di comunicazione digitale
    è il primo blocco del trasmettitore. Si occupa del processo di
    conversione di una sequenza analogica o digitale in una sequenza di
    bit (questo processo è detto **codifica di sorgente o compressione
    dei dati**). Volendo *minimizzare* il numero di bit utilizzati, con
    la compressione è possibile rappresentare una data quantità di
    informazioni con un numero di bit *minore* rispetto alla
    rappresentazione originale.

45. Un modulatore digitale in un sistema di comunicazione digitale è
    l'interfaccia per il canale di comunicazione. Sceglie la forma
    d'onda più adatta alla trasmissione sul canale selezionato, in quanto
    è necessario spostare l'intervallo di frequenze in banda base
    (ovvero dalle frequenze "originali") in altri intervalli
    più adatti. \newline
    Per modulazione s'intende il processo mediante il quale alcune
    caratteristiche di una portante vengono variate in accordo
    con un'onda modulante (segnale).

    La modulazione può essere:

    -   binaria: la sequenza viene trasmessa un bit alla volta, con un
        bit-rate costante e pari a R bit al secondo;
        $\left\{ \begin{array}{cl}0 \to \ \delta_0(t)\\1 \to \ \delta_1(t)\end{array} \right.\to \text{durata della forma d'onda}: \frac{1}{R}s$\

    -   in alternativa il modulatore può trasmettere $b$ bits alla
        volta, utilizzando $M=2^b$ forme d'onda **distinte**
        $s_i(t), i:0, \_, M-1$. Ovvero, viene utilizzata una forma
        d'onda per ognuna delle $2^b$ possibili sequenze di bit
        possibili.

46. Gli effetti del rumore possono essere ridotti aumentando la potenza
    del segnale trasmesso (limite nell'attrezzatura) (?)

47. Vedi sottopunti 45.

48. L'operazione con cui diversi segnali sono trasmessi sullo stesso
    canale (cavo, fibra, radio,...) senza interferenze è chiamata
    multiplexing dei segnali e l'apparato che effettua tale operazione multiplex. 
    Un multiplex riceve N segnali distinti $s_1 (t), s_2 (t), …, s_ N(t)$ e li invia su un 
    unico canale utilizzando opportune regole (o tecniche multiplex).
    Il segnale in uscita è una combinazione degli $N$ segnali in ingresso,
    da cui possiamo ricavare nuovamente i segnali in ingresso con un'operazione
    di multiplexing
    
    - multiplex a **divisione di frequenze** (o FDM - Frequency Division Multiplex):
    
      Se in ingresso al sistema abbiamo $N$ segnali con lo spettro diverso da zero 
      nell'intervallo $(0, B)$, in frequenza l'i-esimo segnale viene shiftato di
      una frequenza $f_i = f_1 + iB$.
      
      Il canale di comunicazione in uscita, utilizzando per trasmettere il 
      segnale $y(t)$, deve avere una larghezza di banda $NB$. I singoli segnali 
      sono recuperabili senza distorsioni da $y(t)$ poiché occupano zone di
      frequenza diverse!
    - multiplex a **divisione di tempo** (o TDM - Time Division Multiplex):
    
         I diversi segnali si differenziano sostanzialmente per l'intervallo di tempo
         utilizzato per la trasmissione. Se abbiamo $N$ segnali da trasmettere in un 
         intervallo di tempo $\tau$, ad ognuno di essi viene assegnato un proprio
         sotto intervallo: ciò vale anche negli intervalli successivi.
         
         L'intervallo $\tau$ è denominato *frame* ed il suo valore varia nell'ordine
         di centinaia-decine di millisecondi.
