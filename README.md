# Hamza Elgoudany — portfolio

Site statique (HTML/CSS/JS, sans build), bilingue FR/EN, tiré de l'artefact Claude d'origine.

- Aperçu local : `npx serve .` ou ouvrir `index.html`
- Déploiement : GitHub Pages, automatique à chaque push sur `main` (`.github/workflows/pages.yml`, source Pages = GitHub Actions). Aucun build.
- Production : https://www.hamzaelgoudany.com (domaine perso, DNS chez Namecheap, fichier `CNAME` à la racine).
- SEO : `sitemap.xml` et `robots.txt` à la racine ; si on ajoute un fichier public, l'ajouter aussi à la commande `cp` du workflow.
- Bouton CV : déposer un fichier `cv.pdf` à la racine pour l'activer.
