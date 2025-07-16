**Definizione** (Porta logica quantistica).
Una *porta logica* a $n$ qubit è un operatore unitario $U$ che opera sullo spazio di Hilbert di un sistema di $n$ qubit.

Risulta ragionevole definire l'applicazione di una o più porte logiche su un sistema con un numero di qubit maggiore di quello in cui operano singolarmente.

**Definizione** (Applicazione simultanea di porte logiche).
Siano $U_1, \cdots, U_k$ porte logiche rispettivamente a $n_1, \cdots, n_k$ qubit. La loro *applicazione simultanea* su sottoinsiemi distinti e ordinati di qubit di un sistema di $n \ge n_\text{tot} = \sum_{i=1}^k n_i$ qubit, è definita dalla seguente porta logica a $n$ qubit:
\begin{equation}
    P^{-1} \left[ U_1 \otimes \cdots \otimes U_k \otimes I^{\otimes (n - n_\text{tot})} \right] P
    \label{eq:porte_simultanee}
\end{equation}
dove $P$ è un operatore di permutazione che porta gli $n_\text{tot}$ qubit target nelle prime $n_\text{tot}$ posizioni del tensore, lasciando gli altri inalterati.

L'evoluzione temporale, essendo un operatore unitario, è a tutti gli effetti una porta logica, pertanto perturbare il sistema in modo tale da modificare a piacimento la sua Hamiltoniana equivale a scegliere la porta logica che vi agisce.

## Circuiti

Un circuito quantistico è una schematizzazione del computer quantistico, quindi dell'applicazione delle porte logiche allo stato dei suoi qubit.

Ogni linea orizzontale rappresenta un qubit, ogni simbolo che vi giace indica la porta logica agente su di essi, fatta eccezione per l'unico simbolo rappresentante la misurazione (figura \ref{fig:meter}).
Le porte allineate verticalmente si applicano simultaneamente, pertanto combinandosi come nell'espressione \eqref{eq:porte_simultanee}. Le porte risultanti vanno moltiplicate tra loro da destra a sinistra.
A sinistra del circuito possono essere presenti eventuali nomi assegnati ai qubit e vettori che ne rappresentano lo stato iniziale. In particolare, se accanto alla linea corrispondente al qubit in posizione $n$ è indicato un vettore $\ket\psi$, lo stato iniziale del sistema è una combinazione lineare dei vettori della base computazionale, in cui il termine associato alla posizione $n$ nel prodotto tensoriale è sostituito da $\ket\psi$ anziché dal consueto $\ket 0$ o $\ket 1$.

\begin{figure}[H]
    \centering
    \begin{quantikz}
        \lstick{} & \meter{} & \rstick{}
    \end{quantikz}
    \caption{Simbolo rappresentante la misurazione di singolo qubit.}
    \label{fig:meter}
\end{figure}

**Esempio**.
Circuito di un computer quantistico con 4 qubit (2 generici e 2 inizializzati) e 6 porte logiche:
\begin{figure}[H]
    \centering
    \begin{quantikz}
        \lstick{$q_1$} & \gate{A} &                   & \gate{F}   & &          \\
        \lstick{$q_2$} & \gate{B} & \gate[wires=2]{D} &            & & \meter{} \\
        \lstick{$\ket 0$} &          &                   &            & &          \\
        \lstick{$\ket 1$} & \gate{C} & \gate{E}          &            & & \meter{}
    \end{quantikz}
    %\caption{Circuito esempio di un computer quantistico con 4 qubit e 6 porte logiche.}
    \label{fig:circuito_esempio}
\end{figure}
La porta logica che agisce sul sistema totale dei qubit risulta quindi essere la seguente:
$$U_\text{tot} = (F \otimes I^{\otimes 3}) (I \otimes D \otimes E) (A \otimes B \otimes I \otimes C)$$
Utilizzando la proprietà del prodotto tensoriale tra operatori, enunciata nella proposizione \ref{thm:prodotto_misto}, è possibile riesprimere la porta logica risultante come segue:
$$U_\text{tot} = (F A) \otimes (D (B \otimes I)) \otimes (E C)$$

Lo stato iniziale del sistema, in questo caso, corrisponde a ciò che si ottiene misurando gli ultimi due qubit di diversi sistemi generici e selezionando quello in cui le rispettive misure diano risultati 0 e 1. Tale stato è il seguente:
$$
\alpha \ket{0001} + \beta \ket{0101} + \gamma \ket{1001} + \delta \ket{1101}
$$
dove $\alpha, \beta, \gamma, \delta \in \mathbb C$.

Ciò significa che la matrice rappresentante la porta logica risultante $U_\text{tot}$ agisce sul seguente vettore di coordinate:
$$
(0, \alpha, 0, 0, 0, \beta, 0, 0, 0, \gamma, 0, 0, 0, \delta, 0, 0)
$$

## Porte logiche notevoli

Ogni porta logica quantistica può essere definita con la relativa rappresentazione matriciale o, equivalentemente, specificando l’azione sui vettori della base computazionale, ottenendo quindi una rappresentazione funzionale analoga alla *tavola di verità* dei connettivi logici classici.

Di seguito si riportano le definizioni delle principali porte logiche a singolo qubit.

\begin{table}[H]
    \centering
    \input{circuiti/single_gates.tex}
    \caption{Nomi, simboli, tavole di verità e matrici unitarie per porte logiche a singolo qubit.}
    \label{tab:single_gates}
\end{table}

**Definizione** (Porta logica di rotazione indotta dalle matrici di Pauli).
Sia $\hat n$ un versore in $\mathbb R^3$. La *rotazione* di un angolo $\theta$ attorno all'asse di $\hat n$ è definita come la porta logica a singolo qubit seguente:
$$
R_{\hat n}(\theta) := \exp \left( -\frac{i \theta}{2} \hat n \cdot \vec \sigma \right) = \cos\left( \frac{\theta}{2} \right) I - i \sin\left( \frac{\theta}{2} \right) (\hat n \cdot \vec \sigma)
$$
dove $\vec \sigma = \left( \sigma_1, \sigma_2, \sigma_3 \right)$.

%\begin{proposition}\label{thm:rotazione}
%    La porta logica di rotazione è esprimibile come:
%    $$
%    R_{\hat{n}}(\theta) = \cos\left( \frac{\theta}{2} \right) I - i \sin\left( \frac{\theta}{2} \right) (\hat n \cdot \vec \sigma)
%    $$
%    e rappresenta una rotazione tridimensionale unitaria attorno all’asse $\hat{n}$ di un angolo $\theta$ della rappresentazione sulla sfera di Bloch dello stato normalizzato di un singolo qubit.
%\end{proposition}
%
%\begin{proof}
%    Sviluppo in serie di Taylor dell’esponenziale:
%    $$
%    \exp \left( -\frac{i \theta}{2} \hat n \cdot \vec \sigma \right) = \sum_{k=0}^{\infty} \frac{1}{k!} \left(-\frac{i \theta}{2} \hat n \cdot \vec \sigma\right)^k
%    $$
%    Usando le seguenti proprietà delle matrici di Pauli:
%    \begin{itemize}
%        \item $\sigma_i^2 = I \quad \forall i$
%        \item $\{\sigma_i, \sigma_j\} = 2 \delta_{ij} I$
%    \end{itemize}
%    si può ricavare $(\hat n \cdot \vec \sigma)^2$:
%    \begin{align*}
%        (\hat n \cdot \vec \sigma)^2
%        &= (n_x \sigma_1 + n_y \sigma_2 + n_z \sigma_3)^2 \\
%        &= n_x^2 \sigma_1^2 + n_y^2 \sigma_2^2 + n_z^2 \sigma_3^2 + \sum_{i < j} n_i n_j(\sigma_i \sigma_j + \sigma_j \sigma_i) \\
%        &= (n_x^2 + n_y^2 + n_z^2) I + \sum_{i < j} n_i n_j \{\sigma_i,\sigma_j\} \\
%        &= \|\hat{n}\|^2 I + 0 = I
%    \end{align*}
%    Separando in termini pari e dispari e sommando i due contributi, si ottiene l'identità da dimostrare.
%    \begin{itemize}
%        \item Termini pari ($k = 2m$):
%        $$
%        \sum_{m=0}^{\infty} \frac{1}{(2m)!} \left(-\frac{i \theta}{2} \right)^{2m} (\hat n \cdot \vec \sigma)^{2m} = \sum_{m=0}^{\infty} \frac{1}{(2m)!} \left(-1\right)^m \left(\frac{\theta}{2}\right)^{2m} I = \cos\left( \frac{\theta}{2} \right) I
%        $$
%        \item Termini dispari ($k = 2m + 1$):
%        \begin{align*}
%            &\sum_{m=0}^{\infty} \frac{1}{(2m+1)!} \left(-\frac{i \theta}{2} \right)^{2m+1} (\hat n \cdot \vec \sigma)^{2m+1} \\
%            &= -i \sum_{m=0}^{\infty} \frac{1}{(2m+1)!} \left(-1\right)^m \left(\frac{\theta}{2}\right)^{2m+1} (\hat n \cdot \vec \sigma) \\
%            &= -i \sin\left( \frac{\theta}{2} \right) (\hat n \cdot \vec \sigma)
%        \end{align*}
%    \end{itemize}
%
%    $$
%    \exp\left(-\frac{i \theta}{2} \hat{n} \cdot \vec{\sigma} \right) = \cos\left( \frac{\theta}{2} \right) I - i \sin\left( \frac{\theta}{2} \right) (\hat n \cdot \vec \sigma)
%    $$
%\end{proof}

Come mostrato nella tavola di verità in tabella \ref{tab:not}, la porta $\sigma_1$ presenta un comportamento del tutto analogo a quello della porta logica classica NOT, motivo per cui viene comunemente denominata *porta NOT quantistica*.
Nel circuito quantistico, essa può essere rappresentata indifferentemente con una delle due notazioni illustrate in figura \ref{fig:not}.

\begin{figure}[H]
\begin{center}
    \begin{minipage}{5cm}
        \begin{table}[H]
            \centering
            \begin{tabular}{|c|c|}
                \hline
                $A$ & $\lnot A$ \\
                \hline
                0   & 1         \\
                1   & 0         \\
                \hline
            \end{tabular}
            \begin{tabular}{|c|c|}
                \hline
                $\ket \Psi$ & $\sigma_1 \ket \Psi$ \\
                \hline
                $\ket 0$    & $\ket 1$             \\
                $\ket 1$    & $\ket 0$             \\
                \hline
            \end{tabular}
            \caption{Confronto tra tavole di verità $\lnot$ e $\sigma_1$.}
            \label{tab:not}
        \end{table}
    \end{minipage}
    \hspace{0.5cm}
    \begin{minipage}{5cm}
        \begin{figure}[H]
            \centering
            \begin{quantikz}
                \lstick{} & \targ{} & \rstick{}
            \end{quantikz}
            :=
            \begin{quantikz}
                \lstick{} & \gate{X} & \rstick{}
            \end{quantikz}
            \caption{Rappresentazione circuitale alternativa di $\sigma_1$.}
            \label{fig:not}
        \end{figure}
    \end{minipage}
\end{center}
\end{figure}

**Definizione** (Operazione controllata).
Sia $U$ una porta logica a $k$ qubit. L'*operazione controllata* (o *porta logica controllata*) $C^n(U)$ è una porta logica a $n+k$ qubit definita a blocchi come segue:
\vspace{-0.5cm}
\begin{center}
    \begin{minipage}{6.5cm}
        $$
        C^n(U) :=
        \begin{pmatrix}
            I & 0 \\
            0 & U 
        \end{pmatrix}
        $$
        dove $I$ è la matrice identità di dimensione $2^{n+k} - 2^k$.
    \end{minipage}
    %\hspace{0.5cm}
    \begin{minipage}{4.5cm}
        \begin{figure}[H]
            \centering
            \begin{quantikz}
                \lstick{} & \ctrl{1}          & \rstick[2]{$n$ controllo} \\
                \lstick{} & \ctrl{1}          & \rstick{}           \\
                          & \ \vdots\         &                     \\
                \lstick{} & \gate[wires=2]{U} & \rstick[2]{$k$ target}  \\
                \lstick{} &                   & \rstick{}
            \end{quantikz}
            %\caption{}
            \label{fig:controlled-u}
        \end{figure}
    \end{minipage}
\end{center}
Dei qubit su cui agisce tale porta, i primi $n$ sono detti qubit di *controllo*, i restanti $k$ sono chiamati qubit *target*.

Nella categoria di porte controllate $C^n(U)$ rientrano anche porte i cui qubit di controllo sono preceduti e succeduti da porte $\sigma_1$, i quali sono rappresentati graficamente mediante un cerchio vuoto, come in figura~\ref{fig:empty-controlled-u}. Tale rappresentazione grafica è ragionevole poiché i qubit di controllo a cerchio pieno definiscono una porta che agisce non banalmente solo sui vettori della base computazionale con $\ket 1$ nella posizione di quei qubit, mentre quelli a cerchio vuoto definiscono una porta che agisce solo quando i corrispondenti qubit sono inizializzati a $\ket 0$.
Questa inversione della condizione è ottenuta grazie all’inserimento delle porte NOT, che invertono temporaneamente lo stato del qubit durante il controllo (come visto in tabella \ref{tab:not}).

Quando più porte controllate condividono lo stesso qubit di controllo, è utile adottare una notazione compatta come quella illustrata in figura \ref{fig:cnot-multi-target}.

\begin{figure}[H]
\begin{center}
    \begin{minipage}{5.5cm}
        \begin{figure}[H]
            \centering
            %\begin{quantikz}[column sep=0.45em]%, row sep={1cm,between origins}]
            %    \lstick{} & \octrl{1}          & \raisebox{0ex}{\ \ \ \ \ \ } & \gate{X} & \ctrl{1}          & \gate{X} & \rstick{} \\
            %    \lstick{} & \ctrl{1}           & \raisebox{-8ex}{\ \ :=\ \ }  &          & \ctrl{1}          &          & \rstick{} \\
            %    \lstick{} & \octrl{1}          & \raisebox{0ex}{\ \ \ \ \ \ } & \gate{X} & \ctrl{1}          & \gate{X} & \rstick{} \\
            %    \lstick{} & \gate{U}           & \raisebox{0ex}{\ \ \ \ \ \ } &          & \gate{U}          &          & \rstick{}
            %\end{quantikz}
            \begin{quantikz}[column sep=0.45em, row sep={1cm,between origins}, baseline=(current bounding box.center)]
                \lstick{} & \octrl{1}          & \rstick{} \\
                \lstick{} & \ctrl{1}           & \rstick{} \\
                \lstick{} & \octrl{1}          & \rstick{} \\
                \lstick{} & \gate{U}           & \rstick{}
            \end{quantikz}
            :=
            \begin{quantikz}[column sep=0.45em, row sep={1cm,between origins}, baseline=(current bounding box.center)]
                \lstick{} & \gate{X} & \ctrl{1}          & \gate{X} & \rstick{} \\
                \lstick{} &          & \ctrl{1}          &          & \rstick{} \\
                \lstick{} & \gate{X} & \ctrl{1}          & \gate{X} & \rstick{} \\
                \lstick{} &          & \gate{U}          &          & \rstick{}
            \end{quantikz}
            \caption{Qubit di controllo a cerchio vuoto.}
            \label{fig:empty-controlled-u}
        \end{figure}
    \end{minipage}
    \hspace{0.5cm}
    \begin{minipage}{5.5cm}
        \vspace{0.2cm}
        \begin{figure}[H]
            \centering
            \begin{quantikz}[column sep=0.45em, baseline=(current bounding box.center)]
                \lstick{} & \ctrl{2} & \rstick{} \\
                \lstick{} & \gate{U} & \rstick{} \\
                \lstick{} & \gate{V} & \rstick{}
            \end{quantikz}
            :=
            \begin{quantikz}[column sep=0.45em, baseline=(current bounding box.center)]
                \lstick{} & \ctrl{1} & \ctrl{2} & \rstick{} \\
                \lstick{} & \gate{U} &          & \rstick{} \\
                \lstick{} &          & \gate{V} & \rstick{}
            \end{quantikz}
            \caption{Porte logiche controllate con qubit di controllo condiviso.}
            \label{fig:cnot-multi-target}
        \end{figure}
    \end{minipage}
\end{center}
\end{figure}

Tra le porte logiche a più qubit, rivestono particolare importanza le porte *NOT controllate*, tra cui le due fondamentali — la porta *CNOT* e la porta *Toffoli* — sono definite di seguito.

**Definizione** (NOT controllato).
La porta *NOT controllato*, anche detta *CNOT*, è la porta logica $C(\sigma_1)$:
\begin{figure}[H]
    \centering
    \begin{quantikz}[baseline=(current bounding box.center)]
        \lstick{} & \ctrl{1} & \rstick{} \\
        \lstick{} & \targ{} & \rstick{}
    \end{quantikz}
    =
    \begin{quantikz}[baseline=(current bounding box.center)]
        \lstick{} & \ctrl{1} & \rstick{} \\
        \lstick{} & \gate{X} & \rstick{}
    \end{quantikz}
    =
    $\displaystyle
    \begin{pmatrix}
        1 & 0 & 0 & 0 \\
        0 & 1 & 0 & 0 \\
        0 & 0 & 0 & 1 \\
        0 & 0 & 1 & 0
    \end{pmatrix}
    $
    \quad\quad
    \begin{tabular}{c|c}
        %\hline
        $\ket \Psi$ & CNOT$\ket \Psi$ \\
        \hline
        $\ket{00}$  & $\ket{00}$      \\
        $\ket{01}$  & $\ket{01}$      \\
        $\ket{10}$  & $\ket{11}$      \\
        $\ket{11}$  & $\ket{10}$      \\
        %\hline
    \end{tabular}
    %\caption{}
    \label{fig:cnot}
\end{figure}

**Definizione** (Toffoli).
La porta *Toffoli*, anche detta *CCNOT* o *TOFF*, è la porta logica $C^2(\sigma_1)$:
\begin{figure}[H]
    \centering
    \begin{quantikz}[baseline=(current bounding box.center)]
        \lstick{} & \ctrl{2} & \rstick{} \\
        \lstick{} & \ctrl{0} & \rstick{} \\
        \lstick{} & \targ{} & \rstick{}
    \end{quantikz}
    =
    \begin{quantikz}[baseline=(current bounding box.center)]
        \lstick{} & \ctrl{2} & \rstick{} \\
        \lstick{} & \ctrl{0} & \rstick{} \\
        \lstick{} & \gate{X} & \rstick{}
    \end{quantikz}
    =
    \scalebox{0.6}{
    $\displaystyle
    \begin{pmatrix}
        1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
        0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\
        0 & 0 & 0 & 0 & 0 & 0 & 1 & 0
    \end{pmatrix}
    $}
    \quad\quad
    \begin{tabular}{c|c}
        %\hline
        $\ket \Psi$ & TOFF$\ket \Psi$ \\
        \hline
        $\ket{000}$ & $\ket{000}$    \\
        $\ket{001}$ & $\ket{001}$    \\
        $\ket{010}$ & $\ket{010}$    \\
        $\ket{011}$ & $\ket{011}$    \\
        $\ket{100}$ & $\ket{100}$    \\
        $\ket{101}$ & $\ket{101}$    \\
        $\ket{110}$ & $\ket{111}$    \\
        $\ket{111}$ & $\ket{110}$    \\
        %\hline
    \end{tabular}
    %\caption{}
    \label{fig:toffoli}
\end{figure}

Analogamente al caso della porta NOT, anche la porta Toffoli può essere considerata l’analogo quantistico della porta logica classica *NAND*.
Infatti, se il qubit target viene inizializzato nello stato $\ket{1}$ — come nel circuito mostrato in figura \ref{fig:toff-nand} — e si interpretano i due qubit di controllo come input e il qubit target come output, la tavola di verità risultante (tabella \ref{tab:toff-nand}) coincide con quella della porta NAND classica.

\begin{figure}[H]
    \begin{center}
        \begin{minipage}{4.5cm}
            \begin{figure}[H]
                \centering
                \begin{quantikz}
                    \lstick{$q_1$}    & \ctrl{2} & \rstick{} \\
                    \lstick{$q_2$}    & \ctrl{0} & \rstick{} \\
                    \lstick{$\ket 1$} & \targ{}  & \rstick{}
                \end{quantikz}
                \caption{Circuito NAND con porta Toffoli a qubit target $\ket 1$.}
                \label{fig:toff-nand}
            \end{figure}
        \end{minipage}
        \hspace{0.3cm}
        \begin{minipage}{8.2cm}
            \vspace{-0.5cm}
            \begin{table}[H]
                \centering
                \begin{tabular}{|c|c|}
                    \hline
                    $\ket \Psi \ket 1$ & TOFF$\ket \Psi \ket 1$ \\
                    \hline
                    $\ket{001}$ & $\ket{001}$    \\
                    $\ket{011}$ & $\ket{011}$    \\
                    $\ket{101}$ & $\ket{101}$    \\
                    $\ket{111}$ & $\ket{110}$    \\
                    \hline
                \end{tabular}
                \begin{tabular}{|cc|c|}
                    \hline
                    $A$ & $B$ & $A$ NAND $B$ \\
                    \hline
                    0   & 0   & 1            \\
                    0   & 1   & 1            \\
                    1   & 0   & 1            \\
                    1   & 1   & 0            \\
                    \hline
                \end{tabular}
                \caption{Confronto tra tavole di verità Toffoli e NAND.}
                \label{tab:toff-nand}
            \end{table}
        \end{minipage}
    \end{center}
\end{figure}

La porta NAND classica è *funzionalmente completa* (o *universale*), ovvero consente di costruire qualsiasi altra funzione logica booleana (come AND, OR, NOT) utilizzando esclusivamente combinazioni di porte NAND. Una dimostrazione di questo risultato si trova in \citep[Sezione 8.1]{Nigro2018} ed in \citep[Sezione 1.3]{mendelson2015introduction}.

Poiché un computer quantistico è in grado di replicare il comportamento della porta NAND tramite la porta Toffoli, esso può simulare qualsiasi circuito logico classico e quindi emulare una macchina di Turing. Per una trattazione completa del modello di macchina di Turing si rimanda a \cite{sipser13}. Ne consegue che il modello computazionale quantistico è *Turing completo*.
