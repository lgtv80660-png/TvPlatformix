# Traductions TvPlatformix / TvPlatformix Translations

## 🇫🇷 Français

### Description générale

**TvPlatformix** est un client de streaming de style Netflix pour les comptes IPTV Xtream Codes que vous possédez déjà. L'application regroupe vos films, séries, TV en direct et sports dans une interface moderne et élégante, disponible en tant qu'application web et application de bureau (macOS, Windows).

### Composition technique

- **Langage principal** : TypeScript (87.3%)
- **Styles** : CSS (8.2%)
- **Balisage** : HTML (3.9%)
- **Autre** : 0.6%

### Stack technologique

- **Backend** : Node.js 23 (TypeScript natif) + Fastify + SQLite
- **Frontend** : React + Vite + hls.js
- **Desktop** : Electron
- **Déploiement** : Docker supporté

### Fonctionnalités principales

- 🎬 **Films** avec affiches, synopsis, casting, recherche par catégorie
- 📺 **Séries** avec saisons et épisodes, suivi automatique des visionnages
- 📡 **Télévision en direct** avec tous les canaux de votre fournisseur
- 🗓️ **Guide électronique (EPG)** montrant ce qui diffuse maintenant
- 👤 **Profils** jusqu'à 5 par installation, chacun avec sa propre progression
- ▶️ **Continuer regarder** reprendre où vous avez arrêté
- ❤️ **Liste de favoris** et watchlist
- ⚽ **Appariement du sport** avec les horaires officiels de coups d'envoi
- 🔎 **Recherche** dans films, séries et canaux
- 📱 **Fonctionne partout** du téléphone à la TV, installable comme PWA

### Organisation du code

```
server/       Serveur Node + Fastify + API REST
web/          Application React + Vite
desktop/      Application de bureau Electron
docs/         Documentation technique
```

### Comment démarrer

```bash
# Installation basique
git clone https://github.com/c4rtical/neftlix.git
cd neftlix
npm install
npm start
```

Accédez à `http://localhost:8787`

Nécessite Node.js 23.6 ou plus récent.

#### Docker

```bash
docker compose up -d
```

### Variables d'environnement

| Variable | Défaut | Usage |
|---|---|---|
| `PORT` | `8787` | Port HTTP |
| `HOST` | `0.0.0.0` | Adresse de liaison |
| `NEFTLIX_DATA` | `./data` | Répertoire de la base SQLite |
| `NEFTLIX_PASSWORD` | – | Authentification HTTP basique pour toute l'app |
| `FOOTBALL_DATA_KEY` | – | Clé gratuite de football-data.org pour le calendrier |
| `TMDB_API_KEY` | – | Clé TMDB pour enrichir les métadonnées |
| `LOG_LEVEL` | `info` | Niveau de journal Fastify |

### Raccourcis clavier / télécommande

| Touche | Action |
|---|---|
| Flèches | Naviguer |
| Entrée | Ouvrir / Lire |
| Échap, Retour | Fermer le lecteur |
| En lecteur : ← → | Avancer/Reculer ±10 s |
| En lecteur : ↑ ↓ | Avancer/Reculer ±60 s |
| Espace | Lecture / Pause |
| N | Épisode suivant |
| F | Plein écran |
| M | Muet |

### Contribution

Les rapports de bogues accompagnés d'exemples JSON du panneau sont très précieux. Voir [CONTRIBUTING.md](CONTRIBUTING.md).

Contact : [hi@neftlix.tv](mailto:hi@neftlix.tv)

---

## 🇬🇧 English

### General Description

**TvPlatformix** is a Netflix-style streaming client for Xtream Codes IPTV accounts you already own. The app brings together your movies, series, live TV, and sports in a modern, elegant interface, available as both a web app and desktop application (macOS, Windows).

### Technical Composition

- **Primary Language**: TypeScript (87.3%)
- **Styles**: CSS (8.2%)
- **Markup**: HTML (3.9%)
- **Other**: 0.6%

### Technology Stack

- **Backend**: Node.js 23 (native TypeScript) + Fastify + SQLite
- **Frontend**: React + Vite + hls.js
- **Desktop**: Electron
- **Deployment**: Docker supported

### Key Features

- 🎬 **Movies** with posters, plots, cast, category search and sorting
- 📺 **Series** with seasons and episodes, auto-marked as watched
- 📡 **Live TV** with all your provider's channels
- 🗓️ **EPG (Electronic Program Guide)** showing what's on air now
- 👤 **Profiles** up to 5 per installation, each with its own progress
- ▶️ **Continue Watching** resume where you left off
- ❤️ **Watchlist** and Favourites
- ⚽ **Sports Matching** official kick-off times matched to broadcasting channels
- 🔎 **Search** across movies, series and channels
- 📱 **Works Everywhere** from phone to TV, installable as PWA

### Code Organization

```
server/       Node + Fastify server and REST API
web/          React + Vite application
desktop/      Electron desktop application
docs/         Technical documentation
```

### Getting Started

```bash
# Basic installation
git clone https://github.com/c4rtical/neftlix.git
cd neftlix
npm install
npm start
```

Open `http://localhost:8787`

Requires Node.js 23.6 or newer.

#### Docker

```bash
docker compose up -d
```

### Environment Variables

| Variable | Default | Purpose |
|---|---|---|
| `PORT` | `8787` | HTTP port |
| `HOST` | `0.0.0.0` | Bind address |
| `NEFTLIX_DATA` | `./data` | SQLite database directory |
| `NEFTLIX_PASSWORD` | – | HTTP basic auth for entire app |
| `FOOTBALL_DATA_KEY` | – | Free football-data.org key for fixtures |
| `TMDB_API_KEY` | – | TMDB key to enrich metadata |
| `LOG_LEVEL` | `info` | Fastify log level |

### Keyboard / Remote Shortcuts

| Key | Action |
|---|---|
| Arrows | Move focus |
| Enter | Open / Play |
| Esc, Backspace | Close player |
| In player: ← → | Seek ±10 s |
| In player: ↑ ↓ | Seek ±60 s |
| Space | Play / Pause |
| N | Next episode |
| F | Fullscreen |
| M | Mute |

### Contributing

Bug reports with JSON samples from your panel are most valuable. See [CONTRIBUTING.md](CONTRIBUTING.md).

Contact: [hi@neftlix.tv](mailto:hi@neftlix.tv)

---

## 🇪🇸 Español

### Descripción General

**TvPlatformix** es un cliente de streaming estilo Netflix para cuentas IPTV Xtream Codes que ya posees. La aplicación reúne tus películas, series, TV en directo y deportes en una interfaz moderna y elegante, disponible como aplicación web y aplicación de escritorio (macOS, Windows).

### Composición Técnica

- **Lenguaje Principal**: TypeScript (87.3%)
- **Estilos**: CSS (8.2%)
- **Marcado**: HTML (3.9%)
- **Otro**: 0.6%

### Stack Tecnológico

- **Backend**: Node.js 23 (TypeScript nativo) + Fastify + SQLite
- **Frontend**: React + Vite + hls.js
- **Escritorio**: Electron
- **Despliegue**: Docker soportado

### Características Principales

- 🎬 **Películas** con pósters, sinopsis, elenco, búsqueda por categoría
- 📺 **Series** con temporadas y episodios, seguimiento automático de vistos
- 📡 **Televisión en Directo** con todos los canales de tu proveedor
- 🗓️ **Guía Electrónica (EPG)** mostrando qué está en directo ahora
- 👤 **Perfiles** hasta 5 por instalación, cada uno con su propio progreso
- ▶️ **Continuar Viendo** retomar donde lo dejaste
- ❤️ **Lista de Favoritos** y Watchlist
- ⚽ **Emparejamiento de Deportes** con horarios oficiales de inicio
- 🔎 **Búsqueda** en películas, series y canales
- 📱 **Funciona en Todas Partes** desde teléfono a TV, instalable como PWA

### Organización del Código

```
server/       Servidor Node + Fastify y API REST
web/          Aplicación React + Vite
desktop/      Aplicación de escritorio Electron
docs/         Documentación técnica
```

### Para Comenzar

```bash
# Instalación básica
git clone https://github.com/c4rtical/neftlix.git
cd neftlix
npm install
npm start
```

Accede a `http://localhost:8787`

Requiere Node.js 23.6 o más reciente.

#### Docker

```bash
docker compose up -d
```

### Variables de Entorno

| Variable | Por defecto | Propósito |
|---|---|---|
| `PORT` | `8787` | Puerto HTTP |
| `HOST` | `0.0.0.0` | Dirección de enlace |
| `NEFTLIX_DATA` | `./data` | Directorio de la base de datos SQLite |
| `NEFTLIX_PASSWORD` | – | Autenticación HTTP básica para toda la app |
| `FOOTBALL_DATA_KEY` | – | Clave gratuita de football-data.org para fixture |
| `TMDB_API_KEY` | – | Clave TMDB para enriquecer metadatos |
| `LOG_LEVEL` | `info` | Nivel de registro de Fastify |

### Atajos de Teclado / Control Remoto

| Tecla | Acción |
|---|---|
| Flechas | Mover foco |
| Intro | Abrir / Reproducir |
| Esc, Retroceso | Cerrar reproductor |
| En reproductor: ← → | Buscar ±10 s |
| En reproductor: ↑ ↓ | Buscar ±60 s |
| Espacio | Reproducir / Pausa |
| N | Episodio siguiente |
| F | Pantalla completa |
| M | Silenciar |

### Contribuir

Los informes de errores con muestras JSON de tu panel son más valiosos. Ver [CONTRIBUTING.md](CONTRIBUTING.md).

Contacto: [hi@neftlix.tv](mailto:hi@neftlix.tv)

---

## 🇩🇪 Deutsch

### Allgemeine Beschreibung

**TvPlatformix** ist ein Netflix-ähnlicher Streaming-Client für Xtream Codes IPTV-Konten, die Sie bereits besitzen. Die Anwendung vereint Ihre Filme, Serien, Live-TV und Sport in einer modernen, eleganten Benutzeroberfläche und ist als Web-App und Desktop-Anwendung (macOS, Windows) verfügbar.

### Technische Zusammensetzung

- **Hauptsprache**: TypeScript (87,3%)
- **Stile**: CSS (8,2%)
- **Markup**: HTML (3,9%)
- **Sonstiges**: 0,6%

### Technology Stack

- **Backend**: Node.js 23 (natives TypeScript) + Fastify + SQLite
- **Frontend**: React + Vite + hls.js
- **Desktop**: Electron
- **Bereitstellung**: Docker unterstützt

### Hauptfunktionen

- 🎬 **Filme** mit Postern, Handlung, Besetzung, Kategoriesuche
- 📺 **Serien** mit Staffeln und Episoden, automatische Markierung als angesehen
- 📡 **Live-TV** mit allen Kanälen Ihres Anbieters
- 🗓️ **EPG (elektronischer Programmführer)** zeigt, was gerade läuft
- 👤 **Profile** bis zu 5 pro Installation, jeweils mit eigenem Fortschritt
- ▶️ **Weiterschauen** fortsetzen, wo Sie aufgehört haben
- ❤️ **Merkliste** und Favoriten
- ⚽ **Sport-Zuordnung** mit offiziellen Anstoßzeiten
- 🔎 **Suche** über Filme, Serien und Kanäle
- 📱 **Überall verfügbar** vom Telefon bis zum TV, als PWA installierbar

### Code-Organisation

```
server/       Node + Fastify Server und REST API
web/          React + Vite Anwendung
desktop/      Electron Desktop-Anwendung
docs/         Technische Dokumentation
```

### Erste Schritte

```bash
# Grundlegende Installation
git clone https://github.com/c4rtical/neftlix.git
cd neftlix
npm install
npm start
```

Öffnen Sie `http://localhost:8787`

Erfordert Node.js 23.6 oder neuer.

#### Docker

```bash
docker compose up -d
```

### Umgebungsvariablen

| Variable | Standard | Zweck |
|---|---|---|
| `PORT` | `8787` | HTTP-Port |
| `HOST` | `0.0.0.0` | Bindungsadresse |
| `NEFTLIX_DATA` | `./data` | SQLite-Datenbankverzeichnis |
| `NEFTLIX_PASSWORD` | – | HTTP-Authentifizierung für die gesamte App |
| `FOOTBALL_DATA_KEY` | – | Kostenlose football-data.org-Taste für Spieltermine |
| `TMDB_API_KEY` | – | TMDB-Schlüssel zur Anreicherung von Metadaten |
| `LOG_LEVEL` | `info` | Fastify-Protokollebene |

### Tastatur- / Fernbedienungskürzel

| Taste | Aktion |
|---|---|
| Pfeile | Fokus bewegen |
| Enter | Öffnen / Abspielen |
| Esc, Rücktaste | Spieler schließen |
| Im Spieler: ← → | Suche ±10 s |
| Im Spieler: ↑ ↓ | Suche ±60 s |
| Leerzeichen | Abspielen / Pause |
| N | Nächste Episode |
| F | Vollbild |
| M | Stumm |

### Beitragen

Fehlerberichte mit JSON-Proben von Ihrem Panel sind am wertvollsten. Siehe [CONTRIBUTING.md](CONTRIBUTING.md).

Kontakt: [hi@neftlix.tv](mailto:hi@neftlix.tv)

---

## 🇮🇹 Italiano

### Descrizione Generale

**TvPlatformix** è un client di streaming in stile Netflix per account IPTV Xtream Codes che possiedi già. L'app riunisce film, serie, TV in diretta e sport in un'interfaccia moderna ed elegante, disponibile sia come app web che applicazione desktop (macOS, Windows).

### Composizione Tecnica

- **Linguaggio Principale**: TypeScript (87,3%)
- **Stili**: CSS (8,2%)
- **Markup**: HTML (3,9%)
- **Altro**: 0,6%

### Stack Tecnologico

- **Backend**: Node.js 23 (TypeScript nativo) + Fastify + SQLite
- **Frontend**: React + Vite + hls.js
- **Desktop**: Electron
- **Distribuzione**: Docker supportato

### Funzionalità Principali

- 🎬 **Film** con poster, trama, cast, ricerca per categoria
- 📺 **Serie** con stagioni ed episodi, marcatura automatica come visto
- 📡 **TV in Diretta** con tutti i canali del tuo provider
- 🗓️ **Guida Elettronica (EPG)** mostra cosa va in onda ora
- 👤 **Profili** fino a 5 per installazione, ognuno con il suo progresso
- ▶️ **Continua a Guardare** riprendi da dove hai smesso
- ❤️ **Lista Preferiti** e Watchlist
- ⚽ **Abbinamento Sport** con orari ufficiali di inizio
- 🔎 **Ricerca** su film, serie e canali
- 📱 **Funziona Ovunque** dal telefono alla TV, installabile come PWA

### Organizzazione del Codice

```
server/       Server Node + Fastify e API REST
web/          Applicazione React + Vite
desktop/      Applicazione desktop Electron
docs/         Documentazione tecnica
```

### Primissimi Passi

```bash
# Installazione di base
git clone https://github.com/c4rtical/neftlix.git
cd neftlix
npm install
npm start
```

Apri `http://localhost:8787`

Richiede Node.js 23.6 o più recente.

#### Docker

```bash
docker compose up -d
```

### Variabili d'Ambiente

| Variabile | Predefinita | Scopo |
|---|---|---|
| `PORT` | `8787` | Porta HTTP |
| `HOST` | `0.0.0.0` | Indirizzo di binding |
| `NEFTLIX_DATA` | `./data` | Directory database SQLite |
| `NEFTLIX_PASSWORD` | – | Autenticazione HTTP di base per l'intera app |
| `FOOTBALL_DATA_KEY` | – | Chiave gratuita football-data.org per i calendari |
| `TMDB_API_KEY` | – | Chiave TMDB per arricchire i metadati |
| `LOG_LEVEL` | `info` | Livello log Fastify |

### Scorciatoie da Tastiera / Telecomando

| Tasto | Azione |
|---|---|
| Frecce | Sposta focus |
| Invio | Apri / Riproduci |
| Esc, Backspace | Chiudi lettore |
| Nel lettore: ← → | Cerca ±10 s |
| Nel lettore: ↑ ↓ | Cerca ±60 s |
| Spazio | Riproduci / Pausa |
| N | Episodio successivo |
| F | Schermo intero |
| M | Muto |

### Contribuire

Segnalazioni di bug con campioni JSON del pannello sono più preziose. Vedi [CONTRIBUTING.md](CONTRIBUTING.md).

Contatti: [hi@neftlix.tv](mailto:hi@neftlix.tv)

---

## 📝 Note

Cette documentation a été générée automatiquement pour fournir des traductions cohérentes du repository TvPlatformix dans plusieurs langues. Les informations techniques sont basées sur l'analyse du code source et de la documentation du projet.

---

**Last Updated**: 2026-09-13  
**Repository**: [TvPlatformix](https://github.com/lgtv80660-png/TvPlatformix)
