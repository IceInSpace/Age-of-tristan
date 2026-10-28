# 12 — Espionnage

## Décidé

- Quatre familles d'actions, toutes retenues :
  - **Renseignement** : révéler la carte, les armées, les technologies adverses.
  - **Sabotage** : endommager bâtiments, production, routes.
  - **Vol de technologie** : récupérer une recherche adverse.
  - **Déstabilisation** : baisser la stabilité, provoquer des révoltes.
- L'espionnage existe **avant les satellites**, et les satellites l'étendent à l'ère moderne.

## Propositions (à valider)

### Moyens d'espionnage par ère

| Ère | Moyen | Portée |
|-----|-------|--------|
| Préhistoire – bronze | Éclaireur | Zone proche, visuel seulement |
| Antiquité – Moyen Âge | Espion, marchand infiltré | Une ville |
| Grandes découvertes – électrique | Réseau d'agents, interception de courrier puis de télégrammes | Plusieurs villes |
| Atomique – moderne | Agence de renseignement, avion espion, **satellite** | Région, puis continent |
| Révolution IA | Cyberespionnage, drones | Global, actions à distance |
| Spatial – futur | Sondes, brouillage | Interplanétaire |

### Réussite d'une mission

Probabilité de succès, fonction de la compétence de l'espion $E$ et du contre-espionnage adverse $C$ :

$$
P_{\text{succès}} = \frac{E}{E + C} \cdot \delta_{\text{mission}}
$$

avec $\delta_{\text{mission}} \le 1$ un facteur de difficulté (renseignement facile, vol de technologie difficile). En cas d'échec, une probabilité de **découverte** dégrade les relations diplomatiques.

### Contre-espionnage

- Bâtiments dédiés (poste de garde, puis agence).
- Satellites de surveillance qui détectent les mouvements.
- Désinformation : afficher de fausses informations à l'adversaire.

## Questions ouvertes

- Les espions sont-ils des unités visibles sur la carte, ou des missions lancées depuis un menu ?
- Assassinat de dirigeants ou de généraux : inclus ou exclu ?
- L'IA adverse espionne-t-elle aussi le joueur, et comment le joueur s'en aperçoit-il ?
