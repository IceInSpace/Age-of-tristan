# Synthèse : ce qui est décidé, ce qui reste à décider

Document de pilotage. Il résume les décisions éparpillées dans les chapitres et liste les points encore ouverts, classés par priorité. Le détail est dans chaque chapitre (liens).

## Ce qui est décidé

### Concept et ton

- Stratégie globale en **temps réel pausable**, grille hexagonale en **3D stylisée** (style visé : *Humankind*), inspirée d'*Age of War* ; **prototype simple d'abord**, rendu soigné ensuite ; **Unity 6 + Blender** ; jeu pour soi, sur PC envisagé ([00](00-vision.md)).
- Planète **fictive** générée ; départ à la préhistoire avec **deux tribus éloignées** ([00](00-vision.md), [02](02-carte-exploration.md)).
- **Trois actes** : planétaire (ères 1 à 14), système solaire (15 et 16), hyperspatial (17 et 18) ; **18 ères** ([01](01-eres.md)).
- **Acte I inspiré de l'histoire et simplifié** ; **actes II et III en space opera** ; esthétique gothique industrielle progressive, de l'ère de la fusion à l'ère impériale ([00](00-vision.md)).
- **Thèmes durs inclus** : nucléaire, armes chimiques, bombardement de civils, esclavage et colonisation, avec leurs conséquences ([08](08-guerre-moderne.md), [13](13-diplomatie-ia.md)).
- **À éviter** : micro-gestion lourde, fin de partie molle, aléatoire punitif, unités obsolètes ([00](00-vision.md)).

### Progression

- Passage d'ère : **technologies clés** → **bâtiments** → **évolution des villes une par une** (capitale d'abord, accélérable en payant) → **XP minimale** ([01](01-eres.md)).
- Merveilles pour certaines ères seulement ([01](01-eres.md)).
- Deux arbres technologiques : **planétaire** (actes I et II) et **stellaire** (acte III), avec une branche **logistique** ([05](05-technologies.md)).
- Recherche **militaire, civile et industrielle** ; centres spécialisés ou pluridisciplinaires ; l'industrie et l'armée produisent leur propre recherche ; une technologie peut exiger d'**améliorer les bâtiments** pour s'appliquer ([05](05-technologies.md)).

### Carte et territoire

- **Grille hexagonale**, hexagones de **2 km** (environ 3,5 km²), sans grille hiérarchique ; génération **procédurale réglable** + **éditeur** ; ressources toutes générées au départ, visibles seulement une fois connues ([02](02-carte-exploration.md)).
- **Survie au début** : gibier épuisable, prédateurs, raids ([02](02-carte-exploration.md)).
- **Déforestation visible**, champs de bois et reboisement ([02](02-carte-exploration.md)).
- **Routes** : villes atteignables sans route mais lentement ; sentier → pavé → béton → autoroute ([02](02-carte-exploration.md)).
- Pollution visible ; terraformation ; zoom sur les planètes ([02](02-carte-exploration.md), [10](10-echelles.md)).

### Villes et économie

- Villes obtenues par **fondation, conquête, absorption et croissance** ; écran de ville + quartiers placés librement ; développement automatique quand les conditions sont réunies ([03](03-villes-batiments.md)).
- **Patrimoine** : au changement d'ère, un ancien bâtiment remarquable peut être modernisé, conservé, reconverti ou démoli ; il perd en efficacité, gagne en culture, tourisme et influence ; entretien sinon ruine (restaurable) ; maisons et fermes toujours modernisées ([03](03-villes-batiments.md)).
- **Population agrégée** (main-d'œuvre, consommation, stabilité), sans simulation d'individus ([03](03-villes-batiments.md)).
- **Pas de civils qui récoltent** : chaque ville exploite les ressources de son **rayon d'action** avec des bâtiments ; seuls les colons et les éclaireurs sont non combattants ([04](04-economie.md)).
- **Niveaux** : village 1 à 5, ville 1 à 5, mégalopole (technologie requise, absorbe les villes proches) ; le niveau plafonne le rayon, qui grandit avec routes, technologies et culture ; fondation directe avec demande de peuplement ([03](03-villes-batiments.md)).
- **Stockage limité** ; la transformation conserve mieux (farine, salaison) ; **saisons désactivables** ([04](04-economie.md)).
- **Gisements** : fossiles, minerais et renouvelables s'épuisent ; pierre et argile quasi inépuisables ; couches géologiques et co-produits ; prospection ; friche puis reconversion ; enrichissement de l'uranium en deux étapes ([04](04-economie.md)).
- **Monnaie** dès l'âge du fer ; **véhicules de transport** achetables pour augmenter le débit ; inventaire de **78 ressources validé** ([ressources et chaînes](ressources-et-chaines.md)).
- **Ressources évolutives**, **chaînes de production**, ère du pétrole, **pyrolyse**, fusion, **pollution** ([04](04-economie.md)).
- **Intrant critique** par unité et **guerre des stocks** ([04](04-economie.md)).
- **Stocks par ville** : par défaut, seul le surplus est envoyé ; réserve minimale en %, jours de stock, **villes-entrepôts**, réglages **par ressource**, **priorités** avec l'intendance militaire ; pertes en transport réduites par la technologie ([04](04-economie.md)).
- **Gestion qui s'élargit** : manuelle au début, puis directives (matériaux, nourriture, hommes) et villes générées automatiquement ([10](10-echelles.md)).

### Unités et batailles

- Unités **améliorables**, **vétérans**, **système de contres** ; **diversité croissante** au fil des ères ([06](06-unites.md)).
- Représentation **selon l'échelle** (individuelles → escouades → divisions) ; **généraux recrutés, stratèges ou meneurs** ; factions à **petits bonus** ([06](06-unites.md)).
- **Plafond + entretien** (nourriture, solde, munitions à l'usage, carburant au déplacement, moral) ; **fatigue** et récupération (repos, garnison, rotation au front, ravitaillement) ; impayés : moral, désertion, pillage ; campagne plus chère, réserve, fourrage ; troupes d'élite plus longues à former ; unités « chair à canon » bon marché ; classes et contres, charge, flanc, moral, défenses fortes au début ([06](06-unites.md)).
- Une ère d'avance ne doit pas valoir victoire automatique ([06](06-unites.md)).
- **Fronts** et arrière ; ordres de tenue ; bataille **automatique ou tactique au choix** ([07](07-batailles.md)).
- **Sièges** par encerclement ou assaut ; **tranchées** qui figent le front ; **aviation à rayon d'action** ([07](07-batailles.md)).
- **Armées de forme libre** sur plusieurs hexagones, de plus en plus grandes avec les ères (1, puis 7, puis 19 hexagones proposés) ; unités de **moins en moins nombreuses en hommes** mais plus puissantes et plus encombrantes ;
- **Ligne de front** ; armées formées de plusieurs unités sur une case, renforts et prises à revers ; **formations** ; bataille automatique **dans la durée** ; batailles tactiques **plus tard** ([07](07-batailles.md)).

### Guerre moderne, espace, espionnage, diplomatie

- **ICBM**, défense antimissile **un bâtiment par couche**, satellites en **orbite basse et géostationnaire** ([08](08-guerre-moderne.md)).
- **Nucléaire** : pas de riposte sans arsenal, plusieurs tailles de bombes, malus de zone ; accidents seulement en cas de négligence ([08](08-guerre-moderne.md)).
- Guerre froide : course aux armements et course à l'espace ; drones en capacité et en unités ; IA rebelle optionnelle ([08](08-guerre-moderne.md)).
- Naval par classes ; spatial dès l'ère moderne ; **rivaux qui colonisent aussi le système solaire** ([09](09-naval-spatial.md)).
- Espionnage : renseignement, sabotage, vol de technologie, déstabilisation ([12](12-espionnage.md)).
- Diplomatie avancée ; peuples neutres absorbables ; **faction nomade** au Moyen Âge ; colonies qui deviennent villes ou indépendantes ; **crises de fin et coalitions surmontables** ([13](13-diplomatie-ia.md)).
- Acte III : **unification de l'humanité** sous un empire nommé par le joueur, avec votes politiques ; **nouvel ennemi** avide d'énergie ou extraterrestre ; clonage d'abord mal accepté ([11](11-hyperspatial.md)).

## Méthode avant le développement (décidé)

Avant d'écrire du code, on statue ère par ère sur :

1. les **bâtiments**, les **unités** et la **progression** vers l'ère suivante ;
2. puis les **statistiques** et les **coûts**.

Les validations sont reportées dans le [catalogue des ères](eres/README.md).

| Ère | Contenu | Statistiques et coûts |
|-----|---------|-----------------------|
| 1 — Préhistoire | Validé | À faire |
| 2 — Néolithique | Validé | À faire |
| 3 — Âge du bronze | Validé | À faire |
| 4 à 18 | À valider | À faire |

## Ce qui reste à décider

### Priorité 1 : nécessaire pour la version minimale (préhistoire et néolithique)

| Sujet | Question | Chapitre |
|-------|----------|----------|
| Carte | Taille de la carte jouable à 2 km par hexagone | [02](02-carte-exploration.md) |
| Recherche | Une technologie à la fois par type de recherche, ou points répartis ? | [05](05-technologies.md) |
| Unités | Les généraux peuvent-ils mourir ? | [06](06-unites.md) |
| Batailles | Quelles formations, à partir de quelle ère ? Plafonds d'hexagones par armée ; capacité d'un hexagone | [07](07-batailles.md) |
| Technique | Langue du code et de l'interface | [14](14-technique.md) |
| Feuille de route | Contenu exact de la couche 1 et critère de « fini » | [15](15-feuille-de-route.md) |

### Priorité 2 : nécessaire pour l'acte I complet

| Sujet | Question | Chapitre |
|-------|----------|----------|
| Ères | Valider la liste des 18 ères | [01](01-eres.md) |
| Ères | Une ville en retard d'ère peut-elle produire les unités récentes ? A-t-elle des malus ? Peut-on régresser d'ère ? | [01](01-eres.md) |
| Villes | Nombre maximal de quartiers ; bâtiments destructibles ; prise de la capitale ; ère des villes conquises | [03](03-villes-batiments.md) |
| Économie | Commerce entre factions ? Raffinerie détaillée ou simplifiée ? Ressources obsolètes ? | [04](04-economie.md) |
| Technologies | Technologies exclusives ? Découvertes par exploration ? | [05](05-technologies.md) |
| Routes | Chemin de fer, canaux et lignes maritimes comme routes à part ? Entretien des routes ? | [02](02-carte-exploration.md) |
| Échelles | Passage au niveau N2 : à quelle ère, imposé ou proposé ? Quelles directives ? | [10](10-echelles.md) |
| Espionnage | Espions visibles ou missions par menu ? Assassinats ? Espionnage de l'IA contre le joueur ? | [12](12-espionnage.md) |
| IA | Nombre de factions réglable ? L'IA triche-t-elle aux niveaux élevés ? | [13](13-diplomatie-ia.md) |
| Moderne | ICBM conventionnels ? Réapprovisionnement des intercepteurs ? Sanction d'une frappe nucléaire sur une nation sans arsenal ? | [08](08-guerre-moderne.md) |

### Priorité 3 : actes II et III, et plus tard

| Sujet | Question | Chapitre |
|-------|----------|----------|
| Acte II | Autres planètes complètes ou simplifiées ; batailles spatiales sur la même carte ou à part ; débris orbitaux | [09](09-naval-spatial.md) |
| Acte III | Nouvel ennemi choisi au lancement ou les deux ; poids des votes politiques ; taille de la galaxie ; condition de victoire finale | [11](11-hyperspatial.md) |
| Échelles | Modifier une ville en vue zoomée à l'acte III ; déplacer ou supprimer les villes automatiques | [10](10-echelles.md) |
| Projet | Titre ; durée d'une partie ; démarrer à l'acte II ou III ; ton (sérieux ou humour) ; multijoueur | [00](00-vision.md), [13](13-diplomatie-ia.md) |
| Technique | Outil de génération d'images ; résolution cible | [14](14-technique.md) |
