# /tasks.md: dal piano ai compiti

## Scopo
Dividere il piano in compiti piccoli, da fare uno alla volta, ciascuno verificabile.

## Modalità
**Act** (devi scrivere un file). Non scrivere codice dell'applicazione.

## Cosa leggi
1. `.clinerules/costituzione.md`
2. `specs/spec.md`
3. `specs/plan.md` (obbligatorio: se manca, fermati e suggerisci `/plan.md`)
4. `specs/tasks.md`, se esiste già: in quel caso aggiungi i compiti nuovi senza toccare quelli esistenti

## Passi
1. Ordina il lavoro in modo che dopo ogni compito l'app compili e, quando possibile, si veda qualcosa nel browser.
2. Parti dalle fondamenta (modello dati, servizio di persistenza, regole), poi le pagine storia per storia.
3. Scrivi ogni compito con il formato qui sotto. Numerali T1, T2...
4. Ogni compito deve essere piccolo: tocca pochi file e si fa in una sola sessione.
5. Ogni compito indica i requisiti che copre. Alla fine controlla che ogni R della specifica sia coperto da almeno un compito ed elenca quelli scoperti.
6. Il modo di verifica è concreto: un comando da lanciare (build o test) e/o cosa controllare nel browser, passo per passo.
7. Salva `specs/tasks.md`.
8. Chiedi allo studente di rileggerlo e approvarlo. Applica le correzioni richieste.
9. Quando approvato, concludi: "Prossimo passo: `/implement.md`, in un nuovo task con `/newtask`. Si fa un compito per volta."

## Regole
- Le regole di prenotazione (o in generale la logica) hanno un compito dedicato che include i test unitari.
- Non mettere nello stesso compito due storie diverse.
- Non scrivere il codice dentro i compiti: solo cosa fare e come verificarlo.

## File prodotto: `specs/tasks.md`
```markdown
# Compiti

## US1. <titolo della storia>

### T1. <titolo breve>
- [ ] Stato
- Requisiti: R1, R2
- Cosa fare: <2 o 3 righe>
- File coinvolti: <percorsi previsti>
- Verifica: <comando e/o passi nel browser con il risultato atteso>

### T2. ...

## Copertura
- Requisiti non coperti: <elenco, oppure "nessuno">
```

## Punto di fermo
Non iniziare a implementare. Aspetta l'approvazione esplicita dei compiti.
