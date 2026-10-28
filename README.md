# Age of Tristan — cahier des charges

Jeu de stratégie en temps réel pausable, inspiré d'*Age of War* et élargi vers la stratégie globale. Une civilisation part d'une tribu préhistorique sur un territoire minuscule, s'étend par l'exploration et la conquête, prend la mer, conquiert son système solaire, puis d'autres systèmes stellaires par l'hyperespace.

Le jeu est structuré en **trois actes**, chacun avec sa propre échelle de gestion :

| Acte | Échelle | Ères |
|------|---------|------|
| I — Planétaire | Villes et régions d'une planète | Préhistoire → révolution de l'IA |
| II — Système solaire | Planètes du système d'origine | Ère spatiale → ère de la fusion |
| III — Hyperspatial | Systèmes stellaires | Ère hyperspatiale → ère impériale |

Ce dépôt contient pour l'instant **uniquement le cahier des charges**. Le code viendra ensuite.

## Chapitres

| # | Chapitre | État |
|---|----------|------|
| 00 | [Vision et cadre](docs/00-vision.md) | Structure en 3 actes posée |
| 01 | [Ères et progression](docs/01-eres.md) | Mécanique décidée, liste de 18 ères à valider |
| 02 | [Carte, terrain et exploration](docs/02-carte-exploration.md) | Base posée |
| 03 | [Villes, quartiers et bâtiments](docs/03-villes-batiments.md) | Base posée |
| 04 | [Économie, ressources et production](docs/04-economie.md) | Pétrole, pyrolyse, fusion, pollution ajoutés |
| 05 | [Technologies et recherche](docs/05-technologies.md) | Deux arbres (planétaire, stellaire) |
| 06 | [Unités](docs/06-unites.md) | Base posée |
| 07 | [Batailles et fronts](docs/07-batailles.md) | Base posée |
| 08 | [Guerre moderne : missiles, dissuasion et défense](docs/08-guerre-moderne.md) | Nouveau |
| 09 | [Naval et spatial](docs/09-naval-spatial.md) | Base posée |
| 10 | [Changements d'échelle et gestion automatisée](docs/10-echelles.md) | Nouveau |
| 11 | [Ère hyperspatiale et conquête stellaire](docs/11-hyperspatial.md) | Nouveau |
| 12 | [Espionnage](docs/12-espionnage.md) | Base posée |
| 13 | [Diplomatie, IA et adversaires](docs/13-diplomatie-ia.md) | Unification et domination ajoutées |
| 14 | [Choix techniques](docs/14-technique.md) | Ouvert |
| 15 | [Feuille de route et version minimale](docs/15-feuille-de-route.md) | Proposition |
| — | [Sources](docs/sources.md) | Références des chiffres réels |

## Conventions de rédaction

Chaque chapitre est découpé en trois blocs, pour séparer clairement ce qui est tranché de ce qui ne l'est pas :

- **Décidé** : choix explicitement validés par l'auteur.
- **Propositions (à valider)** : pistes, valeurs et formules proposées, à accepter, modifier ou rejeter.
- **Questions ouvertes** : points à trancher.

Les formules sont écrites en LaTeX (`$...$` et `$$...$$`), rendu nativement par GitHub. Les chiffres tirés du monde réel sont sourcés dans le chapitre concerné et repris dans [Sources](docs/sources.md).
