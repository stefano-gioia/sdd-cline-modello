---
name: sdd-plan
description: Fase 3 dello spec driven development: da specs/spec.md e dalla costituzione produce il piano tecnico specs/plan.md. Nessun codice. Usare solo quando lo studente la richiama esplicitamente con /sdd-plan.
---

# /sdd-plan: dalla specifica al piano tecnico

## Scopo
Decidere COME costruire ciò che la specifica chiede, rispettando la costituzione e le regole Angular. Ancora nessun codice.

## Modalità
**Act** (devi scrivere un file). Non scrivere codice dell'applicazione.

## Cosa leggi
1. `.clinerules/costituzione.md`
2. `.clinerules/angular.md`
3. `specs/spec.md` (obbligatorio: se manca, fermati e suggerisci `/sdd-specify`)
4. Se esiste, la struttura attuale di `frontend/src/app/` (solo per sapere cosa c'è già)

## Passi
1. Se in `specs/spec.md` ci sono `[DA CHIARIRE]` che bloccano il piano, elencali e chiedi allo studente come procedere prima di continuare.
2. Definisci il modello dati come interfacce TypeScript (solo le firme, in un blocco di codice dentro il piano).
3. Elenca i servizi: nome, responsabilità, metodi principali. Rispetta la regola sui dati della costituzione (un solo servizio tocca la persistenza).
4. Elenca le rotte e i componenti: nome, cartella, cosa mostra, quali servizi usa.
5. Scrivi le scelte importanti con una riga di motivazione ciascuna (perché così e non in un altro modo).
6. Scrivi la tabella di tracciabilità: ogni requisito R della specifica deve comparire almeno una volta.
7. Salva `specs/plan.md`.
8. Chiedi allo studente di rileggerlo e approvarlo. Applica le correzioni richieste.
9. Quando approvato, concludi: "Prossimo passo: `/sdd-tasks`, in un nuovo task con `/newtask`."

## Regole
- Il piano deve restare semplice: è un MVP. Se una scelta aggiunge complessità, motivala o toglila.
- Niente librerie esterne non previste dalla costituzione.
- Se ti accorgi che la specifica è incompleta o contraddittoria, non correggerla tu: segnalalo e suggerisci `/sdd-change`.

## File prodotto: `specs/plan.md`
```markdown
# Piano tecnico

## Panoramica
(3 o 4 righe: come è organizzata l'app)

## Modello dati
(blocco di codice TypeScript con le interfacce)

## Servizi
| Servizio | Responsabilità | Metodi principali |
|---|---|---|

## Rotte e componenti
| Rotta | Componente | Cartella | Cosa mostra | Servizi usati |
|---|---|---|---|---|

## Persistenza
(chiavi di localStorage, formato dei dati, dati iniziali)

## Scelte e motivazioni
- <scelta>: <perché>

## Tracciabilità
| Requisito | Dove viene realizzato |
|---|---|
| R1 | ... |
```

## Punto di fermo
Non creare compiti e non scrivere codice. Aspetta l'approvazione esplicita del piano.
