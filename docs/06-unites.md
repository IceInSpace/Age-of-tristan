# 06 — Unités

## Décidé

- **Améliorables** : on paie pour moderniser une unité existante.
- **Vétérans** : les unités gagnent de l'expérience et des bonus en combattant.
- **Système de contres** : chaque type d'unité est fort contre certains et faible contre d'autres.
- Le comportement sur le front dépend des **points de vie** et des **caractéristiques** de l'unité.
- Unités navales et spatiales organisées par classes (torpilleurs, cuirassés…) : voir [chapitre 08](08-naval-spatial.md).

## Propositions (à valider)

### Caractéristiques d'une unité

| Caractéristique | Symbole | Rôle |
|-----------------|---------|------|
| Points de vie | $PV$ | Résistance |
| Attaque | $A$ | Dégâts infligés |
| Armure | $Ar$ | Réduction des dégâts |
| Portée | $p$ | Distance d'attaque |
| Vitesse | $v$ | Déplacement |
| Cadence | $f$ | Attaques par seconde |
| Moral | $m$ | Seuil de retraite |
| Type | $t$ | Classe pour les contres |
| Ère | $n$ | Époque d'origine |

### Grands types et contres (terrestre)

```
Infanterie ──bat──► Distance ──bat──► Cavalerie / Blindés ──bat──► Infanterie
        Antiaérien ──bat──► Aérien ──bat──► Blindés / Bâtiments
                Siège / Artillerie ──bat──► Bâtiments et fortifications
```

### Formule de dégâts

$$
D = A \cdot M\!\left(t_{\text{att}},\, t_{\text{déf}}\right) \cdot \frac{100}{100 + Ar} \cdot \left(1 + 0{,}1\,v_{\text{rang}}\right) \cdot \gamma\!\left(\Delta n\right)
$$

avec :

- $M$ le multiplicateur de contre (par exemple $1{,}5$ si avantage, $0{,}67$ si désavantage, $1$ sinon) ;
- $v_{\text{rang}}$ le rang de vétéran ($0$ à $5$) ;
- $\gamma(\Delta n)$ un facteur d'écart d'ère, avec $\Delta n = n_{\text{att}} - n_{\text{déf}}$. Par exemple $\gamma = 1{,}25^{\,\Delta n}$, pour qu'une unité en retard de deux ères soit nettement dominée sans être totalement inutile.

### Moral et tenue du front

Une unité **tient sa position** tant que :

$$
\frac{PV}{PV_{\max}} > \theta_{\text{retraite}}
\quad\text{et}\quad
m > m_{\min}
$$

Le seuil $\theta_{\text{retraite}}$ dépend de l'ordre donné : « tenir à tout prix » ($\theta = 0$), « tenir » ($\theta = 0{,}3$), « harceler » ($\theta = 0{,}6$).

### Vétérance

Gain d'XP par unité ennemie détruite, proportionnel à sa valeur :

$$
XP_{\text{unité}} \mathrel{+}= \lambda \cdot \text{coût}_{\text{ennemi}}
$$

Un rang de vétéran est atteint à chaque palier d'XP ; chaque rang apporte environ $+10\,\%$ d'efficacité.

## Questions ouvertes

- Combien d'unités par ère (3–4 comme *Age of War*, ou davantage) ?
- Unités individuelles ou **escouades** (groupes affichés comme une seule unité) ?
- Héros ou généraux avec capacités spéciales ?
- Limite de population militaire (entretien en nourriture ou en ressources) ?
- Une unité améliorée garde-t-elle son rang de vétéran ?
