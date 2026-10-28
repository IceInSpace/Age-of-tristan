# 14 — Choix techniques

## Décidé

- Plateforme envisagée : **PC** (non définitif).
- **Docker écarté** pour faire tourner le jeu : il est conçu pour isoler des applications serveur, pas pour afficher un jeu avec accélération graphique. Il pourrait servir plus tard pour un serveur multijoueur.
- **Pas de 3D** à modéliser : la vue isométrique (2.5D) repose sur des sprites 2D, Blender n'est donc pas nécessaire.
- **Graphismes** générés par IA, outils à définir.

## Options comparées

### Moteur de jeu

| Critère | Godot 4 | Unity | Web (JavaScript) |
|---------|---------|-------|------------------|
| Coût | Gratuit, open source (licence MIT) | Gratuit sous conditions de revenus | Gratuit |
| Langage | GDScript (proche de Python), C# possible | C# | JavaScript / TypeScript |
| Poids de l'éditeur | Léger | Lourd | Aucun éditeur |
| Isométrique | Pris en charge par les TileMaps | Pris en charge (Tilemap) | À coder soi-même ou via une bibliothèque |
| Courbe d'apprentissage | Douce | Plus raide | Moyenne, mais beaucoup à construire soi-même |
| Communauté et tutoriels | Large et en croissance | Très large | Très large, mais dispersée |
| Export PC | Windows, Linux, macOS | Windows, Linux, macOS | Navigateur, ou application via Electron |

> Les conditions de licence de Unity ont changé plusieurs fois ces dernières années : à vérifier sur le site officiel au moment du choix.

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
- **Trois vues** à prévoir : carte planétaire isométrique (actes I et II), vue de système (acte II et III), carte galactique en graphe (acte III). C'est un argument de plus en faveur d'un moteur généraliste plutôt que d'un code écrit entièrement à la main.

### Graphismes générés par IA : difficultés connues

- **Cohérence de style** entre des centaines de sprites.
- **Angle isométrique constant** pour toutes les images.
- **Animations** : une image générée est fixe ; il faut des planches de sprites (spritesheets) cohérentes.
- **Variantes par ère** d'un même bâtiment.
- **Inspiration *Warhammer 40 000*** pour le futur : s'inspirer de l'ambiance (gothique industriel, mégastructures) sans reprendre noms, symboles ou designs protégés de la licence.

## Questions ouvertes

- Choix du moteur.
- Outil de génération d'images (à étudier : licences d'usage, cohérence, coût).
- Langue de l'interface et du code (français, anglais ?).
- Résolution d'écran cible.
