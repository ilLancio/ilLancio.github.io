Per gli argomenti trattati in questo capitolo, si segue la presentazione fornita nel Capitolo 4 di [Michael A. Nielsen and Isaac L. Chuang, (2010)](https://www.cambridge.org/highereducation/books/quantum-computation-and-quantum-information/01E10196D0A682A6AEFFEA52D53BE9AE?utm_campaign=shareaholic&utm_medium=copy_link&utm_source=bookmark).

Analogamente al caso classico, anche nell’ambito della computazione quantistica ci si interroga sull’esistenza di un insieme finito di porte logiche quantistiche che possieda la proprietà di completezza funzionale, ovvero tale che ogni operatore unitario (e quindi ogni porta logica quantistica) possa essere realizzato come combinazione circuitale delle porte contenute nell’insieme.
Tuttavia, ciò non è possibile in senso stretto: gli operatori che agiscono su uno spazio di Hilbert a dimensione finita ma su campo complesso formano un insieme non numerabile, mentre le combinazioni finite di elementi di un insieme finito sono numerabili.
Ne consegue che non esiste un insieme finito di porte logiche quantistiche in grado di generare esattamente tutti gli operatori unitari possibili.

La questione viene quindi riformulata in termini più pratici e teoricamente rilevanti:
ci si chiede se esista un insieme finito di porte logiche quantistiche tale che ogni operatore unitario possa essere approssimato con accuratezza arbitraria come combinazione circuitale delle porte che esso contiene.
Tale nozione prende il nome di **completezza funzionale** (o **universalità**) **quantistica**.

In questo capitolo si dimostra che l'insieme $\{\text{Hadamard},\, \pi/8,\, \text{NOT controllato}\}$ è funzionalmente completo.

Per chiarezza espositiva, può essere utile fare riferimento allo schema concettuale riportato in figura \ref{fig:completezza}, che illustra in maniera sintetica i principali passaggi costruttivi attraverso cui è possibile ottenere qualsiasi operatore unitario $U$, a partire dal set universale appena citato.

\begin{figure}[H]
    \centering
    \input{schema/schema.tex}%
    \caption{Schema concettuale di costruzione di qualsiasi porta logica $U$ utilizzando porte Hadamard, $\pi/8$ e NOT controllato. Ogni riquadro rappresenta una porta logica. Le freccie tratteggiate indicano una costruzione approssimata a differenza delle altre.} %fatta eccezione dell'unico stondato sulla destra che indica l'utilizzo di uno specifico teorema.}
    \label{fig:completezza}
\end{figure}

I seguenti risultati sulle porte logiche di rotazione saranno utili in seguito. Per le dimostrazioni, si rimanda al Teorema 4.1 di [Michael A. Nielsen and Isaac L. Chuang, (2010)](https://www.cambridge.org/highereducation/books/quantum-computation-and-quantum-information/01E10196D0A682A6AEFFEA52D53BE9AE?utm_campaign=shareaholic&utm_medium=copy_link&utm_source=bookmark).

**Lemma** (di decomposizione per porte logiche a singolo qubit).
Per ogni $U$ porta logica a singolo qubit, esistono $\alpha, \beta, \gamma, \delta \in \mathbb R$ tali che:
$$
U = e^{i\alpha}R_{\hat z}(\beta)R_{\hat y}(\gamma)R_{\hat z}(\delta)
$$

**Corollario**.
Siano $\hat n$ e $\hat m$ versori in $\mathbb R^3$ non paralleli. Per ogni $U$ porta logica a singolo qubit, esistono $\alpha, \beta, \gamma, \delta \in \mathbb R$ tali che:
$$
U = e^{i\alpha}R_{\hat n}(\beta)R_{\hat m}(\gamma)R_{\hat n}(\delta)
$$

**Corollario**.
Per ogni $U$ porta logica a singolo qubit, esistono $A, B, C$ porte logiche a singolo qubit tali che:
$$
ABC = \mathit{I} \quad \land \quad U = e^{i\alpha}A \sigma_1 B \sigma_1 C
$$
dove $\alpha \in \mathbb R$.

## Approssimazione di porte logiche

**Definizione** (Approssimazione di porte logiche).
Un insieme $A$ di porte logiche si dice *approssimabile* da un insieme $B$ di porte logiche se $\forall \varepsilon \in \mathbb R_{>0}$ e $\forall U \in A$ a $n$ qubit $\exists V$ circuito quantistico di sole porte logiche di $B$ tale che:
$$
E(U, V) := \sup_{\ket\lambda} \sup_{\ket\Psi} |P_U(\lambda, \Psi) - P_V(\lambda, \Psi)| < \varepsilon
$$
dove $\ket\Psi$ è uno stato di un sistema di $n$ qubit[^1] e $\ket\lambda$ un autostato appartenente alla base computazionale, il cui autovalore corrispondente $\lambda$, negli stati $U\ket\Psi$ e $V\ket\Psi$, ha probabilità di essere misurato[^2] rispettivamente $P_U(\lambda, \Psi)$ e $P_V(\lambda, \Psi)$.

**Definizione** (Completezza funzionale quantistica).
Un insieme $C$ di porte logiche quantistiche si dice *funzionalmente completo* se l'insieme di tutte le porte logiche è approssimabile da $C$.

**Definizione** (Norma operatoriale).
Sia $A$ un'operatore lineare che opera sullo spazio di Hilbert $\mathcal{H}$. La *norma* di $A$ è:
$$
\|A\|_\text{op} := \sup_{\ket\Psi}\|A \ket\Psi\|
$$
dove $\ket\Psi \in \mathcal{H}$ è normalizzato.

**Definizione** (Distanza tra operatori).
Siano $A$ e $B$ operatori lineari su uno spazio di Hilbert $\mathcal{H}$. La *distanza* tra $A$ e $B$ è la distanza indotta dalla norma operatoriale:
$$
d(A, B) := \|A - B\|_\text{op}
$$

**Lemma**.
Siano $U$ e $V$ porte logiche a $n$ qubit. Allora:
\begin{equation}
    E(U, V) \le 2d(U, V)
    \label{eq:thm-distanza-1}
\end{equation}
e inoltre, se $U = U_m U_{m-1} \cdots U_1$ e $V = V_m V_{m-1} \cdots V_1$ sono sequenze di $m$ porte logiche a $n$ qubit:
\begin{equation}
    d(U, V) \le \sum_{i=1}^{m} d(U_i, V_i)
    \label{eq:thm-distanza-2}
\end{equation}

*Dimostrazione*.
Siano $P_U$ e $P_V$ le probabilità introdotte nella definizione \ref{def:approssimazione} e $\ket\lambda$ e $\ket\Psi$ gli stati normalizzati tali che $E(U, V) = |P_U(\lambda, \Psi) - P_V(\lambda, \Psi)|$. Secondo il postulato della regola di Born, tali probabilità sono esprimibili come:
\begin{align*}
    P_U - P_V 
    &= |\braket{\lambda|U|\Psi}|^2 - |\braket{\lambda|V|\Psi}|^2 \\
    &= \braket{\Psi|U^\dagger|\lambda} \braket{\lambda|U|\Psi} - \braket{\Psi|V^\dagger|\lambda} \braket{\lambda|V|\Psi}
\end{align*}
Aggiungendo e sottraendo lo stesso termine $\braket{\Psi|U^\dagger|\lambda}\braket{\lambda|V|\Psi}$ e fattorizzando, si ottiene:
\begin{align*}
    P_U - P_V
    &= \braket{\Psi|U^\dagger|\lambda} ( \braket{\lambda|U|\Psi} - \braket{\lambda|V|\Psi} ) + (\braket{\Psi|U^\dagger|\lambda} - \braket{\Psi|V^\dagger|\lambda}) \braket{\lambda|V|\Psi} \\
    &= \braket{\Psi|U^\dagger|\lambda}\braket{\lambda|U-V|\Psi} + \braket{\Psi|(U-V)^\dagger|\lambda}\braket{\lambda|V|\Psi}
\end{align*}
Applicando prima la disuguaglianza triangolare e dopo la disuguaglianza di Cauchy-Schwarz e poiché i fattori $|\braket{\Psi|U^\dagger|\lambda}|$ e $|\braket{\lambda|V|\Psi}|$ sono entrambi minori o uguali ad 1, si ha:
\begin{align*}
    |P_U - P_V|
    &\le |\braket{\Psi|U^\dagger|\lambda}\braket{\lambda|U-V|\Psi}| + |\braket{\Psi|(U-V)^\dagger|\lambda}\braket{\lambda|V|\Psi}| \\
    &\le \|(U - V)\ket\Psi\| + \|(U - V)\ket\Psi\| \\
    &\le 2d(U, V)
\end{align*}
L'espressione \eqref{eq:thm-distanza-1} è così dimostrata.

Siano ora $U = U_2 U_1$ e $V = V_2 V_1$ sequenze di 2 porte logiche a $n$ qubit. Per almeno uno stato $\ket\Psi$ si ha:
$$d(U_2 U_1, V_2 V_1) = \|(U_2 U_1 - V_2 V_1) \ket\Psi\|$$
Aggiungendo e sottraendo lo stesso termine $V_2 U_1 \ket\Psi$ e fattorizzando si ottiene:
$$d(U_2 U_1, V_2 V_1) = \|(U_2 U_1 - V_2 U_1) \ket\Psi + (V_2 U_1 - V_2 V_1) \ket\Psi\|$$
Applicando la disuguaglianza triangolare e la definizione di distanza tra porte logiche, poiché le norme sono invarianti sotto operatori unitari, si ha:
\begin{align*}
    d(U_2 U_1, V_2 V_1)
    &\le \|(U_2 - V_2) U_1 \ket\Psi\| + \|V_2 (U_1 - V_1) \ket\Psi\| \\
    &\le d(U_2, V_2) + d(U_1, V_1)
\end{align*}
La dimostrazione dell'espressione \eqref{eq:thm-distanza-2}, per sequenze di un generico numero $m$ di porte logiche a $n$ qubit, segue per induzione.

**Teorema**.
Tutte le porte logiche a singolo qubit sono approssimabili dalle porte Hadamard e $\pi/8$.

*Dimostrazione*.
Si consideri che:
$$T \cdot HTH = R_{\hat z}(\pi/4) \cdot R_{\hat x}(\pi/4)$$
Ciò è evidente essendo $T = R_{\hat z}(\pi/4)$ e, poiché $H\sigma_3H = \sigma_1$:
$$HTH = HR_{\hat z}(\pi/4)H = H e^{-\frac{i \pi}{8} \sigma_3} H = e^{-\frac{i \pi}{8} H\sigma_3H} = R_{\hat x}(\pi/4)$$
Poiché $\sigma_3 \sigma_1 = i\sigma_2$, segue che:
\begin{align*}
    T \cdot HTH
    &= \cos^2\left(\frac{\pi}{8}\right)I -i \sin\left(\frac{\pi}{8}\right) \left[ \cos\left(\frac{\pi}{8}\right)\sigma_1 + \sin\left(\frac{\pi}{8}\right)\sigma_2 + \cos\left(\frac{\pi}{8}\right)\sigma_3 \right] \\
    &= \cos\left( \frac{\theta}{2} \right) I - i \sin\left( \frac{\theta}{2} \right) (\hat n \cdot \vec \sigma) = R_{\hat n}(\theta)
\end{align*}
dove il versore $\hat n$ e l'angolo $\theta$ sono definiti come segue:
$$
\vec n := \left(\cos\frac{\pi}{8}, \sin\frac{\pi}{8}, \cos\frac{\pi}{8}\right) \implies 
\hat n = \frac{\vec n}{\|\vec n\|} = \frac{\vec n}{\sqrt{1 + \cos^2\left(\frac{\pi}{8}\right)}}
$$
\begin{align*}
    \cos\left(\frac{\theta}{2}\right) := \cos^2\left(\frac{\pi}{8}\right) \implies \sin\left(\frac{\theta}{2}\right)
    &= \sqrt{1 - \cos^2\left(\frac{\theta}{2}\right)} = \sqrt{1 - \cos^4\left(\frac{\pi}{8}\right)} \\
    &= \sin\left(\frac{\pi}{8}\right)\sqrt{1 + \cos^2\left(\frac{\pi}{8}\right)}
\end{align*}
L'angolo $\theta$ così definito è un multiplo irrazionale di $2\pi$, ovvero tale che:
$$
\frac{\theta}{2\pi} \in \mathbb R / \mathbb Q
$$
Per la dimostrazione, si rimanda a \cite{boykin1999universalfaulttolerantquantumcomputing}.

Da ciò e dal \emph{teorema del ritorno di Poincaré}, per il quale si rimanda a \citep[Capitolo 3]{arnold1989mathematical}, consegue che l'immagine $\{a_n\}_{n \in \mathbb N}$ della successione $a_n = (n\theta) \bmod 2\pi$ è un insieme \emph{denso} in $\mathbb R$, ovvero:
$$
\forall \alpha \in \mathbb R \, \forall \delta \in \mathbb R_{>0} \, \exists n \in \mathbb N : \quad |n\theta - \alpha| \bmod 2\pi < \delta
$$
\begin{figure}[H]
    \centering
    \includegraphics[scale=0.45]{denso.pdf}
    \caption{Successione $a_n = (n\theta) \bmod 2\pi$ con $\theta$ tale che $\cos(\theta/2) = \cos^2(\pi/8)$.}
    \label{fig:denso}
\end{figure}

Fissato ora un versore $\hat m \in \mathbb R^3$, si ha per ogni $\alpha, \beta \in \mathbb R$ quanto segue:
$$
R_{\hat m}(\alpha) - R_{\hat m}(\alpha + \beta) = e^{-\frac{i}{2} \alpha \hat m \cdot \vec\sigma} - e^{-\frac{i}{2} (\alpha + \beta) \hat m \cdot \vec\sigma} = R_{\hat m}(\alpha) \left[I - R_{\hat m}(\beta)\right]
$$
Essendo le rotazioni operatori unitari, $R_{\hat m}(\alpha)$ conserva la norma, pertanto:
$$
\| \left[R_{\hat m}(\alpha) - R_{\hat m}(\alpha + \beta)\right] \ket{\Psi} \| = \left\| \left(I - e^{-\frac{i}{2} \beta \hat m \cdot \vec\sigma} \right) \ket\Psi \right\|
$$
Poiché $(\hat m \cdot \vec \sigma)^2 = I$, gli autovalori di $\hat m \cdot \vec \sigma$ sono $\pm 1$, dunque lo spettro di $I - e^{-\frac{i}{2} \beta \hat m \cdot \vec\sigma}$ è $\{1 - e^{\pm \frac{i}{2} \beta}\}$. Ne consegue che
\begin{align*}
    d(R_{\hat m}(\alpha), R_{\hat m}(\alpha + \beta))
    &= \sup_{\|\Psi\| = 1}\|(R_{\hat m}(\alpha) - R_{\hat m}(\alpha + \beta))\ket\Psi\| \\
    &= \max(|1 - e^{-\frac{i}{2} \beta}|, |1 - e^{\frac{i}{2} \beta}|)
    = |1 - e^{\frac{i}{2} \beta}|
\end{align*}

Considerando che $R_{\hat m}^n(\theta) = R_{\hat m}(n\theta)$  $\forall n \in \mathbb N$, dalla continuità della funzione $\beta \mapsto |1 - e^{\frac{i}{2}\beta}|$ segue per definizione che:
$$
\forall \alpha \in \mathbb R \, \forall \varepsilon \in \mathbb R_{>0} \, \exists \delta \in \mathbb R_{>0} :
$$
$$
|n\theta - \alpha| \bmod 2\pi < \delta \implies d(R_{\hat m}(\alpha), R_{\hat m}^n(\theta)) < \varepsilon
$$
Unendo questo risultato a quello di densità si ottiene:
$$
\forall \alpha \in \mathbb R \, \forall \varepsilon \in \mathbb R_{>0} \, \exists n \in \mathbb N : \quad d(R_{\hat m}(\alpha), R_{\hat m}^n(\theta)) < \varepsilon
$$

Ricordando le relazioni $H\sigma_1H = \sigma_3$, $H\sigma_2H = -\sigma_2$, $H\sigma_3H = \sigma_1$, è semplice dedurre che:
$$
H R_{\hat n}(\alpha) H = R_{\hat m}(\alpha)
$$
dove, se $\hat n = (n_x, n_y, n_z)$, allora $\hat m = (n_x, -n_y, n_z)$. In particolare $\hat n$ e $\hat m$ non sono paralleli perché $n_y = \frac{\sin (\pi/8)}{\sqrt{1 + \cos^2 (\pi/8)}} \neq 0$.

Siano $U$ una qualsiasi porta logica a singolo qubit, esprimibile come segue secondo il corollario \ref{thm:decomposizione-2}, e $V$ la seguente porta logica composta da sole porte Hadamard e $\pi/8$:
\begin{align*}
    U = e^{i\alpha}R_{\hat n}(\beta)R_{\hat m}(\gamma)R_{\hat n}(\delta), \quad
    V
    &= R_{\hat n}^{n_1}(\theta) H R_{\hat n}^{n_2}(\theta) H R_{\hat n}^{n_3}(\theta) \\
    &= (THTH)^{n_1} H (THTH)^{n_2} H (THTH)^{n_3}
\end{align*}
Utilizzando la disequazione \eqref{eq:thm-distanza-2} del teorema \ref{thm:distanza} e considerando che, stando alla definizione \ref{def:approssimazione}, $E(U, V) = E(U/e^{i\alpha}, V)$, segue l'approssimabilità da dimostrare.
$$
\forall U_\text{singolo} \, \forall \varepsilon \in \mathbb R_{>0} \, \exists n_1, n_2, n_3 \in \mathbb N : \quad E(U, V) \le 2d(U/e^{i\alpha}, V) < \varepsilon
$$

[^1] Nel caso in cui il circuito $V$ sia ad un numero di qubit $m > n$, la sua applicazione allo stato $\ket\Psi$ è intesa come l'applicazione di $V$ su uno stato esteso ad uno sistema di $m$ qubit, e che il confronto tra $P_U$ e $P_V$ avviene considerando le probabilità di misura sui soli $n$ qubit logici, trascurando quelli ausiliari.

[^2] La misura coinvolge tutti i qubit, in quanto si considera l’osservabile globale $\hat{S}^{\otimes n}$, il cui insieme di autostati ortonormali corrisponde alla base computazionale.

## Costruzione di porte controllate

La porta Toffoli è realizzabile con una composizione di sole porte a singolo qubit e porte CNOT. La dimostrazione per costruzione è data dal seguente circuito.

\begin{figure}[H]
    \centering
    \begin{quantikz}[column sep=0.5em, row sep=2.3em]
        \lstick{} & \ctrl{2} & \rstick{} \\
        \lstick{} & \ctrl{0} & \rstick{} \\
        \lstick{} & \targ{} & \rstick{}
    \end{quantikz}
    =
    \begin{quantikz}[column sep=0.7em]
        \lstick{} &          &          &                  & \ctrl{2} &          &          &                  & \ctrl{2} &                  & \ctrl{1} &                  & \ctrl{1} & \gate{T} & \rstick{} \\
        \lstick{} &          & \ctrl{1} &                  &          &          & \ctrl{1} &                  &          & \gate{T^\dagger} & \targ{}  & \gate{T^\dagger} & \targ{}  & \gate{S} & \rstick{} \\
        \lstick{} & \gate{H} & \targ{}  & \gate{T^\dagger} & \targ{}  & \gate{T} & \targ{}  & \gate{T^\dagger} & \targ{}  & \gate{T}         & \gate{H} &                  &          &          & \rstick{}
    \end{quantikz}
    %\caption{Realizzazione di una porta Toffoli con porte a singolo qubit e CNOT.}
    \label{fig:costruzione-toffoli}
\end{figure}

\def\cPhaseShift{\begin{pmatrix} 1 & 0 \\ 0 & e^{i\alpha} \end{pmatrix}}

Sia $U$ una porta a singolo qubit. L'operazione controllata $C(U)$ è realizzabile con una composizione di sole porte a singolo qubit e porte CNOT. Infatti, come assicura il corollario \ref{thm:decomposizione-3}, esistono $\alpha \in \mathbb R$ e $A, B, C$ porte logiche a singolo qubit tali che $U = e^{i\alpha}A \sigma_1 B \sigma_1 C$, che permettono la costruzione del seguente circuito equivalente alla porta controllata $C(U)$.
\begin{figure}[H]
    \centering
    \begin{quantikz}[column sep=1em, row sep={3.75em,between origins}, baseline=(current bounding box.center)]
        \lstick{} & \ctrl{1} & \rstick{} \\
        \lstick{} & \gate{U} & \rstick{}
    \end{quantikz}
    =
    \begin{quantikz}[baseline=(current bounding box.center)]
        \lstick{} &          & \ctrl{1} &          & \ctrl{1} & \gate{\cPhaseShift} & \rstick{} \\
        \lstick{} & \gate{C} & \targ{}  & \gate{B} & \targ{}  & \gate{A}            & \rstick{}\\
    \end{quantikz}
    %\caption{$U = e^{i\alpha}A \sigma_1 B \sigma_1 C$}
    \label{fig:costruzione-controlled-u}
\end{figure}
L'uguaglianza è evidente calcolando esplicitamente l'operatore matriciale rappresentato dal circuito:
\begin{align*}
    &\left[ \begin{pmatrix} 1 & 0 \\ 0 & e^{i\alpha} \end{pmatrix} \otimes A \right]
    \cdot \text{CNOT} \cdot (I \otimes B) \cdot \text{CNOT} \cdot (I \otimes C) \\
    &=
    \begin{pmatrix}
        A & 0 \\
        0 & e^{i\alpha} A
    \end{pmatrix}
    \begin{pmatrix}
        B & 0 \\
        0 & \sigma_1 B
    \end{pmatrix}
    \begin{pmatrix}
        C & 0 \\
        0 & \sigma_1 C
    \end{pmatrix} \\
    &=
    \begin{pmatrix}
        ABC & 0 \\
        0 & e^{i\alpha} A \sigma_1 B \sigma_1 C
    \end{pmatrix}
    = \begin{pmatrix}
        I & 0 \\
        0 & U
    \end{pmatrix}
    = C(U)
\end{align*}

Sia $U$ una porta a singolo qubit. L'operazione controllata $C^n(U)$ è realizzabile, come mostrato dal circuito seguente, con una composizione di sole porte Toffoli e della porta $C(U)$, sfruttando $n-1$ qubit ausiliari inizializzati a $\ket 0$, detti \emph{qubit di lavoro} (o \emph{qubit ancilla}). L'equivalenza è evidente se si considerano le tavole di verità di queste porte e quindi di come ogni porta che compone il circuito trasformi sequenzialmente gli stati della base computazionale.
\begin{figure}[H]
    \centering
    \hspace{0.5cm} % sposta verso destra
    \resizebox{0.9\textwidth}{!}{
    \begin{quantikz}[column sep=1em, baseline=(current bounding box.center)]
        \lstick{$c_1$} & \ctrl{4}  & \rstick{} \\
        \lstick{$c_2$} & \ctrl{0}  & \rstick{} \\
        \lstick{$c_3$} & \ctrl{0}  & \rstick{} \\
        \lstick{$c_4$} & \ctrl{0}  & \rstick{} \\
                       & \ \vdots\ &           \\
        \lstick{$t$}   & \gate{U}  & \rstick{}
    \end{quantikz}
    \ \ \ =\ \ \ 
    \begin{quantikz}[baseline=(current bounding box.center)]
        \lstick{$c_1$}    & \ctrl{5} &          &          &           &          &          & \ctrl{5} & \rstick[4]{$n$ controllo} \\
        \lstick{$c_2$}    & \ctrl{0} &          &          &           &          &          & \ctrl{0} & \rstick{} \\
        \lstick{$c_3$}    &          & \ctrl{4} &          &           &          & \ctrl{4} &          & \rstick{} \\
        \lstick{$c_4$}    &          &          & \ctrl{4} &           & \ctrl{4} &          &          & \rstick{} \\
                          &          &          &          & \ \vdots\ &          &          &          &           \\
        \lstick{$\ket 0$} & \targ{}  & \ctrl{0} &          &           &          & \ctrl{0} & \targ{}  & \rstick[3]{$n-1$ lavoro} \\
        \lstick{$\ket 0$} &          & \targ{}  & \ctrl{0} &           & \ctrl{0} & \targ{}  &          & \rstick{} \\
        \lstick{$\ket 0$} &          &          & \targ{}  & \ctrl{1}  & \targ{}  &          &          & \rstick{} \\
        \lstick{$t$}      &          &          &          & \gate{U}  &          &          &          & \rstick{target}
    \end{quantikz}}
    %\caption{}
    \label{fig:costruzione-controlled-u-singolo}
\end{figure}

## Porte logiche a due livelli

**Definizione** (Operatore a due livelli).
Sia $A$ un operatore agente sullo spazio di Hilbert a dimensione finita $\mathcal H$. L'operatore $A$ si dice \emph{a due livelli} se esiste un sottospazio $\mathcal V \subseteq \mathcal H$ al più a 2 dimensioni tale che:
$$
\forall \ket{\Psi} \in \mathcal V^\perp,\quad A \ket{\Psi} = \ket{\Psi}
$$
dove $\mathcal V^\perp$ è il sottospazio di $\mathcal H$ ortogonale a $\mathcal V$.

**Teorema**.
Per ogni $U$ porta logica a $n$ qubit a due livelli, esiste un circuito equivalente ad $U$ composto da sole porte $C^{n-1}(\sigma_1)$ e una porta $C^{n-1}(\tilde U)$, dove $\tilde U$ è la porta logica a singolo qubit che definisce l'azione di $U$ nel sottospazio bidimensionale su cui $U$ agisce non banalmente.

*Dimostrazione*.
Sia $\ket\Psi$ un generico stato di $n$ qubit.
$$
\ket\Psi = \sum_{k = 0}^{2^n - 1} \alpha_k \ket k = \alpha_0 \ket{0 \cdots 00} + \alpha_1 \ket{0 \cdots 01} + \cdots + \alpha_{2^n - 1} \ket{1 \cdots 11}
$$
dove $\alpha_k \in \mathbb C$ e $\ket k$ sono gli elementi della base computazionale, quindi $k$ indica il codice binario associato secondo la nomenclatura utilizzata.

La porta logica a due livelli $U$ opera non banalmente sui soli vettori di un sottospazio $\mathcal V$ generato da al massimo due vettori di base $\ket i$ e $\ket j$.
$$
\mathcal V = \mathrm{span} \{ \ket i, \ket j \}, \quad U \ket\Psi = \beta_i \ket i + \beta_j \ket j + \sum_{k \ne i,j} \alpha_k \ket k
$$
dove $\beta_i, \beta_j \in \mathbb C$ e definiscono la porta a singolo qubit $\tilde U$ come:
$$
\tilde U
\begin{pmatrix}
    \alpha_i \\
    \alpha_j
\end{pmatrix}
=
\begin{pmatrix}
    \beta_i \\
    \beta_j
\end{pmatrix}
$$

**Definizione** (Codice Gray).
Siano $i$ e $j$ due codici binari diversi ed entrambi ad $n$ cifre. Un \emph{codice Gray} da $i$ a $j$ è una sequenza finita di codici binari ad $n$ cifre dove il primo è $i$, l'ultimo è $j$ e i codici adiacenti differiscono per esattamente una cifra.

L'implementazione di $U$ avviene tramite l'utilizzo dei \emph{codici Gray} appena definiti ed è suddivisa nei tre seguenti punti:
\begin{enumerate}
    \item Applicazione sequenziale di $m$ porte controllate $C_1 = C_1^n(\sigma_1), \cdots, C_m = C_m^n(\sigma_1)$, in modo da implementare un circuito che trasformi soltanto il vettore di base $\ket i$ in $\ket{g_m}$, dove $g_m$ è il penultimo elemento del codice Gray da $i$ a $j$:
    $$
    i, g_1, g_2, \cdots, g_m, j \quad\quad\quad
    C_m \cdots C_1 \ket{i} = C_m \cdots C_2 \ket{g_1} = \cdots = \ket{g_m}
    $$
    con $m \in [0, n-1] \cap \mathbb N$.
    \item Applicazione di una porta controllata $C^{n-1}(\tilde U)$, con qubit target nella posizione dell'unica cifra diversa tra gli ultimi due elementi del codice Gray, e con qubit di controllo che limitino la trasformazione ai soli vettori di base rappresentati dal codice le cui restanti cifre siano del valore di quelle dell'ultimo codice $j$.
    \item Applicazione in ordine inverso delle porte $C_1, \cdots, C_m$ utilizzate al primo punto.
\end{enumerate}

**Esempio**.
Sia $U$ la seguente porta logica a due livelli e $\tilde U$ la relativa porta logica a singolo qubit che definisce l'azione di $U$ nel sottospazio bidimensionale su cui $U$ agisce non banalmente.
$$
U =
\scalebox{0.5}{$
\begin{pmatrix}
    a & 0 & 0 & 0 & 0 & 0 & 0 & b \\
    0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\
    0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\
    0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
    0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\
    0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
    0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\
    c & 0 & 0 & 0 & 0 & 0 & 0 & d
\end{pmatrix}$}
\quad\quad
\tilde U =
\begin{pmatrix}
    a & b \\
    c & d
\end{pmatrix}
$$
In questo caso i vettori di base su cui $U$ agisce non banalmente sono $\ket i = \ket{000}$ e $\ket j = \ket{111}$, di cui un codice Gray e, di conseguenza, un circuito che implementa $U$ sono:
\begin{center}
    %\vspace{-0.7cm}
    \begin{minipage}{4cm}
        \begin{align*}
            i &= 000 \\
            g_1 &= 001 \\
            g_2 &= 011 \\
            j &= 111
        \end{align*}
\end{minipage}
%\hspace{0.5cm}
\begin{minipage}{6cm}
    \begin{figure}[H]
        \centering
        \begin{quantikz}
            \lstick{}    & \octrl{2} & \octrl{2} & \gate{\tilde U}  & \octrl{2} & \octrl{2} & \rstick{} \\
            \lstick{}    & \octrl{0} & \targ{}   & \ctrl{0}  & \targ{}   & \octrl{0} & \rstick{} \\
            \lstick{}    & \targ{}   & \ctrl{0}  & \ctrl{-2} & \ctrl{0}  & \targ{}   & \rstick{}
        \end{quantikz}
        %\caption{}
        %\label{fig:}
    \end{figure}
\end{minipage}
\end{center}

**Teorema**.
Per ogni $U$ operatore unitario che opera su uno spazio di Hilbert $\mathcal H$ di dimensione $n$, esistono $n$ operatori su $\mathcal H$ unitari a due livelli $U_1, \cdots, U_n$ tali che:
$$
U = U_1 \cdots U_n
$$

*Dimostrazione*.
La seguente è una dimostrazione per costruzione del caso di operatori rappresentati da matrici in $\mathbb C^{3\times3}$, generalizzabile al caso di operatori agenti su spazi di Hilbert $n$-dimensionali.
Abbia quindi $U$ la seguente rappresentazione matriciale:
$$
U =
\begin{pmatrix}
    a & d & g \\
    b & e & h \\
    c & f & j 
\end{pmatrix}
$$
Siano definite di conseguenza le matrici $U_1, U_2, U_3$ come segue\footnote{Si denota con $a^*$ il complesso coniugato di $a \in \mathbb C$.}:
\begin{align*}
    U_1 &=
    \begin{cases}
        \quad\quad I \vphantom{
            \scalebox{0.7}{$
            \begin{pmatrix}
                a^* & b^* & g \\
                b   & -a  & h \\
                c   & f   & \lambda
            \end{pmatrix}$}
        }
        & \text{se } b = 0 \\
        \scalebox{0.7}{$
        \begin{pmatrix}
            a^* & b^* & g \\
            b   & -a  & h \\
            c   & f   & \lambda
        \end{pmatrix}$}
        \cdot
        \dfrac{1}{\lambda}
        & \text{se } b \neq 0
    \end{cases}
    \quad\quad\implies\quad\quad
    U_1 U =
    \begin{pmatrix}
        a' & d' & g' \\
        0  & e' & h' \\
        c' & f' & j' 
    \end{pmatrix}
    \\[15pt]
    U_2 &=
    \begin{cases}
        \scalebox{0.7}{$
        \begin{pmatrix}
            a'^* & 0 & 0 \\
            0    & 1 & 0 \\
            0    & 0 & 1
        \end{pmatrix}$}
        & \text{se } c' = 0 \\[15pt]
        \scalebox{0.7}{$
        \begin{pmatrix}
            a'^* & 0        & c'^* \\
            0    & \lambda'  & 0    \\
            c'   & 0        & -a'
        \end{pmatrix}$}
        \cdot
        \dfrac{1}{\lambda'}
        & \text{se } c' \neq 0
    \end{cases}
    \quad\implies\quad
    U_2 U_1 U =
    \begin{pmatrix}
        1 & d'' & g'' \\
        0 & e'' & h'' \\
        0 & f'' & j''
    \end{pmatrix}
    \\[15pt]
    U_3 &=
    \begin{pmatrix}
        1 & 0     & 0     \\
        0 & e''^* & f''^* \\
        0 & h''^* & j''^*
    \end{pmatrix}
    \quad\quad\quad
    \parbox{0.6\textwidth}{
        dove gli apici definiscono le componenti delle matrici risultanti e
        $$
        \lambda = \sqrt{|a|^2 + |b|^2}, \quad \lambda' = \sqrt{|a'|^2 + |b'|^2}
        $$
    }
\end{align*}
Moltiplicando tra loro le matrici così definite ed essendo la trasposta coniugata di una matrice unitaria a due livelli ancora una matrice unitaria a due livelli, per definizione di operatore unitario, si ottiene la tesi.
$$
U_3 U_2 U_1 U = I \implies U = U_1^{-1} U_2^{-1} U_3^{-1} = U_1^\dagger U_2^\dagger U_3^\dagger
$$

## Bibliografia

- [P. Oscar Boykin, Tal Mor, Matthew Pulver, Vwani Roychowdhury, and Farrokh Vatan. On universal and fault-tolerant quantum computing, 1999.](http://arxiv.org/abs/quant-ph/9906054v1)
- [Michael A. Nielsen and Isaac L. Chuang. *Quantum Computation and Quantum Information: 10th Anniversary Edition*. Cambridge University Press, Cambridge, 2010.](https://www.cambridge.org/highereducation/books/quantum-computation-and-quantum-information/01E10196D0A682A6AEFFEA52D53BE9AE?utm_campaign=shareaholic&utm_medium=copy_link&utm_source=bookmark)