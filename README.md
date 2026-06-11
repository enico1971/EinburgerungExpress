# 🚆 Einbürgerungs-Express — Leben in Deutschland

![Einbürgerungs-Express](screenshots/social-preview.png)

Eine spielerische, kostenlose Lern-App für den deutschen **Einbürgerungstest**.
Läuft komplett im Browser, speichert den Fortschritt lokal und ist als **PWA**
installierbar (offline nutzbar). Kein Backend, kein Build-Schritt.

## ✨ Funktionen

- **Quiz** mit Timer, sofortigem Feedback und Tastatursteuerung (1–4 / A–D)
- **Lernkarten** mit Spaced Repetition (Schwer / Mittel / Einfach)
- **Prüfungssimulation** (30 Fragen, 75 % zum Bestehen)
- **Fortschritts-Dashboard** pro Themenbereich
- **„Fehler üben"** – gezieltes Training falsch beantworteter Fragen
- **Interaktive Karte** mit allen 16 Bundesländern (echte Umrisse)
- **Tagesziel & Lernplan**, Streak und Prüfungsbereitschaft
- **Heller & dunkler Modus**, Design in Schwarz-Rot-Gold
- **PWA**: installierbar, offline-fähig, Fortschritt im `localStorage`

## 📸 Screenshots

<table>
  <tr>
    <td width="50%" valign="top">
      <img src="screenshots/home.png" alt="Startseite" />
      <p align="center"><em>Startseite mit Lernplan & Fortschritt</em></p>
    </td>
    <td width="50%" valign="top">
      <img src="screenshots/bundeslaender-karte.png" alt="Bundesländer-Karte" />
      <p align="center"><em>Interaktive Karte der 16 Bundesländer</em></p>
    </td>
  </tr>
</table>

## 🚀 Schnellstart (lokal)

Ein Service Worker funktioniert nur über `http(s)`, nicht per Doppelklick
(`file://`). Daher die App über einen kleinen Webserver starten:

```bash
# Variante 1: Node
npm start            # startet "npx serve ." auf z. B. http://localhost:3000

# Variante 2: Python (ohne Node)
python3 -m http.server 8080   # dann http://localhost:8080 öffnen
```

## 📦 Deployment

### GitHub Pages (automatisch)
Dieses Repo enthält einen Workflow unter `.github/workflows/deploy.yml`.

1. Repo zu GitHub pushen (Branch `main`).
2. In **Settings → Pages → Build and deployment** die Quelle auf
   **GitHub Actions** stellen.
3. Bei jedem Push auf `main` wird die App automatisch veröffentlicht
   (URL erscheint im Actions-Log und unter Settings → Pages).

Die App nutzt nur **relative Pfade**, funktioniert daher auch unter einem
Unterpfad wie `https://<user>.github.io/<repo>/`.

### Netlify (Drag & Drop)
Die enthaltene `netlify.toml` ist vorbereitet. Entweder das Repo verbinden
(Publish directory = `.`, kein Build-Command) oder den Ordnerinhalt auf
<https://app.netlify.com/drop> ziehen.

## 🗂️ Projektstruktur

```
.
├── index.html            # die komplette App (HTML/CSS/JS, self-contained)
├── manifest.json         # PWA-Manifest
├── service-worker.js      # Offline-Caching (network-first für HTML)
├── icon-192.png           # App-Icon
├── icon-512.png           # App-Icon
├── netlify.toml           # Netlify-Konfiguration (optional)
├── .nojekyll              # GitHub Pages: Dateien unverändert ausliefern
├── screenshots/           # Bilder für die README
└── .github/workflows/     # GitHub-Actions-Deploy
```

## 🔄 Updates / Caching

Nach Änderungen an `index.html` neu deployen. Damit installierte PWAs die neue
Version sicher erhalten, in `service-worker.js` die Cache-Version hochzählen:

```js
const CACHE = 'einbuergerung-v6'; // bei jedem Release erhöhen
```

## 🙏 Credits & Lizenz

- Kartengeometrie: **SimpleMaps.com** (frei für kommerzielle Nutzung,
  Attribution erwünscht) — Details in [`CREDITS.md`](CREDITS.md).
- Code-Lizenz: **MIT** — siehe [`LICENSE`](LICENSE).
- Herkunft des Layouts und rechtliche Hinweise: siehe [`CREDITS.md`](CREDITS.md).

> Die Fragen dienen dem Üben. Maßgeblich sind die offiziellen Fragen des BAMF.
