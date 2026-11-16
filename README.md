# Demografia e narrazione mediatica degli stranieri in Italia (2013–2019)

**Corso:** Introduzione alla Programmazione (Modulo 2) – Progetto Python 2025/26  
**Autori:** Filippo Meli, Simone Naponiello, Marco Ruggiero  

## 📌 Obiettivo del Progetto
Questo progetto analizza il rapporto tra la presenza demografica degli stranieri in Italia e la loro rappresentazione nei media nel periodo 2013-2019. L'analisi si concentra su sei nazionalità (Romania, Albania, Marocco, Cina, Ucraina e Germania come gruppo di controllo occidentale) per esplorare se la stampa funga da "specchio" della realtà demografica o se segua criteri editoriali autonomi.

## 📊 Fonti Dati
L'analisi quantitativa combina due dataset principali:
*   **Archivi ISTAT:** Dati sulla popolazione residente per cittadinanza a livello comunale (2013-2019).
*   **Dataset Change-IT:** Corpus di articoli estratti dal quotidiano "la Repubblica".

## 🛠️ Strumenti e Tecnologie
*   **Linguaggio:** Python
*   **Librerie Principali:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `re` (RegEx).

## 🔍 Struttura dell'Analisi

### 1. Preparazione ed Elaborazione Dati
*   Pulizia testuale e tokenizzazione degli articoli (gestione missing values, rimozione punteggiatura, normalizzazione testuale tramite espressioni regolari).
*   Estrazione di anno e tipologia tematica (cronaca, politica, cultura, ecc.) dagli URL degli articoli.
*   Filtraggio e aggregazione dei dati demografici ISTAT per estrarre le nazioni di interesse.

### 2. Quanto spazio mediatico? (Analisi Quantitativa)
*   **Indice di Sovrarappresentazione:** Confronto tra l'incidenza demografica reale di una nazionalità e il suo peso mediatico.
*   **Filtro Euristico (Persona vs Non-Persona):** Algoritmo basato sul contesto delle parole vicine per distinguere gli articoli che parlano di "persone fisiche" da quelli che usano le nazionalità in senso macroeconomico o istituzionale (es. "governo cinese", "motore tedesco").
*   **Correlazione di Pearson:** Verifica statistica del legame tra la crescita demografica e l'attenzione della stampa.

### 3. Come vengono raccontati? (Analisi Qualitativa)
*   **Analisi dei contesti narrativi:** Mappatura delle occorrenze per tipologia di articolo (es. schiacciamento sulla cronaca per Albania/Marocco/Romania; primato della solidarietà per l'Ucraina; focus su tecnologia e cultura per Cina/Germania).
*   **Indice di Tono:** Creazione di uno *score* quantitativo (da -1.0 a +1.0) basato sulle sezioni del giornale per misurare se il racconto di una data comunità è prevalentemente positivo (es. scienze, cultura), negativo (es. cronaca) o neutro.

## 💡 Risultati Principali
1.  **Il giornalismo non è uno specchio:** L'andamento demografico reale non è il motore principale della visibilità mediatica. Esiste una correlazione spesso inversa: comunità che crescono e si stabilizzano ottengono col tempo meno attenzione.
2.  **Gerarchia narrativa:** I media costruiscono profili fortemente differenziati per cittadinanza. Alcune nazionalità esistono mediaticamente quasi solo come protagoniste di cronaca problematica, mentre altre vengono valorizzate in contesti attivi, economici o culturali, a prescindere dalla loro reale consistenza numerica.
