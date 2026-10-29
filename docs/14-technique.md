# 14 — Choix techniques

## Décidé

- Plateforme envisagée : **PC** (non définitif).
- **Docker écarté** pour faire tourner le jeu : il est conçu pour isoler des applications serveur, pas pour afficher un jeu avec accélération graphique. Il pourrait servir plus tard pour un serveur multijoueur.
- **Style visé en 3D stylisée** (inspiration *Humankind*) : il faudra des **modèles 3D**, faits sous **Blender** ou avec des générateurs de modèles 3D par IA. Cela remplace la décision initiale d'une 2.5D en sprites.
- **Prototype d'abord** : une version jouable avec des formes simples pour valider la logique, puis l'habillage graphique.
- **Graphismes** générés par IA, outils à définir.

## Options comparées

### Moteur de jeu

| Critère | Godot 4 | Unity 6 | Unreal Engine 5 | GameMaker | Bevy | Python + Pygame |
|---------|---------|---------|-----------------|-----------|------|-----------------|
| Coût et licence | Gratuit, open source (MIT), sans redevance | Gratuit (Personal) jusqu'à $200\,000$ USD de revenus et financements annuels ; Pro à $2\,200$ USD par poste et par an au-delà | Gratuit ; redevance de $5\ \%$ au-delà de $1$ million USD de revenus bruts par jeu | Gratuit pour un usage non commercial ; licence unique pour le commercial | Gratuit, open source | Gratuit, open source |
| Langage | GDScript (proche de Python), C# possible | C# | C++ et Blueprints (programmation visuelle) | GML (langage propre) | Rust | Python |
| Point fort | Léger, 2D et 2.5D très bien gérés, hexagones possibles via les TileMaps | Énorme écosystème, beaucoup de tutoriels et de ressources | Rendu 3D de très haut niveau, idéal pour des planètes et des vues spectaculaires | Très simple pour la 2D | Architecture ECS performante pour des milliers d'entités | Langage déjà un peu connu |
| Point faible | Écosystème plus petit que Unity ; 3D moins poussée | Plus lourd, historique de changements de licence | Très lourd et complexe pour un débutant ; surdimensionné pour de la 2.5D | Peu adapté à un jeu de grande stratégie | Rust est difficile pour un débutant ; pas d'éditeur visuel complet | Tout est à construire ; performances limitées pour une grosse simulation |
| Adapté au projet | Très bien pour l'acte I ; 3D possible plus tard | Bien | Surtout si l'on vise une 3D ambitieuse | Faible | Bien techniquement, difficile à apprendre | Prototype seulement |

Sources : [licence Unreal Engine](https://www.unrealengine.com/en-US/license) ; [Unity, annulation de la Runtime Fee, 12 septembre 2024](https://unity.com/blog/unity-is-canceling-the-runtime-fee) ; [GameFromScratch, tarifs GameMaker, novembre 2023](https://gamefromscratch.com/gamemaker-announces-major-pricing-changes/). La branche stable de Godot en 2026 est la 4.6. Les licences changent régulièrement : à revérifier au moment du choix.

**Statut** : choix du moteur **reporté**, à faire après avoir revu les rendus (Godot : cartes isométriques et hexagonales, kit de carte stratégique hexagonale pour Godot 4.6, terrain 3D avec Terrain3D ; Unity : *Humankind*, démo de terrain HDRP).

**Mixer plusieurs moteurs** : un même jeu ne peut pas en pratique tourner sur deux moteurs ; changer de moteur oblige à réécrire l'affichage et une grande partie du code (cas de *Slay the Spire 2*, passé de Unity à Godot en cours de développement, [Game Developer](https://gamedeveloper.com/business/slay-the-spire-devs-followed-through-on-abandoning-unity)). Pour garder la porte ouverte : simulation séparée de l'affichage, données en fichiers, et simulation en C# (commun à Godot et Unity).

**À propos de Unreal Engine 5** : son principal atout, le rendu 3D réaliste (éclairage dynamique, géométrie très détaillée), sert peu à une carte stratégique stylisée comme celle de *Humankind*. En revanche, il deviendrait intéressant si les vues planétaires et spatiales des actes II et III devaient être en vraie 3D. Le coût d'entrée est élevé : C++ ou Blueprints, éditeur lourd, beaucoup de concepts à apprendre pour un débutant.

### Outils à installer (si Godot est retenu)

- **Godot 4** : moteur et éditeur.
- **VS Code** + extension Godot (facultatif, l'éditeur de Godot suffit pour débuter).
- **Git** + **GitHub** : versionnement et sauvegarde.
- **Krita** ou **Aseprite** : retouche des sprites générés.

### Points d'architecture à anticiper

- **Données séparées du code** : ères, unités, bâtiments, recettes et technologies décrits dans des fichiers de données (JSON ou ressources Godot). L'équilibrage se fait alors sans toucher au code, et le cahier des charges peut alimenter directement ces fichiers.
- **Simulation séparée de l'affichage** : la logique (économie, combat) tourne indépendamment du rendu. C'est indispensable pour la pause, l'accélération du temps, la résolution automatique et un éventuel multijoueur.
- **Sauvegarde** : prévue dès le début, car l'état du jeu sera volumineux.
- **Simulation à plusieurs niveaux de détail** (voir [chapitre 10](10-echelles.md)) : la même interface de code (« produire pendant $\Delta t$ ») est implémentée à l'échelle du bâtiment, de la ville, de la planète et du système. Le jeu choisit le niveau selon l'acte et ce que le joueur regarde.
- **Rendu procédural déterministe** : la vue détaillée d'une ville ou d'une planète est regénérée à partir de son état et d'une graine, pas stockée.
- **Trois vues** à prévoir : carte planétaire en 3D stylisée (actes I et II), vue de système (acte II et III), carte galactique en graphe (acte III). C'est un argument de plus en faveur d'un moteur généraliste plutôt que d'un code écrit entièrement à la main.

### Prototype simple, puis rendu soigné

C'est une pratique courante : on développe d'abord un **prototype en formes simples** (« greybox » : hexagones colorés, cubes et cylindres pour les bâtiments et les unités) pour valider la logique et le plaisir de jeu, puis on remplace progressivement ces formes par les vrais modèles.

Deux conditions pour que ce passage ne coûte pas une réécriture :

1. **Faire le prototype directement en 3D**, avec des formes simples, dans le **moteur final**. Le remplacement d'une forme par un modèle devient alors un simple échange de fichier. Un prototype en 2D obligerait au contraire à refaire tout l'affichage.
2. **Séparer la logique de l'affichage** et mettre les données dans des fichiers (déjà prévu) : l'habillage graphique ne touche pas à la simulation.

Conséquence : le choix du moteur peut attendre la fin de la conception, mais **il doit être fait avant le premier prototype**, car le code du prototype est conservé.

```
Prototype « gris »            →   Habillage progressif           →   Rendu final
hexagones colorés,                modèles simples, textures,         style Humankind :
formes primitives, icônes         premier éclairage                  villes qui grandissent,
                                                                     carte « maquette »
```

### Graphismes générés par IA : difficultés connues

- **Cohérence de style** entre des centaines de sprites.
- **Cohérence entre modèles 3D** (échelle, palette, niveau de détail) ; les générateurs 3D par IA produisent souvent des modèles trop détaillés ou mal topologisés pour un jeu, à retoucher.
- **Animations** : une image générée est fixe ; il faut des planches de sprites (spritesheets) cohérentes.
- **Variantes par ère** d'un même bâtiment.
- **Inspiration *Warhammer 40 000*** pour le futur : s'inspirer de l'ambiance (gothique industriel, mégastructures) sans reprendre noms, symboles ou designs protégés de la licence.

## Questions ouvertes

- Choix du moteur.
- Outil de génération d'images (à étudier : licences d'usage, cohérence, coût).
- Langue de l'interface et du code (français, anglais ?).
- Résolution d'écran cible.
