# SIS — Sistemi Informativi Edilcrema snc

Raccolta dei progetti di digitalizzazione e automazione sviluppati per supportare le operazioni di **Edilcrema snc**.

L'obiettivo è costruire un ecosistema leggero di strumenti web che permettano la raccolta dati dal campo, la loro centralizzazione su Google Sheets, e l'analisi tramite database locale.

---

## Architettura

```
App web (GitHub Pages)
        │
        │  HTTP POST/GET
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
Web app mobile-first per la registrazione delle ore lavorate dal capocantiere.

**Funzionalità:**
- Inserimento ore per cantiere con data e note
- Modalità offline con coda automatica di sincronizzazione
- Invio automatico al Google Sheet al ripristino della connessione
- Storico ore filtrabile per cantiere e per mese
- Funziona da qualsiasi dispositivo senza installazione

**Link:** [edoardo2496.github.io/sis/rendicontazione-ore](https://edoardo2496.github.io/sis/rendicontazione-ore)

---

## Stack tecnologico

| Livello | Tecnologia | Note |
|---|---|---|
| Frontend | HTML / CSS / JavaScript | Nessun framework, zero dipendenze |
| Hosting | GitHub Pages | Gratuito, sempre online |
| API | Google Apps Script | Endpoint HTTP pubblico |
| Database intermedio | Google Sheets | Accessibile ovunque |
| Database analitico | SQLite | Locale, alimentato da Python |
| Sincronizzazione | Python | Script schedulato |

---

## Struttura repository

```
sis/
├── gestionale-acquisti/
│   └── index.html
├── rendicontazione-ore/
│   └── index.html
└── README.md
```

---

## Sviluppo

Progetto sviluppato da **Edoardo Crema** nell'ambito della digitalizzazione dei processi operativi e gestionali di Edilcrema snc.

