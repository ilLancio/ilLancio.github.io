**Definizione** (Qubit).
Un *qubit* è un sistema fisico il cui spazio di Hilbert è di dimensione due[^1].

Un esempio di qubit è quello di un qualsiasi fermione di *spin* 1/2.

**Definizione** (Computer quantistico).
Un *Computer Quantistico* è un sistema fisico di $n$ *qubit* unito ad una sequenza di [[Porte Logiche|*porte logiche*]] agenti sul suo stato.

**Definizione** (Base computazionale).
Sia $\hat S$ un'osservabile di singolo qubit e $\left\{ \ket 0, \ket 1 \right\}$ una base ortonormale di autovettori di $\hat S$. Si dice *base computazionale* di un sistema di $n$ qubit la base, di cardinalità $2^n$, dello spazio di Hilbert, isomorfo a $(\mathbb C^2)^{\otimes n}$, del sistema:
$$
\left\{ \ket{0 \cdots 00}, \ket{0 \cdots 01}, \ket{0 \cdots 10}, \cdots, \ket{1 \cdots 11} \right\}
$$

In tutta la trattazione si considererà fissata l'osservabile $\hat S$ di singolo qubit a cui farà riferimento ogni misura. Ogni stato $\ket0$ o $\ket1$ sarà relativo alla base computazionale da essa definita, così come ogni rappresentazione matriciale degli operatori lineari.
Inoltre con l'espressione "*misurare 0 o 1*" verrà inteso "*misurare l'autovalore corrispondente a $\ket0$ o a $\ket1$*".
L'espressione "*misurare l'$i$-esimo qubit*" starà quindi ad indicare l'operazione di misura, sull'intero sistema, dell'osservabile:
$$
I^{\otimes (i-1)} \otimes \hat S \otimes I^{\otimes (n - i)}
$$

Lo stato $\ket\Psi$ di un sistema di $n$ qubit è pertanto definito da una combinazione lineare dei vettori di base:
$$
\ket\Psi = \alpha_0 \ket{0 \cdots 00} + \alpha_1 \ket{0 \cdots 01} + \alpha_2 \ket{0 \cdots 10} + \cdots + \alpha_{2^n - 1} \ket{1 \cdots 11}
$$
dove $\alpha_i \in \mathbb C, \, \forall i \in \left[0, 2^n-1\right] \cap \mathbb N$.

**Esempio** (Singolo qubit).
Lo stato di un singolo qubit è quindi definito da una combinazione lineare dei vettori della base $\left\{ \ket 0, \ket 1 \right\}$:
$$
\ket\Psi = \alpha \ket 0 + \beta \ket 1
$$
dove $\alpha, \beta \in \mathbb C$.

In caso di vettore normalizzato, è semplice verificare che le probabilità che la misura sia 0 piuttosto che 1, quindi le probabilità che lo stato collassi nell'autostato $\ket 0$ piuttosto che $\ket 1$, sono date dal modulo quadro dei coefficienti della combinazione lineare $|\alpha|^2$, $|\beta|^2$.

**Esempio** (Due qubit).
Lo stato di un sistema di due qubit è invece definito dalla base $\left\{ \ket{00}, \ket{01}, \ket{10}, \ket{11} \right\}$:
$$
\ket\Psi = \alpha \ket{00} + \beta \ket{01} + \gamma \ket{10} + \delta \ket{11}
$$
dove $\alpha, \beta, \gamma, \delta \in \mathbb C$.

In questo caso, se il vettore è normalizzato, misurare uno dei due qubit, ad esempio il primo, equivale a misurare l'osservabile $\hat S \otimes I$, i cui autostati sono:
$$
\ket{\lambda_0} = \alpha \ket{00} + \beta \ket{01}, \quad
\ket{\lambda_1} = \gamma \ket{10} + \delta \ket{11}
$$
Quindi le probabilità di misurare 0 piuttosto che 1, o le probabilità che lo stato collassi in $\ket{\lambda_0}$ piuttosto che in $\ket{\lambda_1}$, sono:
$$
P(0) = |\alpha|^2 + |\beta|^2, \quad
P(1) = |\gamma|^2 + |\delta|^2
$$

**Definizione** (Sfera di Bloch).
Viene detta *sfera di Bloch* la superficie sferica di raggio 1 in coordinate sferiche:
\begin{center}
    \begin{minipage}{5.5cm}
    $$
    \left\{
    \begin{aligned}
        x &= \sin\theta \cos\varphi \\
        y &= \sin\theta \sin\varphi \\
        z &= \cos\theta
    \end{aligned}
    \right.
    \quad
    \begin{aligned}
        0 \leq \theta &\leq \pi \\
        0 \leq \varphi &\leq 2\pi
    \end{aligned}
    $$
\end{minipage}
%\hspace{0.5cm}
\begin{minipage}{5.5cm}
    \begin{figure}[H]
        \centering
        \input{bloch.tex}
    \end{figure}
\end{minipage}
\end{center}
della quale ogni punto, quindi ogni coppia di coordinate sferiche $(\theta, \varphi)$, indica univocamente uno stato normalizzato di singolo qubit:
$$\ket\Psi = \cos\frac{\theta}{2} \ket 0 + e^{i\varphi} \sin\frac{\theta}{2} \ket 1$$

Tale cambiamento di variabili in coordinate sferiche è attuabile poiché, come osservato nell'esempio del singolo qubit, il suo stato è:
$$\ket\Psi = \alpha \ket 0 + \beta \ket 1 \quad \alpha, \beta \in \mathbb C$$
Lo stato, se normalizzato, essendo $|\alpha|^2 + |\beta|^2 = 1$, può essere espresso come:
$$\ket\Psi = e^{i\gamma}\cos\frac{\theta}{2} \ket 0 + e^{i(\gamma + \varphi)} \sin\frac{\theta}{2} \ket 1$$
Dove il fattore $e^{i\gamma}$, non essendo influente sullo stato del sistema, può essere ignorato.

## Entanglement

**Definizione** (Stato entangled).
Sia $\ket\Psi$ lo stato di un sistema composto da $n$ sottosistemi i cui spazi di Hilbert sono $\mathcal{H}_1, \cdots, \mathcal{H}_n$. Lo stato $\ket\Psi$ è detto *entangled* se non è decomponibile, cioè se non può essere espresso come prodotto tensoriale degli stati dei singoli sottosistemi ma solo come combinazione lineare non banale dei vettori di base dello spazio $\mathcal{H}_1 \otimes  \cdots \otimes \mathcal{H}_n$ al quale appartiene:
$$
\ket\Psi \neq \ket{v_1 \cdots v_n}, \quad \forall \ket{v_i} \in \mathcal{H}_i
$$

L'effetto che la misura ha sugli stati entangled è un'ovvia conseguenza dell'ipotesi del collasso e delle proprietà del prodotto tensoriale.

**Esempio** (Due qubit entangled).
Sia il sistema di due qubit nello stato entangled:
$$
\ket\Psi = \frac{1}{\sqrt 2}\ket{00} + \frac{1}{\sqrt 2}\ket{11}
$$
Misurando il primo qubit, lo stato collassa in uno dei due autostati equiprobabili $\ket{00}$, $\ket{11}$, quindi la misura del primo qubit determina il risultato di una successiva misura del secondo.

[^1] Lo spazio di Hilbert di un qubit può essere un prodotto tensoriale di spazi in cui almeno uno di essi abbia dimensione 2.