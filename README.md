<div align="center">
  <img src="https://raw.githubusercontent.com/insidegubbio/.github/main/icons/insidegubbio-500-rounded.png" width="300" height="300" />
  <h1>insidegubbio</h1>
  <p>la guida digitale alla città di gubbio</p>
  <p><a href="https://insidegubbio.com">insidegubbio.com</a></p>
  <a href="https://status.insidegubbio.com">
    <img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fstatus.insidegubbio.com%2Fit%2Findex.json&query=%24.data.attributes.aggregate_state&label=status&style=flat-square&color=brightgreen" />
  </a>
</div>

---
 
## perché siamo open source

gubbio è una città piccola. le risorse sono poche, i contributori potenziali anche.

rendere il codice pubblico significa che chiunque può capire come funziona la piattaforma, segnalare un problema o proporre un miglioramento. per noi è anche una questione di trasparenza: non chiediamo fiducia a scatola chiusa, e teniamo alla privacy di chi usa i nostri servizi.

restano private solo le repo con contenuti editoriali o dettagli implementativi sensibili. il resto è tutto qui.

---

## repos

### 🗄️ [console](https://github.com/insidegubbio/console) · privata
`console.insidegubbio.com`

l'api principale della piattaforma. converte file `.docx` hostati su github in json strutturati a runtime.

esistono due versioni attive:
- **v1** basata su cloudflare kv, con documenti in formato legacy
- **v2** basata su build json generato da github actions, con documenti nel formato aggiornato

---

### 🖼️ [araldo](https://github.com/insidegubbio/araldo) · pubblica
`araldo.insidegubbio.com`

media manager, fork di [zipline](https://github.com/diced/zipline). i media vengono serviti tramite bucket b2 backblaze (s3-compatible), rispettando la struttura di path configurata in zipline.

---

### ✏️ [cancelliere](https://github.com/insidegubbio/cancelliere) · pubblica
`cancelliere.insidegubbio.com`

editor web per i file `.docx` hostati su github che alimentano console. sviluppato da zero, senza dipendenze da cms o servizi terzi.

funzionalità: modifica, rinomina e cancellazione di file word, supporto a cartelle, gestione di più branch, supporto a repo private, dark mode.

---

### 🌐 [www](https://github.com/insidegubbio/www) · privata
frontend di insidegubbio. sincronizza con framer i componenti personalizzati del sito.

---

### 🤖 [ikuvium](https://github.com/insidegubbio/ikuvium) · pubblica
`ikuvium.insidegubbio.com`

worker cloudflare che espone ikuvium, l'llm di insidegubbio per la generazione di itinerari personalizzati. basato su gemini. il prompt di sistema è privato, la struttura del worker è pubblica.

| endpoint | descrizione |
|---|---|
| `GET /api/v1/health` | health check |
| `POST /api/v1/itinerary` | genera un itinerario a partire da input utente |

---

### 🗺️ [condottiero](https://github.com/insidegubbio/condottiero) · pubblica
`condottiero.insidegubbio.com`

fork di [gpx.studio](https://gpx.studio) con modifiche custom per gubbio. espone un endpoint `/api/gpx` per la generazione di file gpx da una lista di poi.

```json
{
  "name": "string (opzionale)",
  "description": "string (opzionale)",
  "create_track": true,
  "routing": true,
  "profile": "foot | bike | car | mtb | racingbike | hike",
  "color": "hex (es. 0055ff)",
  "pois": [
    {
      "lat": 43.1122,
      "lon": 12.3888,
      "name": "fontana dei matti",
      "desc": "piazza quaranta martiri",
      "ele": 520
    }
  ]
}
```

---

### 🧭 [gh.condottiero](https://github.com/insidegubbio/gh.condottiero) · pubblica
`graphhopper.insidegubbio.com`

istanza graphhopper custom per condottiero. copertura ridotta al centro italia per ottimizzare risorse e tempi di risposta.

---

### 📊 [camerlengo](https://github.com/insidegubbio/camerlengo) · pubblica
`camerlengo.insidegubbio.com`

istanza [umami](https://umami.is) per l'analytics privacy-friendly della piattaforma.

---

## domini

| dominio | servizio |
|---|---|
| `console.insidegubbio.com` | api contenuti |
| `araldo.insidegubbio.com` | media manager |
| `condottiero.insidegubbio.com` | mappe e gpx |
| `graphhopper.insidegubbio.com` | routing stradale |
| `ikuvium.insidegubbio.com` | llm itinerari |
| `camerlengo.insidegubbio.com` | analytics |
| `status.insidegubbio.com` | status dei servizi |

---

## come contribuire

se vuoi darci una mano, segnalare un bug o proporre una nuova funzionalità, apri una issue nella repository di riferimento. le pull request sono sempre benvenute!

## licenza

i progetti pubblici di insidegubbio sono rilasciati sotto licenza [GNU GPLv3](https://www.gnu.org/licenses/gpl-3.0.html), se non diversamente specificato.
