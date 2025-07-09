## Introduzione

>«In principio era il Logos» — il verso che apre il Vangelo secondo Giovanni — è uno dei più celebri esempi di quanto la *ragione* sia centrale per la *conoscenza* e per la *scienza* che muovono l’uomo. La ragione non perderà mai il suo potere, perché essa è il mezzo per giungere al *significato* e, per coloro che vorranno ascoltare, all'affermazione della *Verità*.

La natura algoritmica dell’inferenza logica formale prende vita nelle computazioni della Macchina di Turing. È pertanto esplorando tali mezzi della deduzione che si può giungere a una risposta, o alla formulazione della giusta domanda.

I confini attuali della computazione sono illuminati dalla fisica contemporanea: la matematica che sottende la Meccanica Quantistica suggerisce un modello capace di estendere le potenzialità computazionali classiche — la Macchina di Turing Quantistica.

Per almeno alcune classi di problemi, la computazione quantistica si dimostra più efficiente rispetto a quella classica, offrendo vantaggi anche esponenziali nella complessità temporale delle soluzioni. Non si tratta soltanto di un’estensione teorica della Macchina di Turing, ma di un nuovo paradigma computazionale radicato nella struttura matematica della Meccanica Quantistica.

Nel contesto quantistico, i bit, ovvero le entità che codificano informazione, sono sostituiti dai *qubit*. Le *porte logiche quantistiche* agiscono su questi stati come trasformazioni unitarie, rappresentando le operazioni con cui il calcolo quantistico manipola l’informazione.

L’elaborato affronta la questione della *completezza funzionale quantistica*, intesa come possibilità di generare qualunque trasformazione unitaria ammissibile attraverso la composizione di un insieme finito di porte logiche. Si tratta di un’analogia diretta con la nozione classica di *completezza funzionale*, secondo cui un numero minimo di porte, come NAND o NOR, è sufficiente a costruire ogni circuito booleano.

A partire dai postulati della Meccanica Quantistica (Capitolo \ref{chap:postulati}), l’elaborato introduce il formalismo del qubit (Capitolo \ref{chap:qubit}) e definisce le trasformazioni ammissibili (Capitolo \ref{chap:porte}). Il percorso culmina nella dimostrazione dell’universalità di un insieme finito di porte logiche (Capitolo \ref{chap:completezza}), che risulta completo per l’elaborazione quantistica dell’informazione.

L'elaborato prende ispirazione principalmente dagli argomenti trattati nei Capitoli 1 e 4 di \cite{Nielsen_Chuang_2010}, nei quali la dimostrazione della completezza funzionale si sviluppa sulla base dell’approccio introdotto in \cite{boykin1999universalfaulttolerantquantumcomputing}. Il quadro teorico generale si colloca nella linea aperta da \cite{doi:10.1098/rspa.1985.0070}, in cui il concetto di calcolatore quantistico universale viene formulato come estensione fisica del modello di Turing.

## Contents

- Preliminari Matematici
  - [[Prodotto tensoriale]]
    - [[Prodotto tensoriale#Prodotto tensoriale di operatori]]
    - [[Prodotto tensoriale#Prodotto di Kronecker|Prodotto di Kronecker]]
- Postulati della Meccanica Quantistica
- Sistema Fisico di un Computer Quantistico
  - Entanglement
- Porte Logiche
  - Circuiti
  - Porte logiche notevoli
- Porte Logiche Universali
  - Approssimazione di porte logiche
  - Costruzione di porte controllate
  - Porte logiche a due livelli
