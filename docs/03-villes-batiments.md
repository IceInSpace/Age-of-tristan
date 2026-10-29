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

### Patrimoine : garder les bâtiments des ères passées (décidé)

L'histoire se construit dans le temps : quand une ville change d'ère, ses anciens bâtiments ne disparaissent pas forcément. Une tour Eiffel ou un château gardés changent simplement de rôle.

- **Quatre options** pour un ancien bâtiment :
  - **moderniser** : il garde sa fonction en version récente (fort → fort Vauban → caserne) ;
  - **conserver** : il reste tel quel ;
  - **reconvertir** : il prend une nouvelle fonction (château → musée, colisée → monument) ;
  - **démolir** : on libère la place.
- Chaque bâtiment peut être traité différemment. Un bâtiment conservé ou reconverti **perd en efficacité mais gagne en culture**. Une ancienne usine, par exemple, **ne produit plus rien**.
- **Bâtiments courants** (maisons, fermes…) : ils ne sont **pas conservés**, ils sont **toujours modernisés** automatiquement.
- **Le patrimoine produit** de la **culture**, du **tourisme** (nouvelle ressource) et de l'**influence**.
- **Entretien** : un bâtiment conservé coûte un entretien. Sans entretien, il tombe en **ruine**. Une ruine garde un peu de valeur et peut être **restaurée**.
- **Au changement d'ère** : les bâtiments courants se modernisent seuls ; seuls les **monuments, forts, châteaux, merveilles** et bâtiments remarquables demandent un choix, présenté dans une même fenêtre.

#### Exemples de trajectoires

| Bâtiment d'origine | Modernisé | Conservé ou reconverti, puis plus tard |
|--------------------|-----------|-----------------------------------------|
| Cercle de pierres (néolithique) | — | Site sacré → site historique |
| Fort (Antiquité, Moyen Âge) | Fort bastionné à la Vauban → caserne | Site historique, musée militaire |
| Château (Moyen Âge) | — | Résidence, mairie → monument, musée |
| Colisée (Antiquité) | — | Arènes → monument → lieu de spectacles |
| Bibliothèque (âge du fer, Antiquité) | Université, archives | Musée, archives nationales |
| Usine (ère industrielle) | Usine moderne | Friche industrielle → lieu culturel, musée de l'industrie |
| Tour de fer monumentale (ère électrique) | — | Monument, symbole de la ville |

#### Modèle proposé

Pour un bâtiment conservé, construit il y a $\Delta n$ ères, l'efficacité de sa fonction d'origine décroît et sa valeur patrimoniale augmente :

$$
\eta(\Delta n) = \eta_0 \cdot \max\!\left(0,\; 1 - a\,\Delta n\right)
\qquad
V(\Delta n) = V_0 \cdot \left(1 + b\,\Delta n\right)
$$

avec par exemple $a = 0{,}4$ (une fonction devient inutile au bout de trois ères) et $b = 0{,}5$. Les merveilles ont un $V_0$ élevé dès leur construction.

Le **tourisme** d'un bâtiment dépend de sa valeur, de l'**accessibilité** de la ville (niveau des routes, gares, aéroports, de $0$ à $1$) et de la stabilité :

$$
T = V \cdot \text{accès} \cdot \varphi(S)
$$

Il rapporte de la **monnaie** et un peu d'influence. Un bâtiment en ruine garde une fraction de sa valeur, par exemple $V_{\text{ruine}} = 0{,}3\, V$, et retrouve sa valeur complète une fois restauré.

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
