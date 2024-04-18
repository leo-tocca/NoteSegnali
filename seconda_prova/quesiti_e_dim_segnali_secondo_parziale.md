author:

- Leonardo Toccafondi   
  date: Maggio, 2023
  title: Dimostrazioni e quesiti per secondo parziale di Teoria dei Segnali

---

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
8. Enunciare e spiegare la Proprietà di Simmetria della TDF per sequenze reali
9. Enunciare e spiegare il teorema dell'Incremento della TDF per sequenze reali
10. Enunciare e spiegare la condizione di convergenza della Trasformata di Fourier per sequenze (vedi n°6)
11. Sia $x[n] = cos(2\pi 0.1 n), \ n ∈ \mathbb{Z}$. Quale è la sua trasformata di Fourier per sequenze? Giustificare la risposta.
12. Se $x[n]$ ha trasformata di Fourier per sequenze $\overline{X}(F)$, quale sequenza $y[n]$ ha trasformata di Fourier $\overline{Y}(F) = \overline{X}(F − F_0)$? Giustificare la risposta.
13. Calcolare la trasfornata di Fourier della sequenza $x[n]$ formata dall'impulso rettangolare discreto, cioe $x[n]= u[n]-u[n-N]$

###### Campionamento e interpolazione
14. Definizione teorema del campionamento e condizione di Nyquist [$^{**}$]
15. Cosa si intende per *aliasing*? Come si evita e perché va evitato. [$^{**}$]
16. Il segnale $x(t) = e^{−t} u(t)$ può essere campionato con assoluta assenza di aliasing? Giustificare la risposta.
17. Data una serie di campioni $x(nT)$ ottenuti campionando il segnale analogico di partenza $x(t)$, scrivere la relazione che lega il segnale ricostruito $\hat{x}(t)$ ai campioni $x(nT)$, nel caso di interpolazione lineare. 
18. Dato il segnale campionato $x_c(t)$ ottenuto campionando il segnale analogico di partenza $x(t)$, scrivere la relazione che lega lo spettro di $x_c(t)$ allo spettro di $x(t)$.
19. Differenza tra interpolazione a mantenimento, cardinale (e/o lineare) $^{**}$
20. Quali sono gli svantaggi e i vantaggi dell'interpolazione a mantenimento?  [$^{**}$]
21. Scrivere l'espressione del segnale interpolato in funzione dei valori della sequenza di campioni nel caso di Interpolazione a mantenimento

##### Trasformata di Fourier discreta
22. Che differenza troviamo tra una trasformata discreta ed una per sequenze [$^{**}$]
23. Da quanti campioni non nulli è composta la DFT a 20 campioni del segnale di durata finita $x[n] = cos^2(\frac{2\pi}{10}n)$, $n = 0, 1, . . . , 19$? Giustificare la risposta.
24. Scrivere i Teoremi del prodotto e della convoluzione della DFT
25. Scrivere la proprietà di traslazione in frequenza della DFT
26. Enunciare la proprietà di traslazione circolare della Trasformata Discreta di Fourier
27. Sia data una sequenza finita $x[n]$, di lunghezza $N = 10$ campioni. Indicando con $X_{10}[k]$ e $X_{20}[k]$ le DFT di $x[n]$ calcolate, rispettivamente, con periodicità $L = 10$ e $L = 20$, quali campioni di $X_{20}[k]$ coincidono con campioni di $X_{10}[k]$? Giustificare la risposta.

##### Sistemi LTI discreti
28. Scrivere la risposta impulsiva di un sistema discreto che implementa una finestra mobile
29. Giustificare la seguente affermazione: "Un sistema LTI è stabile se la sua funzione di trasferimento ha una regione di convergenza che include la circonferenza unitaria del piano z". $^*$.
30. Si supponga di voler usare un algoritmo di convoluzione veloce per eseguire il filtraggio di un segnale con un sistema LTI di tipo FIR, avente una risposta impulsiva lunga $N = 200$ campioni. Misurando la complessità in termini di moltiplicazioni reali per campione di uscita, è più conveniente usare (per il calcolo della convoluzione circolare) una FFT con periodicità $L = 2048$ oppure una con periodicità $L = 512$? Giustificare la risposta.
31. In uno schema di convoluzione veloce, quante moltiplicazioni reali per campione di uscita devono essere effettuate? Giustificare la risposta
32. 
##### Quantizzazione
32. Spiegare la differenza tra un quantizzatore uniforme (a passo $\Delta$ e a $B$ bit) di tipo midtread e uno di tipo midrise
33. Dato un quantizzatore uniforme, scrivere le relazioni che permettono di trovare il valore quantizzato $\hat{x}(nT)$ a partire dal campione $x(nT)$ nel caso dell'operazione di arrotondamento e di troncamento
34. Enunciare le ipotesi che usualmente vengono assunte per il rumore di quantizzazione. Giustificare la seguente affermazione: "Quantizzando un segnale sinusoidale di ampiezza unitaria con un convertitore analogico-digitale avente $B$ bit di quantizzazione e dinamica $[-1, 1]$ si ottiene un rapporto segnale-rumore 0(espresso in $dB$) dato da $SN R ≈ 6.02B + 1.76$".

##### Sistemi di comunicazione digitale
34. Spiegare il ruolo svolto dal codificatore di canale in un sistema di comunicazione digitale
35. Spiegare il ruolo svolto da un codificatore di sorgente nella catena di trasmissione digitale.
36. Spiegare il ruolo svolto da un modulatore digitale nella catena di trasmissione digitale.
37. Spiegare il ruolo svolto dal codificatore di sorgente nella catena di trasmissione digitale.

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
X[K] = \sum_{n=0}^{N-1} x[n] = e^{-j \frac{2\pi}{N} kn}, \ \ \ k = 0, 1 , \dots, N-1
   $$
   
   allora la sequenza $x[n]$ è ricavabile da 
   $$
   \displaystyle
   x[n] = \frac{1}{N} \sum_{n=0}^{N-1} X[K] = e^{j \frac{2\pi}{N} kn}
 $$
   
8. Enunciare e dimostrare la relazione tra le trasformate di Fourier della sequenza somma $y[n]$ di una sequenza data $x[n]$, e la Trasformata di $x[n]$ stessa  [$^{***}$]
   
NOTA BENE: con [$^{**}$] si intendono domande aggiunte da me!
con [$^{***}$] si intende una domanda spostata dai quesiti alle dimostrazioni
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
    $i= 0, \dots, \ \infty$ $$f_x (x, t) = f_x(x, t+ \Delta t)$$
    $$f_x(x_1, x_2, t_1, t_2) = f_x(x_1, x_2, t_1 + \Delta t_1, t_2 + \Delta t_2)
      //
      ...$$

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

    -   $|R_x(\tau)| \leq R_x(\tau) \to$ la funzione di correlazione ha
        il proprio massimo in $\tau = 0$

4.  Il rumore bianco è un tipo di segnale casuale che ha una potenza
    spettrale costante in tutto lo spettro di frequenze. Questo
    significa che tutte le frequenze sono presenti con la stessa
    intensità. Inoltre il rumore/processo bianco $w(t)$ ha campioni
    incorrelati

    -   $R_{ww}(\tau) = \frac{N_0}{2} \delta(\tau), \ \tau \neq 0$

    -   $E[w(t)] = 0$

    -   $S_ww(f) = \mathcal{F} \{\frac{N_0}{2}\} = \frac{N_0}{2} \to$
        Potenza **infinita**

    -   Nota: si chiama bianco in quanto possedendo nello spettro
        *tutte* componenti non nulle, si trova una similitudine con il
        colore bianco nello spettro dei colori

5.  Sapendo che $y(t) = x(t) \otimes h(t)$
    $$\displaystyle E[y(t)] = E[x(t)\otimes h(t)] = E[\int_{-\infty}^{\infty} h(\alpha)x(t - \alpha) d\alpha]$$
    $$= \int_{-\infty}^{\infty} h(\alpha)E[x(t - \alpha)] d\alpha =
       m_x \int_{-\infty}^{\infty} h(\alpha) d\alpha = m_x \cdot H(0)$$
    $$R_y(t_1, t_2) = E[y(t_1), y(t_2)] \to R_y(t, t-\tau) = \\
      E[y(t)y(t-\tau)] \to R_y(\tau) = R_x(\tau) \otimes (\tau) h(\tau) h(-\tau)$$
    $$S_y(\tau) = S_x(f) \cdot H(f) \cdot H(-f) = S_x(f) \cdot H(f) \cdot H^*(-f) = S_x(f) \cdot |H(f)|^2$$

    Quindi è nuovamente un processo WSS

6.  Il segnale $x[n]$ viene espressi mediante la somma di molti termini
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

9.  La Proprietà di Simmetria della Trasformata di Fourier per sequenze
    reali afferma che lo spettro di una sequenza reale è simmetrico
    rispetto all'origine. Questo significa che la parte positiva dello
    spettro è l'immagine speculare della parte negativa.

10. Il teorema dell'Incremento della Trasformata di Fourier per sequenze
    per sequenze reali afferma che l'incremento di una sequenza nel
    dominio del tempo corrisponde a una modulazione nel dominio della
    frequenza.

11. La condizione di convergenza della Trasformata di Fourier per
    sequenze è che la sequenza sia assolutamente sommabile, ovvero la
    somma dei valori assoluti dei suoi elementi sia finita.

12. ~~La trasformata di Fourier della sequenza\...~~

13. Se $x[n]$ ha trasformata di Fourier per sequenze $X(F)$, allora la
    sequenza $y[n]$ con TDF $Y(F)=X(F-F_0)$ è data da
    $y[n]=x[n]ej2\pi F_0n$. Questo è dovuto alla proprietà di
    traslazione in frequenza della trasformata di Fourier, che afferma
    che la traslazione di una funzione nel dominio della frequenza
    corrisponde a una modulazione esponenziale nel dominio del tempo.

14. La trasformata di Fourier della sequenza $x[n]=u[n]-u[n-N]$, dove
    $u[n]$ è la funzione gradino unitario, è data da:
    $$\displaystyle \overline{X}(f) = \sum_{n = -\infty}^{+\infty} (u[n]-u[n-N])e^{-2\pi nfT} = \sum_{n = 0}^{N-1}e^{-2\pi nfT} = \sum_{n = 0}^{N-1}(e^{-2\pi fT})^n =$$
    $$\text{si applica la serie geometrica, con} \ q = e^{-j2\alpha}$$
    $$= \frac{1-e^{-2\pi N\alpha}}{1-e^{-2\pi \alpha}} = \frac{e^{j \alpha N}}{e^{\alpha}} \cdot \frac{e^{j\alpha N} - e^{-j\alpha N}}{e^{j\alpha } - e^{-j\alpha }} = e^{j \alpha (N-1)} \cdot \frac{sen(\alpha N)}{sen(\alpha)} = e^{-j\pi (N-1)fT} \cdot \frac{sen(N\pi fT)}{sen(\pi fT)}$$

15. "Un segnale il cui spettro è **limitato** nella banda $B$ può essere
    ricostruito esattamente dai propri campioni, purché la frequenza di
    campionamento non sia inferiore a $2B$". La condizione di Nyquist:
    "Una volta fissata $B$ la frequenza di campionamento
    $f_c = \frac{1}{T} \geq 2B, \to T \leq \frac{1}{2B}$

16. L'aliasing è un effetto indesiderato che si verifica quando *non
    viene rispettata* la frequenza di Nyquist ($f_c < 2B$). Può essere
    evitato campionando il segnale a una frequenza almeno doppia della
    frequenza di Nyquist. L'aliasing va evitato perché introduce
    distorsioni nel segnale ricostruito dal momento che le repliche, a
    causa della loro sovrapposizione si sommano, rendendo impossibile
    una ricostruzione **fedele** del segnale originale .

17. Il segnale $x(t)=e^{-t}u(t)$ può essere campionato senza aliasing
    solo se la frequenza di campionamento è infinita. Questo perché il
    segnale ha componenti di frequenza che si estendono all'infinito,
    quindi non esiste una frequenza di Nyquist finita che possa essere
    utilizzata per campionare il segnale senza aliasing.

18. $\displaystyle x(nT) = x[n] \text{ ottenuti da:} \ \hat{x}(t)= \sum_{n= -\infty}^{\infty} x[n] \cdot tri(\frac{t-nT}{T})= \sum_{n= -\infty}^{\infty}x[n] (1-\frac{|t|}{T})rect(\frac{t}{2T})$

19. $\overline{X}(f) = \frac{1}{T}\sum_{k=-\infty}^{\infty}X(f-\frac{k}{T})$

20. -   L'interpolazione a mantenimento, o interpolazione a gradino, è
        un metodo di interpolazione che mantiene l'n-esimo valore della
        sequenza $x[n]$ a partire dall'istante $nT$ fino a $nT+1$.
        Successivamente sarà mantenuto $x[n+1]$ e così via\
        $\hat{x}(t)=\sum_{n=-\infty}^{+\infty}x[n]\cdot p(t-nT)\text{, con } p(t)= rect(\frac{t-\frac{T}{2}}{T})$.

    -   L'interpolazione cardinale, o sinc, utilizza come impulso $p(t)$
        una funzione sinc per interpolare tra i campioni:
        $\to p(t)=sinc(\frac{t}{T}) \to \hat{x}(t)=\sum_{x=-\infty}^{+\infty} x[n]\cdot sinc(\frac{f-nT}{T})$.
        Rispetto alla interpolazione a mantenimento introduce meno
        discontinuità, ma nella realtà non è applicabile, dal momento
        che sono necessari un numero infinito di termini, dal fatto che
        non è **causale** e a causa della impossibilità di ricostruire
        un segnale rect in frequenza;

    -   L'interpolazione lineare utilizza un'impulso triangolare, in
        modo tale che la risultante sia una spezzata che unisce i
        vertici dei triangoli:
        $p(t) = tri(\frac{t-nT}{T}) \to \hat{x}(t) = \sum_n x[n]tri(\frac{t-nT}{T})$

        -   L'interpolazione a mantenimento è la più semplice, ma può
            introdurre distorsioni significative. L'interpolazione
            cardinale può fornire risultati più accurati, ma è
            computazionalmente più intensiva.

21. L'interpolazione a mantenimento ha il vantaggio di essere semplice
    da implementare e computazionalmente efficiente. Tuttavia, il
    segnale interpolato **non è limitato in banda**: in questo modo sono
    introdotte delle componenti frequenziali non presenti nel segnale
    analogico $x(t)$. Derivano dalla presenza di repliche dello spettro
    del segnale a cavallo dei multipli delle frequenze di campionamento
    (sono dette *immagini*). Inoltre anche all'interno della cosiddetta
    banda "utile" (intervallo base $[-\frac{1}{2T}, \frac{1}{2T}]$) il
    segnale $x(t)$ viene distorto in ampiezza (i due spettri nono legati
    dalla seguente relazione:
    $\hat{X}(f)=\frac{P(f)X(f)}{T}=X(f)sinc(fT)e^{-j\pi fT}$). Bisogna
    notare come sia possibile ridurre la presenza di immagini
    utilizzando un filtro "*anti-immagine*" all'uscita
    dell'interpolatore: corrisponde ad un filtro passa-basso di banda B,
    che elimina le immagini dallo spettro del segnale interpolato.

22. $\hat{x}(t)=\sum_{n=-\infty}^{+\infty}x[n]\cdot p(t-nT)\text{, con } p(t)= rect(\frac{t-\frac{T}{2}}{T})$

23. La differenza tra una trasformata discreta e una per sequenze
    risiede nel fatto che la trasformata discreta è definita solo per un
    numero finito di punti, mentre la trasformata per sequenze può
    essere definita per sequenze infinite. Inoltre, la trasformata
    discreta assume che il segnale sia periodico, mentre la trasformata
    per sequenze non fa questa assunzione (?).

24. $$x[n] = \cos^2(\frac{2\pi n}{10}), \ n= 0, \cdots, 19$$

    $$x[n] = \frac{1}{2}[1+\cos(2\frac{2\pi n}{10})] = \frac{1}{2} + \frac{1}{4}e^{\frac{j2\pi n}{20}} + \frac{1}{4}e^{\frac{-j2\pi n}{20}}$$

    $$x[k] = \frac{1}{2}\sum_{k=0}^{19} e^{\frac{-j2\pi kn}{20}} + \frac{1}{4}\sum_{k=0}^{19} e^{\frac{-j2\pi (k-4)n}{20}} +\frac{1}{4}\sum_{k=0}^{19} e^{\frac{-j2\pi (k+4)n}{20}} = x_1[k]+x_2[k]+x_3[k]$$

    $x_1[k]=\left\{ \begin{array}{cl}\frac{1}{2}\cdot20 = 10 \text{, per m=0}\\0 \text{ altrimenti}\end{array}, \ x_2[k]=\left\{ \begin{array}{cl}\frac{1}{4}\cdot20 = 5 \text{, per m=4}\\0 \text{ altrimenti}\end{array}, \ x_3[k]=\left\{ \begin{array}{cl}\frac{1}{2}\cdot20 = 5 \text{, per m=16}\\0 \text{ altrimenti}\end{array} \right$

    $x[k]=\left\{ \begin{array}{cl} 10 \text{, per m=0}\\ 5 \text{, per m=4, 16}\\0 \text{ altrimenti}\end{array} \right$

25. Il Teorema del prodotto per la DFT afferma che la DFT del prodotto
    di due sequenze è uguale alla convoluzione circolare delle DFT delle
    due sequenze. Il Teorema della convoluzione per la DFT afferma che
    la DFT della convoluzione di due sequenze è uguale al prodotto delle
    DFT delle due sequenze.

26. La proprietà di traslazione in frequenza della DFT afferma che la
    DFT di una sequenza moltiplicata per un'onda esponenziale complessa
    è uguale alla DFT della sequenza originale spostata in frequenza.

27. La proprietà di traslazione circolare della Trasformata Discreta di
    Fourier afferma che la DFT di una sequenza traslata circolarmente è
    uguale alla DFT della sequenza originale moltiplicata per un'onda
    esponenziale complessa.

28. ?

29. Se $x[n]$ è una sequenza finita di lunghezza $N=10$ campioni, e
    $X_{10}[k]$ e $X_{20}[k]$ sono le DFT di $x[n]$ calcolate con
    periodicità $L=10$ e $L=20$ rispettivamente, allora i campioni di
    $X_{20}[k]$ che coincidono con i campioni di $X_{10}[k]$ sono solo i
    primi 10, in quanto i successivi 10 sono tutti pari a zero (?).

30. $h(n) = \frac{1}{N}(u[n]-u[n-N])$

31. ~~Un sistema LTI (Lineare e Tempo-Invariante) è stabile se la sua
    funzione di trasferimento ha una regione di convergenza che include
    la circonferenza unitaria del piano z. Questo perché la stabilità di
    un sistema LTI è legata alla posizione dei poli della sua funzione
    di trasferimento: se tutti i poli sono all'interno della
    circonferenza unitaria, il sistema è stabile.~~

32. ?

33. ~~In uno schema di convoluzione veloce, il numero di moltiplicazioni
    reali per campione di uscita dipende dalla lunghezza del segnale e
    dalla lunghezza della risposta impulsiva del sistema. In generale,
    la convoluzione veloce richiede meno moltiplicazioni rispetto alla
    convoluzione diretta, ma il numero esatto dipende dai dettagli
    dell'implementazione dell'algoritmo FFT utilizzato per calcolare la
    convoluzione(?).~~

34. Un quantizzatore uniforme è ottenuto imponendo una distanza costante
    tra le soglie e i livelli di quantizzazione (quindi il *passo*
    $\Delta$ è costante
    $\to x_{i+1}-x_i=\Delta; \ \hat{x}_{x+1}-\hat{x}_i = \Delta$). Per
    quanto riguarda i livelli di quantizzazione nei quantizzatori
    uniformi si distinguono i:

    -   Midtread: i livelli di quantizzazione si estendono su un
        intervallo approssimativamente *simmetrico*, dal momento che i
        livelli sono un numero *pari* ed è incluso lo 0 (come estremo?)
        $\to \{\hat{x}_i,i=0,\_,2^B -1\}= \{-2^{B-1}\Delta,\_,-\Delta,0,\Delta,\_,(2^{B-1}-1)=\Delta \}$

    -   Midrise: in questo caso i livelli coprono un intervallo
        **esattamente simmetrico** rispetto all'origine, tuttavia il
        valore 0 **non** è compreso
        nell'insieme:$\to \{\hat{x}_i,i=0,\_,2^B -1\}= \{-(2^{B-1}-\frac{1}{2})\Delta,\_,-\frac{\Delta}{2},0,\frac{\Delta}{2},\_,(2^{B-1}-\frac{1}{2})=\Delta \}$

35. In un quantizzatore uniforme, in base alla scelta della regola di
    associazione tra $x(nT)\leftrightarrow \hat{x}(nT)$ si può usare:

    -   arrotondamento: dove ad $x(nT)$ viene associato il livello
        $\hat{x}_i$ più vicino. Inoltre le soglie di quantizzazione
        risultano essere posizionate nel *punto medio* tra i due livelli
        di quantizzazione. La relazione che permette di trovare il
        valore quantizzato $\hat{x}(nT)$ a partire dal campione $x(nT)$
        è:
        $\hat{x}(nT) = \{x_i \: i=arg \ min_k (|x(nT)=\hat{x}(k)| \}$.
        L'errore è $0 \leq |e(nT)| \leq \frac{\Delta}{2}$

    -   troncamento: ad $x(nT)$ viene associato il livello $\hat{x}_i$
        più vicino tra tutti quelli minori o uguali a $x(nT)$. Le soglie
        di quantizzazione coincidono con i livelli di quantizzazione. La
        relazione che permette di trovare il valore quantizzato
        $\hat{x}(nT)$ a partire dal campione $x(nT)$
        $\hat{x}(nT) = \{x_i \: i=arg \ max_k (\hat{x}_k \text{ con } \hat{x}_k \leq x(nT)) \}$
        L'errore è $0 \leq |e(nT)| < \Delta$

36. Il rumore di quantizzazione $e(nT)$ è l'errore introdotto dal
    processo di quantizzazione. Le ipotesi usualmente assunte per il
    rumore di quantizzazione sono:

    -   $e(nT)$ sia un processo stazionario in senso lato: quindi media,
        potenza e varianza *costanti* e non dipendono da n;

    -   che la densità di probabilità di $e(nT)$ sia di tipo
        **uniforme**, permettendo di valutare tali costanti.

    -   $\{e(nT)\}$ incorrelato con processo $\{x(nT)\}$

    -   I campioni del processo $\{e(nT)\}$ sono **incorrelati** tra
        loro

37. Dal momento che l'escursione (pari a due volte l'ampiezza della
    sinusoide fratto la dinamica del quantizzatore = $\frac{1}{\Delta}$)
    è pari ad $1$ (viene quindi occupata tutta la dinamica), la dinamica
    $D=2$ e la potenza sarà $S=\frac{1}{2}$ allora
    $\sigma^2_e = \frac{\Delta^2}{12}=\frac{1}{12} = \frac{4}{2^{2B}}=\frac{1}{3} 2^{-2B} \to SNR_q=\frac{S}{\sigma^2_e}=\frac{3}{2}2^{2B} \to SNR=6.02+1.76dB$

38. Il codificatore di canale in un sistema di comunicazione digitale
    introduce (in modo *controllato*) una **ridondanza** nella sequenza
    di informazioni binarie. In questo modo il ricevitore può utilizzare
    questa ridondanza per **attenuare e/o correggere** gli effetti
    negativi dovuti al rumore o alle interferenze incontrate nella
    trasmissione del segnale. In questo modo viene aumentata
    l'affidabilità e migliorata la fedeltà del segnale. Può essere
    implementata con una:

    -   codifica "banale": consiste nel ripetere una cifra binaria per
        $m$ volte ($m>0$). Se viene riscontrato un errore vi è una
        decisione "a maggioranza" (se errori
        $\displaystyle < \frac{N}{2}$). Tuttavia vi è un numero elevato
        di bit da trasmettere.

    -   codifica "non banale": vengono mappati $k$ bit (alla volta) di
        una sequenza di $n$ bit ($k<n$) andando a creare una **parola in
        codice**. In questo caso vi è una ridondanza pari a
        $\frac{n}{k}$

39. Il codificatore di sorgente in un sistema di comunicazione digitale
    è il primo blocco del trasmettitore. Si occupa del processo di
    conversione di una sequenza analogica o digitale in una sequenza di
    bit (questo processo è detto **codifica di sorgente o compressione
    dei dati**). Volendo *minimizzare* il numero di bit utilizzati, con
    la compressione è possibile rappresentare una data quantità di
    informazioni con un numero di bit *minore* rispetto alla
    rappresentazione originale.

40. Un modulatore digitale in un sistema di comunicazione digitale è
    l'interfaccia per il canale di comunicazione. Sceglie la forma
    d'onda più adatta alla trasmissione sul canale scelto. Può essere:

    -   binaria: la sequenza viene trasmessa un bit alla volta, con un
        bit-rate costante e pari a R bit al secondo;
        $\left\{ \begin{array}{cl}0 \to \ \delta_0(t)\\1 \to \ \delta_1(t)\end{array} \right.\to \text{durata della forma d'onda}: \frac{1}{R}s$\

    -   in alternativa il modulatore può trasmettere $b$ bits alla
        volta, utilizzando $M=2^b$ forme d'onda **distinte**
        $s_i(t), i:0, \_, M-1$. Ovvero, viene utilizzata una forma
        d'onda per ognuna delle $2^b$ possibili sequenze di bit
        possibili.

41. Gli effetti del rumore possono essere ridotti aumentando la potenza
    del segnale trasmesso (limite nell'attrezzatura),
