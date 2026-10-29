# 06 — Unités

## Décidé

- **Améliorables** : on paie pour moderniser une unité existante.
- **Vétérans** : les unités gagnent de l'expérience et des bonus en combattant.
- **Système de contres** : chaque type d'unité est fort contre certains et faible contre d'autres.
- Le comportement sur le front dépend des **points de vie** et des **caractéristiques** de l'unité.
- Unités navales et spatiales organisées par classes (torpilleurs, cuirassés…) : voir [chapitre 09](09-naval-spatial.md).
- Ères modernes inspirées des **guerres et technologies actuelles** ; missiles, ICBM et défense antimissile détaillés au [chapitre 08](08-guerre-moderne.md).
- Futur inspiré de *Warhammer 40 000*.
- **Clonage d'êtres humains** et **centres robotiques** comme sources d'unités (acte III).
- **Diversité croissante** : peu d'unités dans les premières ères (à la préhistoire, le but est de survivre et de chasser), puis de plus en plus. Exemples : lances, boucliers, fantassins et unités à distance à l'Antiquité ; cavaliers, chevaliers, machines de guerre et navires au Moyen Âge ; avions ensuite. Inspiration : le jeu *War Selection*, riche en unités.
- **Représentation selon l'échelle** : unités individuelles au début, puis escouades, puis divisions et légions (voir [chapitre 10](10-echelles.md)).
- **Généraux** attachés aux armées, avec bonus et expérience (pas de héros uniques). Ils sont **recrutés**, et il en existe **deux types** : le **stratège** (soin, démoralisation de l'ennemi) et le **meneur** (moral, attaque).
- **Taille des armées** : un **plafond** lié à la population et aux casernes, plus un **coût d'entretien**.
- **Ce que consomme une armée** : **nourriture** ; **solde** en monnaie (à partir de l'âge du fer) ; **munitions**, uniquement quand elles sont utilisées ; **carburant** pour les déplacements ; ressources de **moral** (alcool par exemple).
- **Fatigue** : les unités se fatiguent, ont besoin de **repos** et ne peuvent pas enchaîner trop de batailles sans perdre en efficacité. Les **vétérans**, rodés, y sont moins sensibles. Récupération : **au repos sur place** (lente), **en garnison** (rapide), par **rotation au front** (une armée fraîche relève une armée fatiguée sans perdre la position), et accélérée par le **ravitaillement** (nourriture, biens de moral).
- **Armée non payée ou non nourrie** : **moral en baisse**, **désertion**, **pillage** du territoire où elle se trouve.
- **Coût selon la situation** : une armée **en campagne** coûte plus cher qu'en garnison ; on peut **démobiliser en réserve** en temps de paix ; avant l'ère industrielle, une armée peut **fourrager** (vivre en partie sur le pays).
- **Troupes d'élite** : une version élite d'une unité, plus longue à former. Les unités s'améliorent aussi par l'**expérience du combat**.
- **Composition des unités selon l'ère** : au début, une unité compte **beaucoup d'hommes** ; plus on avance, **moins elle compte d'hommes**, car chaque homme ou machine est bien plus puissant. Un char prend aussi beaucoup plus de place qu'un fantassin : il faut **moins d'unités** pour faire autant de dégâts.
- **Chair à canon** : certaines unités doivent rester **bon marché**.
- **Unités des ères précédentes** : toujours disponibles et **améliorables** vers leur version plus récente.
- **Système retenu** : **classes et contres**, **charge, flanc et moral**, **défenses fortes** en début de partie (voir la [recherche sur les unités](recherche/unites-jeux-de-reference.md)).
- **Formations** : le joueur choisit la formation de ses unités, et la résolution automatique en tient compte (voir [chapitre 07](07-batailles.md)).
- **Factions** : mêmes unités pour tous, avec de **petits bonus** de faction.
- **Références étudiées** : *War Selection*, *Empire Earth*, *Age of Empires II* et les *Total War* historiques. Synthèse, classes proposées et formule de dégâts enrichie dans la [recherche sur les unités](recherche/unites-jeux-de-reference.md).

## Propositions (à valider)

### Caractéristiques d'une unité

| Caractéristique | Symbole | Rôle |
|-----------------|---------|------|
| Points de vie | $PV$ | Résistance |
| Attaque | $A$ | Dégâts infligés |
| Armure | $Ar$ | Réduction des dégâts |
| Portée | $p$ | Distance d'attaque |
| Vitesse | $v$ | Déplacement |
| Cadence | $f$ | Attaques par seconde |
| Moral | $m$ | Seuil de retraite |
| Type | $t$ | Classe pour les contres |
| Ère | $n$ | Époque d'origine |

### Grands types et contres (terrestre)

```
Infanterie ──bat──► Distance ──bat──► Cavalerie / Blindés ──bat──► Infanterie
        Antiaérien ──bat──► Aérien ──bat──► Blindés / Bâtiments
                Siège / Artillerie ──bat──► Bâtiments et fortifications
```

### Formule de dégâts

$$
D = A \cdot M\!\left(t_{\text{att}},\, t_{\text{déf}}\right) \cdot \frac{100}{100 + Ar} \cdot \left(1 + 0{,}1\,v_{\text{rang}}\right) \cdot \gamma\!\left(\Delta n\right)
$$

avec :

- $M$ le multiplicateur de contre (par exemple $1{,}5$ si avantage, $0{,}67$ si désavantage, $1$ sinon) ;
- $v_{\text{rang}}$ le rang de vétéran ($0$ à $5$) ;
- $\gamma(\Delta n)$ un facteur d'écart d'ère, avec $\Delta n = n_{\text{att}} - n_{\text{déf}}$. Par exemple $\gamma = 1{,}25^{\,\Delta n}$, pour qu'une unité en retard de deux ères soit nettement dominée sans être totalement inutile.

> **Décidé** : une ère d'avance ne doit **pas** valoir victoire automatique. Pistes pour le garantir : plafonner $\gamma$ (par exemple $\gamma \le 2$), donner au défenseur des bonus de terrain et de fortification indépendants de l'ère, et faire dépendre les unités avancées d'un **intrant critique** rare. Une armée moderne privée de carburant ou de munitions redevient vulnérable.

### Moral et tenue du front

Une unité **tient sa position** tant que :

$$
\frac{PV}{PV_{\max}} > \theta_{\text{retraite}}
\quad\text{et}\quad
m > m_{\min}
$$

Le seuil $\theta_{\text{retraite}}$ dépend de l'ordre donné : « tenir à tout prix » ($\theta = 0$), « tenir » ($\theta = 0{,}3$), « harceler » ($\theta = 0{,}6$).

### Encombrement et effectifs (proposition)

Chaque hexagone offre une capacité de $C_{\text{hex}}$ places, réduite par le terrain ($\tau \le 1$ en forêt, montagne, marais). Chaque unité occupe $e_u$ places :

$$
\sum_{u \,\in\, \text{hexagone}} e_u \;\le\; \tau \cdot C_{\text{hex}}
$$

Avec par exemple $C_{\text{hex}} = 12$ :

| Ère | Unité type | Hommes ou engins par unité (valeur de jeu) | Encombrement $e_u$ | Unités par hexagone en plaine |
|-----|-----------|---------------------------------------------|--------------------|-------------------------------|
| Préhistoire | Bande de guerriers | $\approx 50$ hommes | $1$ | $12$ |
| Antiquité | Centurie, phalange | $\approx 100$ hommes | $1$ | $12$ |
| Poudre | Bataillon de ligne | $\approx 300$ hommes | $1$ ; canon $2$ | $6$ à $12$ |
| Pétrole | Compagnie de chars | $\approx 10$ chars | $3$ | $4$ |
| Moderne | Section mécanisée | $\approx 4$ véhicules | $2$ | $6$ |
| Révolution de l'IA | Essaim de drones | $\approx 50$ drones | $1$ | $12$ |

Les effectifs sont des valeurs de jeu, pas des données historiques sourcées.

### Entretien et fatigue (proposition)

Entretien par pas de temps d'une unité $u$, avec un coefficient de situation $\kappa$ (par exemple $\kappa = 0{,}3$ en réserve, $1$ en garnison, $1{,}5$ en campagne) :

$$
\dot{E}_u = \kappa \cdot \left(e_{\text{nour}} + e_{\text{solde}} + e_{\text{moral}}\right) \;+\; e_{\text{carb}} \cdot v_{\text{déplacement}} \;+\; e_{\text{mun}} \cdot \dot{n}_{\text{tirs}}
$$

Les munitions ne coûtent qu'en tirant, le carburant qu'en se déplaçant. Avec le fourrage, une part $\phi_{\text{fourrage}}$ de la nourriture est prélevée sur le territoire, avec une baisse de stabilité locale.

Fatigue $F \in [0\,;\,1]$ : elle monte en marche et en combat, et redescend au repos.

$$
\frac{dF}{dt} = k_{\text{effort}}\,(1 - F) - k_{\text{repos}}\,F
$$

Efficacité au combat, moins affectée pour les vétérans de rang $v_{\text{rang}} \in [0\,;\,5]$ :

$$
\eta_F = 1 - \varphi_0 \left(1 - 0{,}1\, v_{\text{rang}}\right) F
$$

Avec $\varphi_0 = 0{,}5$ par exemple, une unité épuisée ($F = 1$) perd $50\ \%$ d'efficacité, et un vétéran de rang 5 seulement $25\ \%$.

### Vétérance

Gain d'XP par unité ennemie détruite, proportionnel à sa valeur :

$$
XP_{\text{unité}} \mathrel{+}= \lambda \cdot \text{coût}_{\text{ennemi}}
$$

Un rang de vétéran est atteint à chaque palier d'XP ; chaque rang apporte environ $+10\,\%$ d'efficacité.

### Unités terrestres des ères 11 à 18

| Ère | Infanterie | Blindés et véhicules | Aérien | Soutien |
|-----|-----------|----------------------|--------|---------|
| Pétrole | Fantassin motorisé | Char, automitrailleuse | Chasseur à hélice, bombardier | Artillerie tractée |
| Atomique | Fantassin mécanisé | Char lourd, transport blindé | Chasseur à réaction | Artillerie automotrice |
| Moderne | Infanterie équipée de missiles antichars | Char de combat moderne, véhicule de combat d'infanterie | Chasseur multirôle, hélicoptère d'attaque | Lance-roquettes multiple, défense sol-air |
| Révolution IA | Infanterie + opérateurs de drones | Robots terrestres | **Drones FPV**, drones longue portée, essaims | Guerre électronique (brouillage) |
| Spatiale / fusion | Exosquelettes | Blindés à propulsion électrique | Appareils transatmosphériques | Armes à énergie dirigée |
| Hyperspatiale / impériale | **Clones**, troupes d'élite en armure lourde | Machines de guerre géantes | Vaisseaux de débarquement | Unités robotiques |

### Unités de l'acte III

À cette échelle, on manipule des **régiments** ou des **légions** plutôt que des unités individuelles :

- **Légions de clones** : produites rapidement par les quartiers de clonage, peu chères, moral faible.
- **Légions robotiques** : sans moral (ne battent jamais en retraite), vulnérables à la guerre électronique.
- **Troupes d'élite** : rares, très chères, vétérance rapide.
- **Garnisons planétaires** : fixes, défendent une planète.

## Questions ouvertes

- Les généraux peuvent-ils mourir au combat ?
- Une unité améliorée garde-t-elle son rang de vétéran ?
