# 08 — Guerre moderne : missiles, dissuasion et défense

Ce chapitre couvre les ères 12 à 14 (atomique, moderne, révolution de l'IA) et prépare le passage à l'espace.

## Décidé

- **Missiles balistiques intercontinentaux (ICBM)**.
- **Système avancé de protection** combinant **radars**, **missiles** et **satellites**.
- Inspiration : **guerres et technologies actuelles**.
- **Frappes nucléaires utilisables**, avec retombées et conséquences durables.
- **Armes chimiques** présentes (dès l'ère du pétrole, à partir de 1915), avec sanctions diplomatiques.
- **Bombardement de civils** possible : villes ciblées, pertes civiles, effet sur la stabilité.
- **Guerre des stocks** : intercepteurs, munitions et carburant sont limités (voir [chapitre 04](04-economie.md)).

## Repères chiffrés tirés de la recherche

Détails et sources dans la [recherche](recherche/technologies-et-armes-par-ere.md), section ères 12 à 14. Les chiffres de guerres en cours sont datés et parfois contestés :

- Arsenaux nucléaires mondiaux : environ $12\,187$ ogives en janvier 2026 (SIPRI), dont $4\,012$ déployées.
- Guerre Iran–Israël de juin 2025 : $525$ missiles balistiques, environ $86\ \%$ interceptés ; plus de $1\,000$ drones, environ $99\ \%$ interceptés.
- Coût d'un intercepteur THAAD : environ 15 millions de dollars, avec $2$ à $3$ intercepteurs par cible selon la doctrine.
- Drones Shahed/Geran contre l'Ukraine en 2025 : $54\,538$ lancés, dont environ $32\,200$ d'attaque (le reste sont des leurres).
- Production ukrainienne de drones : environ $4$ millions par an (Bloomberg, novembre 2025).

**Rapport de coût** entre défense et menace, utile pour l'équilibrage :

$$
R = \frac{n \cdot C_{\text{intercepteur}}}{C_{\text{menace}}}
$$

Quand $R \gg 1$, le défenseur perd la guerre des stocks même s'il intercepte tout. D'après les sources, le seul contre durable a été la **destruction des lanceurs** : les tirs iraniens ont chuté d'environ $90\ \%$ en dix jours en 2026.

## Propositions (à valider)

### Dissuasion nucléaire

- **Triade** : silos terrestres, sous-marins lanceurs d'engins, bombardiers stratégiques. Chaque composante a sa vulnérabilité : les silos sont fixes et connus, les sous-marins sont discrets mais chers, les bombardiers sont lents mais rappelables.
- **Seconde frappe** : tant qu'un adversaire conserve des sous-marins non détectés, une frappe contre lui entraîne une riposte. C'est ce qui rend la dissuasion crédible en jeu.
- **Conséquences d'une frappe** : ville détruite ou dévastée, pollution et retombées durables, effondrement de la stabilité, réaction diplomatique de toutes les factions.

### ICBM : trois phases de vol

| Phase | Description | Défense possible |
|-------|-------------|------------------|
| Propulsion | Le moteur brûle, signature infrarouge forte | Détection par satellite d'alerte ; interception très difficile |
| Médiane (exo-atmosphérique) | Vol balistique dans l'espace, la plus longue | Intercepteurs exo-atmosphériques |
| Rentrée | Les têtes rentrent dans l'atmosphère | Intercepteurs haute altitude, puis terminaux |

Améliorations offensives : **têtes multiples (MIRV)**, **leurres**, **planeurs hypersoniques** manœuvrants, plus difficiles à intercepter.

### Défense multicouche

Modèle inspiré de la défense israélienne, organisée en couches qui traitent chacune une famille de menaces : Iron Dome contre les roquettes de courte portée, David's Sling contre les missiles de courte à longue portée, Arrow 2 contre les missiles de moyenne à longue portée, Arrow 3 contre les missiles longue portée, y compris hors de l'atmosphère ([ministère israélien de la Défense, IMDO](https://english.mod.gov.il/About/Innovative_Strength/Pages/IMDO_Israel_Missile_Defense_Organization.aspx)).

Transposition en jeu :

| Couche | Menaces traitées | Ère |
|--------|------------------|-----|
| 1 — Rapprochée | Obus, roquettes, drones | Moderne |
| 2 — Moyenne | Missiles de croisière, balistiques de courte portée | Moderne |
| 3 — Haute | Balistiques de moyenne et longue portée, en rentrée | Moderne |
| 4 — Exo-atmosphérique | ICBM en phase médiane | Révolution de l'IA |
| 5 — Énergie dirigée | Lasers contre drones et roquettes, coût par tir très faible | Ère spatiale |

### Chaîne de détection

```
Satellite d'alerte ──► Radar longue portée ──► Centre de commandement ──► Batteries d'interception
 (détecte le départ)    (calcule la trajectoire)  (répartit les cibles)       (tirent)
```

Chaque maillon peut être **détruit, brouillé ou saboté**. Sans satellite, l'alerte arrive plus tard ; sans radar, la précision chute. C'est un bon terrain pour l'espionnage (voir [chapitre 12](12-espionnage.md)) et pour la guerre spatiale (voir [chapitre 09](09-naval-spatial.md)).

### Interception et saturation

Une salve de $N_k$ menaces arrive sur la couche $k$. Cette couche peut engager au plus $C_k$ cibles (nombre d'intercepteurs disponibles et cadence), chacune avec une probabilité de destruction $p_k$. Nombre de menaces qui passent à la couche suivante :

$$
N_{k+1} = N_k - p_k \cdot \min\left(N_k,\, C_k\right)
$$

Si l'on tire $s$ intercepteurs par cible, la probabilité de destruction par cible devient :

$$
p_k^{(s)} = 1 - \left(1 - p_k\right)^{s}
$$

Mais la capacité effective tombe alors à $C_k / s$ cibles. On retrouve le dilemme réel : tirer plusieurs intercepteurs par menace augmente la fiabilité, mais vide les stocks plus vite. Une **attaque par saturation** (beaucoup de menaces bon marché, dont des leurres) vise précisément à dépasser $C_k$.

**Coût de l'échange** : comparer le coût d'un intercepteur à celui de la menace abattue. Un drone bon marché qui oblige à tirer un missile coûteux est une victoire économique pour l'attaquant, même s'il est abattu.

### Drones et guerre électronique

Leçons de la guerre en Ukraine :

- Les drones FPV pilotés par radio sont sensibles au **brouillage**.
- Les drones **reliés par fibre optique** y sont insensibles et restent en « silence radio », donc difficiles à détecter. Portées rapportées : $15$ à $20\ \text{km}$ côté ukrainien, jusqu'à $30\ \text{km}$ côté russe. Probabilité de toucher la cible d'environ $50\ \%$ par mission selon un commandant d'unité. Ils représentent moins de $5\ \%$ des drones de cette unité, faute de fournisseurs, pour environ 1 200 dollars l'unité jusqu'à $10\ \text{km}$ ([The War Zone](https://twz.com/news-features/inside-ukraines-fiber-optic-drone-war)).
- Inconvénients : la fibre peut casser, la portée est limitée par la bobine et les câbles abandonnés encombrent le terrain.

Cycle de contres proposé :

```
Brouilleur ──bat──► Drone radio ──bat──► Blindés et artillerie isolés
Drone fibre optique ──ignore──► Brouilleur
Défense rapprochée (canons, lasers) ──bat──► Drones (radio et fibre)
Artillerie et drones ──bat──► Défense rapprochée immobile
```

### Guerre spatiale de première génération

- **Armes antisatellites** : détruire les satellites d'alerte ou d'espionnage adverses.
- **Débris** : chaque satellite détruit pollue l'orbite basse et menace tous les satellites, y compris les siens. C'est l'équivalent spatial de la pollution.

## Questions ouvertes

- Une guerre nucléaire peut-elle faire **régresser d'ère** ? Attention à l'**aléatoire punitif**, à éviter : une régression devrait résulter de choix du joueur, pas du hasard.
- Les stocks d'intercepteurs sont limités (guerre des stocks) : réapprovisionnement automatique depuis les usines, ou commandes manuelles ? Pour éviter la micro-gestion, l'automatique semble préférable.
- Des ICBM à charge conventionnelle (frappes de précision à longue portée) sont-ils souhaités ?
- Niveau de détail des drones : unité à part entière, ou capacité de soutien attachée aux autres unités ?
