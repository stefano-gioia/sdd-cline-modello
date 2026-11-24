# /interview.md: intervista per raccogliere i requisiti

## Scopo
Capire cosa deve fare l'applicazione facendo domande allo studente. In questa fase NON si scrive codice e NON si scrive la specifica.

## Modalità
Usa la modalità **Plan** per tutta l'intervista. Alla fine chiederai di passare ad **Act** solo per salvare il file.

## Cosa leggi
1. `.clinerules/costituzione.md` (parte 2: cosa stiamo costruendo e vincoli)
2. `specs/interview.md`, se esiste già: in quel caso riprendi da dove si era rimasti

## Passi
1. Riassumi in 2 o 3 righe cosa hai capito del progetto dalla costituzione. Chiedi se è corretto.
2. Fai le domande **a gruppi di massimo 3**. Aspetta le risposte prima del gruppo successivo.
3. Copri i temi della traccia qui sotto, nell'ordine che ti sembra più naturale. Se una risposta apre un dubbio, fai una domanda di approfondimento.
4. Non suggerire tu le risposte e non dare per scontate le regole: chiedi come funziona davvero.
5. Quando i temi sono coperti, mostra un riepilogo con la struttura del file prodotto (vedi sotto) e chiedi: "Il riepilogo è corretto? Vuoi aggiungere o cambiare qualcosa?"
6. Quando lo studente approva, chiedigli di passare in modalità Act e salva `specs/interview.md`.
7. Concludi dicendo: "Prossimo passo: `/specify.md`. Ti consiglio di aprire un nuovo task con `/newtask`."

## Traccia dei temi
Adatta la traccia al progetto descritto nella costituzione. Per un sistema di prenotazione i temi sono:
- Chi usa l'app e chi può prenotare
- Quali risorse si prenotano (aule, laboratori, aule speciali) e quali informazioni hanno (nome, capienza, attrezzature)
- Fasce orarie fisse o orari liberi
- Durata minima e massima di una prenotazione
- Giorni e orari di apertura della scuola, giorni di chiusura
- Quanto in anticipo si può prenotare
- Conflitti: due prenotazioni sulla stessa risorsa nello stesso momento
- Priorità tra persone o tra usi diversi
- Cancellazioni: chi può cancellare e fino a quando
- Cosa deve vedere chi apre l'app (elenco, calendario, disponibilità)
- Cosa resta fuori da questa prima versione (MVP)

## Regole
- Nessun codice, nessun file oltre a `specs/interview.md`.
- Domande brevi e concrete, una cosa per domanda.
- Se lo studente non sa rispondere, registra il punto tra i dubbi aperti e vai avanti.

## File prodotto: `specs/interview.md`
```markdown
# Intervista

## Progetto in breve
(2 o 3 righe)

## Risposte per tema
### <tema>
- <risposta dello studente, con le sue parole>

## Decisioni prese
- <decisione>

## Fuori dall'MVP
- <cosa resta per dopo>

## Dubbi aperti
- <domanda senza risposta>
```

## Punto di fermo
Non salvare il file finché lo studente non ha approvato il riepilogo.
