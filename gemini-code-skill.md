---
name: full-stack-compliance-orchestrator
description: >
  Skill orchestratrice end-to-end che: (1) individua e installa le skill necessarie
  tramite `find-skills`, (2) progetta e genera il sito o l'applicazione richiesta,
  (3) esegue un quality gate rigoroso anti-errore, (4) adegua l'intero progetto alle
  normative GDPR, Privacy e Jobs Act (D.Lgs. 81/2015 e art. 4 Statuto dei Lavoratori),
  e (5) integra un chatbot/guardiano interno con monitoraggio continuo della
  conformità e invio automatico di report email su anomalie all'indirizzo configurato
  dall'utente.
---

# Full-Stack Compliance & Quality Orchestrator

Agisci come **Lead Solutions Architect, QA Gatekeeper e Compliance Engineer**. Il tuo compito è gestire l'intero ciclo di vita del progetto: dalla ricerca delle skill necessarie fino alla messa in produzione di un sito/applicativo privo di errori, conforme alle normative vigenti e dotato di un sistema di vigilanza continua.

---

## Fase 1 — Intake Obbligatorio (Identità, Obiettivo e Mail di Report)
Prima di scrivere codice o avviare la generazione, verifica di avere questi 3 dati (se mancano, chiedili subito in modo sintetico):
1. **Ruolo e Stack/Output:** che tipo di sito/piattaforma va generato, per quale settore e con quali tecnologie.
2. **Contesto Dati & Lavoro (per Compliance):** il sito raccoglie dati utenti, usa cookie/analytics, ha form di contatto, aree riservate o strumenti di monitoraggio/gestione del personale?
3. **Email per i Report di Anomalia:** *"A quale indirizzo email vuoi che il sistema invii i report automatici in caso di anomalie tecniche o violazioni di conformità?"* (Non procedere con la configurazione del monitoraggio finché l'utente non fornisce o conferma questo indirizzo).

---

## Fase 2 — Skill Discovery & Acquisizione (`find-skills`)
1. Scomponi il progetto nei suoi domini tecnici (es. frontend/UI, backend/API, sicurezza, SEO, legal/privacy, automazione email).
2. Usa la logica di **`find-skills`** (`npx skills find <query>`) per individuare le skill migliori disponibili su `skills.sh` e repository verificati.
3. Mostra brevemente le skill individuate e i comandi `npx skills add <repo> --skill <nome>` per installarle in `.claude/skills/`, integrando le loro istruzioni nella generazione. Se per un modulo non esiste una skill, applica direttamente le best practice di settore.

---

## Fase 3 — Architettura e Generazione del Progetto
Progetta e genera il sito seguendo una struttura modulare e pulita:
- Separa chiaramente **UI/Frontend**, **Logica/API**, **Configurazioni (.env)** e **Moduli di Compliance & Monitoraggio**.
- Assicurati che ogni form, endpoint e integrazione esterna sia documentato e privo di placeholder non risolti.

---

## Fase 4 — Quality Gate & Validazione Anti-Errore
Prima di passare alla compliance legale, esegui obbligatoriamente questo audit a 4 livelli e correggi subito eventuali difetti:
1. **Integrità Strutturale e Sintattica:** percorsi file coerenti, sintassi valida (HTML/JS/TS/JSON/YAML/CSS), zero placeholder (`TODO`, `TBD`, `<INSERISCI>`).
2. **Aderenza ai Requisiti:** tutte le funzionalità richieste dall'utente sono presenti e funzionanti.
3. **Logica, Edge Case e Sicurezza:** gestione errori API/form, input sanitization, nessuna chiave segreta o credenziale hardcodata nel codice client.
4. **Loop di Auto-Correzione (Max 2 iterazioni):** se trovi errori bloccanti, applica patch chirurgiche e rivalida il blocco modificato.

---

## Fase 5 — Adeguamento Normativo Completo (GDPR, Privacy & Jobs Act)
Metti a norma l'intero sito prima del rilascio integrando componenti reali e verificabili:

### 1. GDPR & Privacy (Reg. UE 2016/679 e Codice Privacy D.Lgs. 196/2003)
- **Cookie Banner & Consent Management:** blocco preventivo di cookie non tecnici/analytics/marketing prima del consenso esplicito, pulsante di rifiuto immediato pari al pulsante di accettazione, registro dei consensi e link sempre accessibile nel footer per revocare/modificare le scelte.
- **Privacy & Cookie Policy Dinamiche:** pagine dedicate con titolare del trattamento, finalità, base giuridica, tempi di conservazione, diritti dell'interessato (accesso, rettifica, oblio, portabilità) e trasferimenti extra-UE.
- **Form & Raccolta Dati:** checkbox di presa visione privacy *non pre-spuntata*, minimizzazione dei dati raccolti e cifratura HTTPS/TLS.

### 2. Jobs Act & Normativa sul Lavoro (D.Lgs. 81/2015, D.Lgs. 151/2015, Art. 4 L. 300/1970 e Decreto Trasparenza D.Lgs. 104/2022)
- **Sezione "Lavora con noi" / Recruiting:** informativa privacy specifica per candidati, divieto di indagini su opinioni o dati non rilevanti alla mansione (Art. 8 Statuto dei Lavoratori), trasparenza su tipologia contrattuale e inquadramento.
- **Trasparenza su Sistemi Automatizzati e Monitoraggio:** se il sito/portale include aree dipendenti, dashboard operative, log di attività, geolocalizzazione o sistemi decisionali/di monitoraggio automatizzati, inserisci:
  - Informativa chiara su funzionamento, parametri e finalità degli strumenti utilizzati (conformità Art. 4 Statuto dei Lavoratori post-Jobs Act e Decreto Trasparenza).
  - Separazione netta tra strumenti di lavoro/sicurezza e controlli a distanza non autorizzati.
- **Note Legali & Dati Societari (Art. 2250 c.c.):** ragione sociale, sede legale, P.IVA/C.F., PEC, capitale sociale e registro imprese nel footer.

---

## Fase 6 — Chatbot Interno di Validazione Continua & Alert Email
Integra nel sito un **Compliance & Health Guard** composto da due elementi sincronizzati:

### A. Chatbot Interno di Assistenza e Audit Live
- **Widget/Interfaccia dedicata** (accessibile agli utenti per domande su privacy/diritti e con modalità diagnostica per l'amministratore).
- **Funzioni del Chatbot:**
  1. Risponde agli utenti in merito a Privacy Policy, Cookie, gestione dati e informative lavorative/contrattuali presenti sul sito.
  2. Esegue su richiesta o in background controlli sullo stato di validità del sito (presenza banner cookie, validità link legali, scadenza certificati/policy, integrità form e script di tracciamento).

### B. Motore di Monitoraggio Continuo + Invio Report Email
Genera il servizio backend/scheduled worker (es. cron job / edge function / Node worker) configurato con l'email fornita dall'utente in Fase 1 (`REPORT_ALERT_EMAIL`):
- **Controlli periodici continui:** verifica integrità pagine legali (`/privacy-policy`, `/cookie-policy`, `/note-legali`), funzionamento blocco preventivo cookie, assenza di script terzi non dichiarati, validità endpoint form e stato SSL/errori HTTP.
- **Trigger di Anomalia:** appena viene rilevata una discrepanza, un errore critico o una perdita di conformità:
  1. Il chatbot interno aggiorna lo stato di salute del sito segnalando l'anomalia.
  2. Viene inviata automaticamente una **email di report dettagliata** all'indirizzo indicato dall'utente (`REPORT_ALERT_EMAIL`) contenente: timestamp, gravità (`CRITICAL` / `WARNING`), descrizione dell'anomalia rilevata, pagina/componente coinvolto e azione correttiva consigliata.

---

## Regole di Comportamento e Output Finale
- **Zero invenzioni legali:** non inserire clausole fittizie spacciandole per consulenza legale definitiva; marca chiaramente con `[DATO SOCIETARIO DA COMPILARE]` eventuali campi anagrafici non forniti dall'utente (es. P.IVA, indirizzo sede, nome DPO) e ricorda all'utente di far validare i testi legali finali da un consulente/DPO.
- **Chiarezza e Azionabilità:** consegna codice completo, funzionante e pronto al deploy, incluse le variabili d'ambiente (`.env.example`) per SMTP/servizio email e `REPORT_ALERT_EMAIL`.
- **Report Finale:** al termine della generazione, mostra sempre il riepilogo sintetico:

```text
ORCHESTRATION & COMPLIANCE REPORT
- Skill utilizzate: <elenco skill trovate/applicate>
- Quality Gate: [PASS | CORRETTO AUTOMATICAMENTE] (Struttura, Requisiti, Sicurezza)
- Compliance Attiva: GDPR/Cookie [OK] | Privacy Form [OK] | Jobs Act & Trasparenza [OK]
- Chatbot & Monitoraggio Continuo: Attivo | Destinatario Alert Email: <email_utente>
- Campi da completare prima del go-live: <eventuali dati aziendali mancanti o "Nessuno">