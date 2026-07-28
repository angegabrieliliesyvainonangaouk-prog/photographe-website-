# WAVE vs Lighthouse - Différences

## Lighthouse (Google)

- Outil intégré à Chrome DevTools
- Fournit un **score global** (0-100) par catégorie
- Teste les règles techniques de base :
  - Balises `alt` sur les images
  - Labels associés aux champs de formulaire
  - Hiérarchie de titres (h1-h6)
  - Attributs ARIA présents
  - Meta tags (description, viewport, charset)
  - Langage déclaré (`<html lang="fr">`)
- Exécution rapide (quelques secondes)
- Ne montre **pas** les détails visuels des erreurs
- Utile pour un audit rapide et un score à mettre sur un CV/portfolio

---

## WAVE (WebAIM)

- Extension navigateur (Chrome/Firefox) ou outil en ligne
- Pas de score global — affiche un **compteur d'erreurs et avertissements**
- Détecte des problèmes que Lighthouse **ne voit pas** :
  - **Contraste insuffisant** des couleurs (texte trop clair sur fond clair)
  - **Erreurs ARIA** plus subtiles (rôles incorrects, propriétés manquantes)
  - **Contenu visible uniquement** par les lecteurs d'écran
  - **Ordre de lecture** (tab order) incorrect
  - **Texte alternatif non nécessaire** sur images décoratives
  - **Éléments manquants** pour les utilisateurs de clavier
- Affiche les erreurs **directement sur la page** avec des icônes colorées :
  - 🔴 Rouge = Erreur
  - 🟡 Orange = Avertissement
  - 🟢 Vert = Élément correct
  - 🔵 Bleu = Élément ARIA / structurel
- Utile pour un **audit approfondi** de l'accessibilité

---

## Résumé

| Critère | Lighthouse | WAVE |
|---------|-----------|------|
| Score global | ✅ Oui | ❌ Non |
| Vitesse | ✅ Très rapide | 🟡 Plus lent |
| Contraste couleurs | 🟡 Basique | ✅ Détaillé |
| Erreurs ARIA | 🟡 Basique | ✅ Avancé |
| Affichage visuel sur page | ❌ Non | ✅ Oui |
| Gratuit | ✅ Intégré au navigateur | ✅ Extension gratuite |
| Utilisé par | Google (SEO + perf) | WebAIM (accessibilité) |

---

## Recommandation

Utiliser **les deux** :
1. **Lighthouse** pour un audit rapide et un score mesurable
2. **WAVE** pour identifier et corriger les problèmes d'accessibilité restants
