# 04 — Économie, ressources et production

## Décidé

- **Ressources évolutives par ère** (silex, puis bronze, charbon, pétrole, uranium…).
- **Chaînes de production** : des matières premières transformées en produits.
- **Stock global** : toutes les ressources sont partagées instantanément entre les villes.
- **Ressources visibles sur la carte**, découvertes seulement quand leur existence est connue (voir [chapitre 02](02-carte-exploration.md)).

## Propositions (à valider)

### Familles de ressources

| Famille | Exemples | Apparition |
|---------|----------|------------|
| Vivres | Gibier, baies, céréales, bétail, poisson | Préhistoire → néolithique |
| Matériaux | Bois, pierre, argile | Préhistoire |
| Minerais | Silex, cuivre, étain, fer, charbon | Préhistoire → âge du fer |
| Énergie | Charbon, pétrole, électricité, uranium | Industriel → atomique |
| Produits | Outils, armes, tissus, acier, machines | Selon l'ère |
| Avancés | Silicium, terres rares, hélium-3, antimatière | Moderne → futur |
| Immatériels | Science, culture, XP, influence | Toutes les ères |

### Modèle de production en procédés

Chaque bâtiment de transformation est une **opération unitaire** définie par une recette :

$$
\sum_i a_i \, X_i \;\xrightarrow{\;\tau\;}\; \sum_j b_j \, Y_j
$$

avec $X_i$ les entrées, $Y_j$ les sorties, $a_i$ et $b_j$ les coefficients de la recette, $\tau$ la durée d'un cycle.

Exemple, haut fourneau de l'ère industrielle :

$$
2\,\text{Minerai de fer} + 1\,\text{Charbon} \;\xrightarrow{\;\tau = 10\,\text{s}\;}\; 1\,\text{Acier}
$$

Débit de sortie d'un bâtiment, limité par l'entrée la plus rare, la main-d'œuvre, le terrain et la stabilité :

$$
\dot{Y}_j = \frac{b_j}{\tau} \cdot \min\!\left(1,\; \min_i \frac{\dot{X}_i^{\text{dispo}}}{a_i / \tau},\; \frac{L}{L_{\text{req}}}\right) \cdot \left(1 + \beta_{\text{terrain}}\right) \cdot \varphi(S)
$$

avec $L$ la main-d'œuvre affectée, $L_{\text{req}}$ la main-d'œuvre nominale, $\beta_{\text{terrain}}$ le bonus ou malus de terrain et $\varphi(S) \in [0 \,;\, 1]$ un facteur de stabilité.

### Bilan global

Stock d'une ressource $X$ au cours du temps, comme un bilan matière :

$$
\frac{dM_X}{dt} = \sum_{\text{producteurs}} \dot{X}_{\text{prod}} - \sum_{\text{consommateurs}} \dot{X}_{\text{cons}}
$$

L'interface pourrait afficher ce bilan sous forme de **diagramme de Sankey** pour repérer les goulots d'étranglement.

### Exemple de chaîne complète (ère industrielle)

```
Mine de fer ──┐
              ├──► Haut fourneau ──► Acier ──► Usine d'armement ──► Fusils
Mine charbon ─┘                         └──► Atelier ferroviaire ──► Rails
```

## Questions ouvertes

- Capacité de stockage limitée (entrepôts) ou illimitée ?
- Une ressource obsolète (silex) disparaît-elle, ou reste-t-elle utilisable ?
- Existe-t-il une monnaie, ou uniquement des ressources physiques ?
- Commerce entre factions : troc, marché avec prix variables, ou les deux ?
- Pollution et déchets industriels : un mécanisme de jeu ?
