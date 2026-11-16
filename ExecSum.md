# ExecSum — Portfolio Hamza Elgoudany

## Quoi
Site portfolio statique bilingue (FR/EN), sans build, issu d'un artefact Claude. Transformé en PWA installable.

## Où
- Dépôt : https://github.com/Elgoudany/portfolio (public, branche `main`)
- Site (production) : https://www.hamzaelgoudany.com (GitHub Pages, domaine perso ; DNS chez Namecheap ; fichier `CNAME` = `www.hamzaelgoudany.com`)
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

## SEO
`index.html` : canonical, meta description, Open Graph, Twitter, JSON-LD `Person` (pays seulement : aucune ville dans le site). `sitemap.xml`, `robots.txt`. Cache du service worker : `v2`.

## État / à vérifier
- Après le dernier push, vérifier sur le site en ligne que « Install page as app » (menu ⋮ > Cast, save, and share) et le bouton fonctionnent. Vider le service worker (F12 > Application > Unregister) + Ctrl+Shift+R si cache ancien.
- Le Chrome de l'utilisateur est géré par une organisation (innovx.ma) : l'installation peut être bloquée par politique. Alternative : Edge / profil perso / Android.
- Lien `www.hamzaelgoudany.com` en bas de page : correct (domaine de production).
- Chemins relatifs (`img/...`) : conservés ; le site est servi à la racine du domaine.

## Pistes
- Lien CV simple, vérifier le rendu mobile réel, soumettre `sitemap.xml` à Google Search Console.
