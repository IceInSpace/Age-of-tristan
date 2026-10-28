# 01 — Ères et progression

## Décidé

- **Nombre d'ères** : 12 ou plus.
- **Passage d'une ère à l'autre**, en plusieurs étapes successives :
  1. **Technologies clés** à débloquer. Exemples : travail du fer → âge du fer ; machine à vapeur et industrie → ère industrielle.
  2. **Bâtiments** à construire pour exploiter ces technologies.
  3. **Évolution des villes une par une** : la **capitale passe toujours en premier**, puis les autres villes suivent progressivement. On peut **payer en ressources pour accélérer**.
  4. **XP minimale** requise en plus, pour éviter une progression trop rapide. L'XP s'obtient **de plusieurs façons**.
- **Merveilles** : certaines ères en ont (exemple : un Colisée), pas toutes.
- **Espace** : apparaît à l'ère moderne (satellites, essais de fusées) et aboutit aux vaisseaux spatiaux à l'ère du futur.
- **Entre l'ère moderne et le futur**, plusieurs ères intermédiaires, dont une **révolution de l'IA**.
- **Espionnage** possible avant l'arrivée des satellites.

## Propositions (à valider)

### Liste des ères (15)

| # | Ère | Technologie clé (exemple) | Nouveauté de gameplay |
|---|-----|---------------------------|------------------------|
| 1 | Préhistoire | — | Chasse, cueillette, silex, deux tribus |
| 2 | Néolithique | Agriculture | Villages fixes, élevage, poterie |
| 3 | Âge du bronze | Métallurgie du cuivre et de l'étain | Premières villes, écriture, chars |
| 4 | Âge du fer | Travail du fer | Armées équipées en masse |
| 5 | Antiquité classique | Ingénierie civile | Routes pavées, aqueducs, merveilles |
| 6 | Moyen Âge | Féodalité, fortifications | Châteaux, sièges |
| 7 | Grandes découvertes | Navigation hauturière | **Exploration outre-mer** |
| 8 | Ère de la poudre | Poudre à canon | Armes à feu, artillerie |
| 9 | Révolution industrielle | Machine à vapeur | Usines, chemins de fer, chaînes de production longues |
| 10 | Ère électrique | Électricité | Réseau électrique, télégraphe |
| 11 | Ère atomique | Fission nucléaire | Uranium visible, aviation de masse |
| 12 | Ère moderne | Fusées | **Satellites, essais spatiaux**, espionnage orbital |
| 13 | Révolution de l'IA | Intelligence artificielle | Automatisation, drones, cyberespionnage |
| 14 | Ère spatiale | Propulsion avancée | Stations orbitales, bases lunaires, minage d'astéroïdes |
| 15 | Futur | Vaisseaux de ligne | **Flottes spatiales**, autres planètes |

### Sources d'XP

- Combat : unités ennemies éliminées, batailles gagnées.
- Exploration : nouvelles zones découvertes.
- Construction : bâtiments, merveilles.
- Recherche : technologies débloquées.
- Diplomatie : absorption d'un peuple neutre, traités signés.

### Formules d'équilibrage

XP requise pour atteindre l'ère $n$, croissance géométrique :

$$
XP_{\text{req}}(n) = XP_0 \cdot g^{\,n-1}
$$

avec $XP_0$ l'XP requise pour la première transition et $g$ le facteur de croissance (par exemple $g \in [1{,}3 \,;\, 1{,}6]$).

Durée d'évolution d'une ville vers l'ère suivante, réduite par un paiement $R$ :

$$
t_{\text{évol}} = \frac{t_0 \cdot \left(1 + \alpha \, P_{\text{ville}}\right)}{1 + k \, R}
$$

avec $t_0$ une durée de base, $P_{\text{ville}}$ la population (une grande ville est plus longue à transformer), $\alpha$ un coefficient de taille et $k$ l'efficacité du paiement.

## Questions ouvertes

- Valider, modifier ou fusionner la liste des 15 ères.
- Les villes non encore passées à la nouvelle ère peuvent-elles produire des unités de la nouvelle ère ?
- Une ville en retard d'ère subit-elle des malus (stabilité, production) ?
- Peut-on **régresser** d'ère (catastrophe, guerre, effondrement) ?
- Toutes les factions suivent-elles le même arbre, ou chacune a-t-elle des variantes (unités ou merveilles uniques) ?
