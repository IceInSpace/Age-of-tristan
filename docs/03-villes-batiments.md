# 03 — Villes, quartiers et bâtiments

## Décidé

### Obtention des villes

Quatre moyens, tous retenus :

- **Fondation** : des colons s'installent sur un territoire exploré. Les colons sont la seule unité civile : il n'y a **pas de villageois ni de mineurs**. Chaque ville exploite les ressources de son **rayon d'action** avec des bâtiments (voir [chapitre 04](04-economie.md)).
- **Conquête** : prise d'une ville ennemie.
- **Absorption** : intégration pacifique d'un peuple neutre.
- **Croissance** : un village grandit en ville, puis en mégalopole.

### Niveaux et rayon d'action

- **Niveaux** : village de niveau 1 à 5, puis ville de niveau 1 à 5, puis **mégalopole**, qui demande une technologie.
- Le **niveau** fixe la **taille maximale** du rayon d'action. Dans cette limite, le rayon grandit aussi avec les **routes**, les **technologies** et la **culture**.
- Une **mégalopole** peut être énorme et **absorber les villes proches**.
- On peut **fonder directement un village ou une ville**, en demandant à d'autres cités de fournir la population (**demande de peuplement**).

### Construction

- Gestion mixte : **écran de ville** et **quartiers**.
- Le joueur **place librement les quartiers** dans la ville.
- Le **visuel de la ville évolue** selon les bâtiments construits.
- Les **agrandissements et évolutions liés à la population sont automatiques** quand les conditions sont réunies.
- Le **terrain** limite les constructions et donne des bonus ou des malus.

### Population

- Rôles : **main-d'œuvre**, **consommation** et **stabilité**.
- **Pas de simulation d'individus** : la population est un ensemble agrégé, géré par simulation.

### Évolution de la gestion

- Au début, la gestion des villes est **assez manuelle**.
- Plus il y a de choses à gérer, plus le joueur fixe seulement les **grandes lignes** (production de matériaux, de nourriture ou d'hommes), et les villes **se développent automatiquement**. Détails au [chapitre 10](10-echelles.md).
- **Futur** : villes et habitations **totalement intégrées** (inspiration *Warhammer 40 000*).

## Propositions (à valider)

### Hiérarchie des agglomérations

Mise à jour selon les niveaux décidés (village 1 à 5, ville 1 à 5, mégalopole). Les populations sont des ordres de grandeur à équilibrer.

| Niveau | Population (ordre de grandeur) | Débloque |
|--------|-------------------------------|----------|
| Campement (préhistoire) | $< 50$ | Huttes, feu |
| Village 1 à 5 | $50$ – $2\,000$ | 1 à 3 quartiers |
| Ville 1 à 5 | $2\,000$ – $10^5$ | 3 à 8 quartiers, remparts, merveille |
| Mégalopole (technologie requise) | $10^5$ – $10^7$ | Quartiers nombreux ; absorbe les villes proches |
| Arcologie (ère de la fusion) | $10^7$ – $10^8$ | Ville verticale autonome : logement, production et nourriture dans une seule structure |
| Cité-ruche (ère impériale) | $> 10^8$ | Mégastructure continentale ; la planète entière peut devenir une seule ville |

### Types de quartiers

- **Résidentiel** : capacité de logement.
- **Agricole** : nourriture.
- **Extraction** : mines, carrières, puits.
- **Industriel** : transformation (chaînes de production).
- **Militaire** : casernes, chantiers navals, spatioports.
- **Scientifique** : recherche.
- **Commercial** : échanges, revenus.
- **Culturel et religieux** : stabilité, merveilles.

### Croissance de la population

Croissance logistique, plafonnée par une capacité d'accueil $K$ :

$$
\frac{dP}{dt} = r \, P \left(1 - \frac{P}{K}\right)
\qquad\text{avec}\qquad
K = \min\left(K_{\text{logement}},\; \frac{\dot{N}_{\text{nourriture}}}{c_{\text{nour}}}\right)
$$

avec $r$ le taux de croissance, $K_{\text{logement}}$ la capacité des quartiers résidentiels, $\dot{N}_{\text{nourriture}}$ le débit de nourriture disponible et $c_{\text{nour}}$ la consommation par habitant.

### Stabilité

Indice $S \in [0 \,;\, 100]$, somme pondérée de facteurs :

$$
S = S_0 + \sum_i w_i \, f_i
$$

Facteurs $f_i$ possibles : nourriture, culture, garnison, guerre en cours, retard d'ère, espionnage ennemi. En dessous d'un seuil $S_{\text{révolte}}$, la production baisse, puis la ville peut se révolter.

## Questions ouvertes

- Nombre maximal de quartiers : fixé par le niveau, par le terrain, ou les deux ?
- Un bâtiment peut-il être détruit lors d'une attaque ou d'un sabotage ?
- La capitale peut-elle être déplacée ? Que se passe-t-il si elle est prise ?
- Les villes conquises gardent-elles leur ère, ou s'alignent-elles sur celle du conquérant ?
