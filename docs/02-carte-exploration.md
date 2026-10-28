# 02 — Carte, terrain et exploration

## Décidé

- **Génération procédurale réglable** (taille, continents, climat, richesse…), **plus un éditeur** pour modifier la carte à la main.
- **Vue isométrique** (2.5D).
- **Terrain contraignant** : on ne peut pas tout construire partout. Le terrain donne des **bonus ou des malus**.
- **Routes** à construire entre villages, villes et mégalopoles.
- **Ressources visibles sur la carte**.
- **Toutes les ressources sont générées dès le début de la partie**, mais une ressource n'apparaît au joueur **qu'une fois son existence connue** (exemple : pas d'uranium visible avant l'ère atomique).
- **Exploration progressive** : le territoire de départ est minuscule, puis s'agrandit.
- **Paliers d'accès** : terre ferme → outre-mer (navigation) → espace.

## Propositions (à valider)

### Couches de visibilité

| État | Le joueur voit |
|------|----------------|
| Inconnu | Rien (zone noire) |
| Exploré | Relief, terrain, ressources connues, dernière position connue des villes |
| Observé | Tout en temps réel : unités, constructions, mouvements |

Une zone explorée redevient « explorée » (non observée) quand plus aucune unité, ville ou satellite ne la couvre.

### Types de terrain (première liste)

| Terrain | Déplacement | Construction | Effet |
|---------|-------------|--------------|-------|
| Plaine | Normal | Tout | Agriculture + |
| Forêt | Lent | Limitée | Bois +, défense + |
| Colline | Lent | Limitée | Mines +, défense ++ |
| Montagne | Très lent ou infranchissable | Mines seulement | Défense +++ |
| Marais | Très lent | Aucune avant l'ère industrielle | Maladies − |
| Désert | Lent | Limitée | Pétrole caché |
| Côte | Normal | Ports | Pêche +, commerce + |
| Rivière | Ralentit la traversée | Moulins, irrigation | Agriculture ++ |
| Océan | Navires seulement | Plateformes à l'ère moderne | — |

### Génération procédurale

Méthode classique proposée : un **bruit de Perlin ou Simplex** pour l'altitude $h(x,y)$ et l'humidité $w(x,y)$, puis attribution du biome selon des seuils. Le niveau de la mer $h_{\text{mer}}$ est un paramètre réglable : il fixe la proportion d'océan.

$$
\text{biome}(x,y) = f\big(h(x,y),\, w(x,y)\big)
$$

Les gisements sont placés selon le biome (pétrole en désert et offshore, charbon en colline…), avec une graine aléatoire $s$ qui rend la carte reproductible.

## Questions ouvertes

- Grille de cases (carrées ou hexagonales en isométrique), ou carte continue ?
- Taille de la planète : combien de « régions » ou de cases au total ?
- Les gisements s'épuisent-ils ?
- Y a-t-il des catastrophes naturelles (séismes, éruptions, inondations) ?
- Climat dynamique (saisons, changement climatique dû à l'industrie) ?
