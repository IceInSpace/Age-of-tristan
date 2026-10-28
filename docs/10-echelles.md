# 10 — Changements d'échelle et gestion automatisée

Principe central du jeu : plus l'empire grandit, plus le joueur gère de haut, et plus la simulation devient **large et agrégée**. On peut toujours redescendre voir le détail.

## Décidé

- Au début, la gestion des villes est **assez manuelle**.
- Plus il y a de choses à gérer, plus le joueur choisit seulement les **grandes lignes** : production de **matériaux**, de **nourriture** ou d'**hommes**. Les villes sont alors **générées et développées automatiquement**.
- Le changement d'échelle doit rendre la gestion **plus facile** et permettre une **simulation plus large et moins détaillée**, donc moins coûteuse.
- En **zoomant sur une planète**, on voit ses **routes**, ses **villes développées** et sa **pollution**, avec possibilité de **terraformation**.
- À l'échelle des systèmes (acte III), on envoie des **modules** qui créent des villes automatiquement, et le joueur **choisit le type de quartier** de chaque planète (voir [chapitre 11](11-hyperspatial.md)).

## Propositions (à valider)

### Quatre niveaux de gestion

| Niveau | Période | Le joueur décide | Ce qui est automatique | Granularité de la simulation |
|--------|---------|------------------|------------------------|-------------------|
| **N1 — Ville** | Ères 1 à 8 | Placement des quartiers, bâtiments, recettes | Croissance de la population | Bâtiment |
| **N2 — Région** | Ères 9 à 14 | **Directives** par région (matériaux, nourriture, hommes…) | Fondation des villages, choix des quartiers, routes | Ville |
| **N3 — Planète** | Acte II | Type de quartiers **planétaires**, directives par planète | Développement des villes de la planète | Planète |
| **N4 — Système** | Acte III | Spécialisation des planètes, routes, flottes | Colonisation via modules, logistique | Planète (système si non observé) |

Le passage d'un niveau à l'autre pourrait être **proposé** au joueur (par exemple au-delà de $N_{\text{villes}} > 8$), sans être imposé. À tout moment, le joueur peut **reprendre la main** sur une ville ou une planète précise.

### Directives : les « grandes lignes »

Le joueur répartit des priorités, par exemple avec des curseurs, sur un vecteur :

$$
\mathbf{w} = \left(w_{\text{mat}},\; w_{\text{nour}},\; w_{\text{hom}},\; w_{\text{sci}},\; w_{\text{mil}}\right)
\qquad
\sum_j w_j = 1
$$

Quand une ville doit construire un nouveau quartier, l'automate choisit le type $j$ avec une probabilité proportionnelle à la priorité et à l'adéquation du terrain $a_{c,j}$ :

$$
P(j \mid c) = \frac{w_j \, a_{c,j}}{\sum_{k} w_k \, a_{c,k}}
$$

Une ville en plaine fertile produira ainsi naturellement plus de nourriture qu'une ville de montagne, à directives égales.

### Génération automatique des villes

Quand la population d'une région dépasse sa capacité, un nouveau village apparaît sur le meilleur site disponible :

$$
\text{score}(x) = \sum_r \rho_r(x) \cdot w_{r} + \lambda_{\text{route}} \, e^{-d_{\text{route}}(x)/L} - \lambda_{\text{ville}} \, e^{-d_{\text{ville}}(x)/L}
$$

avec $\rho_r(x)$ la richesse locale en ressource $r$, $d_{\text{route}}$ la distance à la route la plus proche, $d_{\text{ville}}$ la distance à la ville la plus proche (pour éviter l'entassement) et $L$ une distance caractéristique. Une route est ensuite tracée automatiquement vers le réseau existant.

### Simulation agrégée

Au niveau N3, la production d'une planète pour le produit $j$ se résume à :

$$
\dot{Y}_j^{\text{planète}} = n_j \cdot y_j \cdot \left(1 + \beta_j\right) \cdot \varphi(S) \cdot \eta(\Pi)
$$

avec $n_j$ le nombre de quartiers de type $j$, $y_j$ le rendement unitaire d'un quartier (fixé par l'ère et les technologies), $\beta_j$ les bonus de la planète, $\varphi(S)$ la stabilité et $\eta(\Pi)$ la pénalité de pollution.

C'est la même logique que le passage d'un modèle détaillé à un **modèle de boîte noire** en génie des procédés : on ne garde que les relations entrée-sortie.

### Le zoom : « dessiner plus, pas simuler plus »

En zoomant, la simulation ne devient pas plus fine. On **génère l'image** de la planète ou de la ville à partir de son état agrégé (population, quartiers, routes, pollution, ère) et d'une **graine** fixe. La même planète a donc toujours la même apparence tant que son état ne change pas.

```
État agrégé (population, quartiers, Π, ère)  ──┐
                                              ├──► Générateur procédural ──► Vue détaillée (routes, villes, fumées)
Graine de la planète ─────────────────────────┘
```

Avantage : des centaines de planètes peuvent être simulées sans coût, et seule celle que l'on regarde est dessinée en détail.

## Questions ouvertes

- Le passage de niveau est-il **imposé par l'ère**, **proposé selon la taille de l'empire**, ou entièrement **au choix** ?
- En vue zoomée à l'acte III, peut-on encore **modifier** une ville à la main, ou seulement l'observer ?
- Quelles directives proposer exactement ? « Matériaux, nourriture, hommes » ont été cités ; faut-il ajouter science, armée, culture ?
- Les villes générées automatiquement peuvent-elles être **déplacées ou supprimées** par le joueur ?
