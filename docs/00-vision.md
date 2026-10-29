# 00 — Vision et cadre

## Décidé

- **Genre** : stratégie globale en **temps réel pausable**. La progression par ères vient d'*Age of War* ; s'y ajoutent la gestion (villes, ressources, bâtiments), l'exploration, la diplomatie et l'espionnage.
- **Monde** : planète **fictive** générée (pas la Terre).
- **Point de départ** : la préhistoire, avec une guerre entre deux tribus sur un territoire très petit. L'espace jouable s'agrandit avec l'exploration et la conquête.
- **Expansion par paliers** : terre ferme → outre-mer (navigation) → système solaire → autres systèmes stellaires (hyperespace).
- **Structure spatiale** : des **fronts** de bataille et un **arrière** où l'on gère bâtiments, ressources et formation des unités. Les unités sont envoyées vers des points de la carte.
- **Vue** : isométrique (2.5D) à l'échelle planétaire.
- **Changement d'échelle** : la gestion est d'abord manuelle et détaillée, puis plus large et automatisée à mesure que l'empire grandit (voir [chapitre 10](10-echelles.md)).
- **Inspirations** :
  - guerres et technologies **actuelles** pour les ères modernes ;
  - *Warhammer 40 000* pour le futur (villes et habitations totalement intégrées, mégastructures) ;
  - *Stellaris* et *Dyson Sphere Program* (sans la construction des lignes de production) pour l'ère hyperspatiale.
- **Adversaires** : une ou plusieurs IA, plus des peuples neutres absorbables. Multijoueur éventuel, plus tard.
- **Fin de partie** : plusieurs conditions de victoire, choisies au lancement de la partie.
- **Plateforme** : PC envisagé, non définitif.
- **Graphismes** : générés par IA, outils à définir.
- **Objectif du projet** : un jeu pour soi.

### Orientations de conception

Issues du questionnaire qui a suivi la [recherche historique et prospective](recherche/technologies-et-armes-par-ere.md) :

- **Réalisme de l'acte I** : **inspiré et simplifié**. On garde l'esprit de chaque ère et les ordres de grandeur des sources, avec des valeurs arrondies pour la jouabilité.
- **Actes II et III** : **space opera** assumé (warp, énergie exotique, ambiance *Warhammer*). La physique réelle sert de point de départ, pas de limite.
- **Mécaniques retenues** : **intrant critique** (chaque unité ou bâtiment dépend d'une ressource clé dont la pénurie le bloque) et **guerre des stocks** (munitions, carburant, intercepteurs limités : la logistique décide des guerres). Voir [chapitre 04](04-economie.md).
- **Thèmes durs inclus** : frappes nucléaires, armes chimiques, bombardement de civils, esclavage et colonisation. Ils sont représentés avec leurs conséquences (voir [chapitre 08](08-guerre-moderne.md) et [chapitre 13](13-diplomatie-ia.md)).
- **Toutes les périodes comptent** : Antiquité et Moyen Âge, poudre et industrie, guerres mondiales et époque moderne, spatial et futur. Aucune n'est à sacrifier.
- **À éviter absolument** :
  - la **micro-gestion lourde** ;
  - une **fin de partie molle** (effet boule de neige) ;
  - l'**aléatoire punitif** qui ruine une partie ;
  - des **unités obsolètes** qui rendent une ère d'avance synonyme de victoire automatique.
- **Contre l'effet boule de neige** : **crises de fin** et **coalitions d'IA**, qui ajoutent de la difficulté mais doivent rester **surmontables**, sinon on n'atteindrait jamais les dernières ères. Pas de malus automatique de taille.

## Structure en trois actes

| Acte | Échelle | Ères | Unité de gestion | Adversaire principal |
|------|---------|------|------------------|----------------------|
| **I — Planétaire** | Une planète | Préhistoire → révolution de l'IA | Ville et quartier | Tribus, puis nations rivales de la planète natale |
| **II — Système solaire** | Planète natale + lunes et planètes voisines | Ère spatiale → ère de la fusion | Région, puis planète | Les mêmes rivaux : la guerre planétaire peut continuer |
| **III — Hyperspatial** | Plusieurs systèmes stellaires | Ère hyperspatiale → ère impériale | Planète et système | Puissance avide d'énergie ou autres espèces |

- **Passage de l'acte I à II** : progressif, à partir des satellites et des fusées.
- **Passage de l'acte II à III** : la guerre sur la planète natale doit être gagnée, par **unification** ou **domination**. Tant que l'on reste dans le système solaire, cette guerre peut continuer.
- **Entrée dans l'acte III** : changement d'échelle, **nouvel ennemi**, **nouvel arbre technologique**.

## Contraintes du projet

- Auteur débutant en programmation.
- Temps de développement irrégulier (alternance, cours).
- Conséquence : développement **par couches jouables** (voir [chapitre 15](15-feuille-de-route.md)).

## Propositions (à valider)

- **Phrase de pitch** : « Menez votre tribu du silex aux flottes interstellaires, front après front, ville après ville, monde après monde. »
- **Piliers de conception**, pour arbitrer les futures décisions :
  1. **Progression visible** : chaque ère change l'apparence des villes, des unités et de la carte.
  2. **Fronts lisibles** : le joueur comprend d'un coup d'œil où l'on se bat et qui gagne.
  3. **Économie de flux** : la production est pensée comme des procédés (entrées → transformation → sorties).
  4. **Profondeur optionnelle** : tout peut être automatisé (combat automatique, évolution automatique), mais le contrôle fin reste possible.
  5. **Zoom sans perte** : on peut toujours redescendre voir une ville ou une planète en détail, même quand on la gère de loin.

## Questions ouvertes

- **Titre** : « Age of Tristan » (nom du dépôt), ou un autre ?
- **Empire** : *tranché*. Une fois le système solaire conquis, l'humanité est unifiée sous un empire au nom choisi par le joueur, avec des votes politiques. Le nouvel ennemi est une puissance avide d'énergie ou d'autres espèces (voir [chapitre 11](11-hyperspatial.md)).
- Durée visée d'une partie complète : quelques heures, ou une campagne sur plusieurs sessions ?
- Peut-on commencer une partie directement à l'acte II ou III ?
- Ton général : sérieux, ou une touche d'humour comme dans *Age of War* ?
