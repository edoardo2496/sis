# SIS — Sistemi Informativi Edilcrema snc

Raccolta dei progetti di digitalizzazione e automazione sviluppati per supportare le operazioni di **Edilcrema snc**.

L'obiettivo è costruire un ecosistema leggero di strumenti web che permettano la raccolta dati dal campo, la loro centralizzazione su Google Sheets, e l'analisi tramite database locale.

---

## Architettura

```
App web (GitHub Pages)
        │
        │  HTTP GET
        ▼
Google Apps Script (endpoint pubblico)
        │
        │  appendRow / getValues
        ▼
Google Sheets (database intermedio)
        │
        │  script Python di sincronizzazione
        ▼
SQLite locale (database analitico)
        │
        ▼
Conto economico / Analisi di gestione
```

---

## Progetti

### 🛒 Gestionale Acquisti
Web app per la registrazione degli ordini di acquisto nei cantieri.

**Funzionalità:**
- Inserimento ordini con fornitore, cantiere, materiale, quantità, prezzo unitario
- Calcolo automatico del totale ordine
- Gestione stati ordine (Inviato, Confermato, Ricevuto, Fatturato, Preventivo)
- Dashboard con spesa per cantiere, spesa per fornitore, totale mese corrente
- Fornitori e cantieri caricati dinamicamente da Google Sheets

**Link:** [edoardo2496.github.io/sis/gestionale-acquisti](https://edoardo2496.github.io/sis/gestionale-acquisti)

---

### 🕐 Rendicontazione Ore Cantiere
Web app mobile-first per la registrazione strutturata delle ore di manodopera nei cantieri, sviluppata per consentire ai capocantiere di rendicontare in modo preciso le ore ordinarie e straordinarie lavorate. I dati raccolti alimentano il processo di **costing industriale** delle opere edili, contribuendo alla costruzione del conto economico per cantiere.

**Funzionalità:**
- Registrazione ore ordinarie e straordinarie per cantiere
- Selezione tipologia lavoro (muratura, scavi, carpenteria, finiture, ecc.)
- Bottoni rapidi per inserimento veloce delle ore più comuni
- Storico registrazioni filtrabile per cantiere e per mese
- Dashboard con totale ore per cantiere, per tipologia e confronto ordinarie/straordinarie
- Cantieri caricati dinamicamente da Google Sheets
- Ottimizzata per uso mobile in cantiere

**Link:** [edoardo2496.github.io/sis/registrazione-ore-personale](https://edoardo2496.github.io/sis/registrazione-ore-personale)

---

## Stack tecnologico

| Livello | Tecnologia | Note |
|---|---|---|
| Frontend | HTML / CSS / JavaScript | Nessun framework, zero dipendenze |
| Hosting | GitHub Pages | Gratuito, sempre online |
| API | Google Apps Script | Endpoint HTTP pubblico via GET |
| Database intermedio | Google Sheets | Accessibile ovunque |
| Database analitico | SQLite | Locale, alimentato da Python |
| Sincronizzazione | Python | Script schedulato |

---

## Struttura repository

```
sis/
├── gestionale-acquisti/
│   └── index.html
├── registrazione-ore-personale/
│   └── index.html
└── README.md
```

---

## Flusso dati

I dati inseriti dalle app web vengono centralizzati su Google Sheets tramite Google Apps Script. Uno script Python schedulato legge periodicamente i fogli e importa i dati nel database SQLite locale, dove vengono elaborati per:

- **Conto economico per cantiere** — costi di acquisto + costo manodopera
- **Analisi di costing industriale** — costo orario reale per tipologia di lavoro
- **Controllo di gestione** — confronto costi previsti vs consuntivi

---

## Sviluppo

Progetto sviluppato da **Edoardo Crema** nell'ambito della digitalizzazione dei processi operativi e gestionali di Edilcrema snc.
