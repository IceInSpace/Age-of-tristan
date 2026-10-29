# Ressources et chaînes de production (acte I)

Inventaire des ressources de l'acte I, classées par gamme, avec leurs chaînes de transformation. **Statut : le total de 78 ressources est validé** ; le détail de chaque gamme peut encore être ajusté. Les règles générales (recettes, débits, péremption, logistique) sont au [chapitre 04](04-economie.md).

## Récapitulatif

| Gamme | Brutes | Transformées | Total | Ères principales |
|-------|--------|--------------|-------|------------------|
| Vivres | 6 | 5 | 11 | 1 à 9 |
| Matériaux de construction | 6 | 6 | 12 | 1 à 11 |
| Métaux | 5 | 6 | 11 | 2 à 11 |
| Énergie et carburants | 4 | 7 | 11 | 4 à 12 |
| Chimie | 3 | 7 | 10 | 8 à 14 |
| Textiles et biens de moral | 5 | 4 | 9 | 2 à 9 |
| Équipement militaire | — | 7 | 7 | 1 à 14 |
| Matériaux avancés | 4 | 3 | 7 | 13 et 14 |
| **Total** | **33** | **45** | **78** | |

S'y ajoutent les ressources **immatérielles** : science (militaire, civile, industrielle), culture, **tourisme** (produit par le patrimoine, voir [chapitre 03](03-villes-batiments.md)), influence, XP et monnaie (à partir de l'âge du fer).

Le total n'est jamais visible d'un coup : une ressource n'apparaît qu'à son ère, et certaines deviennent secondaires ensuite. À une ère donnée, le joueur manipule plutôt **15 à 30 ressources**.

## 1. Vivres (11)

**Brutes** : gibier, poisson, fruits et baies, céréales, bétail, sel.
**Transformées** : viande, farine, pain, salaison, conserves.

```
Gibier ───┐
Bétail ───┴──► Viande ──(+ Sel)──► Salaison          (conservation longue)
Céréales ──► Moulin ──► Farine ──► Boulangerie ──► Pain
Poisson ──(+ Sel)──► Poisson salé (compté comme salaison)
Viande, légumes + Fer blanc ──► Conserverie ──► Conserves   (ère industrielle)
```

Rôle des transformations : réduire la péremption $\lambda$ (voir [chapitre 04](04-economie.md)).

## 2. Matériaux de construction (12)

**Brutes** : bois, pierre, argile, silex, calcaire, sable.
**Transformées** : planches, briques et tuiles, poteries, chaux, ciment et béton, verre.

```
Bois ──► Scierie ──► Planches
Argile ──► Four ──► Briques, tuiles, poteries
Calcaire ──► Four à chaux ──► Chaux ──(+ argile)──► Ciment ──(+ sable, graviers)──► Béton
Sable ──(+ soude, chaux)──► Verrerie ──► Verre
Silex ──► Atelier de taille ──► outils et armes (préhistoire)
```

La pierre et l'argile existent en **quantités énormes** (décidé). Une partie de la pierre peut venir des **couches stériles** des mines (voir plus bas).

## 3. Métaux (11)

**Brutes** : minerai de cuivre, minerai d'étain, minerai de fer, métaux précieux (or, argent), bauxite.
**Transformées** : bronze, fer, fonte, acier, aluminium, monnaie.

```
Cuivre + Étain ──► Fonderie ──► Bronze
Minerai de fer + Charbon de bois ──► Bas fourneau ──► Fer        (âge du fer)
Minerai de fer + Coke ──► Haut fourneau ──► Fonte ──► Convertisseur ──► Acier   (industriel)
Bauxite ──► Alumine ──(+ beaucoup d'électricité)──► Aluminium        (ère du pétrole)
Métaux précieux ──► Atelier monétaire ──► Monnaie        (âge du fer)
```

## 4. Énergie et carburants (11)

**Brutes** : charbon, pétrole brut, gaz naturel, uranium.
**Transformées** : charbon de bois, coke, essence, gazole et fioul, kérosène, uranium enrichi, électricité.

```
Bois ──► Charbonnière ──► Charbon de bois
Charbon ──► Cokerie ──► Coke
Pétrole brut ──► Raffinerie ──► Essence, Gazole/fioul, Kérosène, Naphta (vers la chimie)
Charbon ──► Liquéfaction ──► Carburant de synthèse (substitut, coûteux)
Uranium ──► Enrichissement ──► Uranium enrichi ──► Centrale ou arme
Charbon, gaz, fioul, uranium enrichi, eau (barrage) ──► Centrale ──► Électricité
```

## 5. Chimie (10)

**Brutes** : soufre, salpêtre, caoutchouc naturel.
**Transformées** : poudre noire, soude, ammoniac, acide nitrique, explosifs, engrais, plastiques.

```
Salpêtre + Soufre + Charbon de bois ──► Poudrerie ──► Poudre noire (75:15:10)
Sel + Calcaire ──► Soudière Solvay ──► Soude (verre, savon)
Air (N₂) + Hydrogène ──► Synthèse ──► Ammoniac ──► Oxydation ──► Acide nitrique
Acide nitrique ──► Explosifs        Ammoniac ──► Engrais (bonus agricole)
Naphta ──► Pétrochimie ──► Plastiques, caoutchouc synthétique
Plastiques usagés ──► Pyrolyse ──► Huile (retour vers la raffinerie)
```

## 6. Textiles et biens de moral (9)

**Brutes** : laine, fibres végétales (lin, coton), vigne, épices, sucre.
**Transformées** : tissus, vêtements, cuir, alcool (vin, bière, spiritueux).

```
Laine, Fibres ──► Filature ──► Tissus ──► Atelier ──► Vêtements   (stabilité)
Bétail ──► Tannerie ──► Cuir   (armures, équipement)
Vigne, Céréales, Sucre ──► Brasserie, Distillerie ──► Alcool   (moral des troupes, stabilité)
Épices, Sucre ──► consommés directement (stabilité, commerce)
```

L'**alcool** sert à l'entretien du **moral** des armées (décidé, voir [chapitre 06](06-unites.md)).

## 7. Équipement militaire (7)

**Transformées uniquement** : armes, armures, munitions, artillerie, véhicules, aéronefs, navires.

Chaque type change de recette selon l'ère. Par exemple, les **armes** sont en silex, puis en bronze, en fer, en acier ; les **munitions** sont des flèches, puis des balles, des obus, des missiles.

## 8. Matériaux avancés (7)

**Brutes** : silicium, terres rares, lithium, titane.
**Transformées** : puces électroniques, batteries, composites.

```
Silicium ──► Fonderie de puces ──► Puces (intrant critique des ères 13 et 14)
Lithium ──► Usine de batteries ──► Batteries (drones, véhicules électriques)
Titane, fibres ──► Composites (aviation, missiles)
Terres rares ──► aimants et électronique (intrant des puces et des moteurs)
```

## Couches géologiques et co-produits (décidé)

- Un gisement de minerai se trouve dans des **couches géologiques**. En l'exploitant, on récupère aussi des **co-produits**, par exemple de la **pierre** issue des couches stériles.
- Ce qui est **en surface** est accessible tout de suite : les technologies y augmentent l'**intensité** et les **débits**.
- Ce qui est **profond** demande une **technologie d'extraction** pour être atteint.

Modèle proposé : pour $1$ tonne de minerai extraite, la mine produit aussi $s$ tonnes de pierre, où $s$ est le **taux de découverture** (rapport stérile/minerai) de la couche :

$$
\dot{X}_{\text{pierre}} = s \cdot \dot{X}_{\text{minerai}}
$$

Plus la couche est profonde, plus $s$ est élevé : l'exploitation devient plus coûteuse, mais fournit beaucoup de matériaux de construction.

## Transport : caravanes, cargos, tankers (décidé)

On peut **acheter des véhicules de transport** (caravanes marchandes, puis bateaux cargos, puis tankers…) pour **augmenter le débit** d'une route. Débit maximal d'une liaison de longueur $d$, avec $n$ véhicules de charge utile $c_v$ roulant à la vitesse $v$ (aller-retour) :

$$
Q_{ab}^{\max} = \min\!\left(Q_{\text{route}},\; \frac{n\, c_v\, v}{2\, d}\right)
$$

Le débit est donc limité soit par l'**infrastructure** (niveau de route, port), soit par le **nombre de véhicules**. Acheter des véhicules ne sert à rien sur une route saturée, et inversement.
