# Simulatore Buy Borrow Die

Simulatore web della strategia *Buy, Borrow, Die*. È una pagina statica senza backend, pronta per **GitHub Pages** (gratuito).

## Contenuto

```
docs/                     ← il sito da pubblicare
├── index.html            ← l'applicazione (da modificare d'ora in poi)
├── sw.js                 ← service worker: uso offline
├── manifest.webmanifest  ← installazione come app (PWA)
├── .nojekyll             ← disattiva l'elaborazione Jekyll di GitHub
├── vendor/chart.umd.min.js  ← Chart.js 4.4.1 (licenza MIT), senza CDN esterni
└── icons/                ← icone del sito e dell'app
```

I file `Simulatore Buy Borrow Die.html` e `... (versione precedente).html` nella cartella principale sono gli originali e il sito non li usa.

## Pubblicare su GitHub Pages

1. Accedi a <https://github.com> e crea un nuovo repository **pubblico** (ad esempio `simulatore-bbd`). Con l'account gratuito, Pages funziona solo con i repository pubblici.
2. Carica i file in uno dei due modi seguenti:
   - **Dal browser**: nel repository scegli *Add file → Upload files*, trascina la cartella `docs` (oppure tutta la cartella del progetto) e premi *Commit changes*.
   - **Con git**, dalla cartella del progetto:
     ```bash
     git init
     git add .
     git commit -m "Prima pubblicazione"
     git branch -M main
     git remote add origin https://github.com/<utente>/<repo>.git
     git push -u origin main
     ```
3. Nel repository apri *Settings → Pages*. Sotto *Build and deployment* scegli **Deploy from a branch**, poi il branch **main** e la cartella **/docs**, e premi *Save*.
   - Se hai caricato direttamente il *contenuto* di `docs` nella radice del repository, scegli **/ (root)**.
4. Dopo uno o due minuti il sito è online all'indirizzo `https://<utente>.github.io/<repo>/`.

## Aggiornare il sito

- Modifica `docs/index.html` e carica di nuovo il file (oppure `git commit` + `git push`). GitHub Pages si aggiorna da solo in pochi minuti.
- Chi apre il sito online riceve sempre l'ultima versione. La copia salvata serve solo quando manca la connessione.
- Se aggiungi, rinomini o rimuovi file da usare offline, aggiorna l'elenco `ASSETS` in `docs/sw.js` e incrementa `VERSION` (ad esempio `'v2'`).

## Note

- Impostazioni, scenari e link di condivisione (`#p=...`) vengono salvati solo nel browser dell'utente (localStorage). Nessun dato viene inviato a un server.
- Dopo la prima visita il sito funziona anche **offline**. Inoltre si può installare come app dal browser (*Installa app* / *Aggiungi a schermata Home*).
- Per provarlo in locale con il service worker attivo:
  ```bash
  python -m http.server 8000 --directory docs
  ```
  poi apri <http://localhost:8000/>.
