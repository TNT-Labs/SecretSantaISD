# 🎅 Secret Santa ISD

Web app statica per il Secret Santa del **pranzo di Natale ISD (11 dicembre)**, pubblicata con GitHub Pages.

- **Pagina principale** (`https://tnt-labs.github.io/SecretSantaISD/`): solo countdown. I partecipanti la vedono ma non possono fare nulla.
- **Area organizzatore** (`…/SecretSantaISD/#organizza`): protetta da password. Solo l'organizzatore fa l'estrazione, dal vivo al pranzo; poi ognuno tocca il proprio nome sullo schermo e scopre in privato da chi riceverà il regalo.

## `partecipanti.csv`
```csv
nome,gruppo
Mario Rossi,1
Laura Bianchi,1
Paolo Verdi,
```
- **nome** (obbligatorio): un partecipante per riga, massimo 40 caratteri.
- **gruppo** (facoltativo): chi ha lo **stesso gruppo non si estrae a vicenda** (es. coppie). Lascia vuoto se non serve.
- Separatore `,` oppure `;` (va bene il CSV di Excel). Le righe che iniziano con `#` sono commenti; i duplicati vengono segnalati e ignorati.

## `config.json`
```json
{
  "titolo": "Pranzo di Natale ISD",
  "dataEvento": "2026-12-11T13:00:00+01:00",
  "budget": "",
  "passwordHash": ""
}
```
- **dataEvento**: data e ora del pranzo (countdown). Gli orari sono mostrati in ora italiana.
- **budget**: testo libero, es. `"20 €"` (facoltativo).
- **passwordHash**: impronta della password dell'organizzatore (la password in chiaro non va mai nel repository).

### Impostare la password
1. Apri `…/SecretSantaISD/#organizza`: finché `passwordHash` è vuoto compare **Imposta la password**.
2. Scrivi la password scelta e premi **Genera impronta**, poi copia la riga in `config.json` e fai commit.
3. Dopo la pubblicazione (circa un minuto) ricarica la pagina ed entra con la password.

## Al pranzo
1. Apri `#organizza`, inserisci la password, controlla l'elenco e premi **Estrai i nomi!**
2. Ognuno tocca il proprio nome → conferma "Sei davvero tu?" → apre il pacco.
3. L'estrazione resta salvata nel browser dell'organizzatore (anche se ricarichi la pagina). **Esci** chiude l'accesso.

## Suoni
Tutti i suoni sono sintetizzati nel browser (nessun file audio): rullo di tamburi durante l'estrazione, piatto e fanfara alla fine, campanellino alla selezione del nome, pacco che trema, coperchio che salta, pioggia di campanelle e accordo quando appare il nome. Il pulsante 🔔 in alto a destra li attiva o disattiva (la scelta viene ricordata).

## Attivare GitHub Pages
1. Unisci questo branch in `main`.
2. **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, cartella `/ (root)`.
