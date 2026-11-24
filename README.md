# Modello per lo spec driven development con Cline

Un repo di partenza per costruire applicazioni con Cline seguendo lo spec driven development (SDD): prima si scrive cosa deve fare l'app, poi come costruirla, poi i compiti, e solo alla fine il codice. Ogni passaggio lo rivedi e lo approvi tu.

Il progetto di esempio è una web app per **prenotare aule e laboratori** della scuola (MVP: solo frontend Angular 22, dati in `localStorage`, nessun login). Il "motore" (regole e workflow) è riusabile per qualsiasi altro progetto.

## Cosa c'è dentro

```
.clinerules/
  costituzione.md      regole del progetto, sempre attive
  angular.md           buone pratiche ufficiali di Angular, sempre attive
  workflows/           comandi da richiamare con /
    interview.md
    specify.md
    plan.md
    tasks.md
    implement.md
    verify.md
    change.md
specs/                 documenti prodotti dai workflow (all'inizio vuota)
frontend/              l'app Angular (la crei tu, vedi sotto)
.clineignore           cartelle che Cline non deve leggere
.nvmrc                 versione di Node consigliata
```

## Setup

### 1. Controlla Node
```bash
node -v
```
Angular 22 richiede Node **22.22.3 o successivo**, **24.15.0 o successivo**, oppure **26**. Se usi nvm, nella cartella del repo basta `nvm use`.

### 2. Clona il repo e aprilo in VS Code
```bash
git clone <url-del-repo> aule
cd aule
code .
```

### 3. Crea l'app Angular nella cartella `frontend/`
Dalla radice del repo:
```bash
npx -y @angular/cli@22 new aule --directory frontend --skip-git --style css --routing --ssr=false --zoneless --ai-config none
```
Cosa significano le opzioni:
- `--directory frontend`: crea l'app nella sottocartella `frontend/` (in futuro potrai aggiungere accanto una cartella `backend/`)
- `--skip-git`: il repo git esiste già, non serve crearne un altro dentro
- `--style css`, `--routing`: CSS semplice e rotte attive
- `--ssr=false`: niente rendering lato server, non serve per l'MVP
- `--zoneless`: rilevamento delle modifiche basato sui signals (è già il default)
- `--ai-config none`: niente file di regole per altri strumenti AI, le regole sono già in `.clinerules/`

Controlla che parta:
```bash
cd frontend
npx ng serve
```
Apri http://localhost:4200, poi ferma il server con `Ctrl+C` e torna alla radice (`cd ..`).

Fai il primo commit:
```bash
git add -A
git commit -m "App Angular vuota"
```

### 4. Controlla Cline
1. Apri Cline e verifica che risponda (provider e modello come configurati a lezione).
2. Nel pannello delle regole di Cline devono comparire `costituzione.md` e `angular.md`, attive.
3. Nella chat scrivi `/`: devono comparire i workflow (`interview.md`, `specify.md`, `plan.md`...). Se non compaiono, chiudi e riapri VS Code.

## Il flusso

| Passo | Comando | Modalità | Produce | Tu fai |
|---|---|---|---|---|
| 1 | `/interview.md` | Plan, poi Act per salvare | `specs/interview.md` | rispondi alle domande |
| 2 | `/specify.md` | Act | `specs/spec.md` | rileggi storie e requisiti, approvi |
| 3 | `/plan.md` | Act | `specs/plan.md` | rileggi le scelte, approvi |
| 4 | `/tasks.md` | Act | `specs/tasks.md` | controlli che i compiti siano piccoli, approvi |
| 5 | `/implement.md` | Act | codice di un compito | verifichi nel browser, fai il commit |
| 6 | `/verify.md` | Plan | tabella requisito, stato, evidenza | decidi cosa sistemare |
| * | `/change.md` | Plan, poi Act | spec, piano e compiti aggiornati | approvi la modifica, poi `/implement.md` |

Consigli:
- Apri un **nuovo task** (`/newtask`) a ogni passo: lo stato del lavoro è nei file di `specs/`, non nella chat.
- Ripeti `/implement.md` finché tutti i compiti sono spuntati. Puoi indicare un compito preciso: `/implement.md T4`.
- Fai un commit dopo ogni compito: se qualcosa va storto, torni indietro facilmente.
- Se vuoi cambiare qualcosa che è già nella specifica, usa `/change.md`: prima cambia la spec, poi il codice.

## Riusare il motore per un altro progetto

1. Copia in un repo nuovo: `.clinerules/`, `.clineignore`, `.nvmrc`, `specs/README.md`.
2. In `.clinerules/costituzione.md` riscrivi solo la **Parte 2** (cosa costruisci, vincoli, struttura).
3. In `.clinerules/workflows/interview.md` adatta la **traccia dei temi** al nuovo dominio.
4. Aggiorna `.clinerules/angular.md` dalla fonte ufficiale (il link è in cima al file) e cambia la data.
5. Parti da `/interview.md`.

## Nota sul formato delle cartelle di Cline

Le versioni più recenti di Cline usano anche una cartella `.cline/` (con `rules/`, `workflows/`, `skills/`...). Questo repo usa `.clinerules/`, che Cline continua a leggere anche nelle versioni recenti ed è riconosciuta anche da quelle meno aggiornate.
