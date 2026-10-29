# 16 — Génération procédurale de la planète (acte I)

Ce chapitre décrit comment le jeu fabrique la carte planétaire de départ. La génération des systèmes solaires et de la galaxie (actes II et III) sera traitée plus tard.

Un **prototype jouable** de ces règles existe : [`prototypes/forge-des-mondes.html`](../prototypes/forge-des-mondes.html) (à ouvrir dans un navigateur). Il sert de référence pour le futur code C# sous Unity.

## Décidé

- **Types de cartes** demandés :
  - **Méditerranée** ;
  - **Archipel** ;
  - **Grandes îles** ;
  - **Pangée** : un supercontinent entouré d'océan ;
  - **Continentale** : uniquement des terres, **avec ou sans lacs** ;
  - **Continents type « monde réel »** : plusieurs continents, des mers, des océans, sans copier la Terre.
- **Tailles** : **petit, grand, très grand, énorme, gigantesque**.
- **Hexagones de 5 km** (voir [chapitre 02](02-carte-exploration.md)).
- **Génération procédurale réglable** + **éditeur manuel** (déjà décidé).
- La planète du joueur n'est **pas la Terre**, et son système solaire ne sera pas forcément le nôtre (actes II et III).

## Propositions (à valider)

### Tailles

Surface d'un hexagone : $A \approx 21{,}7\ \text{km}^2$.

| Taille | Grille | Hexagones | Surface totale | Ordre de grandeur |
|--------|--------|-----------|----------------|-------------------|
| Petit | $128 \times 80$ | $10\,240$ | $\approx 222\,000\ \text{km}^2$ | Royaume-Uni |
| Grand | $200 \times 125$ | $25\,000$ | $\approx 541\,000\ \text{km}^2$ | France |
| Très grand | $256 \times 160$ | $40\,960$ | $\approx 887\,000\ \text{km}^2$ | Turquie |
| Énorme | $320 \times 200$ | $64\,000$ | $\approx 1{,}39\ \text{millions de km}^2$ | Pérou |
| Gigantesque | $400 \times 250$ | $100\,000$ | $\approx 2{,}17\ \text{millions de km}^2$ | Groenland |

Les surfaces de pays sont des ordres de grandeur de comparaison. Dans le prototype, la grande taille se génère en environ $1$ seconde et la taille gigantesque en environ $2{,}5$ secondes, sur un navigateur et sans optimisation.

### Types de cartes

| Type | Part de terres par défaut $\varphi$ | Construction du masque des terres | Particularités |
|------|-------------------------------------|-----------------------------------|----------------|
| Continents (monde réel) | $32\ \%$ (la Terre : $29\ \%$) | 3 à 6 grandes taches + 8 petites îles | Océans, mers, îles ; climat de l'équateur aux pôles |
| Pangée | $42\ \%$ | 1 tache centrale + 4 lobes + quelques îles | Une seule grande masse, intérieur sec |
| Grandes îles | $38\ \%$ | 5 à 8 taches espacées d'une distance minimale | Navigation vite indispensable |
| Archipel | $24\ \%$ | 55 à 85 petites taches + bruit plus fin | Monde maritime dès le début |
| Méditerranée | $58\ \%$ | Terres partout, moins une mer centrale allongée et un détroit | Carte régionale (latitudes $25$ à $50^\circ$), îles dans la mer |
| Continentale | $94\ \%$ | Terres partout | Étendues d'eau = lacs et mers intérieures, désactivables ; latitudes $22$ à $62^\circ$ |

La part de terres reste réglable par un curseur.

### Étapes de génération

```
Graine → Masque des terres → Bruit fractal + plaques → Niveau de la mer → Lacs et écoulement
       → Climat (température, humidité) → Biomes → Rivières → Ressources → Départs → Vérifications
```

#### 1. Graine

Une **graine** (nombre entier) initialise le générateur aléatoire : même graine et mêmes réglages donnent toujours le même monde. On peut ainsi partager une carte avec un simple nombre.

#### 2. Masque des terres

Le masque $M(x,y) \in [0\,;\,1]$ dit où l'on veut des terres. Il est construit en superposant des « taches » gaussiennes de centre $(x_k, y_k)$ et de rayon $r_k$ :

$$
M(x,y) = \max_k \exp\!\left(-\frac{(x' - x_k)^2 + (y' - y_k)^2}{r_k^2}\right)
$$

où $(x', y')$ sont les coordonnées **déformées par du bruit** (« domain warping »), pour obtenir des côtes irrégulières plutôt que des cercles. Les bords de la carte sont ramenés vers l'océan, sauf pour les types Méditerranée et Continentale.

#### 3. Bruit fractal et plaques tectoniques

Le relief de détail vient d'un **bruit fractal** (somme de bruits de Simplex à fréquences croissantes), avec $O$ octaves, une fréquence de base $f$ et une persistance $p$ :

$$
\text{fBm}(x,y) = \frac{\sum_{o=0}^{O-1} p^{\,o}\, \text{bruit}\!\left(2^{o} f x,\; 2^{o} f y\right)}{\sum_{o=0}^{O-1} p^{\,o}}
\qquad O = 6,\; p = 0{,}5
$$

Les **chaînes de montagnes** viennent de **plaques tectoniques** simplifiées : 8 à 13 centres de plaques avec une vitesse aléatoire. Près de la frontière entre deux plaques qui **se rapprochent**, on ajoute un relief en crête. Le relief final combine masque, bruit et crêtes :

$$
h = (1 - w)\, M + w\, \text{fBm} + 0{,}22\, \rho_{\text{crête}}
$$

avec $w \approx 0{,}38$ (et $0{,}5$ pour l'archipel).

#### 4. Niveau de la mer

Le niveau de la mer $h_{\text{mer}}$ est choisi pour obtenir **exactement** la part de terres voulue $\varphi$ : c'est le quantile d'ordre $1 - \varphi$ des altitudes.

$$
h_{\text{mer}} = Q_{1-\varphi}(h)
$$

#### 5. Lacs et écoulement

Un algorithme d'**inondation par priorité** (« priority-flood ») part des océans et remonte vers l'intérieur des terres. Il donne pour chaque hexagone le sens d'écoulement de l'eau, et repère les **cuvettes** : une cuvette assez profonde devient un **lac**. Pour une carte continentale, l'eau s'écoule vers les bords de la carte.

#### 6. Climat

La **température** baisse avec la latitude et l'altitude. Le prototype utilise une forme normalisée :

$$
T = 1 - 0{,}95\, \lambda^{1{,}25} - 0{,}55\, e
$$

avec $\lambda \in [0\,;\,1]$ la latitude normalisée et $e$ l'altitude relative. Repère réel pour calibrer l'altitude : dans l'atmosphère standard, la température baisse d'environ $6{,}5\ ^\circ\text{C}$ par kilomètre d'altitude.

L'**humidité** dépend de la distance à l'eau $d$ (en hexagones), d'un bruit et d'une bande sèche autour de $30^\circ$ de latitude, là où se trouvent la plupart des grands déserts terrestres :

$$
m = 0{,}5\, e^{-d/d_0} + 0{,}55\, \text{fBm}' - 0{,}28\, \exp\!\left(-\left(\frac{\lambda - 0{,}36}{0{,}1}\right)^{2}\right)
$$

#### 7. Biomes

Classement d'après la température et l'humidité (inspiré du diagramme de Whittaker) :

| Condition | Biome | Terrain de jeu correspondant |
|-----------|-------|------------------------------|
| $T < 0{,}1$ | Glace | Infranchissable sans technologie |
| Relief $> 0{,}62$ | Montagne | Montagne |
| Relief $> 0{,}4$ | Colline | Colline |
| $T < 0{,}25$ | Toundra | Plaine froide |
| $m < 0{,}2$ | Désert (chaud) ou steppe (froid) | Désert, steppe |
| $m < 0{,}45$ | Savane (chaud), prairie ou plaine | Plaine, prairie |
| $m < 0{,}7$ | Forêt tropicale, forêt tempérée, taïga | Forêt |
| $m \ge 0{,}7$ | Marais (si très bas), jungle ou forêt | Marais, forêt |
| Plaine sèche au bord de l'océan | Côte sableuse | Côte |

Cela ajoute **toundra, glace, steppe, savane, taïga et jungle** aux types de terrain du [chapitre 02](02-carte-exploration.md).

#### 8. Rivières

Chaque hexagone reçoit une pluie proportionnelle à son humidité. Les débits s'accumulent le long des sens d'écoulement : un hexagone dont le débit cumulé dépasse un seuil devient une **rivière**, plus large à mesure que le débit augmente.

$$
Q_i = q_i + \sum_{j \,\in\, \text{amont}(i)} Q_j
\qquad \text{rivière si } Q_i > Q_{\text{seuil}}
$$

C'est un bilan matière sur un réseau de drainage.

#### 9. Ressources

À placer selon le biome et la géologie : silex, pierre et argile partout ; gibier en forêt et en prairie ; poisson sur les côtes et les rivières ; cuivre et étain près des montagnes ; fer, charbon, pétrole et uranium dans des couches plus ou moins profondes (voir [ressources et chaînes](ressources-et-chaines.md)). Les ressources sont toutes générées dès le départ mais restent invisibles tant qu'elles ne sont pas connues. *Pas encore dans le prototype.*

#### 10. Points de départ

Les deux tribus démarrent **loin l'une de l'autre** (décidé), sur des hexagones tempérés, assez humides et pas trop élevés. Les hexagones près d'une rivière ou de la côte sont favorisés. Le second départ est le candidat le plus éloigné du premier, de préférence sur la **même masse terrestre**.

#### 11. Vérifications

- Chaque départ doit avoir, dans son rayon d'action, le minimum vital : eau, bois, silex et gibier.
- Les deux départs doivent être **équitables** (score de terrain proche).
- Si les tribus ne sont pas sur la même masse terrestre (archipel), la navigation doit être accessible tôt (voir questions ouvertes).

## Questions ouvertes

- **Bouclage est-ouest** : la carte fait-elle le tour de la planète, comme dans *Civilization*, ou a-t-elle des bords ?
- **Pôles** : faut-il des calottes glaciaires en haut et en bas pour les types planétaires ?
- **Rivières** : sur les **bords** des hexagones (comme *Civilization VI*) ou **au centre** des hexagones (comme dans le prototype) ?
- **Archipel** : si les tribus démarrent sur des îles différentes, faut-il des radeaux dès la préhistoire ?
- **Équité des départs** : départs symétriques garantis, ou monde réaliste quitte à être inégal ?
- **Paramètres avancés** à exposer au joueur : climat (plus chaud, plus froid), humidité, nombre de continents, relief ?
- **Taille par défaut** : grand ($25\,000$ hexagones) ?
