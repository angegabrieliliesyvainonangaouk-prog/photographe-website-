# Audit SEO - Nina Carducci Photographe

## Historique des modifications

### Session 1 - Balises alt des images (2024)
**Statut :** ✅ Corrigé

16 images corrigées avec des attributs `alt` descriptifs :

| Image | Ancien alt | Nouveau alt |
|-------|-----------|-------------|
| Slider 1 (ryoji-iwata) | `alt="..."` | `alt="Photographe en action lors d'un événement"` |
| Slider 2 (nicholas-green) | `alt="..."` | `alt="Séance photo professionnelle en lumière naturelle"` |
| Slider 3 (edward-cisneros) | `alt="..."` | `alt="Portrait capturé lors d'un shooting photo"` |
| Nina (à propos) | pas d'alt | `alt="Nina Carducci, photographe professionnelle"` |
| Instagram (nav) | `alt=""` | `alt="Instagram de Nina Carducci"` |
| Gallery - Concert 1 | pas d'alt | `alt="Photo de concert prise par Nina Carducci"` |
| Gallery - Entreprise 1 | pas d'alt | `alt="Portrait professionnel en entreprise"` |
| Gallery - Entreprise 2 | pas d'alt | `alt="Shooting photo corporate"` |
| Gallery - Mariage 1 | pas d'alt | `alt="Photo de mariage capturée par Nina Carducci"` |
| Gallery - Portrait 1 | pas d'alt | `alt="Portrait artistique en studio"` |
| Gallery - Mariage 2 | pas d'alt | `alt="Moments de bonheur lors d'un mariage"` |
| Gallery - Portrait 2 | pas d'alt | `alt="Portrait expressif en lumière naturelle"` |
| Gallery - Concert 2 | pas d'alt | `alt="Ambiance d'un concert en photographie"` |
| Gallery - Entreprise 3 | pas d'alt | `alt="Portrait d'entrepreneur professionnel"` |
| Camera (contact) | pas d'alt | `alt="Appareil photo professionnel"` |

### Session 2 - Accessibilité et sémantique HTML (2024)
**Statut :** ✅ Corrigé

#### 1. Labels formulaire liés aux champs
- `<label>` → `<label for="nom">`, `<label for="email">`, `<label for="message">`
- Permet aux technologies d'assistance de relier chaque label à son champ

#### 2. Wrapper `<main>` ajouté
- Le contenu principal est wrappé dans `<main>...</main>` (lignes 31-160)
- Permet aux lecteurs d'écran d'identifier la zone principale

#### 3. `<footer>` ajouté
- Ajout d'un `<footer>` avec copyright et lien Instagram (lignes 161-164)

#### 4. Attributs ARIA sur les sections
Chaque `<section>` a un attribut d'accessibilité :

| Section | Attribut ajouté |
|---------|----------------|
| `#header` (carousel) | `aria-label="Bannière principale"` |
| `#about` | `aria-labelledby="about-title"` |
| `#gallery` | `aria-labelledby="gallery-title"` |
| `#services` | `aria-labelledby="services-title"` |
| `.quote` (citation) | `aria-label="Citation"` |
| `#contact` | `aria-labelledby="contact-title"` |

#### 5. Hiérarchie de titres corrigée
- Les `<h4>` des prix dans les services ont été remplacés par des `<p class="service__price-title">`
- Évite un saut hiérarchique h2 → h4 (problème d'accessibilité)

#### 6. IDs ajoutés pour aria-labelledby
- `id="about-title"` sur le h2 "A propos de moi"
- `id="gallery-title"` sur le h2 "Portfolio"
- `id="services-title"` sur le h2 "Mes services"
- `id="contact-title"` sur le h3 "Une question ?"

---

## Éléments CORRIGÉS (résumé)

| Critère | Statut | Détail |
|---------|--------|--------|
| `<html lang="fr">` | ✅ | Présent depuis le début |
| `<title>` | ✅ | Présent depuis le début |
| `<meta name="description">` | ✅ | Présent depuis le début |
| Hiérarchie h2/h3 | ✅ | h4 supprimés, remplacés par des `<p>` |
| `alt` sur les images | ✅ | 16 images corrigées |
| HTML sémantique (main/footer) | ✅ | `<main>` et `<footer>` ajoutés |
| Labels formulaire | ✅ | Attributs `for` ajoutés |
| ARIA sur sections | ✅ | `aria-labelledby`/`aria-label` sur 6 sections |

---

## Éléments ENCORE MANQUANTS

### Haute priorité

| Manque | Ce qu'il faut | Priorité |
|--------|---------------|----------|
| Open Graph (`og:*`) | Balises pour preview Facebook/LinkedIn | Haute |
| Twitter Cards (`twitter:*`) | Balises pour preview Twitter/X | Haute |
| Schema.org (JSON-LD) | Données structurées `LocalBusiness` / `Photographer` | Haute |
| `robots.txt` | Fichier pour guider les crawlers | Haute |
| `sitemap.xml` | Fichier pour indexation | Haute |
| `<link rel="canonical">` | Éviter le contenu dupliqué | Haute |

### Moyenne priorité

| Manque | Ce qu'il faut | Priorité |
|--------|---------------|----------|
| Favicon | `<link rel="icon" href="favicon.ico">` | Moyenne |
| Scripts async/defer | Ajouter `defer` aux scripts dans `<head>` | Moyenne |

---

## Résultats Lighthouse (après corrections)

| Catégorie | Score | Notes |
|-----------|-------|-------|
| SEO | 100 | ✅ |
| Accessibilité | 88 → à retester | Les corrections devraient améliorer le score |
| Performance | À tester | Scripts bloquants dans `<head>` |
| Best Practices | À tester | — |

---

## Prochaines étapes recommandées

1. **Ajouter les balises Open Graph** pour les réseaux sociaux
2. **Créer `robots.txt`** et `sitemap.xml` pour le référencement
3. **Ajouter les données structurées JSON-LD** (LocalBusiness + Photographer)
4. **Ajouter un favicon** pour l'icône de navigation
5. **Ajouter `defer` aux balises `<script>`** pour améliorer les performances
6. **Tester avec WAVE** (extension navigateur) pour valider l'accessibilité
7. **Relancer Lighthouse** pour vérifier l'amélioration du score accessibilité
