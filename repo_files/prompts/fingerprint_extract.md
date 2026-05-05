Sei un esperto di comunicazione clinica neurologica. Ti fornisco due documenti:
1. Una cartella clinica anonimizzata (diari, esami, referti)
2. La lettera di dimissione effettivamente scritta da un neurologo basandosi su quella cartella

Il tuo compito è estrarre il "DECORSO PATOLOGIA-SPECIFICO" della lettera in formato JSON strutturato. Questo decorso serve come guida riutilizzabile per scrivere nuove lettere di pazienti con la stessa patologia.

IMPORTANTE: lo schema generale della lettera (anamnesi, terapia domiciliare, motivo del ricovero, EO ingresso, esami ematochimici e strumentali, decorso, EO dimissione, terapia alla dimissione, controlli, raccomandazioni, firme) è già fissato nel prompt di sistema. Concentrati SOLO su ciò che è specifico per questa patologia.

---

OUTPUT — produci SOLO un oggetto JSON con questi 10 campi (nessun preambolo, nessun commento, nessun backtick):

{
  "patologia": "Nome breve e descrittivo della patologia/scenario clinico (max 8 parole, es: 'Ictus ischemico cardioembolico in fibrillazione atriale'). Includi i descrittori chiave che rendono questo caso distinguibile da altri della stessa categoria.",

  "diagnosi_pattern": "Formula tipica della diagnosi finale tra virgolette. Usa [PLACEHOLDERS] per i dettagli da adattare al paziente specifico (territorio vascolare, lato, comorbilità). Esempio: 'Ictus ischemico [territorio] [lato] a verosimile eziologia [eziologia] in paziente con [comorbilità rilevante]'.",

  "logica_diagnostica": "Testo discorsivo (100-300 parole) che spiega quali reperti orientano verso questa diagnosi specifica e quali alternative considerare. Includi i criteri positivi (cosa supporta questa diagnosi) e differenziali (cosa esclude alternative). Esempio: 'Per concludere per eziologia cardioembolica devono essere presenti: 1) lesione corticale; 2) fonte cardioembolica documentata (FA, valvulopatia, FE <35%). In assenza di FA documentata: ECG Holter o impiantabile, ricerca PFO. Se cause cardiache assenti e nessuna stenosi >50% upstream: ESUS. Se stenosi carotidea >50%: aterotrombotico. Se lacuna profonda: lacunare. Se segni dissecazione: dissecazione.'",

  "decorso_esempio": "Paragrafo narrativo (200-500 parole) tratto fedelmente dalla sezione 'Decorso clinico' della lettera fornita. Mantieni lo stile, i connettori, le transizioni. Questo serve come guida stilistica per il modello AI quando scriverà il decorso di nuovi pazienti. Mantieni anche dettagli specifici (farmaci, dosaggi, tempistiche): l'AI sarà istruita a non copiarli letteralmente, ma a usarli come template.",

  "checklist_decorso": [
    "Step diagnostico-terapeutico tipico per questa patologia (es: 'TC encefalo controllo 24h')",
    "Altro step (es: 'Avvio terapia anticoagulante')",
    "..."
  ],

  "esami_aggiuntivi": [
    "Esami specifici da cercare/segnalare per questa patologia (es: 'screening immunologico se paziente <60a')",
    "Altro esame (es: 'Lp(a), omocisteina')",
    "..."
  ],

  "diari_da_monitorare": [
    "Quadri tipici da cercare nelle note di diario per questa patologia. Esempio: 'Tono dell'umore: stroke ha alta incidenza di depressione post-stroke, da cercare nei diari segnali di apatia, anedonia, calo motivazionale → se documentato, inserire in diagnosi e decorso'",
    "Altro quadro (es: 'Delirium: pazienti anziani spesso sviluppano delirium ipo/iperattivo')",
    "..."
  ],

  "raccomandazioni_specifiche": [
    "Raccomandazione tipica per questa patologia (es: 'target LDL <70 mg/dL')",
    "Altra raccomandazione (es: 'controllo CPK e transaminasi a 1 mese se statina')",
    "..."
  ],

  "terapia_pattern": "Pattern di terapia alla dimissione tipico per questa patologia. Esempio: 'Anticoagulante (DOAC nella maggior parte dei casi, warfarin se valvolare/protesi meccanica) + statina ad alto dosaggio + IPP. Se cardioembolico: DOAC sostituisce ASA. Se PFO chiuso: DAPT 6 mesi. NO doppia antiaggregazione.'",

  "note": "Vincoli speciali (es: 'NIHSS sempre alla dimissione, mRS solo dimissione. Sezione neurosonologica obbligatoria. Visita controllo ambulatorio malattie cerebrovascolari.')."
}

---

REGOLE GENERALI:
- Estrai solo informazione patologia-specifica, non duplicare quello che è già nel prompt di sistema
- Se un campo non è applicabile per questa patologia, restituisci array vuoto [] o stringa vuota ""
- Sii concreto e clinicamente preciso
- NON includere [PAZIENTE_NOME] o [DATA_NASCITA] o altri placeholder generici nel decorso_esempio
- decorso_esempio deve essere prosa narrativa fedele all'originale; gli altri campi sono guide strutturate
- Solo JSON valido, senza testo prima o dopo, senza backtick markdown

===== CARTELLA CLINICA =====
[INCOLLA QUI LA CARTELLA CLINICA ANONIMIZZATA]

===== LETTERA DI DIMISSIONE =====
[INCOLLA QUI LA LETTERA DI DIMISSIONE]