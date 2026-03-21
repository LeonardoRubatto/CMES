# ConvertisseurMesure — readme.md

**Site :** convertisseur-mesure.fr
**Langue :** Français
**Catégorie :** Utilitaire / Conversion d'unités
**Couleur accent :** `#0F766E` (teal)
**Dernière mise à jour :** 20 mars 2026

---

## Description

Convertisseur universel d'unités de mesure en français, déployé en statique sur Cloudflare Pages.

- 12 familles de mesure : longueur, masse, surface, volume, température, temps, vitesse, pression, énergie, puissance, angle, données numériques
- Facteurs officiels BIPM SI Brochure 9e édition et NIST Handbook 44 (2026) — aucune valeur approximée
- Mode données binaire/décimal (IEC vs SI) avec bascule dédiée
- Conversion de température via formules affines (Kelvin, Celsius, Fahrenheit) — pas de simple facteur multiplicatif
- Partage par URL (état complet encodé en query params), sauvegarde localStorage, export PDF via jsPDF
- Mode clair / sombre avec anti-flash, cookie banner RGPD, affiliés avec disclaimer

---

## Structure des fichiers

```
convertisseur-mesure.fr/
├── index.html                  # Calculateur principal (~1700 lignes)
├── confidentialite.html        # RGPD, mentions légales, conditions, contact
├── 404.html                    # Page d'erreur personnalisée
├── robots.txt                  # Autorisation crawlers + sitemap
├── sitemap.xml                 # 2 URLs indexées
├── _headers                    # En-têtes Cloudflare Pages (CSP, HSTS, cache)
├── readme.md                   # Ce fichier
├── assets/
│   └── icons/
│       ├── warning.svg
│       ├── info.svg
│       ├── error.svg
│       ├── success.svg
│       ├── share.svg
│       ├── pdf.svg
│       ├── sources.svg
│       ├── theme-dark.svg
│       ├── theme-light.svg
│       └── france.svg
├── favicon.png                 # 32×32 px
├── apple-touch-icon.png        # 180×180 px
└── og-image.png                # 1200×630 px
```

---

## Icônes

Tous les SVG doivent être placés dans `/assets/icons/`.

```
warning.svg, info.svg, error.svg, success.svg,
share.svg, pdf.svg, sources.svg,
theme-dark.svg, theme-light.svg, france.svg
```

Aucun SVG n'est inliné dans le HTML — tous passent par l'objet `ICONS` en JS et la fonction `hydrateIcons()`.

---

## Sources des données

| Source | Description | Date vérification |
|--------|-------------|-------------------|
| BIPM SI Brochure 9e éd. (v3.02) | Unités SI et admises : litre, tonne, hectare, minute, heure, jour, bar, électronvolt, etc. | 08/2025 |
| NIST HB 44 Appendix C (2026) | Pouce international (1 in = 2,54 cm), pied (1 ft = 0,3048 m), mile, yard, once, livre, gallon US | 06/01/2026 |
| NIST SP 811 Appendix B | Facteurs de conversion étendus : psi, mmHg, nœud, cheval-vapeur mécanique, acre, BTU, cal | 06/01/2026 |
| IEC 80000-13 | Préfixes binaires KiB, MiB, GiB, TiB | 08/2025 |
| NIST — Binary Prefixes | Clarification préfixes décimaux vs binaires IEC | 08/2025 |

---

## Déploiement

1. Pousser les fichiers sur le dépôt GitHub lié au projet
2. Cloudflare Pages détecte automatiquement le push et déclenche un déploiement
3. Aucun outil de build requis — fichiers statiques purs (HTML/CSS/JS inline)
4. Le fichier `_headers` est lu nativement par Cloudflare Pages pour injecter les en-têtes HTTP
5. URL de production : https://convertisseur-mesure.fr/

---

## Mise à jour des données

Les facteurs de conversion sont des définitions normatives stables. Une vérification annuelle est recommandée pour s'assurer qu'aucune révision BIPM ou NIST n'a introduit de modification.

**Prochaine vérification recommandée :** janvier 2027

---

## Assets graphiques

À produire manuellement — ne pas copier les assets d'un autre site.

| Fichier | Dimensions | Contenu |
|---|---|---|
| `favicon.png` | 32×32 px | Fond `#0F766E`, lettres **CM** en blanc, bold, centré |
| `apple-touch-icon.png` | 180×180 px | Même design que favicon — iOS ajoute automatiquement les coins arrondis |
| `og-image.png` | 1200×630 px | Fond `#dde6ef`, card blanche centrée avec logo CM + nom « ConvertisseurMesure » + sous-titre « Convertisseur universel d'unités — BIPM & NIST 2026 » |
