# ExecSum — Portfolio Hamza Elgoudany

## Quoi
Site portfolio statique bilingue (FR/EN), sans build, issu d'un artefact Claude. Transformé en PWA installable.

## Où
- Dépôt : https://github.com/Elgoudany/portfolio (public, branche `main`)
- Site : https://elgoudany.github.io/portfolio/
- Déploiement : GitHub Pages, auto à chaque push sur `main` (`.github/workflows/pages.yml`).

## Fichiers
- `index.html` : tout le site (CSS + JS inline, rooms via `#hash`). Lien manifeste dans le `<head>`.
- `manifest.webmanifest`, `sw.js` (réseau d'abord, cache en secours), `img/icon-192.png`, `img/icon-512.png` (tirées de `portrait.jpg`).
- `img/` : portrait, captures CalTrack (`ct-*`), photos voyages (`ph-*`).
- Bouton « ⬇ Installer l'app » dans la barre du haut (`#pwa-btn`) : `beforeinstallprompt` ; sur iPhone, affiche les étapes (Partager > Écran d'accueil).
- Bouton CV : n'apparaît que si `cv.pdf` existe ET dans claude.ai (`window.claude`). À remplacer par un simple lien si besoin ; le workflow copie déjà `cv.pdf` s'il existe.

## Historique
1. Import de l'artefact -> dépôt `portfolio` (créé par l'utilisateur ; la session ne pouvait pas créer de dépôt).
2. Pages exigeait un dépôt public -> rendu public. Source Pages = GitHub Actions.
3. PWA ajoutée : manifeste, service worker, icônes.
4. Bouton d'installation ajouté.
5. Bug corrigé : le `<link rel="manifest">` était dans le `<body>`, donc Chrome l'ignorait. Déplacé dans le `<head>` (installabilité validée en local, aucune erreur).

## État / à vérifier
- Après le dernier push, vérifier sur le site en ligne que « Install page as app » (menu ⋮ > Cast, save, and share) et le bouton fonctionnent. Vider le service worker (F12 > Application > Unregister) + Ctrl+Shift+R si cache ancien.
- Le Chrome de l'utilisateur est géré par une organisation (innovx.ma) : l'installation peut être bloquée par politique. Alternative : Edge / profil perso / Android.
- Lien vers `hamzaelgoudany.com` en bas de page : jamais vérifié (fichier source tronqué à cet endroit).
- Chemins relatifs (`img/...`) : le site fonctionne sous `/portfolio/`.

## Pistes
- Lien CV simple, domaine perso, vérifier le rendu mobile réel.
