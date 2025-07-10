Si denota con $a^*$ il complesso coniugato di $a \in \mathbb C$.

**Definizione** (Prodotto scalare).
Sia $V$ uno spazio vettoriale in campo complesso. Un *prodotto scalare*[^1] (o *Hermitiano* o *interno*) $( \cdot \, , \cdot )$ (o $\langle \cdot , \cdot \rangle$) è una funzione
$$
(\cdot \, , \cdot) : V \times V \to \mathbb C
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
   (\vec v, \vec v) \ge 0 \, ; \quad (\vec v, \vec v) = 0 \implies \vec v = 0
   $$
   $\forall \vec v, \vec w \in V, \quad \forall \lambda, \mu \in \mathbb C$

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

**Definizione** (Norma).

**Definizione** (Distanza).

**Definizione** (Norma indotta dal prodotto scalare).

**Definizione** (Distanza indotta dalla norma).

**Proposizione**.
*La norma indotta dal prodotto scalare è una norma. La distanza indotta dalla norma è una distanza.*

[^1]: Spesso si preferisce definire il prodotto scalare in campo reale e chiamare prodotto Hermitiano (o interno) quello in campo complesso.

[^2]: Tale proprietà è spesso omessa dalla definizione di prodotto Hermitiano e inclusa nella definizione di *prodotto Hermitiano definito positivo*.
