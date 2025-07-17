**Definizione** (Ket).
Sia $\mathcal H$ lo spazio di Hilbert di un sistema quantistico. Si dice *ket* un vettore appartenente a $\mathcal H$, denotato come:
$$
\ket v \in \mathcal H
$$

**Definizione** (Bracket).
Sia $( \cdot \, , \cdot )$ il prodotto scalare dello spazio di Hilbert $\mathcal H$ di un sistema quantistico. Siano $\ket v, \ket w \in \mathcal H$. Sia $A$ un operatore lineare in $\mathcal H$. Si denotano:
$$
\braket{w | v} := (\ket w, \ket v), \quad
\braket{w | A | v} := (\ket w, A \ket v)
$$

**Proposizione**.
Per la simmetria hermitiana del prodotto scalare e per definizione di operatore aggiunto $A^\dagger$ segue che:
$$
\braket{w | A | v} = \braket{v | A^\dagger | w}^*
$$

**Definizione** (Valor medio).
Sia $\mathcal H$ lo spazio di Hilbert di un sistema quantistico, $\ket v \in \mathcal H$ e $A$ un'osservabile del sistema. Si dice *valor medio di $A$ su $\ket v$* il seguente rapporto:
$$
\braket A := \frac{\braket{v | A | v}}{\braket{v | v}}
$$

**Definizione**.
Gli operatori $\ket u \bra w$ e $\sum_i \ket{u_i} \bra{w_i}$, che operano nello spazio di Hilbert a cui appartengono i ket $\ket u, \ket w, \ket{u_i}, \ket{w_i}, \ket v$ sono definiti tali per cui:
$$
\left( \ket u \bra w \right) \ket v :=  \ket u \braket{w | v}
$$
$$
\left( \sum_i \ket{u_i} \bra{w_i} \right) \ket v :=  \sum_i \ket{u_i} \braket{w_i | v}
$$

**Proposizione**.
Sia $\{ \ket{e_i} \}$ una base di uno spazio di Hilbert. Allora:
$$
\sum_i \ket{e_i} \bra{e_i} = I
$$

**Proposizione**.
$$
\left( \ket w \bra v \right)^\dagger = \ket v \bra w
$$
