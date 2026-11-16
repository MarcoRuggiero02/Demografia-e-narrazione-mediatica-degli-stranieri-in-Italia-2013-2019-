# Demografia e narrazione mediatica degli stranieri in Italia (2013–2019)

**Corso:** Introduzione alla Programmazione (Modulo 2) – Progetto Python 2025/26  
**Autori:** Filippo Meli, Simone Naponiello, Marco Ruggiero  

---

## Panoramica

Questo progetto esplora il rapporto tra la presenza demografica degli stranieri in Italia e la loro rappresentazione nei media nel periodo compreso tra il 2013 e il 2019. L'obiettivo principale è rispondere a una domanda fondamentale: *la stampa italiana funziona come uno "specchio" della realtà demografica, oppure segue criteri editoriali propri e indipendenti?*

Per condurre l'analisi, il progetto si concentra su sei nazionalità specifiche: le cinque comunità straniere demograficamente più numerose in Italia (Romania, Albania, Marocco, Cina, Ucraina) e la Germania, inserita intenzionalmente come gruppo di controllo occidentale. 

Lo studio combina dati quantitativi provenienti da due fonti principali:
*   **Archivi ISTAT:** Dati sulla popolazione residente per stato di cittadinanza.
*   **Dataset Change-IT:** Un ampio corpus testuale contenente gli articoli del quotidiano *"la Repubblica"*.

Il progetto consiste in un'analisi esplorativa che si articola in due direzioni: un'indagine quantitativa sullo spazio mediatico dedicato a ciascuna comunità (quanto se ne parla rispetto a quanti sono effettivamente) e un'indagine qualitativa sui contesti narrativi (come vengono raccontati).

---

## Metodologia Utilizzata

L'analisi è stata interamente sviluppata in Python (utilizzando librerie come `pandas`, `numpy`, `matplotlib` e `seaborn`) e si divide in tre fasi principali:

### 1. Preparazione ed Elaborazione dei Dati
*   **Pulizia del testo e Tokenizzazione:** I testi completi e i titoli degli articoli di "la Repubblica" sono stati sottoposti a pulizia. Il processo ha incluso la gestione dei valori mancanti, la conversione in minuscolo, e la rimozione di punteggiatura e caratteri speciali tramite espressioni regolari (RegEx).
*   **Estrazione metadati:** Dall'URL di ogni articolo sono stati estratti l'anno di pubblicazione e la tipologia tematica (cronaca, politica, ecc.). La categoria "esteri" è stata volutamente esclusa per evitare distorsioni legate alla politica internazionale.
*   **Strutturazione dati ISTAT:** I dataset sulla cittadinanza sono stati uniformati filtrando i codici a 6 cifre (comuni), per contare correttamente i residenti senza duplicazioni, isolando poi le 6 nazionalità di interesse.

### 2. Analisi dello Spazio Mediatico
Per rispondere alla domanda "Quanto spazio mediatico riceve una nazionalità?", sono stati applicati i seguenti metodi:
*   **Indice di sovrarappresentazione:** È stato calcolato il rapporto tra il "peso mediatico" (la quota percentuale di articoli che menzionano una nazionalità in un anno) e l'"incidenza demografica" (il peso percentuale dei residenti di quella nazionalità sul totale).
*   **Euristica (Filtro dei contesti non personali):** Per evitare falsi positivi (es. confondere un articolo sul "governo tedesco" o sul "mercato cinese" con un articolo sui cittadini residenti), è stato sviluppato un filtro basato su dizionari lessicali mirati. L'algoritmo analizza le 5 parole precedenti e successive al termine di nazionalità, classificando il contesto come "persona", "non-persona" o "ambiguo", permettendo di ricalcolare indici molto più precisi.
*   **Correlazione di Pearson:** È stata utilizzata per misurare l'esistenza di un legame matematico tra l'incidenza demografica di una nazione e il suo peso mediatico nel tempo, verificando così l'ipotesi del giornalismo come "specchio".

### 3. Analisi del Contesto Narrativo
Per rispondere alla domanda "Come vengono raccontati gli stranieri?", ci si è concentrati sulle tipologie editoriali:
*   **Mappatura delle tipologie:** Sono state analizzate 9 sezioni chiave (cronaca, politica, solidarietà, cultura, tecnologia, scienze, ambiente, salute, scuola) per capire in quali contesti vengono citate le singole comunità, evidenziando gerarchie narrative (es. schiacciamento sulla cronaca per alcune nazioni, primato della solidarietà o dell'economia per altre).
*   **Indice di Tono:** È stato creato uno *score* matematico basato sulla sezione del giornale in cui è collocata la notizia. A ogni categoria è stato assegnato un peso (da -1.0 per la cronaca, a 0 per la politica, fino a valori positivi per cultura, scienze e solidarietà). La media di questi pesi ha permesso di calcolare e tracciare su grafico l'evoluzione temporale dell'orientamento narrativo (positivo o negativo) per ogni nazionalità.
