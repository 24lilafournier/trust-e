# Trust — Assistant de coaching

## Structure du projet

```
trust-coaching/
├── api/
│   └── chat.js          ← fonction serverless (proxy sécurisé vers Anthropic)
├── public/
│   └── index.html       ← interface complète (coach + client)
├── vercel.json          ← configuration Vercel
└── README.md
```

## Déploiement en 5 étapes

### 1. Créer le repo GitHub
- Crée un nouveau repo sur github.com (ex: `trust-coaching`)
- Dépose les 3 fichiers en respectant exactement la structure ci-dessus

### 2. Créer un compte Vercel
- Va sur vercel.com → "Sign up with GitHub"
- Autorise l'accès à ton repo

### 3. Importer le projet
- Dans Vercel : "Add New Project" → sélectionne `trust-coaching`
- Framework preset : **Other**
- Root directory : laisser vide
- Clique "Deploy"

### 4. Ajouter la clé API Anthropic (IMPORTANT)
- Dans Vercel : Settings → Environment Variables
- Ajoute : `ANTHROPIC_API_KEY` = ta clé (commence par `sk-ant-...`)
- Clique "Save"
- **Redéploie** : Deployments → "Redeploy"

### 5. Accéder à l'outil
- Vercel te donne une URL du type `trust-coaching-xyz.vercel.app`
- C'est ton outil en ligne, accessible partout

## Récupérer ta clé Anthropic
- Va sur console.anthropic.com
- "API Keys" → "Create Key"
- Copie-la immédiatement (elle n'est affichée qu'une fois)

## Coût estimé (phase pilote, 3 clients)
- Vercel : gratuit
- Anthropic API : ~1-2€/mois (claude-sonnet, ~500 messages/mois)

## Sécurité
- La clé API n'est jamais exposée côté client
- Toutes les requêtes passent par /api/chat (serverless function)
- Le client ne voit jamais le prompt système
