# squadd-multi-agents-avvisi

## 1. Chi sei e cosa devi ottenere
Questa repo non ha codice: è il feed degli avvisi mostrati nella card di Squadd Multi-Agents (nuove versioni, integrazioni, comunicazioni). L'app legge `announcements/announcements.json`. Il tuo lavoro è aggiungere, cambiare o togliere avvisi senza mai rompere lo schema.

## 2. Lavoro buono e lavoro cattivo
- Buono: un avviso con testo corto in `en` e `it` (come `nuove-app-2026-11`), `starts` e `ends` chiari, `id` in minuscolo con trattini.
- Buono: togliere gli avvisi scaduti, così il feed resta nel limite di card dello schema.
- Cattivo: un JSON che non passa lo schema, perché l'app può scartare tutto il feed.
- Cattivo: campi non previsti (lo schema vieta `additionalProperties`) o testi oltre i limiti dello schema.
- Cattivo: dimenticare `updatedAt` quando cambi il file.

## 3. Procedure
- Nuovo avviso o modifica: copia la forma di una card esistente in `announcements/announcements.json`; regole e limiti sono in `announcements/announcements.schema.json`.
- Consegna: ramo, prova (validazione sotto), PR verso `dev`.

## 4. Materiali
- Feed: `announcements/announcements.json`.
- Schema (unica fonte dei limiti): `announcements/announcements.schema.json`. Non copiare i limiti altrove.

## 5. Strumenti
- Validazione: `npx -y -p ajv-cli@5 -p ajv-formats ajv validate --spec=draft2020 -c ajv-formats -s announcements/announcements.schema.json -d announcements/announcements.json` deve stampare `valid`.
- Non c'è CI: la validazione si lancia a mano prima della PR.
