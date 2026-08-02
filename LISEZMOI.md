# Mon programme minceur — application mobile

Ce dossier contient votre application transformée en **PWA (Progressive Web App)** :
verrouillée en portrait, installable sur l'écran d'accueil Android, fonctionne hors-ligne,
et toutes vos données (repas, courses, pesées) sont stockées **directement sur votre
téléphone** (aucun serveur, aucun compte).

`index.html` est **autonome** : tout le code de l'application est intégré dedans, vous
pouvez donc l'ouvrir directement en double-cliquant dessus, même sans les autres
fichiers du dossier. Les autres fichiers (`manifest.json`, `sw.js`, `icons/`) ne servent
que si vous voulez l'installer comme une vraie app (voir ci-dessous) — gardez-les dans
le même dossier pour cet usage.

## Important — pourquoi pas directement un .apk ?

Je ne peux pas compiler un fichier `.apk` signé dans mon environnement (pas d'accès à
Android Studio / au SDK Android). En revanche, ce que vous avez ici se transforme en
vrai `.apk` en **2 minutes, gratuitement, sans écrire une ligne de code** — voir l'étape 2.

## Étape 1 — Héberger l'application (gratuit, 2 minutes)

Un PWA doit être servi via une URL `https://` pour être installable. Le plus simple :

**Avec Netlify (recommandé, sans compte GitHub) :**
1. Allez sur https://app.netlify.com/drop
2. Glissez-déposez ce dossier entier (`dist`, ou tout son contenu) dans la zone de dépôt.
3. Netlify vous donne une URL du type `https://votre-app.netlify.app`.

**Avec GitHub Pages :** créez un dépôt, uploadez le contenu de ce dossier, activez
Pages dans les réglages du dépôt.

## Étape 2 — Obtenir le vrai fichier .apk

1. Allez sur https://www.pwabuilder.com
2. Collez l'URL obtenue à l'étape 1, cliquez sur « Start ».
3. Cliquez sur le bloc **Android** puis **Generate Package**.
4. Téléchargez le `.apk` (ou `.aab` pour le Play Store) généré — il est signé et
   installable directement sur votre téléphone (autoriser « sources inconnues » si demandé).

C'est un vrai wrapper Android natif (Trusted Web Activity), pas juste un raccourci :
il tourne en plein écran, verrouillé en portrait, avec votre icône.

## Alternative sans hébergement : installer directement en PWA

Sur votre téléphone Android, ouvrez simplement `index.html` hébergé (étape 1) dans
Chrome, puis menu ⋮ → **« Installer l'application »**. Vous obtenez une icône sur
l'écran d'accueil qui se comporte comme une app native — sans passer par un `.apk`.

## Contenu du dossier

- `index.html` — page principale
- `app.js` — application (React) entièrement autonome, aucune dépendance externe
- `manifest.json` — nom, icônes, **orientation verrouillée en portrait**
- `sw.js` — service worker (fonctionnement hors-ligne)
- `icons/` — icônes de l'application

## Vos données

Tout est stocké en local sur l'appareil (`localStorage`). Si vous désinstallez
l'application ou effacez les données du navigateur, l'historique sera perdu — pensez à
exporter vos données importantes si besoin (fonctionnalité à ajouter sur demande).
