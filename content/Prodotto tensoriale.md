La trattazione che segue è ispirata principalmente a [Cohen-Tannoudji, (2019), Capitolo II, Sezione F](https://www.wiley.com/en-us/Quantum+Mechanics%2C+Volume+1%3A+Basic+Concepts%2C+Tools%2C+and+Applications%2C+2nd+Edition-p-9783527822713), con integrazioni e adattamenti ove necessario.

**Definizione** (Prodotto tensoriale).
Siano $\mathcal{H}_1$ e $\mathcal{H}_2$ due spazi di Hilbert[^1]. Il prodotto tensoriale di $\mathcal{H}_1$ e $\mathcal{H}_2$, denotato con $\mathcal{H}_1 \otimes \mathcal{H}_2$, è uno spazio di Hilbert contenente tutte le coppie del tipo $\ket{v_1} \otimes \ket{v_2}$, dove $\ket{v_1} \in \mathcal{H}_1$ e $\ket{v_2} \in \mathcal{H}_2$ (detti *vettori decomponibili*)
$$
\mathcal{H}_1 \otimes \mathcal{H}_2 := \text{span} \left\{ \ket{v_1} \otimes \ket{v_2} : \ket{v_1} \in \mathcal{H}_1 \land \ket{v_2} \in \mathcal{H}_2 \right\}
$$
che soddisfa le proprietà seguenti:

1) *linearità* della moltiplicazione per uno scalare:
    $$
    (\lambda \ket{v_1}) \otimes \ket{v_2} = \ket{v_1} \otimes (\lambda \ket{v_2}) =\lambda (\ket{v_1} \otimes \ket{v_2})
    $$
    $\forall \lambda \in \mathbb C, \quad$
    $\forall \ket{v_1} \in \mathcal{H}_1, \quad$
    $\forall \ket{v_2} \in \mathcal{H}_2$

2) *distributività* dell'addizione tra vettori:
    $$
    \ket{v_1} \otimes (\ket{v_2} + \ket{w_2}) = \ket{v_1} \otimes \ket{v_2} + \ket{v_1} \otimes \ket{w_2}
    $$
    $$
    (\ket{v_1} + \ket{w_1}) \otimes \ket{v_2} = \ket{v_1} \otimes \ket{v_2} + \ket{w_1} \otimes \ket{v_2}
    $$
    $\forall \ket{v_1}, \ket{w_1} \in \mathcal{H}_1, \quad$
    $\forall \ket{v_2}, \ket{w_2} \in \mathcal{H}_2$

3) siano $\left\{\ket{u_{1,i}}\right\}$ e $\left\{\ket{u_{2,i}}\right\}$ due basi rispettivamente di $\mathcal{H}_1$ e $\mathcal{H}_2$. L'insieme $\left\{\ket{u_{1,i}} \otimes \ket{u_{2,j}}\right\}$ è una *base* di $\mathcal{H}_1 \otimes \mathcal{H}_2$.

4) il *prodotto scalare* di $\mathcal{H}_1 \otimes \mathcal{H}_2$ è definito a partire dai prodotti scalari di $\mathcal{H}_1$ e $\mathcal{H}_2$ come segue: sui vettori decomponibili si pone
    $$
    \braket{v_1 v_2 | w_1 w_2} = \braket{v_1 | w_1} \braket{v_2 | w_2}
    $$
    dove
    $\ket{v_1 v_2} = \ket{v_1} \otimes \ket{v_2},$
    $\ket{w_1 w_2} = \ket{w_1} \otimes \ket{w_2}$.
    La definizione è poi estesa per sesquilinearità.

[^1]: In tutta la trattazione, ogni spazio di Hilbert è inteso in campo complesso.

## Prodotto tensoriale di operatori

**Definizione** (Prodotto tensoriale di operatori).
 Siano $A_1$ e $A_2$ operatori lineari agenti rispettivamente sugli spazi di Hilbert $\mathcal{H}_1$ e $\mathcal{H}_2$. Il prodotto tensoriale di $A_1$ e $A_2$, denotato con $A_1 \otimes A_2$, è un operatore lineare agente su $\mathcal{H}_1 \otimes \mathcal{H}_2$ nel modo seguente:
 sui vettori decomponibili si pone
 $$
 (A_1 \otimes A_2)(\ket{v_1} \otimes \ket{v_2}) := A_1 \ket{v_1} \otimes A_2 \ket{v_2}
 $$
 $\forall \ket{v_1} \in \mathcal{H}_1, \, \forall \ket{v_2} \in \mathcal{H}_2$.
 La definizione è poi estesa per linearità.

**Proposizione** (Prodotto misto).
*Siano $A_1$, $B_1$ operatori lineari sullo spazio di Hilbert $\mathcal{H}_1$ e $A_2$, $B_2$ operatori lineari sullo spazio di Hilbert $\mathcal{H}_2$, tali per cui siano ben definiti i prodotti $A_1 B_1$ e $A_2 B_2$. Vale la seguente relazione:*
$$
{(A_1 \otimes A_2)(B_1 \otimes B_2) = (A_1 B_1) \otimes (A_2 B_2)}
$$

**Proposizione**.
*Siano $A_1$ e $A_2$ operatori lineari agenti sugli spazi di Hilbert $\mathcal{H}_1$ e $\mathcal{H}_2$, rispettivamente. Allora:*
$$
A_1, A_2 \textit{ autoaggiunti} \implies A_1 \otimes A_2 \textit{ autoaggiunto}
$$
$$
A_1, A_2 \textit{ unitari} \implies A_1 \otimes A_2 \textit{ unitario}
$$

Per una trattazione più completa delle due proposizioni appena enunciate si veda [Professor Heinz Neudecker and matrix differential calculus, (2024)](https://doi.org/10.1007/s00362-023-01499-w), [Amy N. Langville and William J. Stewart, Sezione 2.2](https://www.sciencedirect.com/science/article/pii/S0377042703009312) o [D.S.G. Pollock (2013), Sezione 8](https://doi.org/10.1080/00207160.2013.783696), tenendo a mente il risultato della proposizione enunciata in seguito sul prodotto di Kronecker.

Si utilizza la notazione $A^{\otimes n}$ per indicare il prodotto tensoriale di un operatore, uno spazio di Hilbert o un vettore $A$ per se stesso $n$ volte.

## Prodotto di Kronecker

**Definizione** (Prodotto di Kronecker).
Siano $A$ una matrice $m \times n$ e $B$ una matrice $p \times q$. Il *prodotto di Kronecker* di $A$ e $B$ è una matrice $mp \times nq$ definita a blocchi come segue:
$$
A \otimes_K B := \begin{pmatrix}a_{11}B&\cdots &a_{1n}B\\\vdots &\ddots &\vdots \\a_{m1}B&\cdots &a_{mn}B\end{pmatrix}
$$

Il prodotto di Kronecker è la rappresentazione matriciale del prodotto tensoriale di operatori lineari quando si scelgono basi fissate negli spazi di Hilbert coinvolti.

**Proposizione**.
*Siano $\mathcal{H}_1$ e $\mathcal{H}_2$ due spazi di Hilbert finito-dimensionali, di dimensione $m$ e $n$, $\left\{ \ket{u_{1, i}} \right\}_{i=1}^m$ una base di $\mathcal{H}_1$, $\left\{ \ket{u_{2,j}} \right\}_{j=1}^n$ una base di $\mathcal{H}_2$.
Allora ogni operatore lineare $A_1$ su $\mathcal{H}_1$ è rappresentato, rispetto alla base $\left\{ \ket{u_{1, i}} \right\}$, da una matrice $m \times m$, e ogni operatore $A_2$ su $\mathcal{H}_2$, rispetto alla base $\left\{ \ket{u_{2,j}} \right\}$, da una matrice $n \times n$. Il prodotto tensoriale $A_1 \otimes A_2$, è rappresentato, rispetto alla base tensoriale $\left\{ \ket{u_{1,i}} \otimes \ket{u_{2,j}} \right\}$, dalla matrice di Kronecker $A_1 \otimes_K A_2$.*

Per un esempio dimostrativo dell'enunciato, si rimanda a [David S. Dummit and Richard M. Foote (2004), Capitolo 11, Proposizione 17](https://www.wiley.com/en-be/Abstract+Algebra%2C+3rd+Edition-p-9780471433347).

Si utilizza il simbolo $\otimes$ per indicare il prodotto di Kronecker o il prodotto tensoriale tra spazi di Hilbert; invece è spesso omesso nella rappresentazione dei vettori del prodotto tensoriale per i quali si adotta la seguente notazione:
$$
\ket{v_1} \otimes \ket{v_2} \otimes \cdots \otimes \ket{v_n} := \ket{v_1} \ket{v_2} \cdots \ket{v_n} := \ket{v_1 v_2 \cdots v_n}
$$

## Bibliografia

- [Claude Cohen-Tannoudji, Bernard Diu, and Franck Laloë. *Quantum Mechanics, Volume 1: Basic Concepts, Tools, and Applications*. Wiley, 2019.](https://www.wiley.com/en-us/Quantum+Mechanics%2C+Volume+1%3A+Basic+Concepts%2C+Tools%2C+and+Applications%2C+2nd+Edition-p-9783527822713)
- [David S. Dummit and Richard M. Foote. *Abstract Algebra*. John Wiley & Sons, 3 edition, 2004.](https://www.wiley.com/en-be/Abstract+Algebra%2C+3rd+Edition-p-9780471433347)
- [Amy N. Langville and William J. Stewart. The Kronecker product and stochastic automata networks. *Journal of Computational and Applied Mathematics*, 167(2):429– 447, 2004.](https://www.sciencedirect.com/science/article/pii/S0377042703009312)
- [Shuangzhe Liu, Götz Trenkler, Tõnu Kollo, Dietrich von Rosen, and Oskar Maria Baksalary. Professor Heinz Neudecker and matrix differential calculus. *Statistical Papers*, 65(4):2605–2639, 2024.](https://doi.org/10.1007/s00362-023-01499-w)
- [D.S.G. Pollock. On kronecker products, tensor products and matrix differential calculus. *International Journal of Computer Mathematics*, 90(11):2462–2476, 2013.](https://doi.org/10.1080/00207160.2013.783696)