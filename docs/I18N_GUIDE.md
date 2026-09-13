# i18n Implementation Guide for TvPlatformix

## 🌍 Options i18n pour React + Node.js

### 1. **react-i18next** (Frontend - React)
Le meilleur choix pour le frontend React, basé sur i18next.

**Avantages:**
- ✅ Support namespace (fichiers séparés par domaine)
- ✅ Lazy loading des traductions
- ✅ Gestion des langues facile
- ✅ Intégration React hooks
- ✅ Traduction dynamique des paramètres
- ✅ Pluralisation et contextes

**Installation:**
```bash
npm install i18next react-i18next i18next-browser-languagedetector i18next-http-backend
```

### 2. **i18next** (Backend - Node.js)
Pour le serveur Fastify.

**Avantages:**
- ✅ Même écosystème que le frontend
- ✅ Traduction des erreurs et messages API
- ✅ Synchronisation frontend/backend

**Installation:**
```bash
npm install i18next i18next-fs-backend
```

### 3. **Alternatives**
- **next-i18next**: Si vous utilisez Next.js (non le cas ici)
- **i18n-js**: Solution plus légère
- **lingui**: Alternative avec meilleure DX

---

## 📁 Structure recommandée pour TvPlatformix

```
web/
  src/
    i18n/
      locales/
        en/
          common.json       # Termes généraux
          nav.json          # Navigation
          movies.json       # Films
          series.json       # Séries
          live.json         # Live TV
          profiles.json     # Profils
          player.json       # Lecteur
          errors.json       # Erreurs
        fr/
          common.json
          nav.json
          ...
        es/
          ...
        de/
          ...
        it/
          ...
      i18n.js             # Configuration
    components/
      i18nProvider.tsx    # Wrapper
    pages/
      home.tsx
      movies.tsx
      ...

server/
  src/
    i18n/
      locales/
        en/
          api.json        # Messages API
          errors.json     # Erreurs serveur
        fr/
          ...
      i18n.ts            # Configuration serveur
```

---

## 💻 Implémentation Frontend (React)

### 1. Configuration i18n.js

```typescript
import i18n from 'i18next';
import { initReactI18next } from 'react-i18next';
import LanguageDetector from 'i18next-browser-languagedetector';
import HttpBackend from 'i18next-http-backend';

// Importation directe (ou via http-backend)
import enCommon from './locales/en/common.json';
import enNav from './locales/en/nav.json';
import frCommon from './locales/fr/common.json';
import frNav from './locales/fr/nav.json';
import esCommon from './locales/es/common.json';
import deCommon from './locales/de/common.json';
import itCommon from './locales/it/common.json';

const resources = {
  en: {
    common: enCommon,
    nav: enNav,
  },
  fr: {
    common: frCommon,
    nav: frNav,
  },
  es: { common: esCommon },
  de: { common: deCommon },
  it: { common: itCommon },
};

i18n
  .use(LanguageDetector)      // Détecte la langue du navigateur
  .use(initReactI18next)      // Intègre React
  .init({
    resources,
    fallbackLng: 'en',
    debug: false,
    
    interpolation: {
      escapeValue: false      // React protège déjà contre XSS
    },
    
    detection: {
      order: ['querystring', 'cookie', 'localStorage', 'navigator'],
      caches: ['localStorage', 'cookie']
    },
    
    ns: ['common', 'nav'],
    defaultNS: 'common',
  });

export default i18n;
```

### 2. Fichier de traduction (locales/en/common.json)

```json
{
  "app": {
    "title": "Neftlix",
    "subtitle": "Your IPTV streaming client",
    "description": "Netflix-style streaming for your Xtream IPTV account"
  },
  "navigation": {
    "home": "Home",
    "movies": "Movies",
    "series": "Series",
    "live": "Live TV",
    "sport": "Sport",
    "profiles": "Profiles",
    "settings": "Settings"
  },
  "features": {
    "movies": "Movies with posters, plot and cast",
    "series": "Series with seasons and episodes",
    "liveTV": "Live TV with all provider channels",
    "epg": "Electronic Program Guide",
    "profiles": "Up to 5 profiles per installation",
    "continueWatching": "Continue watching your shows",
    "watchlist": "Add to watchlist",
    "sports": "Sports matching with kickoff times",
    "search": "Search across movies, series and channels"
  },
  "player": {
    "play": "Play",
    "pause": "Pause",
    "mute": "Mute",
    "fullscreen": "Fullscreen",
    "nextEpisode": "Next Episode",
    "seek": "Seek",
    "loading": "Loading..."
  },
  "errors": {
    "noProfile": "No profile selected",
    "loadingFailed": "Failed to load content",
    "playerError": "Player error",
    "connectionError": "Connection error"
  }
}
```

### 3. Composant avec i18n

```typescript
import { useTranslation } from 'react-i18next';

export function Home() {
  const { t, i18n } = useTranslation(['common', 'nav']);

  const changeLanguage = (lng: string) => {
    i18n.changeLanguage(lng);
  };

  return (
    <div>
      <h1>{t('app.title')}</h1>
      <p>{t('app.description')}</p>
      
      <div>
        <button onClick={() => changeLanguage('en')}>English</button>
        <button onClick={() => changeLanguage('fr')}>Français</button>
        <button onClick={() => changeLanguage('es')}>Español</button>
        <button onClick={() => changeLanguage('de')}>Deutsch</button>
        <button onClick={() => changeLanguage('it')}>Italiano</button>
      </div>
      
      <section>
        <h2>{t('features.movies')}</h2>
        <h2>{t('features.series')}</h2>
      </section>
    </div>
  );
}
```

### 4. Provider (App.tsx)

```typescript
import i18n from './i18n/i18n';
import { I18nextProvider } from 'react-i18next';
import Home from './pages/home';

function App() {
  return (
    <I18nextProvider i18n={i18n}>
      <Home />
    </I18nextProvider>
  );
}

export default App;
```

---

## 🖥️ Implémentation Backend (Node.js + Fastify)

### 1. Configuration serveur (server/src/i18n.ts)

```typescript
import i18next from 'i18next';
import FSBackend from 'i18next-fs-backend';
import path from 'node:path';

const localeDir = path.resolve(process.cwd(), 'server/src/i18n/locales');

i18next
  .use(FSBackend)
  .init({
    lng: 'en',
    fallbackLng: 'en',
    ns: ['api', 'errors'],
    defaultNS: 'api',
    backend: {
      loadPath: `${localeDir}/{{lng}}/{{ns}}.json`,
    },
    interpolation: {
      escapeValue: false,
    },
  });

export default i18next;
```

### 2. Fichier traductions serveur (server/src/i18n/locales/en/errors.json)

```json
{
  "auth": {
    "invalid_credentials": "Invalid username or password",
    "connection_failed": "Failed to connect to provider",
    "no_account": "No account configured"
  },
  "profile": {
    "not_found": "Profile not found",
    "max_profiles": "Maximum 5 profiles allowed"
  },
  "stream": {
    "not_available": "Stream not available",
    "max_connections": "Maximum connections reached"
  },
  "validation": {
    "required": "This field is required",
    "invalid_url": "Invalid URL",
    "invalid_port": "Invalid port number"
  }
}
```

### 3. Middleware Fastify

```typescript
import i18next from './i18n';

export function i18nMiddleware(app: FastifyInstance) {
  app.addHook('preHandler', async (request, reply) => {
    // Détecte la langue depuis Accept-Language header
    const acceptLanguage = request.headers['accept-language'];
    const lang = acceptLanguage?.split(',')[0].split('-')[0] || 'en';
    
    // Change la langue pour ce contexte
    await i18next.changeLanguage(lang);
    
    // Ajoute la fonction de traduction à la requête
    request.t = (key: string, ns?: string) => 
      i18next.t(key, { ns, defaultValue: key });
  });
}
```

### 4. Utilisation dans les routes

```typescript
export async function registerApiRoutes(app: FastifyInstance, ctx: AppContext) {
  app.post('/api/account', async (request, reply) => {
    try {
      const { host, username, password } = request.body as AccountData;
      
      if (!host || !username || !password) {
        return reply.code(400).send({
          error: request.t('validation.required', 'errors')
        });
      }
      
      const client = new XtreamClient({ host, username, password });
      const info = await client.getAccountInfo();
      
      if (!info) {
        return reply.code(401).send({
          error: request.t('auth.invalid_credentials', 'errors')
        });
      }
      
      return { success: true };
    } catch (err) {
      return reply.code(500).send({
        error: request.t('auth.connection_failed', 'errors')
      });
    }
  });
}
```

---

## 🔄 Synchronisation Frontend/Backend

### Partage des traductions communes

```typescript
// web/src/i18n/locales/en/api.json
{
  "messages": {
    "loading": "Loading...",
    "success": "Operation successful",
    "error": "An error occurred"
  }
}

// server/src/i18n/locales/en/api.json (même fichier!)
// Copié depuis le frontend ou source unique
```

---

## 📦 Intégration avec votre architecture

### Pour le **serveur** (server/):
```bash
npm install i18next i18next-fs-backend
```

### Pour le **web** (web/):
```bash
npm install i18next react-i18next i18next-browser-languagedetector
```

### Pour la configuration de **build**:
```json
{
  "scripts": {
    "dev": "npm run dev --workspace=server & npm run dev --workspace=web & wait",
    "i18n:sync": "node scripts/sync-i18n.js"
  }
}
```

---

## ✨ Avantages par rapport aux fichiers statiques

| Aspect | TRANSLATIONS.md | i18n |
|--------|-----------------|------|
| **Chargement** | Une fois au démarrage | Lazy loading |
| **Détection langue** | Manuel | Automatique |
| **Changement langue** | Page reload | Instant |
| **Maintenance** | Fichier unique énorme | Fichiers organisés |
| **Frontend/Backend** | Séparé | Synchronisé |
| **Pluralisation** | Non | Oui |
| **Contextes** | Non | Oui |
| **Scalabilité** | ❌ | ✅ |

---

## 🚀 Prochaines étapes

1. ✅ Installer i18n dans les workspaces
2. ✅ Créer la structure `/locales`
3. ✅ Traduire les textes clés
4. ✅ Implémenter le changement de langue
5. ✅ Tester détection automatique
6. ✅ Intégrer serveur API

**Recommandation**: Commencez par le frontend, puis étendez au serveur.

