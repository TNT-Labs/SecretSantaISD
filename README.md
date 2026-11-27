# 🎅 Secret Santa ISD

Web app per l'estrazione del Secret Santa del **pranzo di Natale ISD (11 dicembre)**.
È un'unica pagina statica (`index.html`), senza backend: funziona su GitHub Pages.

## Funzioni
- **Partecipanti**: aggiunta rapida (anche più nomi incollati, separati da virgola o a capo); i duplicati vengono bloccati.
- **Esclusioni**: coppie che non devono estrarsi a vicenda (es. partner).
- **Estrazione**: algoritmo completo (trova sempre una soluzione se ne esiste una), nessuno estrae sé stesso; se possibile evita gli scambi reciproci (A→B e B→A).
- **Scoperta a schermo condiviso**: ognuno tocca il proprio nome e apre il pacco animato (con coriandoli, raggi di luce e suoni); i nomi già scoperti vengono segnati.
- **Link personali**: un link per persona da inviare (WhatsApp/condivisione): mostra solo il proprio abbinamento. I nomi nel link sono codificati (non leggibili a colpo d'occhio, ma non è una cifratura forte).
- Conto alla rovescia, budget e data/ora del pranzo modificabili.

I dati restano salvati nel browser del dispositivo dell'organizzatore (`localStorage`).

## Pubblicazione su GitHub Pages
1. Unisci questo branch in `main`.
2. Su GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, cartella `/ (root)`.
3. Dopo un minuto l'app sarà su `https://tnt-labs.github.io/SecretSantaISD/`.

> I link personali puntano all'indirizzo da cui li generi: creali dalla versione pubblicata su Pages, non da un file aperto in locale.
