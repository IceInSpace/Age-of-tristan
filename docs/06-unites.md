# 06 — Unités

## Décidé

- **Améliorables** : on paie pour moderniser une unité existante.
- **Vétérans** : les unités gagnent de l'expérience et des bonus en combattant.
- **Système de contres** : chaque type d'unité est fort contre certains et faible contre d'autres.
- Le comportement sur le front dépend des **points de vie** et des **caractéristiques** de l'unité.
- Unités navales et spatiales organisées par classes (torpilleurs, cuirassés…) : voir [chapitre 09](09-naval-spatial.md).
- Ères modernes inspirées des **guerres et technologies actuelles** ; missiles, ICBM et défense antimissile détaillés au [chapitre 08](08-guerre-moderne.md).
- Futur inspiré de *Warhammer 40 000*.
- **Clonage d'êtres humains** et **centres robotiques** comme sources d'unités (acte III).
- **Diversité croissante** : peu d'unités dans les premières ères (à la préhistoire, le but est de survivre et de chasser), puis de plus en plus. Exemples : lances, boucliers, fantassins et unités à distance à l'Antiquité ; cavaliers, chevaliers, machines de guerre et navires au Moyen Âge ; avions ensuite. Inspiration : le jeu *War Selection*, riche en unités.
- **Représentation selon l'échelle** : unités individuelles au début, puis escouades, puis divisions et légions (voir [chapitre 10](10-echelles.md)).
- **Généraux** attachés aux armées, avec bonus et expérience (pas de héros uniques).
- **Factions** : mêmes unités pour tous, avec de **petits bonus** de faction.

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

> **Décidé** : une ère d'avance ne doit **pas** valoir victoire automatique. Pistes pour le garantir : plafonner $\gamma$ (par exemple $\gamma \le 2$), donner au défenseur des bonus de terrain et de fortification indépendants de l'ère, et faire dépendre les unités avancées d'un **intrant critique** rare. Une armée moderne privée de carburant ou de munitions redevient vulnérable.

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

### Unités terrestres des ères 11 à 18

| Ère | Infanterie | Blindés et véhicules | Aérien | Soutien |
|-----|-----------|----------------------|--------|---------|
| Pétrole | Fantassin motorisé | Char, automitrailleuse | Chasseur à hélice, bombardier | Artillerie tractée |
| Atomique | Fantassin mécanisé | Char lourd, transport blindé | Chasseur à réaction | Artillerie automotrice |
| Moderne | Infanterie équipée de missiles antichars | Char de combat moderne, véhicule de combat d'infanterie | Chasseur multirôle, hélicoptère d'attaque | Lance-roquettes multiple, défense sol-air |
| Révolution IA | Infanterie + opérateurs de drones | Robots terrestres | **Drones FPV**, drones longue portée, essaims | Guerre électronique (brouillage) |
| Spatiale / fusion | Exosquelettes | Blindés à propulsion électrique | Appareils transatmosphériques | Armes à énergie dirigée |
| Hyperspatiale / impériale | **Clones**, troupes d'élite en armure lourde | Machines de guerre géantes | Vaisseaux de débarquement | Unités robotiques |

### Unités de l'acte III

À cette échelle, on manipule des **régiments** ou des **légions** plutôt que des unités individuelles :

- **Légions de clones** : produites rapidement par les quartiers de clonage, peu chères, moral faible.
- **Légions robotiques** : sans moral (ne battent jamais en retraite), vulnérables à la guerre électronique.
- **Troupes d'élite** : rares, très chères, vétérance rapide.
- **Garnisons planétaires** : fixes, défendent une planète.

## Questions ouvertes

- Les généraux : recrutés, gagnés par la vétérance, ou issus d'événements ? Peuvent-ils mourir au combat ?
- Limite de population militaire (entretien en nourriture ou en ressources) ?
- Une unité améliorée garde-t-elle son rang de vétéran ?
