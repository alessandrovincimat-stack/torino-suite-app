# torino-suite-app

Due applicazioni web indipendenti, ognuna in un unico file HTML senza dipendenze da installare
né passaggi di build: basta aprire il file (o servirlo da un qualsiasi hosting statico).

## `index.html` — Torino Suite, controllo accessi

Gestione degli ospiti per affitti brevi: schedine Alloggiati Web, ISTAT/Regione Piemonte,
imposta di soggiorno, fatturazione tramite Fatture in Cloud e lettura automatica dei documenti.
Richiede il proprio backend, configurato da *Impostazioni → Backend*.

## `quaderno.html` — Quaderno, appunti a penna con IA

Quaderno digitale per la scuola: si scrive a mano con la penna (Apple Pencil, penne Windows Ink,
stilo Android) come su un foglio vero, e l'intelligenza artificiale prepara pagine di appunti
già impaginate che poi si annotano a mano.

### Scrittura
- Penna con **spessore variabile in base alla pressione** e quattro punte pronte (fine, media, grossa, marker);
  chi non ha una penna sensibile alla pressione ottiene lo stesso effetto dalla velocità del tratto.
- **Rifiuto del palmo**: dopo il primo tratto di penna il dito serve solo a spostare e ingrandire,
  quindi si può appoggiare la mano sullo schermo.
- Evidenziatore con fusione *multiply*, gomma **parziale** (cancella solo dove passi, spezzando il tratto)
  oppure **a tratto intero**, e supporto per la punta-gomma della penna.
- Selezione a lazo: sposta, ingrandisce, duplica, elimina e ricolora quello che cerchi.
- Forme (linea, freccia, rettangolo, ellisse, triangolo) e **raddrizzamento automatico**:
  disegni un cerchio a mano libera, resti fermo un istante e diventa perfetto.
- Caselle di testo, immagini da file o incollate dagli appunti, annulla/ripeti a più livelli.
- Zoom con due dita, rotella e pulsanti; scorciatoie da tastiera.

### Pagine e quaderni
- Quaderni divisi per materia, con ricerca, colore e copertina che mostra l'anteprima della prima pagina.
- Nove tipi di foglio (bianco, righe, quadretti, puntini, Cornell, pentagramma, righe con margine…)
  e quattro colori di carta, compresa una carta scura per scrivere di sera.
- Miniature laterali per muoversi tra le pagine, duplicarle ed eliminarle.
- **Importazione di un PDF** (compiti, dispense, slide) che diventa lo sfondo di pagine da annotare.
- Esportazione in **PDF** (generato senza librerie esterne) e in PNG.
- Tutto resta sul dispositivo in IndexedDB, con salvataggio automatico e copia di backup
  esportabile/ripristinabile in un file.

### Intelligenza artificiale
Il pulsante **IA** genera pagine nuove, già impaginate e pronte da studiare: spiegazioni,
riassunti, schemi di ripasso, esercizi con la soluzione, verifiche con le risposte nascondibili,
formulari, traduzioni e correzioni. Attivando *«leggi anche la pagina che sto guardando»* manda al
modello un'immagine del foglio, così può correggere quello che è stato scritto a mano, risolvere un
esercizio o riassumere un PDF importato. Il risultato arriva come contenuto strutturato e viene
impaginato automaticamente su quante pagine servono, mantenendosi nitido a ogni livello di zoom.

Si configura da *Impostazioni → Intelligenza artificiale*, in due modi:

1. **Tramite un proprio server** (consigliato): l'app invia una `POST` a `/api/ia` con lo stesso
   corpo dell'API Anthropic e si aspetta indietro la risposta così com'è; la chiave resta sul
   server. Se serve, si può aggiungere una parola segreta inviata nell'intestazione `x-app-secret`.
2. **Chiave API sul dispositivo**: più rapido da provare, ma la chiave resta salvata nel browser e
   le richieste partono dal dispositivo. Da evitare su dispositivi condivisi.
