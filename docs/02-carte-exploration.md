# 02 — Carte, terrain et exploration

## Décidé

- **Taille d'un hexagone : 5 km** de largeur (d'un côté plat à l'autre), soit une surface d'environ $22\ \text{km}^2$ (révisé : 2 km donnait trop d'hexagones). **Pas de grille hiérarchique** : une seule taille d'hexagone pour toute la planète.
- **Échelles ajustées pour le jeu** : les **villes** et les **armées** sont **dilatées** (elles occupent plus d'hexagones que leur surface réelle, pour rester lisibles), le **temps** est **compressé** (déplacements plus rapides que dans la réalité), et les **distances** entre villes restent **réelles** à l'échelle de l'hexagone.
- **Bouclage est-ouest**, **calottes polaires** pour les types planétaires, **rivières sur les bords** des hexagones (voir [chapitre 16](16-generation-procedurale.md)).
- **Grille hexagonale**, vue en 3D stylisée avec caméra inclinée (style visé : *Humankind*, voir [chapitre 00](00-vision.md)).
- **Génération procédurale réglable** (taille, continents, climat, richesse…), **plus un éditeur** pour modifier la carte à la main.
- **Terrain contraignant** : on ne peut pas tout construire partout. Le terrain donne des **bonus ou des malus**.
- **Routes** à construire entre villages, villes et mégalopoles. **Toutes les villes sont atteignables sans route**, mais très lentement. Créer une route **défriche** le terrain et fait apparaître un **sentier**, qu'on améliore ensuite en **route pavée**, puis en **route en béton**, puis en **autoroute**. Chaque niveau augmente la vitesse de transport.
- **Ressources visibles sur la carte**.
- **Toutes les ressources sont générées dès le début de la partie**, mais une ressource n'apparaît au joueur **qu'une fois son existence connue** (exemple : pas d'uranium visible avant l'ère atomique).
- **Exploration progressive** : le territoire de départ est minuscule, puis s'agrandit.
- **Départ à distance** : les deux tribus commencent loin l'une de l'autre. Phase de survie et de chasse d'abord, rencontre après exploration.
- **Survie au début** : **gibier épuisable**, **prédateurs** qui attaquent chasseurs et campements, **raids** entre tribus. Saisons à l'étude (proposition simple au [chapitre 04](04-economie.md)).
- **Déforestation visible** : les forêts coupées disparaissent de la carte. On peut planter des **champs de bois** (taillis, plantations) ou **faire repousser la forêt**, avec une règle de gestion durable : « un arbre coupé, un arbre replanté ».
- **Paliers d'accès** : terre ferme → outre-mer (navigation) → système solaire → systèmes stellaires.
- **Pollution visible** sur la carte.
- **Terraformation** possible (voir [chapitre 11](11-hyperspatial.md)).
- Même quand la gestion devient large (actes II et III), on peut **zoomer sur une planète** et voir ses routes, ses villes développées et sa pollution (voir [chapitre 10](10-echelles.md)).
- Les autres planètes et systèmes sont **générés avec leurs propres ressources**.

## Propositions (à valider)

### Couches de visibilité

| État | Le joueur voit |
|------|----------------|
| Inconnu | Rien (zone noire) |
| Exploré | Relief, terrain, ressources connues, dernière position connue des villes |
| Observé | Tout en temps réel : unités, constructions, mouvements |

Une zone explorée redevient « explorée » (non observée) quand plus aucune unité, ville ou satellite ne la couvre.

### Types de terrain (première liste)

| Terrain | Déplacement | Construction | Effet |
|---------|-------------|--------------|-------|
| Plaine | Normal | Tout | Agriculture + |
| Forêt | Lent | Limitée | Bois +, défense + |
| Colline | Lent | Limitée | Mines +, défense ++ |
| Montagne | Très lent ou infranchissable | Mines seulement | Défense +++ |
| Marais | Très lent | Aucune avant l'ère industrielle | Maladies − |
| Désert | Lent | Limitée | Pétrole caché |
| Côte | Normal | Ports | Pêche +, commerce + |
| Rivière | Ralentit la traversée | Moulins, irrigation | Agriculture ++ |
| Océan | Navires seulement | Plateformes à l'ère moderne | — |

### Génération procédurale

> Détaillée et mise à jour au [chapitre 16](16-generation-procedurale.md).

Méthode classique proposée : un **bruit de Perlin ou Simplex** pour l'altitude $h(x,y)$ et l'humidité $w(x,y)$, puis attribution du biome selon des seuils. Le niveau de la mer $h_{\text{mer}}$ est un paramètre réglable : il fixe la proportion d'océan.

$$
\text{biome}(x,y) = f\big(h(x,y),\, w(x,y)\big)
$$

Les gisements sont placés selon le biome (pétrole en désert et offshore, charbon en colline…), avec une graine aléatoire $s$ qui rend la carte reproductible.

### Taille des hexagones : repères (décidé : 5 km)

Surface d'un hexagone de largeur $d$ :

$$
A = \frac{\sqrt{3}}{2}\, d^{2} \;\approx\; 21{,}7\ \text{km}^2 \quad \text{pour } d = 5\ \text{km}
$$

| Repère | Ordre de grandeur réel | En hexagones de 5 km |
|--------|------------------------|----------------------|
| Marche d'une légion romaine | environ $30$ km par jour (Végèce : 20 milles romains en 5 heures) | environ $6$ hexagones par jour (avant compression du temps) |
| Rome dans l'enceinte d'Aurélien | environ $14\ \text{km}^2$ (à revérifier) | moins d'un hexagone ; **dilatée** en jeu sur plusieurs |
| Paris intra-muros | environ $105\ \text{km}^2$ (à revérifier) | environ $5$ hexagones |
| Carte de départ proposée | $200 \times 150 = 30\,000$ hexagones | environ $650\,000\ \text{km}^2$, l'ordre de grandeur de la France |
| Plus grande carte de *Civilization VI* | $106 \times 66 \approx 7\,000$ cases | environ $150\,000\ \text{km}^2$ à cette échelle |

### Dilatation des villes et des armées (proposition)

Les villes et les armées sont représentées plus grandes que nature. Emprise urbaine proposée (les quartiers construits, distincte du rayon d'action qui sert à l'exploitation) :

| Agglomération | Emprise urbaine en hexagones | Surface en jeu | Surface réelle typique |
|---------------|------------------------------|----------------|------------------------|
| Village | $1$ (partagé avec les champs) | $22\ \text{km}^2$ | bien moins de $1\ \text{km}^2$ |
| Ville | $1$ à $3$ | $22$ à $65\ \text{km}^2$ | quelques $\text{km}^2$ |
| Grande ville (Rome antique) | jusqu'à $7$ | jusqu'à $150\ \text{km}^2$ | environ $14\ \text{km}^2$ |
| Mégalopole | jusqu'à $19$ ou plus | $400\ \text{km}^2$ et plus | plusieurs centaines de $\text{km}^2$ |

Le facteur de dilatation $f = A_{\text{jeu}} / A_{\text{réel}}$ est donc grand au début (une ville antique est très dilatée) et se rapproche de $1$ pour les mégalopoles modernes, qui sont réellement immenses.

### Compression du temps (proposition)

Les distances restant réelles, les déplacements sont accélérés d'un facteur $\kappa_t$ pour que les parties avancent : une armée qui couvre réellement $v$ hexagones par jour en parcourt $\kappa_t \cdot v$ par unité de temps de jeu. La valeur de $\kappa_t$ et la durée d'un « jour » de jeu seront fixées avec les statistiques et les coûts.

### Niveaux de route (proposition)

| Niveau | Débloqué à | Vitesse relative $m$ | Capacité relative |
|--------|-----------|----------------------|-------------------|
| Hors route | Toujours | $1$ | $1$ |
| Sentier (défriché) | Préhistoire | $2$ | $2$ |
| Route pavée | Antiquité (ingénierie civile) | $4$ | $5$ |
| Route en béton ou asphaltée | Ère du pétrole | $8$ | $15$ |
| Autoroute | Ère atomique ou moderne | $15$ | $40$ |

Les valeurs sont indicatives, à équilibrer en jeu. Le temps de trajet entre deux villes $a$ et $b$ se calcule segment par segment, avec $d_i$ la longueur du segment $i$, $v_0$ la vitesse de base de l'ère (marche, cheval, camion…), $m_i$ le multiplicateur du niveau de route et $\tau_i \le 1$ le facteur de terrain (forêt, montagne, marais) :

$$
t_{ab} = \sum_i \frac{d_i}{v_0 \cdot m_i \cdot \tau_i}
$$

Sur une route, le terrain pèse peu ($\tau_i$ proche de $1$) ; hors route, il pèse beaucoup. Ce temps $t_{ab}$ alimente directement la logistique du [chapitre 04](04-economie.md) : une ville reliée par autoroute est ravitaillée bien plus vite qu'un village isolé.

### Forêts : croissance et coupe (proposition)

Croissance logistique de la surface boisée $F$ d'une zone, avec $g$ le taux de repousse, $F_{\max}$ la surface boisable et $\dot{k}$ le rythme de coupe :

$$
\frac{dF}{dt} = g\,F\left(1 - \frac{F}{F_{\max}}\right) - \dot{k}
$$

La règle « un arbre coupé, un arbre replanté » revient à une politique automatique qui plafonne la coupe à la repousse, $\dot{k} \le g\,F\,(1 - F/F_{\max})$ : la forêt se maintient, au prix d'une production de bois limitée. Les **champs de bois** sont des parcelles plantées à forte valeur de $g$, mais qui occupent des terres cultivables.

## Questions ouvertes

- **Taille de la carte** : les $30\,000$ hexagones de départ proposés (environ $650\,000\ \text{km}^2$) conviennent-ils, et la planète s'agrandit-elle par l'exploration outre-mer ?
- **Compression du temps** : combien dure un « jour » de jeu, et la compression change-t-elle selon les ères ?

- **Chemin de fer**, **canaux** et **lignes maritimes** : des types de routes à part (très grande capacité, mais construits seulement entre deux gares ou deux ports) ?
- Les routes s'usent-elles, avec un coût d'entretien ?
- Taille de la planète : combien de « régions » ou de cases au total ?
- Les gisements s'épuisent-ils ?
- Climat dynamique (saisons, réchauffement dû à la pollution industrielle) ? La pollution étant désormais un mécanisme retenu, le réchauffement en serait la suite logique.
- Catastrophes naturelles : si elles existent, elles doivent rester annoncées et prévisibles (pas d'aléatoire punitif). Les retombées nucléaires sont traitées en malus de zone au [chapitre 08](08-guerre-moderne.md).
