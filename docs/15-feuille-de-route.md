# 15 — Feuille de route et version minimale

## Principe

Le jeu décrit dans ce cahier des charges réunit des systèmes que l'on trouve habituellement dans plusieurs jeux distincts (gestion, stratégie en temps réel, grande stratégie). Il est donc construit **par couches** : chaque couche doit donner un **jeu jouable et complet en soi**, même petit.

## Propositions (à valider)

### Couche 1 — Version minimale : « La tribu »

Objectif : une carte, une ville, une économie qui tourne.

- Petite carte hexagonale générée procéduralement (3 à 4 types de terrain), en **3D avec des formes simples** (prototype « gris »).
- Une ville (la capitale) à l'ère préhistorique.
- 3 ressources : nourriture, bois, silex.
- 3 à 4 bâtiments : hutte, cueillette, chasse, taille de silex.
- Population agrégée qui grandit et consomme.
- Temps réel avec pause.
- Pas encore de combat ni d'IA.

### Couche 2 — « Le néolithique »

- Deuxième ère et premier passage d'ère complet (technologie clé + bâtiment + XP).
- Petit arbre technologique.
- Exploration et brouillard de guerre.
- Fondation d'une deuxième ville.

### Couche 3 — « La guerre des tribus »

- Unités (3 types, système de contres).
- Fronts avec ordres et résolution automatique dans la durée (pas de bataille tactique en version 1).
- Une IA rivale simple.
- Une condition de victoire : domination.

### Couche 4 — « Les premiers empires »

- Âge du bronze, âge du fer, Antiquité.
- Chaînes de production à plusieurs étapes.
- Peuples neutres et absorption.
- Diplomatie de base.
- Merveilles.

### Couches suivantes de l'acte I (ordre à définir)

- Espionnage.
- Naval et exploration outre-mer.
- Batailles tactiques.
- Ères industrielles : chaînes longues, ère du pétrole, pyrolyse, pollution.
- **Gestion par directives (niveau N2)** : à faire avant les ères modernes, car le nombre de villes devient alors difficile à gérer à la main.
- Ères atomique et moderne : dissuasion, missiles, défense multicouche.
- Diplomatie avancée.

### Couche « Acte II » — le système solaire

- Vue de système, planètes voisines générées.
- Gestion au niveau planète (N3) et zoom procédural.
- Fusion, terraformation.
- Poursuite de la guerre planétaire, conditions d'unification et de domination.

### Couche « Acte III » — l'hyperespace

- Carte galactique en graphe, routes hyperspatiales.
- Modules de colonisation, quartiers planétaires.
- Nouvel arbre technologique, nouvel ennemi.
- Mégastructures.

### Hors couches

- Éditeur de carte.
- Multijoueur.

### Ordre de grandeur

L'acte I à lui seul (14 ères) représente déjà un jeu de stratégie complet. Les actes II et III sont presque deux jeux supplémentaires, avec leurs propres vues, leur simulation et leur arbre technologique. Il est donc conseillé de **concevoir l'architecture pour les trois actes** (simulation à plusieurs niveaux, données séparées du code), mais de **ne développer l'acte II qu'une fois l'acte I jouable de bout en bout**.

## Questions ouvertes

- Valider le contenu de la couche 1.
- Quelle couche viendrait juste après la 4 : naval ou espionnage ?
- Fixer un critère de « fini » pour chaque couche (par exemple : une partie de 20 minutes jouable sans bug bloquant).
