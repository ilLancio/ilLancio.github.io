# Completezza Funzionale di Porte Logiche nei Computer Quantistici

[**documento pdf**](tesi.pdf)

---

Relatore
[Prof. Domenico Monaco](https://sites.google.com/view/dmonaco)

Anno Accademico 2024/2025

[Sapienza Università di Roma](https://www.uniroma1.it)

© 2025 Daniele Lanciotti. Tutti i diritti riservati

## Prerequisiti

- [Algebra Lineare](https://www.bollatiboringhieri.it/libri/serge-lang-algebra-lineare-9788833958699/)
- [[Prodotto scalare, Norma, Distanza]]
- [[Notazione di Dirac]]
- [[Spazio di Hilbert]]

## Introduzione

>«In principio era il Logos» — il verso che apre il Vangelo secondo Giovanni — è uno dei più celebri esempi di quanto la *ragione* sia centrale per la *conoscenza* e per la *scienza* che muovono l’uomo. La ragione non perderà mai il suo potere, perché essa è il mezzo per giungere al *significato* e, per coloro che vorranno ascoltare, all'affermazione della *Verità*.

La natura algoritmica dell’inferenza logica formale prende vita nelle computazioni della Macchina di Turing. È pertanto esplorando tali mezzi della deduzione che si può giungere a una risposta, o alla formulazione della giusta domanda.

I confini attuali della computazione sono illuminati dalla fisica contemporanea: la matematica che sottende la Meccanica Quantistica suggerisce un modello capace di estendere le potenzialità computazionali classiche — la Macchina di Turing Quantistica.

Per almeno alcune classi di problemi, la computazione quantistica si dimostra più efficiente rispetto a quella classica, offrendo vantaggi anche esponenziali nella complessità temporale delle soluzioni. Non si tratta soltanto di un’estensione teorica della Macchina di Turing, ma di un nuovo paradigma computazionale radicato nella struttura matematica della Meccanica Quantistica.

Nel contesto quantistico, i bit, ovvero le entità che codificano informazione, sono sostituiti dai *qubit*. Le *porte logiche quantistiche* agiscono su questi stati come trasformazioni unitarie, rappresentando le operazioni con cui il calcolo quantistico manipola l’informazione.

L’elaborato affronta la questione della *completezza funzionale quantistica*, intesa come possibilità di generare qualunque trasformazione unitaria ammissibile attraverso la composizione di un insieme finito di porte logiche. Si tratta di un’analogia diretta con la nozione classica di *completezza funzionale*, secondo cui un numero minimo di porte, come NAND o NOR, è sufficiente a costruire ogni circuito booleano.

A partire dai [[Postulati della Meccanica Quantistica|postulati della Meccanica Quantistica]], l’elaborato introduce il formalismo del [[Sistema Fisico di un Computer Quantistico|qubit]] e definisce le [[Porte Logiche|trasformazioni ammissibili]]. Il percorso culmina nella [[Porte Logiche Universali|dimostrazione dell’universalità]] di un insieme finito di porte logiche, che risulta completo per l’elaborazione quantistica dell’informazione.

L'elaborato prende ispirazione principalmente dagli argomenti trattati nei Capitoli 1 e 4 di [Michael A. Nielsen and Isaac L. Chuang, (2010)](https://www.cambridge.org/highereducation/books/quantum-computation-and-quantum-information/01E10196D0A682A6AEFFEA52D53BE9AE?utm_campaign=shareaholic&utm_medium=copy_link&utm_source=bookmark), nei quali la dimostrazione della completezza funzionale si sviluppa sulla base dell’approccio introdotto in [On universal and fault-tolerant quantum computing, (1999)](http://arxiv.org/abs/quant-ph/9906054v1). Il quadro teorico generale si colloca nella linea aperta da [David Deutsch, (1985)](https://doi.org/10.1098/rspa.1985.0070), in cui il concetto di calcolatore quantistico universale viene formulato come estensione fisica del modello di Turing.

## Indice

- Preliminari Matematici
  - [[Prodotto tensoriale]]
    - [[Prodotto tensoriale#Prodotto tensoriale di operatori]]
    - [[Prodotto tensoriale#Prodotto di Kronecker]]
- [[Postulati della Meccanica Quantistica]]
- [[Sistema Fisico di un Computer Quantistico]]
  - [[Sistema Fisico di un Computer Quantistico#Entanglement]]
- [[Porte Logiche]]
  - [[Porte Logiche#Circuiti]]
  - [[Porte Logiche#Porte logiche notevoli]]
- [[Porte Logiche Universali]]
  - [[Porte Logiche Universali#Approssimazione di porte logiche]]
  - [[Porte Logiche Universali#Costruzione di porte controllate]]
  - [[Porte Logiche Universali#Porte logiche a due livelli]]

## Bibliografia

- [P. Oscar Boykin, Tal Mor, Matthew Pulver, Vwani Roychowdhury, and Farrokh Vatan. On universal and fault-tolerant quantum computing, 1999.](http://arxiv.org/abs/quant-ph/9906054v1)
- [David Deutsch and Roger Penrose. Quantum theory, the Church–Turing principle and the universal quantum computer. *Proceedings of the Royal Society of London. A. Mathematical and Physical Sciences*, 400(1818):97–117, 1985.](https://doi.org/10.1098/rspa.1985.0070)
- [Michael A. Nielsen and Isaac L. Chuang. *Quantum Computation and Quantum Information: 10th Anniversary Edition*. Cambridge University Press, Cambridge, 2010.](https://www.cambridge.org/highereducation/books/quantum-computation-and-quantum-information/01E10196D0A682A6AEFFEA52D53BE9AE?utm_campaign=shareaholic&utm_medium=copy_link&utm_source=bookmark)
