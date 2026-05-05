# hospital-assistant-data

Repository di dati per l'app **Lettera.AI** (clinical letter generation tool).

Questo repository contiene:
- 📚 Casi clinici della libreria (con fingerprint patologia-specifici)
- 📝 Prompt globali del sistema di generazione AI
- 📋 Template di lettera (libreria condivisa)
- 👤 Personalizzazioni per utente (override regole + template)
- 🔧 Configurazione dell'app
- 🐛 Segnalazioni utenti

## Struttura

```
hospital-assistant-data/
├── cases.json                    # Libreria casi clinici (fingerprint)
├── reports.json                  # Segnalazioni errori
├── user_preferences.json         # Preferenze utente per generazione
│
├── prompts/                      # 📝 Prompt globali (admin)
│   ├── default_sys.md            # Prompt sistema generazione lettera
│   ├── fingerprint_extract.md    # Prompt estrazione decorso patologia
│   └── verifica.md               # Prompt verifica anti-allucinazioni
│
├── templates/                    # 📋 Libreria template (admin)
│   ├── default.json              # Dimissione standard a domicilio
│   ├── trasferimento.json        # Trasferimento ad altro reparto
│   └── completamento.json        # Lettera di completamento
│
├── user_overrides/               # 👤 Aggiunte personali (per utente)
│   └── <username>.md             # Es. raffaele.md
│
├── user_templates/               # 👤 Scelta template + customizzazioni utente
│   └── <username>.json           # Es. raffaele.json
│
└── config/
    └── version.json              # Metadata versioning
```

## Modifica dei contenuti

### Dall'app (consigliato)

- **Admin** (raffaele, test) hanno accesso al pannello "Editor Prompt" che permette di:
  - Modificare i prompt globali (`prompts/`)
  - Creare/modificare/eliminare template di libreria (`templates/`)
  - Le modifiche vengono committate automaticamente tramite GitHub API

- **Tutti gli utenti** hanno accesso al pannello "Mie personalizzazioni" che permette di:
  - Aggiungere regole/preferenze personali (file in `user_overrides/`)
  - Scegliere un template di base e personalizzarlo (file in `user_templates/`)

### Direttamente da GitHub

Tutti i file possono essere editati anche direttamente da GitHub web. L'app li ricaricherà automaticamente al prossimo login (cache 1 ora) o quando l'admin clicca "Ricarica da repo".

## Fallback embedded

Se questa repository è irraggiungibile o un file specifico non esiste, l'app usa fallback embedded nel codice JavaScript. Questo significa che l'app continua a funzionare anche in assenza di questi file, ma con il comportamento di default.

## Permessi GitHub

Il token GitHub di ogni utente deve avere permessi `repo` (read+write) su questo repository. Le modifiche scritte da utenti normali sono limitate dall'app a:
- Il proprio file `user_overrides/<username>.md`
- Il proprio file `user_templates/<username>.json`

(NB: GitHub API non impone questi limiti — il controllo è applicato dall'app stessa.)

## Setup iniziale

Per inizializzare un repository vuoto, copiarci il contenuto della cartella iniziale fornita dall'app:

1. Caricare i file in `prompts/` (3 file `.md`)
2. Caricare i file in `templates/` (almeno `default.json`)
3. Creare le directory `user_overrides/` e `user_templates/` (anche solo con un README dentro)
4. Caricare `config/version.json`

L'app può funzionare anche senza questa struttura, ma una volta presente diventa la sorgente unica di verità per i prompt e template.
