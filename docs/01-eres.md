# 01 — Ères et progression

## Décidé

- **Nombre d'ères** : 12 ou plus, réparties en trois actes (voir [chapitre 00](00-vision.md)).
- **Passage d'une ère à l'autre**, en plusieurs étapes successives :
  1. **Technologies clés** à débloquer. Exemples : travail du fer → âge du fer ; machine à vapeur et industrie → ère industrielle.
  2. **Bâtiments** à construire pour exploiter ces technologies.
  3. **Évolution des villes une par une** : la **capitale passe toujours en premier**, puis les autres villes suivent progressivement. On peut **payer en ressources pour accélérer**.
  4. **XP minimale** requise en plus, pour éviter une progression trop rapide. L'XP s'obtient **de plusieurs façons**.
- **Merveilles** : certaines ères en ont (exemple : un Colisée), pas toutes.
- **Ère du pétrole** : une ère dédiée à l'exploitation pétrolière.
- **Espace** : apparaît à l'ère moderne (satellites, essais de fusées) et aboutit aux vaisseaux spatiaux.
- **Entre l'ère moderne et le futur**, plusieurs ères intermédiaires, dont une **révolution de l'IA**.
- **Fusion nucléaire** présente dans la progression.
- **Ère hyperspatiale** : débloquée une fois le système solaire conquis. Elle apporte un **changement d'échelle**, un **nouvel ennemi** et un **nouvel arbre technologique**.
- **Futur** inspiré de *Warhammer 40 000* : villes et habitations totalement intégrées.
- **Espionnage** possible avant l'arrivée des satellites.

## Propositions (à valider)

### Liste des ères (18)

#### Acte I — Planétaire

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
| 9 | Révolution industrielle | Machine à vapeur | Charbon, usines, chemins de fer, chaînes de production longues |
| 10 | Ère électrique | Électricité | Réseau électrique, télégraphe, radio |
| 11 | **Ère du pétrole** | Moteur à explosion, raffinage | Puits et plateformes, pétrochimie, blindés, aviation, carburants de synthèse |
| 12 | Ère atomique | Fission nucléaire | Uranium visible, centrales, **arme nucléaire et dissuasion** |
| 13 | Ère moderne | Fusées, électronique | **Satellites, radars, missiles, ICBM, défense antimissile** |
| 14 | Révolution de l'IA | Intelligence artificielle | Drones autonomes, guerre électronique, cyberespionnage, gestion automatisée |

#### Acte II — Système solaire

| # | Ère | Technologie clé (exemple) | Nouveauté de gameplay |
|---|-----|---------------------------|------------------------|
| 15 | Ère spatiale | Lanceurs lourds réutilisables | Stations orbitales, bases lunaires, minage d'astéroïdes, colonies dans le système |
| 16 | Ère de la fusion | **Fusion nucléaire** | Énergie abondante, propulsion interplanétaire, **terraformation**, arcologies |

#### Acte III — Hyperspatial

| # | Ère | Technologie clé (exemple) | Nouveauté de gameplay |
|---|-----|---------------------------|------------------------|
| 17 | Ère hyperspatiale | Hyperpropulsion | Conquête de systèmes, modules de colonisation, routes hyperspatiales |
| 18 | Ère impériale | Mégastructures | Cités-ruches, vaisseaux-cathédrales, sphères de Dyson |

> Repères réels pour l'ère de la fusion : le réacteur expérimental ITER vise un gain $Q \ge 10$, soit $500\ \text{MW}$ de puissance de fusion pour $50\ \text{MW}$ de chauffage, en impulsions de $400\ \text{s}$. Selon le calendrier publié en 2024, les opérations deutérium-tritium y débuteraient en 2039 ([ITER, 2024](https://iter.org/sites/default/files/media/2024-07/baseline_press_conference_summary_july-2024_b.pdf)). La fusion commerciale relève donc bien du « futur proche », ce qui justifie de la placer après la révolution de l'IA.

### Sources d'XP

- Combat : unités ennemies éliminées, batailles gagnées.
- Exploration : nouvelles zones, nouvelles planètes, nouveaux systèmes découverts.
- Construction : bâtiments, merveilles, mégastructures.
- Recherche : technologies débloquées.
- Diplomatie : absorption d'un peuple neutre, traités signés.

### Formules d'équilibrage

XP requise pour atteindre l'ère $n$, croissance géométrique :

$$
XP_{\text{req}}(n) = XP_0 \cdot g^{\,n-1}
$$

avec $XP_0$ l'XP requise pour la première transition et $g$ le facteur de croissance (par exemple $g \in [1{,}3 \,;\, 1{,}6]$). Avec 18 ères, l'écart entre la première et la dernière transition vaut $g^{17}$, soit environ $87$ pour $g = 1{,}3$ et environ $2{,}9 \times 10^{3}$ pour $g = 1{,}6$. Comme les sources d'XP grandissent aussi avec les ères, $g$ devra être calé en jeu.

Durée d'évolution d'une ville vers l'ère suivante, réduite par un paiement $R$ :

$$
t_{\text{évol}} = \frac{t_0 \cdot \left(1 + \alpha \, P_{\text{ville}}\right)}{1 + k \, R}
$$

avec $t_0$ une durée de base, $P_{\text{ville}}$ la population (une grande ville est plus longue à transformer), $\alpha$ un coefficient de taille et $k$ l'efficacité du paiement.

## Questions ouvertes

- Valider, modifier ou fusionner la liste des 18 ères.
- Dans l'acte III, le passage d'ère suit-il le même mécanisme (technologie + bâtiment + évolution des villes + XP), ou un mécanisme propre à l'échelle des systèmes ?
- Les villes non encore passées à la nouvelle ère peuvent-elles produire des unités de la nouvelle ère ?
- Une ville en retard d'ère subit-elle des malus (stabilité, production) ?
- Peut-on **régresser** d'ère (catastrophe, guerre nucléaire, effondrement) ?
- Toutes les factions suivent-elles le même arbre, ou chacune a-t-elle des variantes (unités ou merveilles uniques) ?
