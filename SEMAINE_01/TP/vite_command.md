# Vite JS 

## Introduction

[Vite.js](https://vitejs.dev/) est un outil de développement rapide pour la création d'applications web modernes en JavaScript et TypeScript. 

Il est conçu pour être simple à utiliser, performant et évolutif. Vite se concentre sur la rapidité en offrant une expérience de développement proche de la production.

### Caractéristiques Principales

1. **Développement Rapide :** Vite offre un temps de rechargement ultra-rapide et un serveur de développement performant grâce à son utilisation de l'Esm (ECMAScript Modules) natif.

1. **React.js Préconfiguré :** Vite est souvent utilisé avec `React.js`, où il offre une configuration par défaut pour une expérience de développement rapide avec React.

1. **Importation Dynamique :** Vite prend en charge l'importation dynamique des modules, permettant le chargement à la demande pour une performance optimale.

1. **Construction Optimisée :** En production, Vite produit des bundles optimisés avec des dépendances minifiées, ce qui améliore les performances.

## Installation

Pour créer un nouveau projet Vite, assurez-vous d'avoir (version LTS) [Node.js](https://nodejs.org/) installé, puis exécutez les commandes suivantes dans votre terminal :

```bash
# Créez un nouveau projet Vite
npm create vite my-vite-app

# Accédez au répertoire du projet
cd my-vite-app

# Installez les dépendances
npm install
```

## Structure du Projet

La structure de base d'un projet Vite ressemble à ceci :

```
my-vite-app
├── node_modules
├── public
│   └── index.html
├── src
│   └── main.js
├── .gitignore
├── package.json
├── vite.config.js
```

## Exemple Vanilla JS

Créons un exemple simple avec Vite utilisant JavaScript pur.

1. Créez un nouveau projet Vite :

   ```bash
   npm create vite my-vanilla-vite-app
   cd my-vanilla-vite-app
   ```

1. Installez les dépendances :

   ```bash
   npm install
   ```

1. Créez un fichier HTML dans le répertoire `public` :

   ```html
   <!-- public/index.html -->
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta http-equiv="X-UA-Compatible" content="IE=edge">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Vanilla Vite App</title>
   </head>
   <body>
       <div id="app"></div>
       <script type="module" src="/src/main.js"></script>
   </body>
   </html>
   ```

1. Créez un fichier JavaScript dans le répertoire `src` :

   ```javascript
   // src/main.js
   const app = document.getElementById('app');
   app.innerHTML = '<h1>Hello from Vanilla Vite!</h1>';
   ```

1. Lancez l'application :

   ```bash
   npm run dev
   ```

   Ouvrez votre navigateur et accédez à [http://localhost:3000](http://localhost:3000). Vous devriez voir le message "Hello from Vanilla Vite!".
