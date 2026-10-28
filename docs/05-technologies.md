# 05 — Technologies et recherche

## Décidé

- La recherche fait partie du passage d'ère : certaines **technologies clés** sont indispensables pour changer d'ère (voir [chapitre 01](01-eres.md)).
- Exemples de technologies clés : travail du fer, machine à vapeur, industrie, technologies spatiales.
- Le **vol de technologie** est possible par espionnage, et l'**échange de technologies** par diplomatie.

## Propositions (à valider)

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
