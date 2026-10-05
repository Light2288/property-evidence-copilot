# Review della versione corretta del questionario di validazione

## Analysis Metadata

- **Status:** `PARTIAL — NO MATERIAL FINDINGS`
- **Coverage:** contenuto testuale e tabelle del DOCX completi; `PARTIAL` riguarda esclusivamente il layout non incluso nell'ingestione deterministica.
- **Generated:** `2026-10-06T01:09:02.893+02:00`
- **ADR mode:** disabilitato; nessun ADR letto.
- **Oggetto:** verifica della versione `1.2 - 6 ottobre 2026`, inclusa la risoluzione di tutti i findings della review precedente.

## Sources

| ID | Fonte | Copertura e uso |
|---|---|---|
| S1 | `docs/evidence/questionnaire-review/sources/S1/content.md` | `PARTIAL` solo per il layout; estrazione completa di paragrafi e tabelle dal DOCX corrente. |
| S2 | `docs/evidence/questionnaire-review/sources/S2/content.md` | `COMPLETE`; Markdown corrente del questionario. |
| S3 | `AGENTS.md` | `COMPLETE`; confini di progetto, evidenza, revisione umana e privacy. |
| S4 | `README.md` | `COMPLETE`; stato e safety boundary del progetto. |
| S5 | `docs/context/project-candidate.md` | `COMPLETE`; utente, ipotesi, gate e confini v0.1. |
| S6 | `docs/kickoff.md` | `COMPLETE`; soglie di discovery, rischio, scope e criteri approvati. |

## Actors and Goals

- **Partecipante/agente immobiliare:** descrivere processo reale, strumenti, documenti, tempi, problemi e casi rappresentativi senza fornire dati identificativi o allegati; può saltare domande o interrompere. [S1, DOCX paragrafi 3-20, 261-330]
- **Responsabile della ricerca/intervistatore:** spiegare scopo e uso delle risposte, ottenere conferma verbale, assegnare codici non nominativi, proteggere eventuali recapiti, aggregare i risultati e gestire rettifica, ritiro e cancellazione. [S1, DOCX paragrafi 17-23, 430-438]
- **Agenzia/design partner:** consentire, se autorizzato, l'osservazione del software con un immobile fittizio o schermate prive di dati reali e valutare il flusso sintetico separato dai sistemi correnti. [S1, DOCX paragrafi 123-130, 381-405, 437; S5, “Primary User” e “Discovery Gate”]
- **Professionista umano o abilitato:** concludere i controlli che richiedono competenza, fonti esterne o sopralluogo; il prodotto può mostrare evidenze, scadenze esplicite, mancanze e conflitti, non certificare conformità. [S1, DOCX paragrafi 201-258, 331-350; S3, “Evidence and Human Review”]
- **Prodotto futuro:** proporre dati con provenienza visibile, preservare incertezza e conflitti, richiedere revisione esplicita ed esportare solo dati confermati senza pubblicazione automatica. [S1, DOCX paragrafi 331-350; S3, “Scope Gate” e “Evidence and Human Review”]

## Functional Requirements

1. Il questionario raccoglie ruoli, responsabilità, stati del processo, distinzione vendita/affitto, strumenti, conservazione e classificazione degli allegati, formati ricevuti e problemi ricorrenti. [S1, DOCX paragrafi 22-130]
2. Misura tempo attivo, informazioni mancanti, contraddizioni, ricontatti e conseguenze di errori od omissioni sia in forma tipica sia nei casi rappresentativi. [S1, DOCX paragrafi 136-168, 261-330]
3. Verifica disponibilità e lavoro manuale dei documenti, incluse le pratiche edilizie e urbanistiche, e raccoglie i campi normalmente ricopiati o verificati. [S1, DOCX paragrafi 171-196 e tabelle 1-2]
4. Esplora i controlli su validità APE, pratiche edilizie/urbanistiche, confronto planimetria-stato di fatto e atto di provenienza senza chiedere né produrre certificazioni. [S1, DOCX paragrafi 201-258; S3, “Evidence and Human Review”]
5. Testa il valore del flusso limitato: evidenze con pagina di origine, mancanze/incertezze/conflitti, revisione umana, export confermato e nessuna pubblicazione automatica. [S1, DOCX paragrafi 331-405; S5, “Proposed Value” e “v0.1 Boundary”]
6. Verifica la fattibilità di ricostruire problemi rappresentativi con un esempio inventato senza dati, documenti o planimetrie reali. [S1, DOCX paragrafi 386-397; S5, “Discovery Gate”]
7. Include istruzioni operative per osservare il software in sicurezza e per contare interviste e casi fino alle soglie di discovery. [S1, DOCX paragrafi 437-438; S6, “Discovery Plan and Go/No-Go”]
8. Dichiara partecipazione facoltativa, accesso alle risposte, reporting non identificativo, retention, rettifica/ritiro e canale di contatto; l'appendice applica le stesse regole. [S1, DOCX paragrafi 15-23, 430-436; S2, “Prima di iniziare” e appendice A]

## Quantified Non-Functional Requirements

- **Durata dichiarata e allineata:** `30-45 minuti` in Word e Markdown. [S1, DOCX paragrafo 5; S2, “Istruzioni”]
- **Gestione risposte:** cancellazione entro `90 giorni` dalla decisione se proseguire e comunque non oltre `12 mesi` dalla raccolta. [S1, DOCX paragrafo 20; S2, “Prima di iniziare”]
- **Profilo e frequenza:** esperienza `<2`, `2-5`, `6-10`, `>10` anni; agenzia di `1`, `2-5`, `6-15`, `>15` persone; nuovi immobili/mese `0-5`, `6-15`, `16-30`, `>30`. [S1, DOCX paragrafi 32-51]
- **Tempo attivo per scheda:** `<15`, `15-30`, `31-60`, `61-120`, `>120` minuti, oppure non misurato/molto variabile. [S1, DOCX paragrafi 138-144]
- **Frequenza di mancanze e conflitti:** mai/quasi mai; `<1 caso su 10`; `1-3 casi su 10`; `4-6 casi su 10`; `>6 casi su 10`. [S1, DOCX paragrafi 146-158]
- **Ricontatti:** `0`, `1`, `2`, `3-5`, `>5`, oppure non misurato/molto variabile. [S1, DOCX paragrafi 160-166]
- **Campione per questionario:** massimo `3` casi; massimo `3` documenti più consultati; massimo `3` documenti con maggiore lavoro manuale; massimo `3` supporti desiderati. [S1, DOCX paragrafi 175-183, 261-262, 341-348]
- **Soglia di valore proposta al partecipante:** almeno `5`, `10` o `20 minuti` per immobile oppure almeno `20%` del tempo attuale. [S1, DOCX paragrafi 369-374]
- **Confine v0.1:** `1` caso, al massimo `3` tipi di documento e `30-50` campi. [S1, DOCX paragrafi 415-422; S3, “Scope Gate”]
- **Gate discovery:** almeno `5` interviste e `15` casi; preferibilmente `2` agenzie; almeno `3` intervistati con lo stesso problema; documenti rilevanti disponibili in almeno `12` casi; percorso credibile verso almeno `20%` di tempo attivo o `10 minuti/caso` risparmiati; almeno `1` agenzia disponibile alla prova. [S4, “Current Status”; S6, “Discovery Plan and Go/No-Go”]
- **Controllo operativo del campione:** se un partecipante descrive meno di `3` casi, l'intervistatore ne raccoglie altri separatamente fino ad almeno `5` interviste e `15` casi. [S1, DOCX paragrafo 438]

## Constraints and Assumptions

### Fatti

- Il progetto è ancora in discovery e specificazione; nessuna applicazione è stata implementata. [S4, introduzione e “Current Status”]
- Non si devono raccogliere o committare documenti reali e dati sensibili; sviluppo, test e dimostrazioni usano solo dati sintetici o correttamente anonimizzati. [S3, “Data and Privacy”; S4, “Safety Boundary”]
- Il questionario vieta allegati, planimetrie, fotografie, dati catastali completi, credenziali e altri dati identificativi o riservati. [S1, DOCX paragrafi 6-14]
- Il progetto non può diventare CRM, integrazione portali o strumento di certificazione/compliance e non può sostituire professionisti. [S3, “Scope Gate” e “Evidence and Human Review”; S6, “Must Not Build”]
- Word e Markdown riportano entrambi versione `1.2`, data `6 ottobre 2026`, durata `30-45 minuti`, identica disclosure essenziale e le stesse istruzioni operative. [S1, DOCX paragrafi 5, 15-23, 430-438; S2, “Istruzioni”, “Prima di iniziare” e appendice A]

### Inferenze

- **Tono:** l'apertura è sufficientemente leggera per una prima somministrazione informale: usa linguaggio diretto, non presenta una lunga informativa e conserva le informazioni minime necessarie. [S1, DOCX paragrafi 15-20]
- **Codice partecipante:** il codice riduce l'identificazione diretta ma non garantisce anonimato in un gruppo ristretto; il testo corretto non promette anonimato e parla invece di dettagli che non permettano di riconoscere facilmente una persona. [S1, DOCX paragrafi 19, 23-51]
- **Durata:** l'intervallo `30-45 minuti` è più credibile del precedente valore singolo e lascia spazio alla variabilità dovuta a domande aperte e fino a tre casi. [S1, DOCX paragrafi 5, 22-429]

## Contradictions

Nessuna contraddizione materiale residua.

- La disclosure nel corpo e le istruzioni dell'appendice ora concordano su volontarietà, uso delle risposte, conferma verbale, gestione tramite codice e cancellazione. [S1, DOCX paragrafi 17-20, 431-436]
- Word e Markdown sono sostanzialmente allineati su contenuto, durata, versione, profilo, nuova domanda sull'esempio inventato e appendice. [S1, DOCX paragrafi 5, 17-51, 386-397, 430-438; S2, “Istruzioni”, “Prima di iniziare”, “1. Profilo professionale”, “5. Valutazione della possibile soluzione” e appendice A]

## Ambiguities

Nessuna ambiguità materiale residua.

- Il canale per rettifica o ritiro è intenzionalmente informale — “chi ti ha consegnato il questionario” — ma è operativo per questa modalità di somministrazione e l'appendice impone di registrare la richiesta tramite codice. [S1, DOCX paragrafi 20, 435]
- Word dice “un massimo di tre casi”, mentre il Markdown invita a descriverne tre; l'appendice chiarisce in entrambi che sono ammesse risposte con meno di tre casi e che il conteggio va completato separatamente. La differenza non modifica il gate o il trattamento delle risposte. [S1, DOCX paragrafi 261-262, 438; S2, “4. Tre casi recenti” e appendice A, punto 8]

## Gaps

Nessun gap materiale residuo rispetto allo scopo del questionario e ai gate che può supportare.

### Verifica dei findings precedenti

| Finding precedente | Esito | Evidenza |
|---|---|---|
| Disclosure minima volontaria e gestione risposte | Risolto | [S1, DOCX paragrafi 17-20] |
| Coerenza tra corpo e appendice | Risolto | [S1, DOCX paragrafi 431-436] |
| Allineamento Word/Markdown | Risolto sul contenuto sostanziale | [S1, DOCX paragrafi 3-51, 386-438; S2, sezioni corrispondenti] |
| Durata incoerente | Risolto: `30-45 minuti` | [S1, DOCX paragrafo 5; S2, “Istruzioni”] |
| Versione/data obsolete | Risolto: `1.2 - 6 ottobre 2026` | [S1, DOCX paragrafo 21; S2, “Prima di iniziare”] |
| Dimensione agenzia e area geografica mancanti | Risolto | [S1, DOCX paragrafi 38-45; S2, “1. Profilo professionale”] |
| Refusi `Piu` / `e disponibile` | Risolti | [S1, DOCX paragrafi 146-158, 173; S2, sezioni 2.3 e 3.1] |
| Domanda su esempio inventato poco esplicita/assente | Risolto in linguaggio semplice | [S1, DOCX paragrafi 391-397; S2, “5. Valutazione della possibile soluzione”] |
| Osservazione diretta del software non coperta | Risolto nell'appendice con alternativa sicura | [S1, DOCX paragrafo 437; S2, appendice A, punto 7] |
| Conteggio interviste/casi non operativo | Risolto nell'appendice | [S1, DOCX paragrafo 438; S2, appendice A, punto 8] |

### Copertura del feedback operativo e dei confini

Server/cartelle e sottocartelle, stati pending/attivato, vendita/affitto, classificazione manuale, PDF/scansioni/immagini, pratiche edilizie e urbanistiche, APE, planimetria, atto di provenienza e controlli professionali sono coperti. [S1, DOCX paragrafi 68-120, 171-258]

Il questionario mantiene il confine corretto: il prodotto può segnalare evidenze, mancanze e contraddizioni, ma non certificare conformità né sostituire un professionista. [S1, DOCX paragrafi 201-258, 331-350; S3, “Evidence and Human Review”]

La compilazione del questionario non soddisfa da sola il gate: le interviste, i casi, l'osservazione e la decisione GO/NO-GO/PIVOT devono ancora essere eseguiti e documentati. Questa è un'attività successiva, non una lacuna del documento. [S4, “Current Status”; S5, “Discovery Gate”; S6, “Discovery Plan and Go/No-Go”]

## Input Issues

- Il report resta `PARTIAL` perché l'ingestione deterministica del DOCX copre paragrafi e tabelle ma non il layout. Il caller riferisce che il parent ha renderizzato e ispezionato separatamente tutte le `17` pagine con esito positivo; questa verifica visuale esterna non cambia la classificazione deterministica della copertura.
- Non era disponibile un render deterministico LibreOffice nell'evidence set fornito.
- Nessun ADR è stato letto perché ADR mode era disabilitato.

## Output

- **Path:** `/Users/davide/Personal/Projects/property-evidence-copilot/docs/analysis/questionario-validazione-review.md`
- **Purpose:** review citata della versione corretta del questionario.
- **Status:** aggiornato; nessun finding materiale residuo.
- **Coverage:** `PARTIAL` esclusivamente per il layout DOCX non incluso nell'ingestione; contenuto testuale e tabelle coperti.
