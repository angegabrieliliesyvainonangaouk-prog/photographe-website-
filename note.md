 La navigation dans la modale de la galerie entre images précédente et suivante ne fonctionne pas. (En gros quand tu veux avancer de l'image x à l'image y tu ne peux pas utiliser  les selecteur  car il  ne fonctionne pas j'ignore si ce sont des balises spécifiwque ou juste des css avec des liens ou c'tes fait avec du javascript  mais à arranger)

Lorsque l’on change de filtre pour afficher les images, on ne voit pas quelle catégorie est sélectionnée après avoir cliquer sur le lien des catégories . Normalement, la catégorie devrait avoir la couleur dorée en fond. Comme pour le filtre par défaut.   


En gros pour toutes les images on a mis aucune valeur dans l'attribut alt  qui permet aux personne handicapés et aux navigateurs d'avoir des infos   sur l'image car le navigateur cherche des informations aussi dans ces attributs 

Analyse avec ligthouse  mode mobile (restrictions plus fermes)
lors du chargement de la première requête  
Performance=50
Accessibilité=68
Best practices=100
seo=73

---

## Problème de contraste corrigé

**Détecté par :** WAVE
**Fichier :** `Nina-Carducci-Dev/assets/style.css`
**Ligne :** 104

**Problème :** Texte blanc (`#fff`) sur fond `#BEB45A` (jaune/olive clair) → ratio de contraste ~2:1, bien inférieur au minimum WCAG AA de 4.5:1 pour le texte normal.

**Impact :** Illisible pour les utilisateurs malvoyants, non conforme aux normes d'accessibilité.

**Correction appliquée :**
```css
/* Avant */
color: #fff;

/* Après */
color: #000;
```
Le noir (`#000`) sur `#BEB45A` donne un ratio ~10:1 → conforme WCAG AAA.

**Résultat Lighthouse accessibilité attendu :** 96 → devrait passer à 100 après cette correction et rafraîchissement du cache.