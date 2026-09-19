# Project_Work_Unipegaso_L31

**Progettazione di un sito web per la comunicazione della sostenibilità: il caso Tinazzi**

Project Work di laurea — Informatica per le aziende digitali (L-31), Università Telematica Pegaso.
Traccia: *Tecnologia web per la sostenibilità d'impresa — Sviluppo di una pagina web per il download dei report di sostenibilità di un'impresa del settore primario.*

🔗 **Repository GitHub:** https://github.com/michelecipriani-mc/Project_Work_Unipegaso_L31

> ⚠️ **Progetto accademico non ufficiale.** Il sito è dimostrativo e non è affiliato a Tinazzi Srl.
> I contenuti sono basati su fonti pubbliche e il Bilancio di Sostenibilità viene aperto direttamente dal dominio ufficiale tinazzi.it.

---

## Indice

- [Descrizione](#descrizione)
- [Funzionalità](#funzionalità)
- [Tecnologie](#tecnologie)
- [Struttura del progetto](#struttura-del-progetto)
- [Avvio in locale](#avvio-in-locale)
  - [Opzione A — Da terminale (Bash)](#opzione-a--da-terminale-bash)
  - [Opzione B — VS Code con Live Server](#opzione-b--vs-code-con-live-server)
- [Navigazione e rotte](#navigazione-e-rotte)
- [Risoluzione dei problemi](#risoluzione-dei-problemi)
- [Fonti](#fonti)
- [Limiti del prototipo](#limiti-del-prototipo)
- [Licenza](#licenza)

---

## Descrizione

Il sito sintetizza i principali risultati del **Bilancio di Sostenibilità 2025** di Tinazzi, azienda vitivinicola familiare attiva in Veneto, Puglia e Toscana.
Le informazioni sono organizzate secondo le dimensioni **ESG** (Environmental, Social, Governance), alcuni risultati quantitativi sono presentati come **KPI** e una sezione dedicata permette di raggiungere il **documento ufficiale in PDF**.

Il sito non sostituisce il Bilancio: è un livello informativo intermedio che accompagna l'utente dalla sintesi dei risultati alla consultazione della fonte completa.

## Funzionalità

- **Caricamento dinamico** di navbar, footer e pagine tramite `fetch`, senza duplicare il codice comune.
- **Navigazione tramite hash** (`#home`, `#chi-siamo`, `#sostenibilita`, `#report`) con evidenziazione della voce attiva.
- **Menu Offcanvas** (Bootstrap) su tutte le dimensioni dello schermo, chiuso automaticamente dopo la selezione.
- **KPI animati**: i contatori partono quando la card entra nell'area visibile (IntersectionObserver).
- **Animazioni di comparsa** delle sezioni durante lo scorrimento.
- **Sezione Report** con collegamento al Bilancio di Sostenibilità ufficiale.
- **Newsletter dimostrativa**: il form valida l'indirizzo email ma non invia né memorizza dati.
- **Layout responsive** con CSS Grid, Flexbox e media query (900px e 760px).

## Tecnologie

| Ambito | Strumenti |
|---|---|
| Struttura e contenuti | HTML5 |
| Presentazione | CSS3 (custom properties, Grid, Flexbox, media query) |
| Comportamento | JavaScript (ES2017+, `fetch`, `async/await`, IntersectionObserver) |
| Componenti UI | Bootstrap 5.3, MDB UI Kit 9 |
| Icone e font | Font Awesome 6, Google Fonts (Fraunces, Manrope) |
| Versionamento | Git, GitHub Desktop, GitHub |

Le librerie esterne sono caricate da CDN: **non serve installare dipendenze** (niente `npm install`).

## Struttura del progetto

```
Project_Work_Unipegaso_L31/
├── index.html            # Punto di ingresso: banner, header, main, footer
├── components/
│   ├── navbar.html       # Barra di navigazione con menu Offcanvas
│   └── footer.html       # Footer: fonti, sede, newsletter
├── pages/
│   ├── home.html         # Header principale e attività del gruppo
│   ├── chi-siamo.html    # Missione, valori e timeline aziendale
│   └── sostenibilita.html# KPI, iniziative ESG e sezione Report
├── css/
│   └── style.css         # Foglio di stile personalizzato
├── js/
│   ├── components.js     # Caricamento dei componenti e navigazione tramite hash
│   └── script.js         # Navbar, banner, newsletter, animazioni e contatori KPI
├── img/
│   ├── img_header.jpg    # Immagine dell'header della Home
│   └── logo.png          # Favicon
├── LICENSE
└── README.md
```

## Avvio in locale

> ❗ **Il sito deve essere servito da un server web.**
> Navbar, footer e pagine vengono caricati con `fetch`: aprendo `index.html` con un doppio clic (indirizzo `file://...`) il browser blocca le richieste e la pagina resta vuota.

Prima di tutto scarica il progetto:

```bash
git clone https://github.com/michelecipriani-mc/Project_Work_Unipegaso_L31
cd Project_Work_Unipegaso_L31
```

In alternativa, da GitHub: **Code → Download ZIP**, poi estrai l'archivio.

È necessaria una connessione a Internet, perché Bootstrap, MDB, Font Awesome e Google Fonts vengono caricati da CDN.

### Opzione A — Da terminale (Bash)

Serve **Python 3**, che include un piccolo server web. Verifica che sia installato:

```bash
python3 --version
```

Dalla cartella principale del progetto (quella che contiene `index.html`) avvia il server:

```bash
python3 -m http.server 8000
```

Poi apri nel browser:

```
http://localhost:8000
```

Per fermare il server premi `Ctrl + C` nel terminale.

**Note per Windows (Git Bash):** il comando può chiamarsi `python` oppure `py`:

```bash
python -m http.server 8000
```
```bash
py -m http.server 8000
```

**Alternativa con Node.js**, se è installato al posto di Python:

```bash
npx serve .
```

Il terminale indica l'indirizzo da aprire (di solito `http://localhost:3000`).

Se la porta `8000` è già occupata, usane un'altra (es. `8080`) e aggiorna l'indirizzo di conseguenza.

### Opzione B — VS Code con Live Server

1. Installa **[Visual Studio Code](https://code.visualstudio.com/)**.
2. Apri il pannello **Estensioni** (`Ctrl + Shift + X`), cerca **Live Server** (autore *Ritwick Dey*) e clicca **Installa**.
3. Apri la cartella del progetto con **File → Apri cartella…**, selezionando la cartella che contiene direttamente `index.html` (non una cartella superiore).
4. Avvia il server in uno di questi modi:
   - clicca **Go Live** in basso a destra nella barra di stato;
   - oppure clic destro su `index.html` → **Open with Live Server**.
5. Il browser si apre automaticamente su:

   ```
   http://127.0.0.1:5500/index.html
   ```

Per fermare il server clicca di nuovo sul pulsante nella barra di stato (ora mostra **Port : 5500**).

Live Server ricarica la pagina automaticamente a ogni salvataggio dei file.

## Navigazione e rotte

La navigazione usa l'hash dell'URL. `index.html` è la struttura fissa, mentre il contenuto di `<main>` viene sostituito in base alla rotta.

| URL | Contenuto caricato |
|---|---|
| `#home` (o nessun hash) | `pages/home.html` |
| `#chi-siamo` | `pages/chi-siamo.html` |
| `#sostenibilita` | `pages/sostenibilita.html` |
| `#report` | `pages/sostenibilita.html`, con scorrimento alla sezione Report |
| rotta non valida | Home |

Esempio: `http://localhost:8000/#report` apre direttamente la sezione di download del Bilancio.

## Risoluzione dei problemi

| Problema | Causa e soluzione |
|---|---|
| Pagina vuota, visibile solo il banner | Il file è stato aperto con doppio clic (`file://`). Avvia un server (Opzione A o B). |
| Pagina senza stile o senza icone | Manca la connessione a Internet: le librerie sono caricate da CDN. |
| `python3: command not found` | Su Windows usa `python` o `py`, oppure installa Python da [python.org](https://www.python.org/downloads/). |
| `Address already in use` | La porta è occupata: avvia il server su un'altra porta, es. `python3 -m http.server 8080`. |
| Live Server mostra l'elenco delle cartelle | È stata aperta una cartella superiore: apri direttamente la cartella che contiene `index.html`. |
| Modifiche non visibili | Ricarica forzando la cache con `Ctrl + F5`. |

## Fonti

- Tinazzi — [About us](https://www.tinazzi.it/en/about-us/)
- [Bilancio di Sostenibilità 2025 (PDF)](https://www.tinazzi.it/wp-content/uploads/2026/03/Report_Tinazzi_2025_ITA_compressed.pdf) — fonte principale dei dati
- [Bilancio di Sostenibilità 2024 (PDF)](https://www.tinazzi.it/wp-content/uploads/2025/02/Report_Tinazzi_2024_ITA_20250224.pdf) — confronto tra esercizi
- [Gardapost — Tinazzi presenta il Bilancio di Sostenibilità 2025](https://www.gardapost.it/2026/04/10/tinazzi-presenta-il-bilancio-di-sostenibilita-2025/)
- [Winemag — Tinazzi presenta il Bilancio di Sostenibilità 2025](https://www.winemag.it/tinazzi-presenta-bilancio-sostenibilita-2025-investimenti-vigneto-riduzione-consumi-impegno-sociale/)

## Limiti del prototipo

- Sito **solo front-end**: i dati sono inseriti direttamente nei file HTML e vanno aggiornati manualmente.
- Nessun database, CMS o collegamento ai sistemi aziendali.
- Il form newsletter è **dimostrativo** e non trasmette né memorizza dati.
- Il collegamento al Bilancio dipende dal percorso del file sul sito ufficiale Tinazzi.

## Licenza

Codice distribuito con licenza **MIT** (vedi [LICENSE](LICENSE)).
Marchi, nomi e documenti di Tinazzi Srl appartengono ai rispettivi proprietari.