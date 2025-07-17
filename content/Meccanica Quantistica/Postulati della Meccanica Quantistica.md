Ogni teoria fisica si basa su un insieme minimale di definizioni prime irriducibili, che facciano da ponte tra la loro natura sperimentale (il significato) e le definizioni matematiche (il significante) che ne permettono di enunciare relazioni sotto forma di postulati. Se nel caso della Meccanica Newtoniana queste definizioni prime includono lo *spazio* o il *tempo*, nella Meccanica Quantistica sono protagonisti i concetti di *osservabile* e *misura*.

- **Sistema fisico**: Un sistema quantistico è la coppia $(\mathcal H, \hat H)$ dove $\mathcal H$ è uno spazio di Hilbert complesso separabile e $\hat H$ un operatore autoaggiunto  su $\mathcal H$, detto *Hamiltoniana*, corrispondente alla quantità fisica *energia del sistema*.
- **Sistema composto**: Sia $\mathcal H$ lo spazio di Hilbert di un sistema fisico composto da $n$ sottosistemi, i cui spazi sono $\mathcal H_1, \cdots, \mathcal H_n$. Allora:
    $$
    \mathcal H = \mathcal H_1 \otimes \mathcal H_2 \otimes \cdots \otimes \mathcal H_n
    $$
- **Stato del sistema**: Si definisce una relazione di equivalenza $\sim$ su $\mathcal H \setminus \{0\}$ ponendo $\ket\Psi \sim \ket\Phi \, \Leftrightarrow \, \exists \, \alpha \in \mathbb C \setminus \{0\}$ tale che $\ket\Psi = \alpha \ket\Phi$.
Lo *stato fisico* di un sistema quantistico è allora un elemento dello spazio quoziente $\mathcal{H}/\sim$, ovvero un raggio dello spazio di Hilbert $\mathcal H$.
- **Osservabile**: Ogni quantità sperimentalmente misurabile (osservabile) è associata ad un operatore autoaggiunto che agisce sullo spazio di Hilbert del sistema quantistico.
- **Misura dell'osservabile**: Una misura dell’osservabile $\hat{A}$ produce come risultato uno degli autovalori $\lambda_i$ dello spettro di $\hat{A}$.
- **Ipotesi del collasso** (interpretazione di Copenaghen): Dopo aver misurato il valore $\lambda_i$ per un'osservabile, lo stato del sistema diventa il suo autovettore (anche detto *autostato*) corrispondente $\ket{\lambda_i}$.
- **Probabilità di transizione** (regola di Born): La probabilità di misurare il valore $\lambda_i$ nello stato $\ket\Psi$ è data dalla relazione
    $$
    P = \frac{|\braket{\lambda_i|\Psi}|^2}{ \braket{\lambda_i|\lambda_i} \braket{\Psi|\Psi}}
    $$
- **definizione di $\hbar$** (costante di Planck): $[\hat{q}, \hat{p}] = i \hbar \mathit{I}$, dove $\hat{q}$ e $\hat{p}$ sono le osservabili *posizione* e *impulso*.
- **Evoluzione temporale**: Uno stato $\ket\Psi$ dopo un intervallo di tempo $t$ diventa lo stato
    $$
    e^{-i\frac{\hat{H}}{\hbar}t}\ket\Psi
    $$
