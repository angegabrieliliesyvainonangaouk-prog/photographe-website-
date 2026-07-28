# Optimisation Performance Lighthouse

## Score actuel : Performance = 55

---

## Plan de correction (5 étapes)

| # | Tâche | Fichier(s) concernés | Impact |
|---|-------|----------------------|--------|
| 1 | Compresser et redimensionner les images (qualité 70%, max 1920px, format WebP) | `assets/images/` (15 fichiers) | 🔴 Très fort |
| 2 | Remplacer `bootstrap.css` → `bootstrap.min.css` | `index.html` ligne 5 | 🟡 Moyen |
| 3 | Remplacer `bootstrap.bundle.js` → `bootstrap.bundle.min.js` | `index.html` ligne 13 | 🟡 Moyen |
| 4 | Ajouter `defer` aux 4 balises `<script>` dans `<head>` | `index.html` lignes 13-16 | 🟡 Moyen |
| 5 | Ajouter `loading="lazy"` sur les images de la galerie | `index.html` lignes 75-84 | 🟢 Faible |

---

## Détail des images à optimiser (étape 1)

| Image | Poids actuel | Format | Cible |
|-------|-------------|--------|-------|
| `slider/edward-cisneros-...jpg` | 5,5 Mo | JPEG | ~200 Ko |
| `slider/nicholas-green-...jpg` | 1,9 Mo | JPEG | ~150 Ko |
| `slider/ryoji-iwata-...jpg` | 1,6 Mo | JPEG | ~150 Ko |
| `gallery/mariage/jakob-owens-...jpg` | 6,0 Mo | JPEG | ~200 Ko |
| `gallery/mariage/hannah-busing-...jpg` | 1,7 Mo | JPEG | ~150 Ko |
| `gallery/portrait/nino-van-prattenburg-...jpg` | 2,5 Mo | JPEG | ~150 Ko |
| `gallery/portrait/ade-tunji-...jpg` | 979 Ko | JPEG | ~120 Ko |
| `gallery/concert/austin-neill-...jpg` | 1,5 Mo | JPEG | ~150 Ko |
| `gallery/concert/aaron-paul-...jpg` | 1012 Ko | JPEG | ~120 Ko |
| `gallery/entreprise/mateus-campos-felipe-...jpg` | 1,9 Mo | JPEG | ~150 Ko |
| `gallery/entreprise/ali-morshedlou-...jpg` | 1,1 Mo | JPEG | ~150 Ko |
| `gallery/entreprise/jason-goodman-...jpg` | 698 Ko | JPEG | ~100 Ko |
| `nina.png` | 2,1 Mo | PNG | ~100 Ko (WebP) |
| `camera.png` | 1,6 Mo | PNG | ~80 Ko (WebP) |
| `instagram.png` | 721 o | PNG | ~721 o (déjà OK) |
| **Total** | **~31 Mo** | | **~900 Ko** |

---

## Plan d'optimisation (score : 61 → 90+)

| # | Action | Détail | Fichier(s) | Impact |
|---|--------|--------|-----------|--------|
| 1 | ✅ `bootstrap.css` → `bootstrap.min.css` | Version minifiée : 201 Ko → 161 Ko | `index.html:5` | -40 Ko CSS |
| 2 | ✅ `bootstrap.bundle.js` → `bootstrap.bundle.min.js` | Version minifiée : 205 Ko → 77 Ko | `index.html:13` | -128 Ko JS |
| 3 | ✅ `defer` sur 4 scripts | Les scripts ne bloquent plus le rendu initial (passent après le HTML) | `index.html:13-16` | Render non-bloquant |
| 4 | ✅ Google Fonts non-bloquant | `media="print"` → le CSS des polices est chargé sans bloquer le rendu, puis `onload="this.media='all'"` l'applique après chargement | `index.html:9` | Render non-bloquant |
| 5 | ✅ `nina.png` → `nina.webp` (29 Ko) | Redimensionné à 600px (taille d'affichage ~450px dans section À propos). Format WebP qualité 85 | `assets/images/nina.png` | 2,1 Mo → 29 Ko |
| 5b | ✅ `camera.png` → `camera.webp` (2,8 Ko) | Icône décorative, redimensionnée à 200px. WebP qualité 80 | `assets/images/camera.png` | 1,6 Mo → 2,8 Ko |
| 6 | ✅ `loading="lazy"` sur 11 images | Galerie (9), nina, camera — chargées uniquement quand elles entrent dans le viewport. Pas appliqué au slider (LCP). | `index.html:63,76-84,156` | Chargement différé |
| 7 | ✅ `width`/`height` + `height:auto` | Attributs `width="1920" height="888"` sur les 3 images du slider pour réserver l'espace. `style.css:10` ajoute `height: auto` pour éviter l'étirement avec `w-100`. | `index.html:42-48` + `style.css:10` | CLS réduit |
| 8 | ✅ `<link rel="preload">` image LCP | La 1ère image du carousel est préchargée dans le `<head>` pour que le navigateur la découvre immédiatement | `index.html:4` | Découverte précoce |

---

## Commandes ImageMagick exécutées

### Slider (3 images) — ✅ Fait
```bash
cd assets/images/slider
for img in *.jpg; do
  convert "$img" -resize 1920x -quality 85 -strip "${img%.jpg}.webp"
done
```
Résultat : 9 Mo → 416 Ko (-95%)

### Galerie (9 images) — ✅ Fait
```bash
cd assets/images/gallery
for dir in concerts entreprise mariage portraits; do
  for img in "$dir"/*.jpg; do
    convert "$img" -resize "800x800>" -quality 82 -strip "${img%.jpg}.webp"
  done
done
```
Résultat : 17,4 Mo → 225 Ko (-99%)

### Justification des tailles choisies

| Taille | Référence CSS/JS | Raison |
|--------|------------------|--------|
| **1920px** (slider) | `style.css:2` — `body { max-width: 1920px; }` | Les images du carousel sont en `w-100`, elles ne dépassent jamais 1920px |
| **800px** (galerie) | `style.css:119` — `padding-bottom: 100%` (carré) + `scripts.js:4-9` — 3 colonnes (`xl: 3`) | Chaque colonne fait ~550px. 800px couvre les écrans Retina (2×). `object-fit: cover` rogne l'excédent |
