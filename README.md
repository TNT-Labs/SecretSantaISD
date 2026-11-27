# 🎅 Secret Santa ISD

Web app statica per il Secret Santa del **pranzo di Natale ISD (11 dicembre)**, pubblicata con GitHub Pages.

| Pagina | Indirizzo | Chi la vede |
|---|---|---|
| Home (solo countdown) | `https://tnt-labs.github.io/SecretSantaISD/` | tutti |
| Link personale | `…/SecretSantaISD/#r=…` | ogni partecipante (il suo link) |
| Area organizzatore | `…/SecretSantaISD/#organizza` | solo tu (non è collegata da nessuna parte) |

## File da modificare nel repository

### `partecipanti.csv`
```csv
nome,gruppo
Mario Rossi,1
Laura Bianchi,1
Paolo Verdi,
```
- **nome** (obbligatorio): un partecipante per riga, massimo 40 caratteri.
- **gruppo** (facoltativo): chi ha lo **stesso gruppo non si estrae a vicenda** (es. coppie, stesso ufficio). Lascia vuoto se non serve.
- Separatore `,` oppure `;` (va bene anche il CSV esportato da Excel). Le righe che iniziano con `#` sono commenti. I duplicati vengono segnalati e ignorati.

### `config.json`
```json
{
  "titolo": "Pranzo di Natale ISD",
  "dataEvento": "2026-12-11T13:00:00+01:00",
  "sblocco": "2026-12-11T13:00:00+01:00",
  "chiave": "",
  "budget": ""
}
```
- **dataEvento**: data del pranzo (countdown della home).
- **sblocco**: da quando si possono aprire i pacchi. Se vuoto (`""`), si aprono appena pubblichi la chiave.
- **chiave**: vuota finché i pacchi sono bloccati. Per sbloccarli incolla qui la chiave dell'estrazione.
- **budget**: testo libero, es. `"20 €"` (facoltativo).

I pacchi si aprono solo quando **la chiave è pubblicata e l'orario di sblocco è passato**. Le pagine aperte ricontrollano `config.json` ogni 30 secondi: lo sblocco arriva da solo, senza ricaricare.

## Come funziona la sicurezza
Il destinatario dentro ogni link è **cifrato (AES‑GCM)** con una chiave generata durante l'estrazione. Finché la chiave non è in `config.json` nessuno, nemmeno tu, può leggerlo. Il nome di chi riceve il link è legato al testo cifrato, quindi i link non si possono scambiare o manomettere.

## Procedura
1. Compila `partecipanti.csv` e fai commit.
2. Apri `https://tnt-labs.github.io/SecretSantaISD/#organizza`, controlla l'elenco e premi **Estrai i nomi!**
3. Invia a ciascuno il proprio link (**Copia** / **Invia**) e scarica il **backup .txt**: contiene la chiave e tutti i link (l'estrazione è salvata solo nel browser in cui l'hai fatta).
4. Il giorno dello sblocco copia la chiave in `config.json` (il pulsante **Copia config.json** ti dà il file già pronto) e fai commit. Dopo circa un minuto GitHub Pages pubblica la modifica.

> Se rifai l'estrazione viene generata una nuova chiave: i vecchi link non funzionano più e vanno rimandati.

## Attivare GitHub Pages
1. Unisci questo branch in `main`.
2. **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, cartella `/ (root)`.
