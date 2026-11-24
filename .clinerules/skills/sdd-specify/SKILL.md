---
name: sdd-specify
description: Fase 2 dello spec driven development. Trasforma specs/interview.md in specs/spec.md con user story, requisiti EARS numerati e casi limite. Nessun codice. Usare solo quando lo studente la richiama esplicitamente con /sdd-specify.
---

# /sdd-specify: dalla intervista alla specifica

## Scopo
Trasformare l'intervista in una specifica chiara: user story, requisiti numerati scritti con EARS, casi limite. Descrive COSA fa l'app, non COME è fatta.

## Modalità
**Act** (devi scrivere un file). Non scrivere codice.

## Cosa leggi
1. `.clinerules/costituzione.md`
2. `specs/interview.md` (obbligatorio: se manca, fermati e suggerisci `/sdd-interview`)

## Passi
1. Scrivi le user story: poche, piccole e verificabili. Formato: "Come <chi>, voglio <cosa>, per <perché>". Numerale US1, US2...
2. Sotto ogni storia scrivi i criteri di accettazione come requisiti EARS, numerati in modo progressivo su tutto il documento: R1, R2, R3...
3. Usa solo questi cinque modelli EARS:
   - Sempre: "Il sistema deve <risposta>."
   - Quando: "Quando <evento>, il sistema deve <risposta>."
   - Mentre: "Mentre <stato>, il sistema deve <risposta>."
   - Dove: "Dove <caratteristica presente>, il sistema deve <risposta>."
   - Se/allora: "Se <condizione indesiderata>, allora il sistema deve <risposta>."
4. Ogni requisito deve essere verificabile: qualcuno deve poter dire "sì, lo fa" o "no, non lo fa".
5. Elenca i casi limite (dati mancanti, valori al confine, conflitti) e collega ciascuno a un requisito.
6. Tutto ciò che l'intervista non chiarisce va marcato `[DA CHIARIRE]` con la domanda da fare. Non inventare la risposta.
7. Salva `specs/spec.md`.
8. Mostra un riepilogo: numero di storie, numero di requisiti, elenco dei `[DA CHIARIRE]`.
9. Chiedi allo studente di rileggere il file e di approvarlo o indicare correzioni. Applica le correzioni e richiedi approvazione.
10. Quando approvato, concludi: "Prossimo passo: `/sdd-plan`, in un nuovo task con `/newtask`."

## Regole
- Niente nomi di componenti, servizi, librerie o file: quelli vanno nel piano.
- Un requisito dice una sola cosa. Se contiene "e" tra due comportamenti diversi, dividilo.
- Usa le parole dello studente per i concetti del dominio (aula, corso, fascia...).

## File prodotto: `specs/spec.md`
```markdown
# Specifica

## Obiettivo
(2 o 3 righe)

## Glossario
- <termine>: <significato>

## User story e requisiti

### US1. <titolo breve>
Come <chi>, voglio <cosa>, per <perché>.

- R1. <requisito EARS>
- R2. <requisito EARS>

### US2. <titolo breve>
...

## Casi limite
- <caso> (vedi R..)

## Fuori ambito (MVP)
- <cosa non si fa ora>

## Da chiarire
- [DA CHIARIRE] <domanda>

## Storico modifiche
- <data>: prima versione
```

## Punto di fermo
Non passare al piano. Aspetta l'approvazione esplicita della specifica.
