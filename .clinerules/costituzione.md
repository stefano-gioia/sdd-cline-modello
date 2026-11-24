# Costituzione del progetto

Queste regole valgono per ogni richiesta, in ogni fase. Se una richiesta va contro una regola, fermati e segnalalo invece di procedere.

La prima parte è generale e si riusa in qualsiasi progetto. La seconda parte descrive questo progetto: quando riusi il repo per un progetto nuovo, riscrivi solo la seconda parte.

## Parte 1. Regole generali (non cambiano tra progetti)

### Metodo di lavoro
- Si lavora con lo spec driven development: prima la specifica, poi il piano, poi i compiti, poi il codice.
- I documenti del metodo stanno nella cartella `specs/` alla radice del repo:
  - `specs/interview.md`: risposte dell'intervista e dubbi aperti
  - `specs/spec.md`: user story, requisiti numerati (R1, R2...), casi limite
  - `specs/plan.md`: come si costruisce (componenti, servizi, modello dati)
  - `specs/tasks.md`: compiti piccoli numerati (T1, T2...)
- La specifica è la fonte di verità. Se il codice e la specifica non sono d'accordo, si corregge prima la specifica (con `/change.md`) e poi il codice.
- Non inventare requisiti. Se un'informazione manca, scrivi `[DA CHIARIRE]` e chiedi.
- Ogni passaggio finisce con un punto di fermo: mostri il risultato e aspetti l'approvazione esplicita dello studente prima di andare avanti.
- Un compito per volta. Non anticipare il lavoro dei compiti successivi.
- Non cancellare e non rinumerare requisiti o compiti già scritti: quelli eliminati si marcano `[RIMOSSO]`, quelli nuovi prendono il numero successivo libero.

### Codice
- Modifica solo i file necessari al compito in corso.
- Niente dipendenze npm nuove senza chiedere prima e spiegare perché servono.
- Nomi di variabili, funzioni e file in inglese; testi visibili all'utente in italiano.
- Dopo ogni modifica al codice il progetto deve compilare senza errori.
- Non scrivere chiavi, password o token nel codice o nei documenti.

### Comandi
- Il frontend sta nella cartella `frontend/`. I comandi npm e ng vanno lanciati da lì, per esempio `cd frontend && npx ng build`.
- Comandi utili:
  - compilare: `cd frontend && npx ng build`
  - test: `cd frontend && npx ng test --watch=false`
  - avviare in locale: `cd frontend && npx ng serve` (resta attivo: non aspettare che finisca)
- Non lanciare comandi git che modificano la storia (reset, rebase, push --force). Puoi proporre un commit, ma lo esegue lo studente.

## Parte 2. Questo progetto: prenotazione aule e laboratori

### Cosa stiamo costruendo
Una web app per prenotare aule e laboratori della scuola. Questa versione è un MVP (minimum viable product): la versione più piccola che si può già usare davvero.

### Vincoli dell'MVP
- Solo frontend, Angular 22, nella cartella `frontend/`.
- Nessun login. Chi prenota scrive il proprio nome in un campo di testo.
- I dati restano nel browser, in `localStorage`. Nessun backend, nessuna chiamata HTTP.
- L'elenco delle aule è un dato iniziale scritto nel codice (seed) e caricato al primo avvio.

### Regola sui dati (importante per il futuro backend)
- Solo un servizio dedicato alla persistenza legge e scrive `localStorage`. Nessun componente e nessun altro servizio usa `localStorage` direttamente.
- I componenti parlano solo con i servizi, mai con il meccanismo di salvataggio.
- Scopo: in una lezione successiva si sostituirà `localStorage` con un backend (Supabase, Firebase, PocketBase o Node con SQLite) cambiando solo il servizio di persistenza.

### Date e orari
- Le date si salvano come testo `YYYY-MM-DD` e gli orari come testo `HH:mm`, nell'ora locale italiana.
- Non salvare oggetti `Date` in `localStorage`.
- Le regole di prenotazione (sovrapposizioni, orari, durate) stanno in un servizio, non nei componenti, così si possono testare.

### Struttura delle cartelle (dentro `frontend/src/app/`)
- `models/`: interfacce e tipi TypeScript
- `services/`: logica e persistenza
- `pages/`: componenti collegati a una rotta
- `components/`: componenti riusabili più piccoli

### Test
- Le regole di prenotazione hanno test unitari (Vitest, già configurato da Angular) nel servizio che le contiene.
- Il resto si verifica a mano nel browser, seguendo il modo di verifica scritto nel compito.

### Da evitare
- NgModules, `standalone: true`, `*ngIf` e `*ngFor`, iniezione nel costruttore, `CommonModule`: vedi `angular.md`.
- Librerie di componenti (Angular Material, Bootstrap e simili): nell'MVP bastano HTML e CSS.
- Funzionalità non presenti nella specifica, anche se sembrano utili.
