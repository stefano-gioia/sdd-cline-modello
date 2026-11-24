---
name: sdd-change
description: Gestisce una modifica o evolutiva nello spec driven development. Aggiorna prima specs/spec.md, poi plan.md e tasks.md, senza scrivere codice. Usare solo quando lo studente la richiama esplicitamente con /sdd-change.
---

# /sdd-change: gestire una modifica (evolutiva)

## Scopo
Applicare una richiesta di modifica partendo dalla specifica: prima si aggiorna la spec, poi il piano, poi i compiti. Il codice si scrive dopo, con `/sdd-implement`.

## Modalità
**Plan** per l'analisi (passi 1-4), **Act** per aggiornare i file (passi 5-8).

## Cosa leggi
1. `.clinerules/costituzione.md`
2. `specs/spec.md`, `specs/plan.md`, `specs/tasks.md` (obbligatori)
3. La richiesta di modifica dello studente

## Passi
1. Riformula la richiesta in 1 o 2 righe e chiedi se è corretta.
2. Analizza l'impatto sulla specifica ed elenca:
   - requisiti **nuovi** (con il prossimo numero R libero)
   - requisiti **modificati** (vecchio testo e nuovo testo)
   - requisiti **contraddetti** dalla richiesta: evidenziali in modo chiaro, sono la cosa più importante da decidere
   - requisiti da **rimuovere**
3. Se la richiesta va contro la costituzione (per esempio introduce un login o un backend nell'MVP), segnalalo.
4. Se mancano informazioni, fai domande (massimo 3 alla volta). Poi chiedi approvazione della proposta.
5. Dopo l'approvazione, passa ad Act e aggiorna `specs/spec.md`:
   - modifica i requisiti cambiati mantenendo il loro numero
   - marca i requisiti eliminati con `[RIMOSSO]` senza cancellarli
   - aggiungi una riga in "Storico modifiche" con data e descrizione
6. Aggiorna `specs/plan.md` solo nelle parti toccate, compresa la tabella di tracciabilità.
7. Aggiorna `specs/tasks.md`:
   - aggiungi compiti nuovi con il prossimo numero T libero, in una sezione "Modifica: <titolo>"
   - se un compito già fatto va rifatto, non riaprirlo: crea un compito nuovo che lo cita
8. Mostra il riepilogo dei file cambiati e concludi: "Prossimo passo: `/sdd-implement` in un nuovo task con `/newtask`."

## Regole
- Non scrivere codice dell'applicazione in questa skill.
- Non rinumerare requisiti o compiti esistenti.
- Una modifica alla volta. Se lo studente chiede più cose insieme, proponi di separarle.

## File prodotti
`specs/spec.md`, `specs/plan.md`, `specs/tasks.md` aggiornati.

## Punto di fermo
Due punti di fermo: dopo il passo 4 (approvazione della proposta) e dopo il passo 8 (fine, nessuna implementazione).
