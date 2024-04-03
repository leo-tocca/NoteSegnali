---
title: "Quesiti e dimostrazioni (con soluzioni) per primo parziale di Teoria dei Segnali"
#author: [Leonardo Toccafondi]
date: 2024-02-22
subject: "Segnali"
tags: [Appunti]
titlepage: false
#mainfont: "Playfair-RegularSemiCondensed"
...

## QUESITI

1.  Un segnale deterministico a tempo continuo $s(t)$ periodico ha Energia e Potenza finite e/o infinite?
2.  Si definisca la Potenza istantanea di un segnale deterministico a tempo continuo $s(t)$
3.  Si definisca la potenza media di un segnale deterministico a tempo continuo $s(t)$
4.  Calcolare Energia e Potenza media del segnale a tempo continuo $x(t) = Ae ^{-t} u(t)$.
5.  Calcolare l’energia del segnale $x(t) = sinc(t)$.
6.  Calcolare Energia e Potenza media di un segnale a tempo continuo sinusoidale di ampiezza 2 e di periodo 2 secondi.
7.  Calcolare Energia e Potenza media di un segnale a tempo continuo sinusoidale di ampiezza $A$ e di periodo $T$.
8.  Calcolare Energia e Potenza media di un segnale a tempo continuo costante
9.  Sotto quali condizioni un segnale deterministico a tempo continuo $s(t)$ ha Potenza media finita?
10. Giustificare la seguente affermazione: “Lo spettro di ampiezza di un segnale tempo-continuo aperiodico reale è una funzione pari”.
11. Giustificare la seguente affermazione: “Lo spettro di fase di un segnale tempo-continuo aperiodico reale è una funzione dispari”.
12. Calcolare la quantità $\int_{- \infty}^{\infty} sinc(t) dt$
13. Tra onda quadra e onda triangolare, quale dei due segnali ha coefficienti della serie di Fourier con modulo che va a zero più velocemente al crescere di $n$ e perché?
14. Tra la rampa e l’onda triangolare, quale dei due segnali ha coefficienti della serie di Fourier con modulo che va a zero più velocemente al crescere di $n$, e perché?
15. Quali sono le proprietà della serie di Fourier di un segnale periodico pari
16. Quali sono le proprietà della serie di Fourier di un segnale periodico dispari
17. Se il segnale periodico $x(t)$ è reale e pari, allora la serie di Fourier si semplifica in modo tale che ...
18. Se il segnale periodico $x(t)$ è reale e dispari, allora la serie di Fourier si semplifica in modo tale che ...
19. Elencare le Condizioni di Dirichlet per la convergenza della serie di Fourier
20. Elencare le Condizioni di Dirichlet per la convergenza della trasformata di Fourier
21. Se il segnale aperiodico $x(t)$ è pari, allora la sua trasformata di Fourier è
22. Se il segnale aperiodico $x(t)$ è dispari, allora la sua trasformata di Fourier è
23. Se il segnale aperiodico $x(t)$ è reale e pari, allora la sua trasformata di Fourier è 
24. Se il segnale aperiodico $x(t)$ è reale e dispari, allora la sua trasformata di Fourier è…
25. Se la trasformata di Fourier di $x(t)$ è $X(f)$, allora la trasformata di $x(\alpha t)$ con $|\alpha| >1$ risulta modificata in modo che ...
26. Se la trasformata di Fourier di $x(t)$ è $X(f)$, allora la trasformata di $x(\alpha t)$ con $|\alpha| >1$ risulta modificata in modo che ...
27. In cosa differiscono le trasformate di Fourier di $rect (\frac{t}{T})$ e di $rect (\frac{t-5}{T})$? Spiegare le differenze sia per lo spettro di ampiezza che per lo spettro di fase.
28. In cosa differiscono le trasformate di Fourier di $rect(\frac{t}{T})$ e di $rect(\frac{t}{4T})$? Spiegare le differenze sia per lo spettro di ampiezza che per lo spettro di fase
29. Se $x(t)$ è un segnale complesso e $X(f)$ la sua trasformata di Fourier, quale è la trasformata di Fourier della parte reale di  $x(t$)? Giustificare la risposta
30. Se $x(t)$ è un segnale complesso e $X(f)$ la sua trasformata di Fourier, quale è la trasformata di Fourier della parte immaginaria di $x(t$)? Giustificare la risposta
31. Quale è la trasformata di Fourier di $e ^{-j2 \pi t}$? Giustificare la risposta
32. Se $x(t) \leftrightarrow X(f)$ sono una funzione e la sua trasformata di Fourier, qual è la trasformata di Fourier di $x(-t)$? Giustificare la risposta
33. In cosa differiscono le trasformate di Fourier di $rect(\frac{t}{T})$ e di $rect(\frac{t}{2T})$? Spiegare le differenze sia per lo spettro di ampiezza che per lo spettro di fase.
34. Se il segnale periodico x(t) è reale, quali proprietà hanno rispettivamente lo spettro di ampiezza e lo spettro di fase?
35. Un sistema a tempo continuo si definisce causale se… Fare poi un esempio di sistema causale e uno di sistema non causale.
36. Un sistema a tempo continuo si definisce stabile se 
37. Dato un sistema LTI con risposta impulsiva $h(t) = \delta (t - 1) +\delta (t - 2)$, disegnare l’uscita quando il suo ingresso è il segnale $x(t) = u(t)$
38. La risposta impulsiva di un sistema LTI causale è... 
39. La risposta impulsiva di un sistema LTI causale soddisfa la seguente condizione:
40. Un sistema che produce in uscita il valore assoluto del segnale al suo ingresso è un sistema lineare? Si argomenti la risposta con almeno un esempio.
41. Se un sistema LTI tempo-continuo ha una risposta impulsiva con energia finita, possiamo affermare che il sistema è stabile? Giustificare la risposta.
42. Quale è la risposta in frequenza di un sistema LTI retto dall’equazione differenziale $y(t) - \frac{d^{2}y(t)}{dt^2} = x(t)$?
43. Definire la densità spettrale di potenza di un segnale $x(t)$ a potenza finita. 
44. Un processo aleatorio si definisce stazionario in senso lato se 
45. Elencare le proprietà che definiscono un processo aleatorio stazionario in senso lato (WSS).
46. Enunciare le proprietà che devono essere soddisfatte affinché un processo aleatorio sia stazionario in senso lato

## DIMOSTRAZIONI

1.  Dimostrare che se un segnale periodico è reale, allora i coefficienti della sua espansione in serie di Fourier (nella sua forma complessa) sono caratterizzati da una simmetria Hermitiana.
2.  Enunciare e dimostrare il Teorema di dualità della Trasformata continua di Fourier
3.  Enunciare e dimostrare il Teorema del cambiamento di scala della Trasformata continua di Fourier
4.  Enunciare e dimostrare il Teorema di integrazione completo della Trasformata continua di Fourier
5.  Enunciare e dimostrare il Teorema della moltiplicazione (o prodotto?) della Trasformata continua di Fourier.
6.  Dato un segnale x(t), enunciare e dimostrare la formula somma di Poisson che lega i coeffcienti della serie di Fourier di  $\displaystyle y(t) = \sum_{n = -\infty}^{\infty} x(t - nT)$ alla trasformata (aperiodica) di Fourier di x(t).
7.  Dimostrare che la trasformata di Fourier del prodotto di funzioni $x(t) \cdot y(t)$ è la convoluzione di $X(f)$ con $Y (f)$.
8.  Enunciare e dimostrare il Teorema di Parseval
9.  Enunciare il Teorema di Wiener-Khintchine

\newpage

## RISPOSTE QUESITI

1.  Un segnale deterministico a tempo continuo $s(t)$ periodico ha potenza finita (pari alla potenza media calcolata in un singolo periodo) e energia infinita (somma di infinite aree).
2.  La potenza istantanea di un segnale deterministico a tempo continuo $s(t)$ è definita come $P(t) = |s(t)|^2$.
3.  La potenza media di un segnale deterministico a tempo continuo $s(t)$ è definita come
    $$
    p(t) = \lim_{T\to\infty} \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} s^2(t) \,dt
    $$ 
    dove T è il periodo del segnale.
4.  Per $x(t) = Ae^{-t}u(t),$ l’energia è 
    $$
    E = \int_{0}^{\infty} |Ae^{-t}|^2 dt = A^2 \int_0^\infty e^{-2t} dt = \frac{A^2}{2}
    $$ 
    La potenza media è pari a: 
    $$
    \displaystyle P_t = \lim_{T \to \infty} \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} |x(t)|^2 dt = \lim_{T \to \infty} \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} |A e^{-t} u(t)|^2 dt =  \lim_{T \to \infty} \frac{A^2}{T} \int_{0}^{\frac{T}{2}} e^{-2t} dt = \lim_{T \to \infty} \frac{A^2}{T}*0 = 0
    $$
5.  L’energia del segnale $x(t) = sinc(t)$ è pari ad uno, in quanto utilizzando il teorema di Parseval, $\displaystyle\int_{-\infty}^{+\infty}|x(t)|^2dt = \int_{-\infty}^{+\infty}|X(f)|^2df$, e la trasformata di $sinc(t)$ è pari a $rect(f)$, quindi equivalente ad un rettangolo di altezza e base 1. $\displaystyle E = \int_{-\infty}^\infty (\frac{sin(\pi t)}{( \pi t)})^2 dt = 1.$
6.  Per un segnale sinusoidale di ampiezza 2 e periodo 2 secondi, l’energia è infinita perché il segnale è periodico e la potenza media è $P_m = \frac{1}{2} * (2^2) = 2.$
7.  Per un segnale sinusoidale di ampiezza A e periodo T, l’energia è infinita perché il segnale è periodico e la potenza media è $P_m = \frac{1}{2} * A^2$.
8.  Per un segnale costante, l’energia è infinita perché il segnale è periodico e la potenza media è $P_m = C^2,$ dove C è il valore costante.
9.  Un segnale deterministico a tempo continuo $s(t)$ ha potenza media finita se: $\displaystyle \lim_{s\to\infty} \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} s^2(t)dt < \infty$.
10.  Lo spettro di ampiezza di un segnale tempo-continuo aperiodico reale è una funzione pari. La trasformata di Fourier di un segnale reale gode della proprietà di simmetria Hermitiana $(X(f) = X^*(-f))$: quindi ha componenti simmetriche rispetto all’asse delle ordinate $(R(f)=R(-f); A(f)=|X(f)| \to A(f)=A(-f))$.
11.  Lo spettro di fase di un segnale tempo-continuo aperiodico reale è una funzione dispari. La trasformata di Fourier di un segnale reale gode della proprietà di simmetria Hermitiana $(X(f) = X^*(-f))$: quindi la fase della trasformata di Fourier di un segnale reale è uguale all’opposto della fase della sua componente coniugata. $(I(f)=-I(-f); \Theta(f)=\angle X(f) \to \Theta(f)=-\Theta(-f))$.
12.  $\displaystyle \int_{-\infty}^\infty sinc(t)dt = 1$, in quanto integrale di una funzione $sinc$ normalizzata.
13.  L’onda triangolare, non presentando discontinuità (a differenza del  segnale onda quadra), nella sua ricostruzione del segnale tramite serie di Fourier le componenti ad alta frequenza hanno importanza minore.
14.  L’onda triangolare, non presentando discontinuità, (a differenza del segnale dente di sega), nella sua ricostruzione del segnale tramite serie di Fourier le componenti ad alta frequenza hanno importanza minore.
15.  
    1.  Coefficiente della serie di Fourier è una funzione pari:$X_k = X_{-k}$;
    2.  se il segnale è anche reale: $X_k$ reale e pari $(X_k = X^*_k) \to$ si sviluppa in soli coseni. $\displaystyle x(t)= X_0 + 2 \sum_{k=1}^{\infty} X_k cos (2\pi k f_0 t)$
16.  1.  Coefficiente della serie di Fourier è una funzione dispari:$X_{-k} = -X_{k}$;
    1.  se il segnale è anche reale: $X_k$ immaginaria pura e dispari $(-X_k = X^*_k) \to$ si sviluppa in soli seni. $\displaystyle x(t)= 2j \sum_{k=1}^{\infty} X_k sin (2\pi k f_0 t)$
17.  $\displaystyle x(t)=X_0 + 2\sum_{k=1}^{\infty} X_k cos (2\pi k f_0 t) \to X_k = \frac{2}{T_0} \int_{0}^{\frac{T_0}{2}} x(t) cos (2\pi k f_0 t) dt$
18.  $\displaystyle x(t)= 2j \sum_{k=1}^{\infty} X_k sin (2\pi k f_0 t) \to X_k = -\frac{2j}{T_0} \int_{0}^{\frac{T_0}{2}} x(t) sin (2\pi k f_0 t)dt$
19.  Le Condizioni di Dirichlet per la convergenza della serie di Fourier sono:
    1.  la funzione deve essere assolutamente integrabile sul periodo $T_0$: $\displaystyle \int_{-\frac{T_0}{2}}^{\frac{T_0}{2}} |x(t)| dt < +\infty$
    2.  la funzione deve essere continua o presentare un numero finito di discontinuità di prima specie
    3.  la funzione deve avere un numero finito di massimi e minimi all’interno di un periodo. Oppure $x(t)$ derivabile rispetto al tempo nel periodo $T_0$, esclusi al più un numero finito di discontinuità di prima specie.
20.  Le Condizioni di Dirichlet per la convergenza della trasformata di Fourier sono simili a quelle per la serie di Fourier:
    1.  la funzione deve essere assolutamente sommabile: $\displaystyle \int_{-\infty}^{\infty} |x(t)| dt < +\infty$
    2.  se in qualunque intervallo finito $(t_1, t_2)$ è continua o presenta un numero finito di discontinuità di prima specie
    3.  se in qualunque intervallo finito $(t_1, t_2)$ la funzione ha un numero finito di massimi e minimi.
21.  La trasformata è pari a sua volta.
22.  La trasformata è dispari a sua volta.
23.  Se il segnale aperiodico $x(t)$ è reale e pari, la sua trasformata di Fourier è reale e pari.
24.  Se il segnale aperiodico $x(t)$ è reale e dispari, la sua trasformata di Fourier è immaginaria pura e dispari.
25.  Se la trasformata di Fourier di $x(t)$ è $X(f)$, allora la trasformata di $x(\alpha t)$ con$|\alpha| > 1$ è $\displaystyle \frac{1}{\alpha} X(\frac{f}{\alpha})$. Quindi per il teorema del cambiamento di scala, con una compressione nel tempo abbiamo una dilatazione in frequenza.
26.  Se la trasformata di Fourier di $x(t)$ è $X(f)$, allora la trasformata di $x(\alpha t)$ con$|\alpha| < 1$ è $\displaystyle \frac{1}{|\alpha|} X(\frac{f}{\alpha})$. Quindi per il teorema del cambiamento di scala, con una dilatazione nel tempo abbiamo una compressione in frequenza.
27.  Le trasformate di Fourier di $rect (\frac{t}{T})$ e di $rect (\frac{t-5}{T})$ differiscono solo per la fase. Lo spettro di ampiezza è lo stesso, mentre lo spettro di fase di $rect (\frac{t-5}{T})$ ha una componente lineare aggiuntiva rispetto a $rect (\frac{t}{T})$.
28.  Per il teorema del cambiamento di scala, lo spettro di ampiezza di $rect(\frac{t}{4T})$ viene alterato rispetto a $rect(\frac{t}{T})$, mentre lo spettro di fase non viene alterato. (Dilatazione nel tempo $\leftrightarrow$ Compressione in frequenza)
29.  $\displaystyle R(f) = \int_{- \infty}^{+\infty} x(t) cos(2\pi ft)dt$ Dato che $\displaystyle X(f) = R(f)+ jI(f)$
30.  $\displaystyle I(f) =- \int_{- \infty}^{+\infty} x(t) sin(2\pi ft)dt$ Dato che $\displaystyle X(f) = R(f)+ jI(f)$
31.  La trasformata di Fourier di $e^{-j2\pi t}$ è un impulso di Dirac centrato in $f = 1$. Utilizzando il teorema della traslazione in frequenza: $\to 1*e^{-j2 \pi t} =\Leftrightarrow \delta (f+1)$
32.  Per il teorema del cambiamento di scala: $\displaystyle x(\alpha t) = \frac{1}{|\alpha|} X(\frac{f}{\alpha})$ con $\alpha = -1$, allora: $\to x(-t) \Leftrightarrow X(-f)$
33.  Per il teorema del cambiamento di scala, lo spettro di ampiezza di $rect(\frac{t}{2T})$ viene alterato rispetto a $rect(\frac{t}{T})$, mentre lo spettro di fase non viene alterato. (Dilatazione nel tempo $\leftrightarrow$ Compressione in frequenza)
34.  Se il segnale periodico $x(t) \in \mathbb{R}$, dato che il coefficiente della serie di Fourier $X_k$ gode della simmetria Hermitiana, $X_{-k} =X_k^* = \begin{cases} |X_k| =|X_{-k}| \\ \angle X_k = - \angle X_{-k} \end{cases} \to$ lo spettro di ampiezza è pari e lo spettro di fase è dispari.
35.  Quando il valore dell’uscita al tempo $t$ dipende soltanto dai valori assunti dall’ingresso agli istanti precedenti.  $\to y(t) = T[x(\alpha), \alpha < t, t]$ Un esempio di sistema causale è un filtro passa-basso RC (o un moltiplicatore?), mentre un esempio di sistema non causale è un derivatore.
36.  Quando il sistema, se sollecitato da un segnale con ampiezza limitata, produce in uscita un segnale a sua volta con ampiezza limitata.
37.  Dato un sistema LTI con risposta impulsiva $h(t) = \delta(t - 1) + \delta(t - 2)$, l’uscita quando il suo ingresso è il segnale $x(t) = u(t)$ sarà $y(t) = u(t - 1) + u(t - 2).$
38.  La risposta impulsiva di un sistema LTI causale è un segnale causale $h(t)$ tale che $h(t) = 0$ per $t < 0$.
39.  La risposta impulsiva di un sistema LTI causale soddisfa la condizione $h(t) = 0$ per $t < 0$.
40.  Un sistema che produce in uscita il valore assoluto del segnale (raddrizzatore a doppia onda) al suo ingresso non è un sistema lineare. Ad esempio: se $\displaystyle x(t)=  x_1(t)+x_2(t) \to T[x(t)]  = |x(t)| = |x_1(t)+x_2(t)| \neq y_1(t)+y_2(t) = |x_1(t)|+|x_2(t)|$. Altro esempio: Siano $x_1(t) = t$ e $x_2(t) = -t$: il sistema produce $y_1(t) = |t|$ e $y_2(t) = |-t| = t$. Tuttavia, $y_1(t) + y_2(t) = 2t$, mentre il sistema applicato alla somma dei segnali in ingresso produce $|t - t| = 0$, che non è uguale a$2t$.
41.  Se un sistema LTI tempo-continuo ha una risposta impulsiva con energia finita, possiamo affermare che il sistema è stabile, perché l’energia finita implica che la risposta impulsiva è assolutamente integrabile $\to  \displaystyle \int_{-\infty}^\infty |h(t)| dt < \infty$.
42.  Passando nel dominio della frequenza: $\displaystyle Y(f)(1-(j2\pi f)^2)=X(f)$. Sapendo che $Y(f)=X(f)H(f)$, $\displaystyle H(f)X(f)(1+4\pi^2 f^2)=H(f) \to H(f)=\frac{1}{1+4\pi^2 f^2}$
43.  La densità spettrale di potenza di un segnale $x(t)$ è definita come: $\displaystyle S_x(f) \triangleq \lim_{T \to \infty} \frac{E_{X_T}(f)}{T} = \lim_{T \to \infty} \frac{|X_T(f)|^2}{T}$. Per il teorema di Wiener-Khintchine afferma però che la densità spettrale di potenza$^*$ è uguale alla trasformata di Fourier della funzione di autocorrelazione così modificata:
$$
R_x(\tau) \triangleq  \lim_{T \to \infty} \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}}x(t)x(t-\tau)
$$ La densità spettrale di potenza è: 
\begin{gather*}\displaystyle S_x(f)= \int_{-\infty}^{\infty} R_x(\tau)e^{-j2 \pi f \tau} d\tau = 2\int_{0}^{\infty}  R_x(\tau) cos(2 \pi f \tau) d\tau
\end{gather*}
