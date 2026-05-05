# templates/

Libreria dei template di lettera condivisi.

Ogni file `<id>.json` definisce un template di lettera con:
- Intestazione, saluto, apertura, chiusura
- Ordine delle sezioni
- Etichette di firma (placeholder per privacy)

## Template inclusi

- **`default.json`** — Dimissione standard a domicilio (template di default)
- **`trasferimento.json`** — Lettera di trasferimento ad altro reparto
- **`completamento.json`** — Lettera di completamento post-dimissione (più snella, solo accertamenti pendenti + raccomandazioni aggiuntive)

## Schema template

```json
{
  "id": "default",
  "name": "Dimissione standard a domicilio",
  "scenario": "dimissione_domicilio",
  "intestazione": "Alla cortese attenzione del Medico Curante",
  "saluto": "Egregi Colleghi,",
  "apertura": "dimettiamo in data odierna ...",
  "ordine_sezioni": [
    "diagnosi_quotata",
    "anamnesi_patologica_remota",
    "..."
  ],
  "chiusura": "Rimaniamo a disposizione e porgiamo cordiali saluti.",
  "firma_specializzando_label": "[NOME_SPECIALIZZANDO]",
  "firma_dirigente_label": "[NOME_DIRIGENTE]",
  "firma_ruolo_sx": "Medico in formazione specialistica",
  "firma_ruolo_dx": "Dirigente medico",
  "createdAt": "2026-04-25T..."
}
```

## Sezioni disponibili

L'array `ordine_sezioni` può contenere i seguenti id (in qualsiasi ordine):

| ID | Descrizione |
|---|---|
| `diagnosi_quotata` | Diagnosi (in apertura, dopo il saluto) |
| `anamnesi_patologica_remota` | Anamnesi patologica remota |
| `terapia_domiciliare` | Terapia domiciliare |
| `motivo_ricovero` | Motivo del ricovero |
| `ricoveri_precedenti` | Ricoveri precedenti (auto-skip se assenti) |
| `eo_neurologico_ingresso` | Esame obiettivo neurologico all'ingresso |
| `eo_generale_ingresso` | Esame obiettivo generale all'ingresso |
| `esami_ematochimici` | Esami ematochimici |
| `indagini_strumentali` | Indagini diagnostico-strumentali |
| `decorso_clinico` | Decorso clinico |
| `eo_neurologico_dimissione` | Esame obiettivo neurologico alla dimissione |
| `terapia_dimissione` | Terapia alla dimissione (tabella) |
| `visite_controllo` | Visite di controllo |
| `raccomandazioni` | Raccomandazioni |

## Modifica

I template possono essere creati/modificati/eliminati:
1. **Dall'app**: pannello "Editor Prompt" (admin), card "Libreria Template Lettera"
2. **Direttamente da GitHub**: editare i file `.json` qui

## Permessi

- Solo gli **admin** possono creare/modificare/eliminare template di libreria dall'app
- Gli utenti normali possono **scegliere** un template di base e aggiungere `overrides` personali tramite il file `user_templates/<username>.json` (non modificano la libreria)
- Il template `default` non può essere eliminato (l'app lo blocca)
