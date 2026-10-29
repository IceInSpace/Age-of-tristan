# 07 — Batailles et fronts

## Décidé

- **Fronts** de bataille séparés de l'**arrière** (gestion, production, formation).
- Les unités sont **envoyées vers des points de la carte**.
- On peut **faire tenir des fronts** ; le comportement des unités dépend de leurs points de vie et de leurs caractéristiques.
- **Mode de bataille au choix** : résolution automatique, ou contrôle direct des unités pour faire de la stratégie.
- **Temps réel pausable**.
- **Sièges** : **encerclement** (on affame la ville, lent et peu coûteux) ou **assaut** (rapide et coûteux), au choix.
- **Guerre de tranchées** : avec mitrailleuses et artillerie (ère électrique), le front **se fige**. Gaz, chars et tactiques d'infiltration permettent de le débloquer.
- **Aviation à rayon d'action** : les avions partent d'un aérodrome, frappent dans un rayon, puis reviennent.
- **Ligne de front** dessinée entre les zones contrôlées, qui avance ou recule.
- **Armées** : plusieurs unités sur la **même case** forment une armée. Plusieurs armées peuvent avancer **côte à côte** : quand l'une engage le combat, une autre peut venir **en renfort** ou **prendre l'ennemi à revers**.
- **Formations** choisies par le joueur ; la résolution automatique tient compte de l'**ordre et de la disposition** des unités.
- **Bataille automatique dans la durée** : elle n'est pas instantanée, ce qui laisse le temps de contourner, d'envoyer des renforts ou de bombarder.
- **Batailles tactiques** (contrôle direct) : **plus tard**, pas dans la première version.
- **Ravitaillement** : les fronts sont approvisionnés par la logistique automatique, avec priorités à partir de l'intendance militaire (voir [chapitre 04](04-economie.md)).

## Propositions (à valider)

### Ordres de front

| Ordre | Comportement |
|-------|--------------|
| Avancer | Progression vers l'objectif, combat au contact |
| Tenir | Maintien de la ligne, retraite sous un seuil de PV |
| Tenir à tout prix | Aucune retraite |
| Harceler | Attaques à distance, repli dès que l'ennemi approche |
| Retraite | Repli vers l'arrière ou la ville la plus proche |

### Résolution automatique

Pour ne pas simuler chaque unité quand le joueur ne regarde pas, une résolution agrégée de type **lois de Lanchester** est possible. Avec $N_1$ et $N_2$ les effectifs, et $\alpha_{12}$, $\alpha_{21}$ les efficacités de tir (qui intègrent attaque, contres et ère) :

$$
\frac{dN_1}{dt} = -\alpha_{21}\, N_2
\qquad
\frac{dN_2}{dt} = -\alpha_{12}\, N_1
$$

Loi « carrée » : le camp 1 l'emporte si

$$
\alpha_{12}\, N_1^2 > \alpha_{21}\, N_2^2
$$

Cela traduit le fait que la supériorité numérique compte davantage pour les combats à distance. Pour la mêlée des premières ères, une loi « linéaire » est plus adaptée :

$$
\frac{dN_1}{dt} = -\alpha_{21}\, N_1 N_2
\qquad
\frac{dN_2}{dt} = -\alpha_{12}\, N_1 N_2
$$

dont la grandeur conservée est $\alpha_{12} N_1 - \alpha_{21} N_2$ : l'avantage du nombre n'y est plus que proportionnel.

### Résolution automatique dans la durée (proposition)

La bataille se déroule par pas de temps $\Delta t$ (par exemple une seconde de jeu). À chaque pas :

1. Seuls les **rangs engagés** combattent, selon la formation : la première ligne d'abord, les unités à distance derrière elle, la cavalerie sur les ailes.
2. Les dégâts suivent la formule du [chapitre 06](06-unites.md), avec le multiplicateur de flanc selon le côté de l'hexagone par lequel arrive l'attaquant.
3. Le moral baisse avec les pertes ; une unité dont le moral tombe sous un seuil recule ou fuit.
4. Toute armée qui arrive sur une case voisine **rejoint** la bataille, du côté où elle se trouve.

Sur une grille hexagonale, une armée fait face à l'un des six côtés :

| Côté d'arrivée | Multiplicateur $f_{\text{flanc}}$ |
|----------------|-------------------------------|
| Face (1 côté) | $1$ |
| Avant-flanc (2 côtés) | $1{,}25$ |
| Arrière-flanc (2 côtés) | $1{,}5$ |
| Dos (1 côté) | $2$ |

Prendre une armée à revers pendant qu'elle est engagée de face devient ainsi décisif, comme dans les *Total War*. Le joueur peut suivre la bataille, mettre en pause, envoyer des renforts ou un bombardement.

### Bataille tactique

- Déclenchée quand deux armées se rencontrent, si le joueur choisit de la mener.
- Se déroule sur une portion de carte reprenant le terrain réel (collines, rivières, forêts).
- Le résultat se répercute sur la carte stratégique.

### Sièges

- Une ville fortifiée ne se prend pas d'assaut directement : il faut des **unités de siège** ou un **encerclement** (réduction progressive du ravitaillement).

## Questions ouvertes

- Le temps s'arrête-t-il sur le reste de la carte pendant une bataille tactique ?
- Combien de formations proposer (ligne, colonne, carré, coin…), et à partir de quelle ère ?
- Nombre maximal d'unités par case ou par armée ?
