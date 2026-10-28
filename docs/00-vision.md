# 00 — Vision et cadre

## Décidé

- **Genre** : stratégie globale en **temps réel pausable**, inspirée d'*Age of War* pour la progression par ères, enrichie de gestion (villes, ressources, bâtiments), d'exploration, de diplomatie et d'espionnage.
- **Monde** : planète **fictive** générée (pas la Terre).
- **Point de départ** : préhistoire, guerre entre deux tribus sur un territoire très petit. L'espace jouable s'agrandit avec l'exploration et la conquête.
- **Expansion par paliers** : terre ferme → outre-mer (navigation) → espace (satellites, fusées, puis vaisseaux).
- **Structure spatiale** : des **fronts** de bataille et un **arrière** où l'on gère bâtiments, ressources et formation des unités. Les unités sont envoyées vers des points de la carte.
- **Vue** : isométrique (2.5D).
- **Adversaires** : une ou plusieurs IA, plus des peuples neutres absorbables. Multijoueur éventuel, plus tard.
- **Fin de partie** : plusieurs conditions de victoire, choisies au lancement de la partie.
- **Plateforme** : PC envisagé, non définitif.
- **Graphismes** : générés par IA, outils à définir.
- **Objectif du projet** : un jeu pour soi.

## Contraintes du projet

- Auteur débutant en programmation.
- Temps de développement irrégulier (alternance, cours).
- Conséquence : développement **par couches jouables** (voir [chapitre 12](12-feuille-de-route.md)).

## Propositions (à valider)

- **Phrase de pitch** : « Menez votre tribu du silex aux flottes interplanétaires, front après front, ville après ville. »
- **Piliers de conception**, pour arbitrer les futures décisions :
  1. **Progression visible** : chaque ère change l'apparence des villes, des unités et de la carte.
  2. **Fronts lisibles** : le joueur comprend d'un coup d'œil où ça se bat et qui gagne.
  3. **Économie de flux** : la production est pensée comme des procédés (entrées → transformation → sorties).
  4. **Profondeur optionnelle** : tout peut être automatisé (combat auto, évolution auto), le contrôle fin reste possible.

## Questions ouvertes

- Titre définitif du jeu ?
- Durée visée d'une partie complète (de la préhistoire au futur) : quelques heures, ou une campagne sur plusieurs sessions ?
- Peut-on commencer une partie à une ère avancée (comme dans *Civilization*) ?
- Ton général : sérieux, ou une touche d'humour comme dans *Age of War* ?
