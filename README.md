# Modello per lo spec driven development con Cline

Un repo di partenza per costruire applicazioni con Cline seguendo lo spec driven development (SDD): prima si scrive cosa deve fare l'app, poi come costruirla, poi i compiti, e solo alla fine il codice. Ogni passaggio lo rivedi e lo approvi tu.

Il progetto di esempio è una web app per **prenotare le aule** della scuola (MVP: solo frontend Angular 22, dati in `localStorage`, nessun login). Il "motore" (regole e skill) è riusabile per qualsiasi altro progetto.

## Cosa c'è dentro

```
.clinerules/
  costituzione.md      regole del progetto, sempre attive
  angular.md           buone pratiche ufficiali di Angular, sempre attive
  skills/              le fasi del metodo, da richiamare con /
    sdd-interview/SKILL.md
    sdd-specify/SKILL.md
    sdd-plan/SKILL.md
    sdd-tasks/SKILL.md
    sdd-implement/SKILL.md
    sdd-verify/SKILL.md
    sdd-change/SKILL.md
specs/                 documenti prodotti dalle skill (all'inizio vuota)
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
2. Clicca l'icona della bilancia sotto la chat (accanto al nome del modello):
   - nella scheda **Rules**, tra le Workspace Rules, ci sono `angular.md` e `costituzione.md`, attive;
   - nella scheda **Skills**, tra le Workspace Skills, ci sono le sette skill `sdd-...`, attive.
3. Nella chat scrivi `/sdd`: devono comparire le sette skill. Se non compaiono, chiudi e riapri VS Code.

## Il flusso

| Passo | Comando | Modalità | Produce | Tu fai |
|---|---|---|---|---|
| 1 | `/sdd-interview` | Plan, poi Act per salvare | `specs/interview.md` | rispondi alle domande |
| 2 | `/sdd-specify` | Act | `specs/spec.md` | rileggi storie e requisiti, approvi |
| 3 | `/sdd-plan` | Act | `specs/plan.md` | rileggi le scelte, approvi |
| 4 | `/sdd-tasks` | Act | `specs/tasks.md` | controlli che i compiti siano piccoli, approvi |
| 5 | `/sdd-implement` | Act | codice di un compito | verifichi nel browser, fai il commit |
| 6 | `/sdd-verify` | Plan | tabella requisito, stato, evidenza | decidi cosa sistemare |
| * | `/sdd-change` | Plan, poi Act | spec, piano e compiti aggiornati | approvi la modifica, poi `/sdd-implement` |

Consigli:
- Apri un **nuovo task** (`/newtask`) a ogni passo: lo stato del lavoro è nei file di `specs/`, non nella chat.
- Ripeti `/sdd-implement` finché tutti i compiti sono spuntati. Puoi indicare un compito preciso: `/sdd-implement T4`.
- Fai un commit dopo ogni compito: se qualcosa va storto, torni indietro facilmente.
- Se vuoi cambiare qualcosa che è già nella specifica, usa `/sdd-change`: prima cambia la spec, poi il codice.

## Riusare il motore per un altro progetto

1. Copia in un repo nuovo: `.clinerules/`, `.clineignore`, `.nvmrc`, `specs/README.md`.
2. In `.clinerules/costituzione.md` riscrivi solo la **Parte 2** (cosa costruisci, vincoli, struttura).
3. In ``.clinerules/skills/sdd-interview/SKILL.md`` adatta la **traccia dei temi** al nuovo dominio.
4. Aggiorna `.clinerules/angular.md` dalla fonte ufficiale (il link è in cima al file) e cambia la data.
5. Parti da `/sdd-interview`.

## Nota sul formato delle cartelle di Cline

Le fasi del metodo sono **skill** (una cartella con un file `SKILL.md`), non workflow: Cline ha deprecato i workflow in favore delle skill, che seguono uno standard aperto usato anche da altri assistenti. Ogni skill si richiama con `/nome-skill`; il prefisso `sdd-` le tiene raggruppate ed evita conflitti con i comandi di Cline.

Le versioni più recenti di Cline usano anche una cartella `.cline/` (con `rules/`, `skills/`...). Questo repo usa `.clinerules/`, che Cline continua a leggere. Se in futuro serve, basta spostare il contenuto in `.cline/rules/` e `.cline/skills/`.
