# 10 — Diplomatie, IA et adversaires

## Décidé

- **Adversaires** : une ou plusieurs IA, plus des **peuples neutres** qu'on peut **absorber** dans sa civilisation.
- **Multijoueur** : éventuel, plus tard.
- **Diplomatie avancée** : alliances, commerce, traités, échanges de technologies.
- **Conditions de victoire** : plusieurs options à choisir au début de la partie.

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

### Conditions de victoire (à choisir au lancement)

- **Domination** : détruire ou soumettre toutes les factions rivales.
- **Conquête planétaire** : contrôler tous les territoires de la planète.
- **Victoire spatiale** : coloniser une autre planète, ou achever un projet final.
- **Victoire scientifique** : atteindre la dernière ère en premier.
- **Victoire culturelle ou diplomatique** : absorber assez de peuples, ou être élu à la tête d'une alliance mondiale.
- **Bac à sable** : aucune fin.

### Comportement de l'IA

- Plusieurs **personnalités** : conquérante, bâtisseuse, commerçante, scientifique.
- Plusieurs **niveaux de difficulté**, qui jouent sur la qualité des décisions plutôt que sur des bonus de ressources (à trancher).

## Questions ouvertes

- Nombre de factions IA par partie : réglable ?
- Les factions ont-elles des identités différentes (bonus, unités uniques) ?
- L'IA « triche »-t-elle aux niveaux élevés (bonus de ressources, vision), ou joue-t-elle à armes égales ?
- Multijoueur : un objectif réel à garder en tête dès l'architecture, ou une idée lointaine ?
