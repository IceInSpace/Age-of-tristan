# 09 — Naval et spatial

## Décidé

### Naval

- La **navigation** débloque l'**exploration outre-mer**, avec une progression de l'exploration.
- Les navires sont organisés en **classes**, comme dans les batailles navales historiques (torpilleurs, cuirassés…).

### Spatial

- Débute à l'**ère moderne** : satellites, essais de fusées.
- Aboutit aux **vaisseaux spatiaux** à l'ère du futur.
- **Espionnage par satellite**.
- **Frappes au sol** depuis l'espace.
- **Autres planètes** accessibles.
- **Batailles de flottes** avec positionnement en 2D, **tirs de barrage** et classes de vaisseaux.
- **Acte II — système solaire** : conquête des lunes et planètes du système d'origine. La guerre contre les rivaux de la planète natale **peut continuer** pendant toute cette phase.
- **Routes spatiales** à l'intérieur d'un système et **routes hyperspatiales** entre systèmes (acte III, voir [chapitre 11](11-hyperspatial.md)).
- **Satellites, radars et missiles** intégrés à la défense planétaire (voir [chapitre 08](08-guerre-moderne.md)).

## Propositions (à valider)

### Classes navales (par grandes périodes)

| Période | Classes |
|---------|---------|
| Antiquité – Moyen Âge | Pirogue, galère, trirème, cogue |
| Grandes découvertes – poudre | Caravelle, galion, vaisseau de ligne, frégate |
| Industriel – électrique | Cuirassé, croiseur, torpilleur, sous-marin |
| Atomique – moderne | Porte-avions, destroyer, sous-marin nucléaire |

### Classes spatiales

Transposition des classes navales :

| Classe | Rôle | Équivalent naval |
|--------|------|------------------|
| Chasseur | Interception, escorte | Aviation embarquée |
| Corvette torpilleuse | Frappe rapide contre gros vaisseaux | Torpilleur |
| Frégate | Écran, défense antichasseurs | Destroyer |
| Croiseur | Polyvalent | Croiseur |
| Cuirassé | Puissance de feu et blindage, barrages longue portée | Cuirassé |
| Porte-vaisseaux | Transporte et lance des chasseurs | Porte-avions |
| Transport | Troupes et colons vers d'autres planètes | Transport de troupes |

### Tir de barrage

Un tir de barrage vise une **zone** plutôt qu'une cible. Probabilité qu'un vaisseau situé dans la zone de surface $S_{\text{zone}}$ soit touché par $n$ projectiles de surface utile $s$ :

$$
P_{\text{touché}} = 1 - \left(1 - \frac{s}{S_{\text{zone}}}\right)^{n}
$$

Les petits vaisseaux rapides (faible $s$, capables de sortir de la zone) sont ainsi avantagés contre les barrages, et désavantagés contre les tirs ajustés.

### Couches orbitales

```
Espace profond   ─ autres planètes, flottes
Orbite haute     ─ stations, chantiers spatiaux
Orbite basse     ─ satellites espions, armes orbitales
Atmosphère       ─ aviation
Surface          ─ carte principale
```

### Acte II : déroulé proposé de la conquête du système

1. **Ère moderne** : satellites d'observation et d'alerte, premiers essais de fusées, sondes vers les planètes voisines (elles révèlent leurs ressources).
2. **Révolution de l'IA** : sondes robotisées, premières installations automatiques sur la lune principale.
3. **Ère spatiale** : stations orbitales, bases lunaires, minage d'astéroïdes, premières colonies, chantiers spatiaux.
4. **Ère de la fusion** : propulsion à fusion (trajets interplanétaires courts), terraformation, flottes de guerre, conquête des planètes rivales.

Les rivaux de la planète natale peuvent eux aussi coloniser des planètes du système. La course à l'espace est un nouveau front de la même guerre.

## Questions ouvertes

- Les autres planètes sont-elles générées comme la planète principale (villes, ressources, peuples) ou plus simples (bases, gisements) ?
- Peut-il y avoir de la vie ou des civilisations extraterrestres ?
- Les batailles spatiales se déroulent-elles sur la même carte isométrique, ou sur un écran 2D dédié ?
- Les satellites peuvent-ils être détruits (armes antisatellites, débris) ?
