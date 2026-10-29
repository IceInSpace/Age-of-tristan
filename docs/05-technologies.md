# 05 — Technologies et recherche

## Décidé

- La recherche fait partie du passage d'ère : certaines **technologies clés** sont indispensables pour changer d'ère (voir [chapitre 01](01-eres.md)).
- Exemples de technologies clés : travail du fer, machine à vapeur, industrie, technologies spatiales.
- Le **vol de technologie** est possible par espionnage, et l'**échange de technologies** par diplomatie.
- Technologies demandées explicitement : **missiles ICBM**, **défense avancée** (radars, missiles, satellites), **fusion nucléaire**, **pyrolyse**, **exploitation pétrolière**, **clonage**, **robotique**, **terraformation**, **hyperpropulsion**.
- **Nouvel arbre technologique** à l'entrée dans l'ère hyperspatiale.
- **Branche logistique** : débloque progressivement les réglages fins des stocks (réserve en %, villes-entrepôts, réglages par ressource), améliore les automatismes et réduit les pertes en transport. Détail au [chapitre 04](04-economie.md).

## Propositions (à valider)

### Deux arbres distincts

| Arbre | Actes | Branches proposées |
|-------|-------|--------------------|
| **Arbre planétaire** | I et II | Militaire, économie, logistique, sciences, culture, exploration |
| **Arbre stellaire** | III | Propulsion et navigation hyperspatiale, colonisation et terraformation, biologie (clonage, adaptation), robotique et IA, armement de flotte, mégastructures |

L'arbre planétaire n'est plus affiché à l'acte III : toutes ses technologies sont considérées comme acquises une fois l'hyperespace atteint.

### Exemples de technologies clés par ère (acte I et II, ères 9 à 16)

| Ère | Technologies clés |
|-----|-------------------|
| Révolution industrielle | Machine à vapeur, métallurgie au coke |
| Ère électrique | Électricité, télégraphe |
| Ère du pétrole | Moteur à explosion, raffinage, forage offshore |
| Ère atomique | Fission, enrichissement de l'uranium |
| Ère moderne | Fusées, radar, électronique, satellites |
| Révolution de l'IA | Réseaux de neurones, robotique autonome, pyrolyse des plastiques |
| Ère spatiale | Lanceurs réutilisables, habitats orbitaux |
| Ère de la fusion | Confinement magnétique, propulsion à fusion |

### Structure de l'arbre

- Un **arbre technologique** par ère, avec des branches : militaire, économie, sciences, culture, exploration.
- Chaque ère possède **1 à 3 technologies clés** (obligatoires pour passer à l'ère suivante) et des technologies optionnelles.
- Une technologie peut :
  - débloquer un bâtiment, une unité, une ressource visible ou une recette ;
  - améliorer un rendement (exemple : $+10\,\%$ sur l'agriculture) ;
  - débloquer une capacité (naviguer en haute mer, mettre un satellite en orbite).

### Coût de recherche

Coût en points de science d'une technologie de l'ère $n$, au rang $k$ dans l'ère :

$$
C(n, k) = C_0 \cdot g_s^{\,n-1} \cdot \left(1 + 0{,}2\,k\right)
$$

Durée de recherche, avec $\dot{\Sigma}$ le débit de science de la civilisation :

$$
t_{\text{recherche}} = \frac{C(n,k)}{\dot{\Sigma}}
$$

## Questions ouvertes

- Une recherche à la fois, ou plusieurs en parallèle ?
- La science est-elle une ressource produite par des bâtiments, ou générée par la population ?
- Y a-t-il des technologies exclusives (choisir l'une bloque l'autre) ?
- Peut-on découvrir des technologies par l'exploration (ruines, artefacts) ?
