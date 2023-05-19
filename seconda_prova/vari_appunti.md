# Varie definizioni probabilità per segnali
### Densità spettrale di energia:
In un segnale $x(t)$ ad **energia finita**: $E_x(f) = |X(f)|^2$: 
    - rappresenta la distribuzione dell'energia del segnale alle diverse frequenze. Rappresenta il _duale_ della potenza istantanea $p_x(t)=|x(t)|^2$.
        - Proprietà:
            1.  $E_x(f) \geq 0$ 
            2. $E_x = \int_{-\infty}^{\infty} E_x(f) df$ 
            3. se $x(t)$ è $\in \mathbb{R}$: $\ E_x(f)=E_x(-f)  \ \to$ è una funzione _pari_
         - Osservazione:
             - Ai fini del calcolo dell'energia di un segnale $x(t)$ risulta determinante il solo **spettro di ampiezza** del segnale stesso, mentre quello di fase risulta essere *ininfluente*. Ciò risulta ancora valido in un sistema SLS "filtrato" da una funzione $h(t)$: per calcolare l'energia del segnale in uscita $y(t)$ è sempre determinante la sola ampiezza del sistema: $E_y(f)=E_x(f)|H(f)|^2$
         
 ### Densità spettrale di potenza:
   In un segnale $x(t)$ a potenza finita: la densità spettrale di potenza è pari alla densità di energia del segnale troncato sull'intervallo di osservazione $\displaystyle(\frac{-T}{2}, \frac{T}{2}) \ \Rightarrow S_x(f) = \lim_{T \to \infty} \frac {E_{x_T}(f)}{T} = \lim_{T \to \infty} \frac {|X_T(f)|^2}{T}$ 
      - Proprietà:
            1.  $S_x(f) \geq 0$ 
            2.  se $x(t)$ è $\in \mathbb{R}$: $\ S_x(f)=S_x(-f)  \ \to$ è una funzione _pari_
            3.  $P_x = \int_{-\infty}^{\infty} S_x(f) df \ \Rightarrow$ $P_x$ potenza del segnale 
            - Osservazione:
                -   Se il segnale $x(t)$ è posto in ingresso ad un SLS con risposta in  frequenza $H(f)$ la densità spettrale di potenza del segnale di uscita $y(t)$ è legata a quella del segnale di ingresso dalla relazione: $S_y(f)=S_x(f)|H(f)|^2$
  
 ### Funzione di autocorrelazione e Teorema di Wiener-Chinčin
 Entrambe le tipologie di densità possono essere calcolate una volta introdotta la:
      - **Funzione di autocorrelazione**: per un segnale ad energia finita $R_x(\tau) = \int_{-\infty}^{\infty} x(t) \ x(t -\tau) dt$
      - Serve a vedere quanto e se due forme d'onda sono simili tra loro. Auto perché è il prodotto del segnale con una sua replica, correlazione perché indica il legame tra le repliche (di cui una ritardata).
      - Fornisce informazioni utili sulla rapidità di variazione del segnale $x(t)$
          - Proprietà
              1. $R_x(0) =\int_{-\infty}^{\infty} x^2(t)dt = E_x$
              2. $|R_x(t)| \leq R_x(0), \ \forall t \neq 0$. Ciò significa che assume il suo massimo in 0, poi decresce
              3. $R_x(\tau) = R_x(-\tau)$  è una funzione _pari_
             
   ####
   Per mettere in releazione la funzione di autocorrelazione con la _densità spettrale di energia_ si introduce il **teorema di Wiener–Chinčin**, il quale afferma che la densità spettrale di energia di un segnale è pari alla trasformata di Fourier della rispettiva funzione di autocorrelazione
$$
\displaystyle E_x(f) = \int_{-\infty}^{\infty} R_x(\tau)e^{-2j\pi f \tau} d\tau = 2 \int_{0}^{\infty} R_x(\tau)cos(2\pi f \tau) d\tau
$$
  Quindi, se il segnale preso in considerazione è a energia finita (e reale)
 $$
   \displaystyle R_x(\tau) = x(\tau) \otimes x(-\tau) \Leftrightarrow X(f)X(-f) = |X(f)|^2 = E_x(f)
 $$
 questo perché essendo $x(t)$ reale, vale la simmetria Hermitiana ($X(f) = X^*(f)$)
 Nel caso invece dei segnali a potenza finita, la definizione di funzione di autocorrelazione diviene $\displaystyle R_x(\tau) = \lim_{T \to \infty} \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} x(t)x(t-\tau) dt$ ed in particolare $R_x(0) = P_x$. Il teorema di W-Krisulta essere nuovamente applicabile e stabilisce l'uguaglianza tra la trasformata di Fourier della funzione di autocorrelazione e la densità spettrale di potenza del segnale $x(t)$:
 $$
 S_x(f) = \int_{-\infty}^{\infty} R_x(\tau)e^{-2j\pi f \tau} d\tau = 2 \int_{0}^{\infty} R_x(\tau)cos(2\pi f \tau) d\tau
$$

Il teorema è importante perché mostra come la densità spettrale di energia/potenza possa essere calcolata con il calcolo della trasformata di Fourier della rispettiva funzione di autocorrelazione, la quale moltè volte è più semplice della definizione diretta.
