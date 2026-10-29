# Unités et contres dans les jeux de référence

Recherche ciblée sur *War Selection*, *Empire Earth*, *Age of Empires II* et les *Total War* historiques, pour inspirer le système d'unités d'Age of Tristan. Les faits sont sourcés ; les propositions pour le jeu sont séparées en fin de document.

## War Selection

- RTS en accès anticipé depuis le 8 octobre 2019 (Glyph Worlds), gratuit.
- **7 ères historiques**, de l'âge de pierre jusqu'aux chars lourds, à l'artillerie longue portée et aux dirigeables de combat.
- **Plus de 300 types d'unités** répartis en trois branches (terre, air, mer) et **plus de 200 bâtiments**.
- Chaque joueur commence à l'âge de pierre, puis **choisit une culture, puis un pays, en cours de partie** : 8 cultures gratuites, 12 pays supplémentaires payants, chacun avec ses unités, bâtiments et mécaniques.
- Modes notables : Survie (contre des hordes), Armageddon (il faut étendre son territoire en permanence).
- Source : [page Steam de War Selection](https://store.steampowered.com/app/1022450/War_Selection/). La page ne décrit pas le système de contres ni le mode de récolte.

## Empire Earth (2001)

- **14 époques**, de la préhistoire à l'âge nano, plus un âge spatial dans l'extension *The Art of Conquest*, qui permet de coloniser d'autres planètes ([Wikipédia](https://en.wikipedia.org/wiki/Empire_Earth_(video_game))).
- **Triangle de contres** des époques 1 à 6 : « les flèches battent les armes perçantes, les armes perçantes battent les armes de choc, les armes de choc battent les flèches ». Exemples : la phalange (perçant) contre les cavaliers isauriens (choc), les épéistes (choc) contre les archers ([Empire Earth Wiki, Combat and Defense](https://empireearth.fandom.com/wiki/Combat_and_Defense)).
- **Siège** : le lance-pierres fait des dégâts de zone, utile contre les groupes ; la catapulte frappe plus fort à l'impact, utile contre les bâtiments (même source).
- **Héros** de deux types : le **stratège** soigne les unités proches et démoralise l'ennemi ; le **guerrier** renforce le moral et frappe plus fort. Un système de **moral** modifie les statistiques des unités (Wikipédia).
- **Cybers** (robots) à l'âge numérique ; avions, chars et sous-marins à partir de la Première Guerre mondiale (Wikipédia).
- Une analyse des matrices d'unités montre par exemple, à l'âge de pierre, un rapport tactique de $7{,}22$ du lancier contre le lanceur de pierres, et une tour primitive qui domine toutes les unités de l'époque ([empire-earth.readthedocs.io](https://empire-earth.readthedocs.io/en/latest/_autosummary/empire_earth.units.relationships.epochs.epoch_02_stone.land.html)). Les défenses fixes y sont donc très fortes en début de partie.

## Age of Empires II

Règles officielles ([Age of Empires, leçon « Military & Economy »](https://ageofempires.com/learn-to-play/military-and-economy-aoe2)) :

- les **archers** contrent la plupart de l'infanterie ;
- les **lanciers** contrent la plupart de la cavalerie, et restent toujours le meilleur choix contre elle ;
- la **cavalerie** contre la plupart des archers ;
- la **milice** (infanterie d'épée) est efficace contre toutes les unités qui ne coûtent pas d'or.

Autres éléments :

- **Unités sans or** (lanciers, tirailleurs, éclaireurs à cheval) : elles ne coûtent que nourriture et bois et forment le gros des armées de fin de partie quand l'or manque (même source).
- **Tirailleurs** : forts contre les archers et les lanciers, faibles contre la mêlée et le siège, avec une portée minimale ([AoE Wiki, Skirmisher](https://ageofempires.fandom.com/wiki/Skirmisher_(Age_of_Empires_II))).
- **Siège** : le mangonneau contre les unités à distance, le bélier contre les bâtiments, le scorpion contre les unités en ligne, la tour de siège pour franchir les murs, le trébuchet qui surclasse en portée la plupart des bâtiments (leçon officielle).
- **Bonus par classe d'armure** : par exemple, l'archer a $+3$ contre la classe « lancier », le tirailleur d'élite $+4$ ([AoE Wiki, Armor class: Spearman](https://ageofempires.fandom.com/wiki/Armor_class:_Spearman)).
- **Récolte par villageois** : chaque villageois est affecté à une ressource (leçon officielle). Age of Tristan fait le choix inverse, sans unité de récolte.

## Total War historiques

- **Catégories d'unités** (*Attila*) : infanterie de mêlée, infanterie à lance, infanterie à pique, infanterie à distance, cavalerie de mêlée, **cavalerie de choc**, cavalerie à distance, artillerie de siège, artillerie de campagne ([Total War Wiki, Contarii](https://totalwar.fandom.com/wiki/Contarii_(Total_War:_Attila))).
- **Statistiques** : moral, attaque et défense de mêlée, **bonus de charge**, **masse**, points de vie, vitesse, armure, dégâts perforants (« armour-penetration »), **bonus contre infanterie, cavalerie ou éléphants** (même source).
- Exemple : les *contarii*, cavalerie de choc, ont un bonus de charge de $201$ et $+10$ contre la cavalerie, mais une défense de mêlée de $2$ seulement : ils sont redoutables à l'impact et fragiles en mêlée prolongée (même source).
- Contres observés par les joueurs (*Shogun 2*) : la lance bat la cavalerie ; l'épée bat la lance ; la cavalerie à l'épée bat tout ce qui ne porte pas de lance ; la cavalerie à la lance bat la cavalerie à l'épée ; les archers abattent les lanciers peu protégés et les cibles larges ([TWCenter, Rock Paper Scissors](https://www.twcenter.net/threads/rock-paper-scissors.436992/)).
- Contres observés (*Medieval II*) : selon un joueur, une cavalerie lourde qui charge des piques de face peut perdre le tiers à la moitié de ses hommes avant d'infliger des pertes. Les piques sont faibles en attaque et peu adaptées hors des terrains plats et dégagés. Les armes à deux mains servent à prendre de flanc et à briser les piques ([discussion Steam, Medieval II](https://steamcommunity.com/app/4700/discussions/0/613939294274363278)). Ce sont des retours de joueurs, pas des données officielles.

## Ce que l'on peut en retenir (propositions)

1. **Diversité croissante**, comme le veut le cahier des charges : peu d'unités au début, beaucoup plus ensuite (War Selection, plus de 300 types sur 7 ères).
2. **Classes plutôt qu'unités** : les contres s'appliquent à des **classes** (lance, épée, distance, choc…), et chaque ère ajoute des unités dans ces classes. C'est le principe d'Empire Earth et d'Age of Empires.
3. **Unités de base sans intrant critique** : comme les unités sans or d'Age of Empires, chaque ère aurait des unités bon marché toujours disponibles. Elles évitent qu'une pénurie bloque toute l'armée et soutiennent le refus des « unités obsolètes ».
4. **Charge, masse, flanc, moral et terrain**, comme dans les Total War : ce sont eux qui rendent les batailles tactiques intéressantes au-delà du simple pierre-feuille-ciseaux.
5. **Défenses fixes fortes au début** (tours d'Empire Earth), qui favorisent la survie de la tribu.
6. **Généraux de deux types**, inspirés des héros d'Empire Earth : un **stratège** (soin, démoralisation de l'ennemi) et un **meneur** (moral, attaque).

### Classes proposées pour Age of Tristan

| Classe | Exemples | Fort contre | Faible contre |
|--------|----------|-------------|---------------|
| Mêlée (épée, hache) | Guerrier, légionnaire, homme d'armes | Lance et pique en mêlée, distance au contact | Cavalerie de choc, distance à découvert |
| Lance et pique | Lancier, hoplite, piquier | Cavalerie (surtout de face) | Mêlée, distance, terrain accidenté |
| Distance | Frondeur, archer, arbalétrier, fusilier | Lance et pique, mêlée lente | Cavalerie, tirailleurs |
| Tirailleurs | Lanceur de javelots, tirailleur | Distance, lance | Mêlée, cavalerie |
| Cavalerie de mêlée | Cavalier, dragon | Distance, siège, cavalerie de choc en mêlée | Lance et pique |
| Cavalerie de choc | Char, cataphracte, chevalier, cuirassier | Mêlée et distance (à la charge) | Piques de face, mêlée prolongée |
| Cavalerie à distance | Archer monté | Infanterie lente | Cavalerie de mêlée, tirailleurs |
| Siège et artillerie | Bélier, trébuchet, canon | Bâtiments, formations serrées | Cavalerie, unités au contact |
| Blindé | Char, véhicule de combat | Infanterie | Antichar, aviation, drones |
| Antichar | Canon et missile antichar | Blindé | Infanterie, artillerie |
| Aérien | Chasseur, bombardier, hélicoptère | Blindé, bâtiments | Antiaérien, chasseurs |
| Antiaérien | Canon, missile sol-air | Aérien | Blindé, artillerie |
| Drone | FPV, munition rôdeuse | Blindé, infanterie | Brouillage, défense rapprochée |

### Formule de dégâts enrichie

Reprise de la formule du [chapitre 06](../06-unites.md), avec la charge, le flanc et la pénétration d'armure :

$$
D = A \cdot M\!\left(k_{\text{att}}, k_{\text{déf}}\right) \cdot \left(1 + c \cdot \mathbb{1}_{\text{charge}}\right) \cdot f_{\text{flanc}} \cdot \frac{100}{100 + Ar\,(1 - \pi)}
$$

avec :

- $M$ le multiplicateur de contre entre les classes $k$ ;
- $c$ le bonus de charge, appliqué au premier contact seulement ;
- $f_{\text{flanc}}$ valant par exemple $1$ de face, $1{,}5$ de flanc et $2$ de dos ;
- $\pi \in [0\,;\,1]$ la part de l'armure ignorée (armes perforantes, arbalètes, armes à feu).
