# prompts/

Prompt globali del sistema, condivisi da tutti gli utenti.

## File

- **`default_sys.md`** — Prompt di sistema principale per la generazione delle lettere di dimissione/trasferimento. Contiene tutte le regole editoriali (formato, sottolineature, NIHSS, trend con frecce, interpretazione note di diario, ecc.).

- **`fingerprint_extract.md`** — Prompt per l'estrazione del decorso patologia-specifico (fingerprint V3) da una lettera reale. Utilizzato quando si aggiunge un caso alla libreria con estrazione AI.

- **`verifica.md`** — Prompt per il controllo automatico anti-allucinazioni della lettera generata contro la cartella clinica anonimizzata.

## Modifica

I prompt vengono caricati automaticamente all'avvio dell'app (con cache di 1 ora in sessionStorage). Possono essere modificati:

1. **Dall'app**: pannello "Editor Prompt" (visibile solo agli admin), che committa le modifiche tramite GitHub API
2. **Direttamente da GitHub**: editare i file `.md` qui — al prossimo refresh con bypass cache, l'app prenderà la nuova versione

## Fallback

Se i file qui non esistono o il repo è irraggiungibile, l'app usa un fallback embedded nel codice JavaScript. Quindi modifiche errate o file mancanti non rompono il sistema, ma fanno tornare al comportamento embedded.

## Permessi

- Solo gli **admin** (raffaele, test) possono modificare questi file dall'app
- Tutti gli utenti li leggono al login
