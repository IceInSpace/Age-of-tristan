# 13 — Diplomatie, IA et adversaires

## Décidé

- **Adversaires** : une ou plusieurs IA, plus des **peuples neutres** qu'on peut **absorber** dans sa civilisation.
- **Multijoueur** : éventuel, plus tard.
- **Diplomatie avancée** : alliances, commerce, traités, échanges de technologies.
- **Conditions de victoire** : plusieurs options à choisir au début de la partie.
- **Guerre de la planète natale** : gagnée par **unification** ou par **domination**. Elle peut se prolonger pendant toute la conquête du système solaire, et doit être gagnée pour entrer dans l'acte III (voir [chapitre 11](11-hyperspatial.md)).
- **Acte III** : **nouvel ennemi** (nature à préciser).

## Propositions (à valider)

### Relations diplomatiques

Score de relation $R \in [-100 \,;\, 100]$ entre deux factions :

| Plage | État |
|-------|------|
| $R < -50$ | Hostile : guerre probable |
| $-50 \le R < 0$ | Méfiant |
| $0 \le R < 50$ | Neutre : commerce possible |
| $R \ge 50$ | Amical : alliance possible |

Le score évolue avec le commerce, les traités respectés ou rompus, l'espionnage découvert, les frontières partagées et les écarts d'ère.

### Traités possibles

- Paix, trêve, pacte de non-agression.
- Alliance défensive ou offensive.
- Accord commercial (échange régulier de ressources).
- Échange de technologies.
- Droit de passage.
- Vassalisation.

### Absorption des peuples neutres

Un peuple neutre rejoint la civilisation quand son affinité dépasse un seuil :

$$
\text{Affinité} = w_c \cdot \text{culture} + w_m \cdot \text{commerce} + w_p \cdot \text{proximité} - w_g \cdot \text{guerres récentes}
$$

### Unification ou domination de la planète natale

| Voie | Moyen | Conséquence proposée pour l'acte III |
|------|-------|--------------------------------------|
| **Unification** | Diplomatie, absorption, alliances, fédération | Stabilité élevée, bonus de science et de culture, factions intégrées avec leurs spécialités |
| **Domination** | Conquête militaire | Bonus militaires et industriels, mais régions instables et risque de rébellions |

### Conditions de victoire (à choisir au lancement)

Chaque condition peut s'appliquer à la fin d'un acte, ce qui permet des parties courtes :

| Condition | Fin à l'acte I ou II | Fin à l'acte III |
|-----------|----------------------|------------------|
| Domination | Toutes les factions de la planète natale soumises | Nouvel ennemi vaincu |
| Unification | Planète natale unifiée pacifiquement | Alliance galactique dirigée par le joueur |
| Scientifique | Premier à l'ère hyperspatiale | Dernière technologie de l'arbre stellaire |
| Expansion | Tout le système solaire colonisé | $X\ \%$ des systèmes de la galaxie contrôlés |
| Bac à sable | Aucune fin | Aucune fin |

### Comportement de l'IA

- Plusieurs **personnalités** : conquérante, bâtisseuse, commerçante, scientifique.
- Plusieurs **niveaux de difficulté**, qui jouent sur la qualité des décisions plutôt que sur des bonus de ressources (à trancher).

## Questions ouvertes

- Nombre de factions IA par partie : réglable ?
- Les factions ont-elles des identités différentes (bonus, unités uniques) ?
- L'IA « triche »-t-elle aux niveaux élevés (bonus de ressources, vision), ou joue-t-elle à armes égales ?
- Multijoueur : un objectif réel à garder en tête dès l'architecture, ou une idée lointaine ?
