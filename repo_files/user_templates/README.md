# user_templates/

Configurazione del template di lettera per ogni utente.

Ogni file `<username>.json` contiene:
1. `base_template_id`: l'ID del template di libreria (in `templates/`) scelto come base
2. `overrides`: campi specifici che l'utente vuole personalizzare rispetto al template di base

## Schema

```json
{
  "base_template_id": "default",
  "overrides": {
    "saluto": "Gentili Colleghi,",
    "firma_specializzando_label": "[NOME_SPECIALIZZANDO]",
    "ordine_sezioni": [
      "diagnosi_quotata",
      "anamnesi_patologica_remota",
      "..."
    ]
  },
  "updatedAt": "2026-04-25T..."
}
```

I file vengono creati e modificati automaticamente dall'app dal pannello "Mie personalizzazioni".

## Permessi

- Ogni utente può modificare **solo** il proprio file `<username>.json`
- Se il file non esiste, l'utente usa il template di base `templates/default.json` senza personalizzazioni
- Il pulsante "Resetta a default" nell'app cancella questo file dal repo
