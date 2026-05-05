# user_overrides/

Aggiunte personali alle regole editoriali, per ogni utente.

Ogni file `<username>.md` contiene regole/preferenze additive che vengono **aggiunte** al prompt di sistema globale al momento della generazione della lettera. Non sostituiscono le regole standard.

## Esempio

`user_overrides/raffaele.md`:

```
AGGIUNTE PERSONALI:
- Per pazienti con FA cronica: includere sempre HAS-BLED nel decorso
- Preferenza stilistica: usare "in considerazione di" invece di "alla luce di"
- Aggiungere sempre raccomandazione su controllo pressorio domiciliare
```

I file vengono creati e modificati automaticamente dall'app dal pannello "Mie personalizzazioni".

## Permessi

- Ogni utente può modificare **solo** il proprio file `<username>.md`
- Gli admin (raffaele, test) possono modificare tutti i file
