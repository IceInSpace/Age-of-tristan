# 04 — Économie, ressources et production

## Décidé

- **Pas de civils qui récoltent** : aucune unité de type villageois ou mineur. Une ville ou un village exploite les ressources situées dans son **rayon d'action** en y construisant un **bâtiment d'exploitation** (mine, carrière, camp de chasse, puits…). La main-d'œuvre est la population agrégée de la ville.
- **Ressources évolutives par ère** (silex, puis bronze, charbon, pétrole, uranium…).
- **Chaînes de production** : des matières premières transformées en produits.
- **Stocks par ville** (remplace le « stock global » décidé au départ) : chaque ville a son stock et ses **greniers**. Une ville entourée d'assez de champs se suffit à elle-même ; sinon, des **routes commerciales** entre villes et villages équilibrent les ressources.
- **Jours de stock** : le joueur fixe un objectif en jours de réserve (par exemple de nourriture) par ville.
- **Logistique automatique avec priorités** : les surplus partent seuls vers les villes en manque. Avec la technologie **intendance militaire** (ère de la poudre), le joueur peut marquer une ville **prioritaire**, par exemple un village proche du front qui doit recevoir beaucoup de munitions.
- **Par défaut**, si aucune option n'est choisie, **seul le surplus est envoyé**.
- **Villes et mégavilles-entrepôts** : elles retiennent tous les surplus des autres villes.
- **Réserve minimale en pourcentage** par ville, et réglages **par ressource**.
- **Technologies de logistique** : elles débloquent les réglages fins, améliorent les automatismes et réduisent les pertes en transport.
- **Ressources visibles sur la carte**, découvertes seulement quand leur existence est connue (voir [chapitre 02](02-carte-exploration.md)).
- **Ère du pétrole** avec exploitation pétrolière.
- **Pyrolyse** pour « fabriquer » du pétrole.
- **Fusion nucléaire** comme source d'énergie avancée.
- **Pollution** : mécanisme de jeu, visible sur la carte.
- **Intrant critique** et **guerre des stocks** (détaillés plus bas).
- **Monnaie** à partir de l'**âge du fer** (technologie Monnaie) ; avant, troc et ressources physiques.
- **Véhicules de transport** achetables (caravanes, cargos, tankers) pour augmenter le débit des routes.
- Inventaire proposé : **78 ressources** dans l'acte I, en 8 gammes, voir [ressources et chaînes](ressources-et-chaines.md).
- **Changement d'échelle** : aux actes II et III, l'économie est simulée de façon plus large et moins détaillée, par planète (voir [chapitre 10](10-echelles.md)). Pas de construction manuelle de lignes de production comme dans *Dyson Sphere Program*.

## Propositions (à valider)

### Exploitation par rayon d'action

Chaque agglomération possède un **rayon d'action** $R$ qui grandit avec son niveau. Tout gisement situé dans ce rayon peut être exploité par un bâtiment dédié, sans unité à envoyer.

Le **niveau** de l'agglomération fixe le **rayon maximal** ; dans cette limite, le rayon effectif grandit avec les **routes**, les **technologies** et la **culture** (décidé).

| Agglomération | Rayon maximal indicatif (hexagones) |
|---------------|-------------------------------------|
| Campement | $2$ |
| Village 1 à 5 | $2$ à $4$ |
| Ville 1 à 5 | $4$ à $6$ |
| Mégalopole | $7$ et plus |

Rayon effectif proposé, avec $R_{\max}(\text{niveau})$ le plafond, $R_0$ le rayon de base et $b_{\text{routes}}$, $b_{\text{tech}}$, $b_{\text{culture}}$ des bonus en hexagones :

$$
R = \min\!\left(R_{\max}(\text{niveau}),\; R_0 + b_{\text{routes}} + b_{\text{tech}} + b_{\text{culture}}\right)
$$

Les valeurs sont à équilibrer en jeu. Production d'un bâtiment d'exploitation $b$ sur un gisement $g$ :

$$
\dot{X}_b = y_b \cdot q_g \cdot \min\!\left(1,\; \frac{L_b}{L_b^{\text{req}}}\right) \cdot \left(1 + \beta_{\text{tech}}\right)
$$

avec $y_b$ le rendement nominal du bâtiment, $q_g$ la richesse du gisement, $L_b$ la main-d'œuvre que la ville lui affecte automatiquement et $\beta_{\text{tech}}$ le bonus des technologies.

**Règles proposées** :

- **Gisement hors de portée** : on fonde un **village** ou un **avant-poste** à côté. C'est le même principe que les modules de colonisation de l'acte III (voir [chapitre 11](11-hyperspatial.md)).
- **Rayons qui se chevauchent** : un gisement n'est exploité que par **un seul** bâtiment, rattaché à la ville qui l'a construit.
- **Gisement à la frontière** : il peut être revendiqué par deux factions, ce qui crée une source de conflit.
- **Chasse** : le camp de chasse prélève le gibier de son rayon, qui s'épuise si l'on chasse trop vite (voir [chapitre 02](02-carte-exploration.md)).

### Gisements : épuisement (décidé)

- **S'épuisent** : les **fossiles** (pétrole, gaz, charbon), les **minerais** (fer, cuivre, étain, uranium…) et les **renouvelables** (gibier, poisson, bois), ces derniers se régénérant si l'on ne prélève pas trop vite.
- **Pierre et argile** : quantités **énormes**, en pratique inépuisables.
- **Mécanismes retenus** : récupération par la technologie, **gisements étendus** (pétrole, gaz) exploités par de nombreux puits, **mines à ciel ouvert qui s'étendent**, et **prospection** (la taille d'un gisement est d'abord estimée, puis précisée).
- **Couches géologiques** : les minerais se trouvent dans des couches dont on tire aussi des **co-produits** (pierre). Ce qui est en **surface** est accessible d'emblée et les technologies y augmentent l'**intensité et les débits** ; les technologies d'**extraction** servent à atteindre ce qui est **profond**.
- **Gisement épuisé** : il devient une **friche** polluée, puis peut être **reconverti** grâce à une technologie (lac, décharge, stockage, musée minier).
- Détail des ressources, des chaînes et du taux de découverture dans [ressources et chaînes](ressources-et-chaines.md).

Modèle : un gisement contient une quantité en place $Q_{\text{place}}$, répartie en couches de profondeur croissante. Seule la fraction accessible avec la technologie du moment est extractible :

$$
Q_{\text{extractible}} = \sum_{\text{couches accessibles}} f_{\text{rec}}(\text{tech}) \cdot Q_{\text{couche}}
$$

Chaque technologie d'extraction donne accès à une couche plus profonde, ou augmente $f_{\text{rec}}$ pour les gisements étendus : des gisements déjà exploités redeviennent rentables. La prospection affiche une estimation $\hat{Q} = Q_{\text{place}}\,(1 \pm \varepsilon)$, dont l'incertitude $\varepsilon$ diminue avec les technologies de géologie.

### Uranium : l'enrichissement comme technologie clé (décidé)

La technologie clé de l'uranium est son **enrichissement**, en deux étapes : d'abord la **diffusion gazeuse**, chère et très coûteuse en énergie, puis l'**ultracentrifugation**, beaucoup plus économe et plus efficace.

Repères réels : environ $2\,400$ à $2\,500\ \text{kWh}$ par unité de travail de séparation (UTS) pour la diffusion gazeuse, contre environ $50$ à $60\ \text{kWh/UTS}$ pour la centrifugation, soit environ $45$ fois moins d'énergie ([Wikipédia, Separative work units](https://en.wikipedia.org/wiki/Separative_work_units)). En jeu, l'usine d'enrichissement consommerait donc énormément d'électricité tant que l'ultracentrifugation n'est pas recherchée.

### Stockage et péremption (décidé)

- La **capacité de stockage** d'une ville est **limitée** par ses greniers et entrepôts.
- **Transformer la nourriture la conserve mieux** : blé frais → farine, viande fraîche → salaison.

Chaque produit a son propre taux de péremption $\lambda$, avec $\lambda_{\text{farine}} \ll \lambda_{\text{blé frais}}$ et $\lambda_{\text{salaison}} \ll \lambda_{\text{viande fraîche}}$. Pour un stock $M$ :

$$
\frac{dM}{dt} = \dot{M}_{\text{entrée}} - \dot{M}_{\text{sortie}} - \lambda\, M
$$

La transformation devient ainsi un choix de gestion : on perd un peu à la transformation, mais on conserve beaucoup plus longtemps. Ce même $\lambda$ sert aux pertes en transport (voir plus bas).

### Familles de ressources

| Famille | Exemples | Apparition |
|---------|----------|------------|
| Vivres | Gibier, baies, céréales, bétail, poisson | Préhistoire → néolithique |
| Matériaux | Bois, pierre, argile | Préhistoire |
| Minerais | Silex, cuivre, étain, fer, charbon | Préhistoire → âge du fer |
| Énergie | Charbon, pétrole, gaz, électricité, uranium, deutérium | Industriel → fusion |
| Produits | Outils, armes, tissus, acier, carburants, plastiques, électronique | Selon l'ère |
| Avancés | Silicium, terres rares, lithium, hélium-3, exotiques | Moderne → impérial |
| Immatériels | Science, culture, XP, influence | Toutes les ères |

### Modèle de production en procédés

Chaque bâtiment de transformation est une **opération unitaire** définie par une recette :

$$
\sum_i a_i \, X_i \;\xrightarrow{\;\tau\;}\; \sum_j b_j \, Y_j
$$

avec $X_i$ les entrées, $Y_j$ les sorties, $a_i$ et $b_j$ les coefficients de la recette, $\tau$ la durée d'un cycle.

Exemple, haut fourneau de l'ère industrielle :

$$
2\,\text{Minerai de fer} + 1\,\text{Charbon} \;\xrightarrow{\;\tau = 10\,\text{s}\;}\; 1\,\text{Acier}
$$

Débit de sortie d'un bâtiment, limité par l'entrée la plus rare, la main-d'œuvre, le terrain et la stabilité :

$$
\dot{Y}_j = \frac{b_j}{\tau} \cdot \min\!\left(1,\; \min_i \frac{\dot{X}_i^{\text{dispo}}}{a_i / \tau},\; \frac{L}{L_{\text{req}}}\right) \cdot \left(1 + \beta_{\text{terrain}}\right) \cdot \varphi(S)
$$

avec $L$ la main-d'œuvre affectée, $L_{\text{req}}$ la main-d'œuvre nominale, $\beta_{\text{terrain}}$ le bonus ou malus de terrain et $\varphi(S) \in [0 \,;\, 1]$ un facteur de stabilité.

### Bilan global

Stock d'une ressource $X$ au cours du temps, comme un bilan matière :

$$
\frac{dM_X}{dt} = \sum_{\text{producteurs}} \dot{X}_{\text{prod}} - \sum_{\text{consommateurs}} \dot{X}_{\text{cons}}
$$

L'interface pourrait afficher ce bilan sous forme de **diagramme de Sankey** pour repérer les goulots d'étranglement.

### Exemple de chaîne complète (ère industrielle)

```
Mine de fer ──┐
              ├──► Haut fourneau ──► Acier ──► Usine d'armement ──► Fusils
Mine charbon ─┘                         └──► Atelier ferroviaire ──► Rails
```

### Ère du pétrole : exploitation et raffinage

```
Puits terrestre ─────┐
                     ├──► Brut ──► Raffinerie ──┬──► Essence ──► Véhicules, aviation
Plateforme offshore ─┘                          ├──► Gazole ──► Blindés, navires, engins
                                                ├──► Fioul lourd ──► Centrales, marine
                                                └──► Naphta ──► Pétrochimie ──► Plastiques, explosifs, engrais
```

**Épuisement des gisements fossiles** : la production d'un gisement pourrait suivre une courbe de Hubbert. Avec $Q(t)$ la quantité cumulée extraite et $Q_\infty$ la réserve récupérable totale :

$$
Q(t) = \frac{Q_\infty}{1 + e^{-b\,(t - t_m)}}
\qquad
\dot{Q}(t) = b\,Q(t)\left(1 - \frac{Q(t)}{Q_\infty}\right)
$$

La production passe par un pic à $t = t_m$, puis décline. C'est cette raréfaction qui rend la pyrolyse intéressante en jeu.

### Pyrolyse : « fabriquer » du pétrole

Trois voies de carburants de synthèse, réparties sur les ères :

| Ère | Procédé | Charge | Produit |
|-----|---------|--------|---------|
| Ère du pétrole | Liquéfaction du charbon (hydrogénation, Fischer-Tropsch) | Charbon | Carburant de synthèse, coûteux |
| Ère moderne | Pyrolyse rapide de biomasse + valorisation | Bois, résidus agricoles | Bio-huile, puis carburant |
| Révolution de l'IA | Pyrolyse des déchets plastiques | Plastiques usagés | Huile de pyrolyse, recyclage |

**Repères réels (pyrolyse de biomasse)**, d'après Bridgwater ([IEA Bioenergy, 2013](https://www.ieabioenergy.com/wp-content/uploads/2013/10/ExCo66-P2-Biomass-pyrolysis-Tony-Bridgwater.pdf)) :

| Mode | Conditions | Liquide | Charbon (char) | Gaz |
|------|-----------|---------|----------------|-----|
| Rapide | $\approx 500\ ^\circ\text{C}$, vapeurs $\approx 1\ \text{s}$ | $75\ \%$ | $12\ \%$ | $\approx 13\ \%$ (par différence) |
| Intermédiaire | $\approx 500\ ^\circ\text{C}$, $10$–$30\ \text{s}$ | $50\ \%$ (deux phases) | $25\ \%$ | — |
| Lente | $\approx 400\ ^\circ\text{C}$, longue | $35\ \%$ | $35\ \%$ | — |

Propriétés de la bio-huile de pyrolyse rapide (même source) : environ $25\ \%$ d'eau, $35$–$40\ \%$ d'oxygène en masse, $\text{PCS} \approx 17\ \text{MJ/kg}$, $\text{pH} \approx 2{,}5$. Elle doit être **valorisée** avant de servir de carburant :

- **hydrotraitement** : l'oxygène est rejeté sous forme d'eau, il faut de l'hydrogène sous pression ;
- **craquage sur zéolithes** : l'oxygène est rejeté sous forme de $\text{CO}_2$, sans hydrogène, mais avec régénération continue du catalyseur ;
- **gazéification puis Fischer-Tropsch** ou synthèse du méthanol.

**Repères réels (pyrolyse des plastiques)** : à $500\ ^\circ\text{C}$, des polyoléfines (PE et PP) donnent de $62$ à $76\ \%$ massique de liquide selon le grade ([Wu *et al.*, *Green Chemistry*, 2024](https://pubs.rsc.org/en/content/articlepdf/2024/gc/d4gc04029e)).

Recettes de jeu proposées, calées sur ces ordres de grandeur :

$$
100\,\text{Biomasse} \;\xrightarrow{\text{pyrolyse rapide}}\; 75\,\text{Bio-huile} + 12\,\text{Char} + 13\,\text{Gaz}
$$

$$
100\,\text{Bio-huile} + h\,\text{H}_2 \;\xrightarrow{\text{hydrotraitement}}\; y\,\text{Carburant} + \text{Eau}
$$

$$
100\,\text{Déchets plastiques} \;\xrightarrow{\text{pyrolyse}}\; 70\,\text{Huile} + 20\,\text{Gaz} + 10\,\text{Résidus}
$$

Les valeurs de $h$ et de $y$ restent à fixer. Le rendement final en carburant étant nettement plus faible que celui du raffinage du brut, la pyrolyse reste un **substitut**, pas une solution gratuite. La répartition $20/10$ entre gaz et résidus des plastiques est une valeur de jeu, pas une donnée de la source.

### Fusion nucléaire

- **Combustible** : deutérium (eau de mer) et tritium (produit à partir du lithium).
- **Rôle en jeu** : énergie quasi illimitée, qui rend possibles la terraformation, les arcologies et la propulsion interplanétaire.
- **Variante avancée** : fusion à l'hélium-3, ressource rare extraite de la Lune ou des géantes gazeuses, ce qui donne une raison économique d'aller dans l'espace.

### Pollution

Modèle de premier ordre par zone (région ou planète), avec $\Pi$ le niveau de pollution :

$$
\frac{d\Pi}{dt} = \sum_i e_i - k_{\text{abs}}\,\Pi - k_{\text{dépol}}\,D
$$

avec $e_i$ les émissions des bâtiments (usines, raffineries, centrales), $k_{\text{abs}}$ la capacité d'absorption naturelle (forêts, océans) et $D$ l'effort de dépollution (bâtiments de traitement, technologies vertes, terraformation).

Effets proposés : baisse de la croissance de population et de la stabilité, rendement agricole réduit, et au-delà d'un seuil, changement climatique de la zone.

### Intrant critique et guerre des stocks (décidé)

Deux mécaniques retenues après la [recherche](recherche/technologies-et-armes-par-ere.md). D'après les sources, l'avantage militaire vient moins de la qualité de l'arme que de l'accès à un intrant critique et du débit de production.

**Intrant critique** : chaque unité ou bâtiment clé dépend d'une ressource dont la pénurie le bloque ou le dégrade. Repères tirés de la recherche :

| Ère | Intrant critique | Ordre de grandeur sourcé |
|-----|------------------|--------------------------|
| Bronze | Étain (importé) | Environ $1\ \text{t/an}$ d'étain d'Assur vers l'Anatolie |
| Fer | Charbon de bois | $m_{\text{charbon}} / m_{\text{fer}} \approx 13$ ; plus de $50\ \%$ de pertes au forgeage |
| Poudre | Salpêtre | Poudre à $75:15:10$ (salpêtre, charbon, soufre) |
| Poudre (naval) | Chêne | Environ $4\,000$ chênes pour un vaisseau de 100 canons |
| Électrique et pétrole | Nitrates, puis ammoniac de synthèse | Haber–Bosch : environ $15\ \%$ de conversion par passe, $97$–$98\ \%$ avec recyclage |
| Pétrole | Carburant | Un char de 1940 consomme environ $2\ \text{L/km}$ sur route |
| Révolution de l'IA | Puces, terres rares, intercepteurs | Drone FPV à quelques centaines de dollars contre intercepteur à plusieurs millions |
| Ère spatiale | Coût de mise en orbite | De $\approx 54\,000$ à $\approx 2\,700$ dollars par kg vers l'orbite basse |

Les valeurs de jeu seront **arrondies et simplifiées** (orientation « inspiré, simplifié »), mais les rapports entre ressources s'inspireront de ces ordres de grandeur.

**Guerre des stocks** : munitions, carburant et intercepteurs sont des stocks qui se vident pendant les combats et se remplissent au débit des usines. Pour une unité ou une défense $u$ :

$$
\frac{dS_u}{dt} = \dot{P}_u - \dot{C}_u^{\text{combat}}
$$

avec $\dot{P}_u$ le débit de production et $\dot{C}_u^{\text{combat}}$ la consommation en combat. Quand $S_u = 0$, l'unité perd l'essentiel de son efficacité. Pour éviter la micro-gestion, le réapprovisionnement est **automatique** par la logistique d'offre et de demande décrite ci-dessous. Le joueur agit sur la production et sur les priorités, pas sur les convois.

### Logistique : stocks par ville, offre et demande

#### Réglages décidés

| Réglage | Description |
|---------|-------------|
| **Par défaut** | Si aucune option n'est choisie, la ville garde ce dont elle a besoin et **seul le surplus est envoyé** |
| **Réserve minimale (%)** | Pourcentage de stock que la ville garde toujours, quoi qu'il arrive |
| **Jours de stock** | Objectif de réserve exprimé en jours de consommation |
| **Ville-entrepôt** | Une ville ou mégaville désignée comme stock **retient tous les surplus** non demandés ailleurs, puis les redistribue |
| **Priorité** | Une ville prioritaire (par exemple près du front) est servie en premier. Débloquée par l'**intendance militaire** |
| **Par ressource** | Chaque réglage peut être fixé ressource par ressource (par exemple : garder 80 % des munitions, mais tout envoyer en bois) |

Ces réglages ne sont pas tous disponibles d'emblée : ils sont débloqués par des **technologies de logistique** qui affinent aussi les automatismes et réduisent les pertes en transport (voir plus bas).

#### Modèle proposé

Pour une ville $c$ et une ressource $r$, avec $\dot{C}_{c,r}$ sa consommation, $S^{\max}_{c,r}$ sa capacité de stockage (greniers, entrepôts), $j_{c,r}$ l'objectif en jours et $\rho_{c,r} \in [0\,;\,1]$ la réserve minimale en pourcentage, le stock que la ville garde est :

$$
S^{\text{garde}}_{c,r} = \max\!\left(j_{c,r}\, \dot{C}_{c,r},\;\; \rho_{c,r}\, S^{\max}_{c,r}\right)
$$

Par défaut, $j$ vaut une valeur de base (par exemple $10$ jours) et $\rho = 0$ : la ville garde juste ses besoins et envoie le reste.

Déficit et surplus :

$$
D_{c,r} = \max\left(0,\; S^{\text{garde}}_{c,r} - S_{c,r}\right)
\qquad
O_{c,r} = \max\left(0,\; S_{c,r} - S^{\text{garde}}_{c,r}\right)
$$

**Ordre de distribution** des surplus d'une ville $a$ :

1. Vers les villes **en déficit**, au prorata de leur priorité $p_b$, de leur déficit et de la proximité :

$$
\varphi_{a \to b} = \min\!\left(Q_{ab}^{\max},\; O_{a,r} \cdot \frac{p_b\, D_{b,r} / t_{ab}}{\sum_{k} p_k\, D_{k,r} / t_{ak}}\right)
$$

2. Le reste vers les **villes-entrepôts**, au prorata de leur capacité libre $S^{\max}_e - S_e$ et de la proximité.
3. S'il n'y a ni déficit ni entrepôt, le surplus **reste sur place** (et peut être perdu si les greniers sont pleins).

Les villes-entrepôts redistribuent ensuite leurs stocks vers les villes en déficit, en suivant la même règle 1.

Le temps $t_{ab}$ dépend du **niveau de route** et du terrain (voir [chapitre 02](02-carte-exploration.md)). Toutes les villes sont reliées, même sans route, mais très lentement.

#### Pertes en transport

Les pertes suivent une loi du premier ordre, comme une dégradation : avec $\lambda_r$ le taux de perte de la ressource $r$ (élevé pour la nourriture périssable, quasi nul pour les métaux) et $\eta_L \in [0\,;\,1]$ le facteur de réduction apporté par les technologies de logistique, la quantité reçue vaut :

$$
\varphi^{\text{reçu}}_{a \to b} = \varphi_{a \to b} \cdot \exp\!\left(-\,\eta_L\, \lambda_r\, t_{ab}\right)
$$

Un trajet long hors route peut ainsi faire perdre une bonne part de la nourriture envoyée, alors qu'une autoroute et une logistique avancée rendent les pertes négligeables.

#### Technologies de logistique (proposition)

| Ère | Technologie | Débloque |
|-----|-------------|----------|
| Préhistoire | — | Mode par défaut : surplus envoyé vers la ville voisine en manque, pertes élevées ($\eta_L = 1$) |
| Néolithique | Greniers | Capacité de stockage, réserve en **jours** |
| Âge du bronze | Comptabilité (écriture) | Réserve minimale en **%** par ville |
| Antiquité | Entrepôts publics | **Villes-entrepôts** ; pertes réduites ($\eta_L = 0{,}8$) |
| Moyen Âge | Guildes marchandes | Réglages **par ressource** |
| Ère de la poudre | Intendance militaire | **Priorités** (décidé), ravitaillement des armées en campagne |
| Révolution industrielle | Chemin de fer et télégraphe | Anticipation des besoins (les envois partent avant la pénurie) ; $\eta_L = 0{,}5$ |
| Ère du pétrole | Logistique motorisée | Capacité des routes accrue |
| Ère moderne | Conteneurisation | Pertes quasi nulles hors nourriture ($\eta_L = 0{,}2$) |
| Révolution de l'IA | Logistique par IA | Optimisation automatique des réserves et des flux, pertes minimales ($\eta_L = 0{,}05$) |

Les valeurs de $\eta_L$ sont indicatives. Avant l'intendance militaire, toutes les villes ont la même priorité ($p_b = 1$).

C'est le principe des stations d'offre et de demande de *Dyson Sphere Program*, appliqué aux villes. Les routes deviennent stratégiques : couper une route, c'est affamer une ville ou un front. Le niveau de détail suit les échelles du [chapitre 10](10-echelles.md) : stocks par ville au niveau N1 et N2, par planète aux niveaux N3 et N4.

### Saisons (décidé : oui, désactivables)

Pour garder les saisons simples, elles n'agiraient **que sur la production de nourriture**, avec un calendrier visible et prévisible :

$$
f_s(t) = 1 + A_n \sin\!\left(\frac{2\pi\, t}{T}\right)
$$

avec $T$ la durée d'une année de jeu et $A_n$ l'amplitude saisonnière, qui **diminue avec les ères** : par exemple $A_n = 0{,}5$ à la préhistoire, puis vers $0$ à l'ère industrielle, grâce à la conservation, au commerce et à la réfrigération. Les saisons pèsent donc au début, puis disparaissent d'elles-mêmes.

Le seul geste demandé au joueur est d'avoir assez de **greniers** pour passer l'hiver. Le stock minimal se calcule comme l'intégrale du déficit pendant la mauvaise saison :

$$
S_{\min} = \int_{\text{hiver}} \left(\dot{C} - \dot{P}\, f_s(t)\right) dt
$$

L'interface peut afficher directement « réserves : 40 jours, hiver dans 25 jours ». Les saisons pourraient aussi être désactivables dans les réglages de partie.

## Questions ouvertes

- Une ressource obsolète (silex) disparaît-elle, ou reste-t-elle utilisable ?
- Commerce entre factions : troc, marché avec prix variables, ou les deux ?
- Raffinerie détaillée (plusieurs coupes : essence, gazole, fioul, naphta) ou simplifiée (brut → carburant) ?
