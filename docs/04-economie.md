# 04 — Économie, ressources et production

## Décidé

- **Ressources évolutives par ère** (silex, puis bronze, charbon, pétrole, uranium…).
- **Chaînes de production** : des matières premières transformées en produits.
- **Stock global** : toutes les ressources sont partagées instantanément entre les villes.
- **Ressources visibles sur la carte**, découvertes seulement quand leur existence est connue (voir [chapitre 02](02-carte-exploration.md)).
- **Ère du pétrole** avec exploitation pétrolière.
- **Pyrolyse** pour « fabriquer » du pétrole.
- **Fusion nucléaire** comme source d'énergie avancée.
- **Pollution** : mécanisme de jeu, visible sur la carte.
- **Changement d'échelle** : aux actes II et III, l'économie est simulée de façon plus large et moins détaillée, par planète (voir [chapitre 10](10-echelles.md)). Pas de construction manuelle de lignes de production comme dans *Dyson Sphere Program*.

## Propositions (à valider)

### Familles de ressources

| Famille | Exemples | Apparition |
|---------|----------|------------|
| Vivres | Gibier, baies, céréales, bétail, poisson | Préhistoire → néolithique |
| Matériaux | Bois, pierre, argile | Préhistoire |
| Minerais | Silex, cuivre, étain, fer, charbon | Préhistoire → âge du fer |
| Énergie | Charbon, pétrole, gaz, électricité, uranium, deutérium | Industriel → fusion |
| Produits | Outils, armes, tissus, acier, carburants, plastiques, électronique | Selon l'ère |
| Avancés | Silicium, terres rares, lithium, hélium-3, exotiques | Moderne → impérial |
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

### Ère du pétrole : exploitation et raffinage

```
Puits terrestre ─────┐
                     ├──► Brut ──► Raffinerie ──┬──► Essence ──► Véhicules, aviation
Plateforme offshore ─┘                          ├──► Gazole ──► Blindés, navires, engins
                                                ├──► Fioul lourd ──► Centrales, marine
                                                └──► Naphta ──► Pétrochimie ──► Plastiques, explosifs, engrais
```

**Épuisement des gisements fossiles** : la production d'un gisement pourrait suivre une courbe de Hubbert. Avec $Q(t)$ la quantité cumulée extraite et $Q_\infty$ la réserve récupérable totale :

$$
Q(t) = \frac{Q_\infty}{1 + e^{-b\,(t - t_m)}}
\qquad
\dot{Q}(t) = b\,Q(t)\left(1 - \frac{Q(t)}{Q_\infty}\right)
$$

La production passe par un pic à $t = t_m$, puis décline. C'est cette raréfaction qui rend la pyrolyse intéressante en jeu.

### Pyrolyse : « fabriquer » du pétrole

Trois voies de carburants de synthèse, réparties sur les ères :

| Ère | Procédé | Charge | Produit |
|-----|---------|--------|---------|
| Ère du pétrole | Liquéfaction du charbon (hydrogénation, Fischer-Tropsch) | Charbon | Carburant de synthèse, coûteux |
| Ère moderne | Pyrolyse rapide de biomasse + valorisation | Bois, résidus agricoles | Bio-huile, puis carburant |
| Révolution de l'IA | Pyrolyse des déchets plastiques | Plastiques usagés | Huile de pyrolyse, recyclage |

**Repères réels (pyrolyse de biomasse)**, d'après Bridgwater ([IEA Bioenergy, 2013](https://www.ieabioenergy.com/wp-content/uploads/2013/10/ExCo66-P2-Biomass-pyrolysis-Tony-Bridgwater.pdf)) :

| Mode | Conditions | Liquide | Charbon (char) | Gaz |
|------|-----------|---------|----------------|-----|
| Rapide | $\approx 500\ ^\circ\text{C}$, vapeurs $\approx 1\ \text{s}$ | $75\ \%$ | $12\ \%$ | $\approx 13\ \%$ (par différence) |
| Intermédiaire | $\approx 500\ ^\circ\text{C}$, $10$–$30\ \text{s}$ | $50\ \%$ (deux phases) | $25\ \%$ | — |
| Lente | $\approx 400\ ^\circ\text{C}$, longue | $35\ \%$ | $35\ \%$ | — |

Propriétés de la bio-huile de pyrolyse rapide (même source) : environ $25\ \%$ d'eau, $35$–$40\ \%$ d'oxygène en masse, $\text{PCS} \approx 17\ \text{MJ/kg}$, $\text{pH} \approx 2{,}5$. Elle doit être **valorisée** avant de servir de carburant :

- **hydrotraitement** : l'oxygène est rejeté sous forme d'eau, il faut de l'hydrogène sous pression ;
- **craquage sur zéolithes** : l'oxygène est rejeté sous forme de $\text{CO}_2$, sans hydrogène, mais avec régénération continue du catalyseur ;
- **gazéification puis Fischer-Tropsch** ou synthèse du méthanol.

**Repères réels (pyrolyse des plastiques)** : à $500\ ^\circ\text{C}$, des polyoléfines (PE et PP) donnent de $62$ à $76\ \%$ massique de liquide selon le grade ([Wu *et al.*, *Green Chemistry*, 2024](https://pubs.rsc.org/en/content/articlepdf/2024/gc/d4gc04029e)).

Recettes de jeu proposées, calées sur ces ordres de grandeur :

$$
100\,\text{Biomasse} \;\xrightarrow{\text{pyrolyse rapide}}\; 75\,\text{Bio-huile} + 12\,\text{Char} + 13\,\text{Gaz}
$$

$$
100\,\text{Bio-huile} + h\,\text{H}_2 \;\xrightarrow{\text{hydrotraitement}}\; y\,\text{Carburant} + \text{Eau}
$$

$$
100\,\text{Déchets plastiques} \;\xrightarrow{\text{pyrolyse}}\; 70\,\text{Huile} + 20\,\text{Gaz} + 10\,\text{Résidus}
$$

Les valeurs de $h$ et de $y$ restent à fixer. Le rendement final en carburant étant nettement plus faible que celui du raffinage du brut, la pyrolyse reste un **substitut**, pas une solution gratuite. La répartition $20/10$ entre gaz et résidus des plastiques est une valeur de jeu, pas une donnée de la source.

### Fusion nucléaire

- **Combustible** : deutérium (eau de mer) et tritium (produit à partir du lithium).
- **Rôle en jeu** : énergie quasi illimitée, qui rend possibles la terraformation, les arcologies et la propulsion interplanétaire.
- **Variante avancée** : fusion à l'hélium-3, ressource rare extraite de la Lune ou des géantes gazeuses, ce qui donne une raison économique d'aller dans l'espace.

### Pollution

Modèle de premier ordre par zone (région ou planète), avec $\Pi$ le niveau de pollution :

$$
\frac{d\Pi}{dt} = \sum_i e_i - k_{\text{abs}}\,\Pi - k_{\text{dépol}}\,D
$$

avec $e_i$ les émissions des bâtiments (usines, raffineries, centrales), $k_{\text{abs}}$ la capacité d'absorption naturelle (forêts, océans) et $D$ l'effort de dépollution (bâtiments de traitement, technologies vertes, terraformation).

Effets proposés : baisse de la croissance de population et de la stabilité, rendement agricole réduit, et au-delà d'un seuil, changement climatique de la zone.

## Questions ouvertes

- Capacité de stockage limitée (entrepôts) ou illimitée ?
- Une ressource obsolète (silex) disparaît-elle, ou reste-t-elle utilisable ?
- Existe-t-il une monnaie, ou uniquement des ressources physiques ?
- Commerce entre factions : troc, marché avec prix variables, ou les deux ?
- Les gisements fossiles s'épuisent-ils (courbe de Hubbert proposée ci-dessus) ? Et les autres ressources ?
- Raffinerie détaillée (plusieurs coupes : essence, gazole, fioul, naphta) ou simplifiée (brut → carburant) ?
