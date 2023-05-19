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
34. Enunciare le ipotesi che usualmente vengono assunte per il rumore di quantizzazione. Giustificare la seguente affermazione: "Quantizzando un segnale sinusoidale di ampiezza unitaria con un convertitore analogico-digitale avente $B$ bit di quantizzazione e dinamica $[−1, 1]$ si ottiene un rapporto segnale-rumore 0(espresso in $dB$) dato da $SN R ≈ 6.02B + 1.76$".

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
