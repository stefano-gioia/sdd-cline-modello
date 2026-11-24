---
name: sdd-verify
description: Controlla, senza modificare nulla, che il codice rispetti ogni requisito di specs/spec.md e mostra una tabella requisito, stato, evidenza. Usare solo quando lo studente la richiama esplicitamente con /sdd-verify.
---

# /sdd-verify: controllare che il codice rispetti la specifica

## Scopo
Confrontare ogni requisito della specifica con il codice e dire se è soddisfatto, con un'evidenza. NON si modifica nulla.

## Modalità
**Plan** (solo lettura). Se lo studente chiede di salvare il resoconto, passa ad Act solo per quello.

## Cosa leggi
1. `specs/spec.md` (obbligatorio)
2. `specs/tasks.md`
3. Il codice in `frontend/src/app/`

## Passi
1. Per ogni requisito R della specifica (anche quelli marcati `[RIMOSSO]`, per controllare che non siano rimasti nel codice) cerca nel codice dove viene realizzato.
2. Assegna uno stato:
   - **OK**: realizzato, e l'evidenza lo mostra
   - **Parziale**: realizzato solo in parte (spiega cosa manca)
   - **Mancante**: non trovato nel codice
   - **Da provare a mano**: non si capisce dal codice, serve una prova nel browser (scrivi quale)
3. L'evidenza è concreta: percorso del file e nome della funzione o del test, oppure i passi della prova manuale.
4. Se lo studente è d'accordo, proponi di lanciare build e test (`cd frontend && npx ng build`, `cd frontend && npx ng test --watch=false`) e riporta l'esito. Questi comandi non modificano il codice.
5. Segnala anche:
   - compiti segnati come fatti ma con requisiti non OK
   - codice che fa cose non previste dalla specifica
6. Mostra la tabella e il riepilogo.
7. Concludi suggerendo cosa fare: `/sdd-implement` per completare un compito, oppure `/sdd-change` se è la specifica a dover cambiare.

## Regole
- Non correggere nulla, nemmeno un errore evidente: lo segnali e basta.
- Non dare OK senza evidenza.

## Risultato (in chat, oppure in `specs/verifica.md` se richiesto)
```markdown
# Verifica del <data>

| Requisito | Stato | Evidenza |
|---|---|---|
| R1 | OK | `services/booking.service.ts`, metodo `hasConflict`, test "rifiuta sovrapposizione" |

## Riepilogo
- OK: n, Parziale: n, Mancante: n, Da provare a mano: n
- Build: <esito>, Test: <esito>

## Altre segnalazioni
- ...
```

## Punto di fermo
Finisci con la tabella. Non avviare correzioni.
