# 11 — Ère hyperspatiale et conquête stellaire (acte III)

## Décidé

- **Condition d'entrée** : système solaire conquis, et guerre sur la planète natale gagnée par **unification** ou **domination**.
- **Changement d'échelle** : on gère des **systèmes stellaires** et des **planètes** plutôt que des villes.
- **Nouvel ennemi** et **nouvel arbre technologique**.
- **Systèmes générés** avec leurs ressources ; **chaque planète a ses propres ressources**.
- **Modules** envoyés sur une planète pour **créer des villes automatiquement** et exploiter ses ressources.
- **Choix du type de quartier par planète** : garnison, clonage d'êtres humains, centre robotique, etc.
- **Routes spatiales** (dans un système) et **routes hyperspatiales** (entre systèmes).
- Inspirations : *Stellaris* (carte galactique, planètes spécialisées) et *Dyson Sphere Program* (logistique interstellaire et exploitation des ressources planétaires), **sans** la construction manuelle des lignes de production.
- **Zoom** sur une planète : routes, villes développées, pollution, terraformation.

## Propositions (à valider)

### Structure de la galaxie

```
Galaxie ──► Systèmes (nœuds) reliés par des routes hyperspatiales (arêtes)
   Système ──► Étoile + planètes + lunes + ceintures d'astéroïdes
      Planète ──► Taille, habitabilité, ressources, quartiers
```

- La galaxie est un **graphe** : les systèmes sont des nœuds, les routes hyperspatiales des arêtes. Les points de passage obligés (systèmes à une seule route) deviennent des positions stratégiques à fortifier.
- Le type d'étoile fixe l'énergie disponible (naine rouge faible, géante bleue forte) et les mégastructures possibles.

### Types de planètes

| Type | Habitabilité | Ressources typiques | Usage naturel |
|------|-------------|---------------------|---------------|
| Tellurique tempérée | Élevée | Équilibrées | Capitale de secteur, population |
| Océanique | Moyenne | Vivres, deutérium | Agriculture, énergie de fusion |
| Désertique | Faible | Minerais, silicium | Extraction, industrie |
| Glacée | Faible | Eau, volatils | Ravitaillement, terraformation d'autres mondes |
| Volcanique | Très faible | Métaux lourds, terres rares | Extraction robotisée |
| Géante gazeuse | Nulle | Hélium-3, hydrogène | Stations d'écopage orbitales |
| Ceinture d'astéroïdes | Nulle | Métaux, glace | Minage automatique |

### Quartiers planétaires

| Quartier | Production | Remarque |
|----------|-----------|----------|
| Résidentiel (arcologies, puis cité-ruche) | Population, main-d'œuvre | Base de tout développement |
| Agricole (hydroponie) | Vivres | Indépendant du sol sur les mondes hostiles |
| Extraction | Ressources de la planète | Rendement selon les gisements |
| Industriel (fonderies) | Produits transformés | Pollue fortement |
| Énergie (fusion, collecteurs stellaires) | Énergie | — |
| **Garnison** | Défense planétaire, troupes | Rend l'invasion coûteuse |
| **Clonage** | Légions de clones | Production rapide d'hommes |
| **Centre robotique** | Légions robotiques, ouvriers robots | Permet d'exploiter les mondes sans habitants |
| Recherche | Science | — |
| Chantier spatial | Vaisseaux | Nécessaire pour construire des flottes |
| Terraformation | Change le climat de la planète | Long et coûteux |

### Colonisation par modules

```
Sonde ──► révèle les ressources ──► Module (choisi) ──► Avant-poste ──► Ville automatique ──► Planète développée
```

Trois modules proposés :

- **Module d'extraction** : avant-poste robotisé, sans population, sur n'importe quelle planète.
- **Module de colonie** : population, nécessite une habitabilité minimale (sinon dômes et pénalités).
- **Module de forteresse** : garnison et défenses, pour tenir un point de passage.

### Habitabilité et terraformation

Habitabilité $H \in [0 \,;\, 1]$, produit de facteurs pour chaque paramètre $x_k$ (température, pression, eau, oxygène, gravité), chacun centré sur une valeur idéale $x_k^\star$ :

$$
H = \prod_k \exp\!\left(-\frac{\left(x_k - x_k^\star\right)^2}{2\,\sigma_k^2}\right)
$$

La terraformation rapproche chaque paramètre de sa cible avec une constante de temps $\tau_{\text{terra}}$, qui dépend de la taille de la planète et des technologies :

$$
\frac{dx_k}{dt} = \frac{x_k^{\text{cible}} - x_k}{\tau_{\text{terra}}}
$$

Seule la gravité n'est pas modifiable.

### Routes et logistique

- **Routes spatiales** (dans un système) : temps de trajet $t = d / v$, avec $v$ la vitesse sous-luminique des vaisseaux.
- **Routes hyperspatiales** (entre systèmes) : temps de trajet $t = t_{\text{saut}} + d_{\text{hyper}} / v_{\text{hyper}}$, avec $t_{\text{saut}}$ un temps fixe d'entrée et de sortie de l'hyperespace.
- **Logistique automatique**, comme les stations interstellaires de *Dyson Sphere Program* : le joueur ne gère pas les transports.
- **Compatibilité avec le stock global** : le stock reste global **à l'intérieur d'un réseau connexe**. Un système coupé du réseau (blocus, route détruite) ne partage plus ses ressources. Les routes gardent ainsi un rôle stratégique sans ajouter de micro-gestion.

### Invasion planétaire

1. **Supériorité orbitale** : bataille de flotte (voir [chapitre 09](09-naval-spatial.md)).
2. **Bombardement orbital** : affaiblit garnisons et défenses, mais augmente la pollution et détruit des quartiers.
3. **Débarquement** : légions contre garnison, en résolution automatique ou en bataille tactique (voir [chapitre 07](07-batailles.md)).

### Mégastructures (merveilles de l'acte III)

- **Essaim ou sphère de Dyson** : capte une part de l'énergie d'une étoile.
- **Porte hyperspatiale** : crée une route entre deux systèmes non reliés.
- **Monde-forteresse** : une planète entière transformée en forteresse.
- **Cité-ruche** : une planète entièrement urbanisée.

## Questions ouvertes

- **Nouvel ennemi** : « l'Empire de la Terre » est-il **l'adversaire** (la « vraie » Terre découverte dans l'hyperespace), ou **le nom de l'empire du joueur** ? Voir [chapitre 00](00-vision.md).
- Y a-t-il **plusieurs** puissances dans la galaxie (empires, extraterrestres, pirates), ou un seul grand ennemi ?
- Taille de la galaxie : combien de systèmes (quelques dizaines, quelques centaines) ?
- Combien de types de quartiers par planète au maximum, selon sa taille ?
- Les rivaux vaincus sur la planète natale sont-ils intégrés (unification) avec des bonus différents de ceux d'une domination ?
- Condition de victoire finale de l'acte III ?
