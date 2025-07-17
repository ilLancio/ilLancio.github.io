Si denota con $a^*$ il complesso coniugato di $a \in \mathbb C$.

**Definizione** (Prodotto scalare).
Sia $V$ uno spazio vettoriale in campo $K$ reale o complesso. Un *prodotto scalare*[^1] (o *hermitiano* o *interno*) $( \cdot \, , \cdot )$ (o $\langle \cdot \, , \cdot \rangle$) è una funzione
$$
(\cdot \, , \cdot) : V \times V \to K
$$
che soddisfa le proprietà seguenti:

1) *linearità sulla seconda componente*:
   $$
   (\vec w, \lambda \vec v + \mu \vec u) = \lambda (\vec w, \vec v) + \mu (\vec w, \vec u)
   $$
2) *simmetria Hermitiana (o coniugata)*:
   $$
   (\vec w, \vec v) = (\vec v, \vec w)^*
   $$
3) *positività definita*[^2]:
   $$
   (\vec v, \vec v) \ge 0 \, ; \quad (\vec v, \vec v) = 0 \implies \vec v = \vec 0
   $$

$\forall \vec v, \vec w \in V, \quad \forall \lambda, \mu \in K$

La coppia $\left(V, ( \cdot \, , \cdot )\right)$ è detta *spazio di pre-Hilbert* (o *prehilbertiano* o *hermitiano*).

**Proposizione**. (Antilinearità sulla prima componente)
$$
(\lambda \vec v + \mu \vec u, \vec w) = \lambda^* (\vec v, \vec w) + \mu^* (\vec u, \vec w)
$$
$\forall \vec v, \vec w \in V, \quad \forall \lambda, \mu \in \mathbb C$

L'insieme delle proprietà di *linearità sulla seconda componente* e *antilinearità sulla prima componente* è chiamata proprietà di *sesquilinearità*.

**Definizione** (Prodotto scalare canonico).
Sia $V$ lo spazio vettoriale in campo complesso delle $n$-uple a componenti complesse. Siano $\vec v = (v_1, \cdots, v_n)$ e $\vec w = (w_1, \cdots, w_n)$. Il *prodotto scalare canonico* è definito come:
$$
(\vec v, \vec w) := \sum_{i = 1}^n v_i^* w_i
$$

**Definizione** (Prodotto scalare canonico).
Sia $V$ uno spazio vettoriale in campo reale o complesso di dimensione finita $n$. Siano $(v_1, \cdots, v_n)$ e $(w_1, \cdots, w_n)$ i vettori delle coordinate di $\vec v$ e $\vec w \in V$, rispettivamente, rispetto alla base $B = \{ \vec b_1, \cdots, \vec b_n \}$. Il *prodotto scalare canonico* tra $\vec v$ e $\vec w$ rispetto alla base $B$ è definito come:
$$
(\vec v, \vec w) := \sum_{i, j = 1}^n v_i^* G_{ij} w_j
$$
dove $G$ è la *matrice metrica*

COORDINATE? BASE? NORMA P?

**Definizione** (Norma).
Sia $V$ uno spazio vettoriale in campo reale o complesso. Una *norma* $\| \cdot \|$ è una funzione
$$
\| \cdot \| : V \to \mathbb R
$$
che soddisfa le proprietà seguenti:

1) $\| \vec v \| = 0 \Leftrightarrow \vec v = \vec 0$
2) $\| \lambda \vec v \| = |\lambda| \cdot \| \vec v \|$
3) $\| \vec v + \vec w \| \le \| \vec v \| + \| \vec w \|\quad$ (*disuguaglianza triangolare*)

$\forall \vec v, \vec w \in V, \quad \forall \lambda \in \mathbb R$

La coppia $\left( V, \| \cdot \| \right)$ è detta *spazio normato*.

**Definizione** (Distanza).

**Definizione** (Norma indotta dal prodotto scalare).

**Definizione** (Distanza indotta dalla norma).

**Proposizione**.
*Ogni norma indotta dal prodotto scalare è una norma. Ogni distanza indotta dalla norma è una distanza.*

- Spazio di pre-Hilbert
- Spazio normato
- spazio metrico

[^1]: Spesso si preferisce definire il prodotto scalare in campo reale e chiamare prodotto Hermitiano (o interno) quello in campo complesso.

[^2]: Tale proprietà è spesso omessa dalla definizione di prodotto Hermitiano e inclusa nella definizione di *prodotto Hermitiano definito positivo*.
