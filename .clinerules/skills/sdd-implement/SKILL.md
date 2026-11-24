---
name: sdd-implement
description: Fase 5 dello spec driven development. Implementa un solo compito di specs/tasks.md, lo verifica e lo spunta. Usare solo quando lo studente la richiama esplicitamente con /sdd-implement.
---

# /sdd-implement: realizzare un compito

## Scopo
Scrivere il codice di UN solo compito di `specs/tasks.md`, verificarlo e segnarlo come fatto.

## Modalità
**Act**.

## Cosa leggi
1. `.clinerules/costituzione.md` e `.clinerules/angular.md`
2. `specs/tasks.md` (obbligatorio: se manca, fermati e suggerisci `/sdd-tasks`)
3. `specs/spec.md`: solo i requisiti citati dal compito
4. `specs/plan.md`: solo le parti che riguardano il compito
5. I file del progetto che il compito tocca

## Passi
1. Scegli il compito:
   - se lo studente ha indicato un numero (per esempio `/sdd-implement T3`), usa quello;
   - altrimenti prendi il primo compito con `- [ ] Stato`.
2. Scrivi in 2 o 3 righe cosa farai e quali file toccherai. Chiedi conferma.
3. Implementa solo quel compito, rispettando costituzione e regole Angular.
4. Lancia la compilazione: `cd frontend && npx ng build`. Se ci sono errori, correggili.
5. Se il compito prevede test, lanciali: `cd frontend && npx ng test --watch=false`. Se falliscono, correggi.
6. Spiega allo studente come fare la verifica manuale scritta nel compito (passi nel browser e risultato atteso). Chiedi di confermare che funziona.
7. Solo dopo la conferma, cambia lo stato del compito in `- [x] Stato` in `specs/tasks.md`.
8. Proponi il commit, senza eseguirlo:
   `git add -A && git commit -m "T<n>: <titolo del compito>"`
9. Concludi: "Prossimo passo: apri un nuovo task con `/newtask` e lancia `/sdd-implement` per il compito successivo."

## Regole
- Un compito alla volta. Se ti accorgi che serve altro lavoro, non farlo: proponi di aggiungere un compito con `/sdd-change` o di modificare `specs/tasks.md`.
- Se il compito richiede qualcosa che contraddice la specifica o il piano, fermati e segnalalo.
- Non segnare il compito come fatto se la build fallisce, se i test falliscono o se lo studente non ha confermato.

## File prodotto
Il codice del compito e `specs/tasks.md` aggiornato (solo la casella dello stato).

## Punto di fermo
Dopo il punto 8 fermati. Non iniziare il compito successivo nello stesso task.
