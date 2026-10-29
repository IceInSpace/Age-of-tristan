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
- **Ravitaillement** : les fronts sont approvisionnés par la logistique automatique avec priorités (voir [chapitre 04](04-economie.md)).

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

### Bataille tactique

- Déclenchée quand deux armées se rencontrent, si le joueur choisit de la mener.
- Se déroule sur une portion de carte reprenant le terrain réel (collines, rivières, forêts).
- Le résultat se répercute sur la carte stratégique.

### Sièges

- Une ville fortifiée ne se prend pas d'assaut directement : il faut des **unités de siège** ou un **encerclement** (réduction progressive du ravitaillement).

## Questions ouvertes

- Le temps s'arrête-t-il sur le reste de la carte pendant une bataille tactique ?
- Comment représenter visuellement un front : une ligne dessinée, des zones colorées, des positions fortifiées ?
- Les batailles tactiques sont-elles indispensables pour la première version ?
