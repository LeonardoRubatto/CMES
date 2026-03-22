# Convertisseur de Mesures

> Convertisseur universel d'unités de mesure — facteurs officiels BIPM & NIST 2026  
> Domaine : https://mesures.wecalc.fr · Langue : fr · Catégorie : Outils · Accent : `#0F766E`

## Fonctionnalités

- Conversion dans 12 familles d'unités : longueur, masse, volume, surface, température, temps, vitesse, pression, énergie, puissance, angle, données numériques
- Facteurs de conversion issus exclusivement du Bureau International des Poids et Mesures (BIPM) et du NIST — précision maximale, pas d'arrondi intermédiaire
- Conversion bidirectionnelle : saisie dans n'importe quelle unité de la famille, résultat instantané dans toutes les autres
- Swap en un clic pour inverser le sens de conversion
- Partage de résultat par URL encodée, export PDF, dark mode, cookie banner RGPD, responsive mobile
- 4 blocs JSON-LD : `WebApplication`, `WebSite`, `BreadcrumbList`, `FAQPage` — rich results Google activés

## Structure des fichiers

```
CMES/
├── index.html
├── confidentialite.html
├── 404.html
├── _headers
├── robots.txt
├── sitemap.xml
├── readme.md
├── favicon.png
├── apple-touch-icon.png
├── og-image.png
└── assets/
    └── icons/
        ├── logo-fibo4.svg
        ├── bonus.svg
        ├── calc.svg
        ├── egal.svg
        ├── europe.svg
        ├── exam.svg
        ├── france.svg
        ├── info.svg
        ├── monitor.svg
        ├── op.svg
        ├── pdf.svg
        ├── share.svg
        ├── sources.svg
        ├── sources-dark.svg
        ├── success.svg
        ├── swap.svg
        ├── theme-dark.svg
        ├── theme-light.svg
        └── warning.svg
```

## Icônes SVG requises

Installer dans `/assets/icons/` : `logo-fibo4.svg`, `bonus.svg`, `calc.svg`, `egal.svg`, `europe.svg`, `exam.svg`, `france.svg`, `info.svg`, `monitor.svg`, `op.svg`, `pdf.svg`, `share.svg`, `sources.svg`, `sources-dark.svg`, `success.svg`, `swap.svg`, `theme-dark.svg`, `theme-light.svg`, `warning.svg`

## Sources des données

| Source | Organisme | URL | Vérifié le |
|--------|-----------|-----|------------|
| Facteurs de conversion SI — longueur, masse, volume, surface, temps | BIPM | https://www.bipm.org/en/measurement-units | 2026-03-20 |
| Facteurs de conversion — unités non-SI (pouce, pied, mile, livre, gallon…) | NIST | https://www.nist.gov/pml/weights-and-measures/metric-si/unit-conversion | 2026-03-20 |
| Conversions de température (Celsius, Fahrenheit, Kelvin, Rankine) | NIST | https://www.nist.gov | 2026-03-20 |
| Unités de données numériques (bit, octet, kibioctet…) | IEC 80000-13 | https://www.iec.ch | 2026-03-20 |

## Déploiement

Push GitHub → Cloudflare Pages. Aucun outil de build. Le dossier `CMES/` est la racine du site.

```bash
git add .
git commit -m "update: [description courte]"
git push origin main
```

Cloudflare Pages détecte le push et redéploie automatiquement en ~30 secondes.

## Mise à jour des données

- Fréquence recommandée : tous les 3 ans (les facteurs SI sont très stables) ou lors d'une révision BIPM
- Prochaine vérification : janvier 2029
- Fichiers à mettre à jour : `index.html` (facteurs dans `CFG`), `sitemap.xml` (`lastmod`)

## Assets graphiques à produire manuellement

| Fichier | Dimensions | Contenu |
|---------|------------|---------|
| `favicon.png` | 32×32 px | Fond `#0F766E`, lettres **CM** en blanc, bold, centré |
| `apple-touch-icon.png` | 180×180 px | Même design — iOS arrondit automatiquement les coins |
| `og-image.png` | 1200×630 px | Fond `#dde6ef`, card blanche centrée : logo + "Convertisseur de Mesures 2026 — Longueur, Masse, Volume, Température" |

