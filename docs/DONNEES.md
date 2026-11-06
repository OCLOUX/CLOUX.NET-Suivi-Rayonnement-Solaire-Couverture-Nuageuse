# Données, API et limites — 3.1.11

## Fournisseur

Open-Meteo est appelé côté serveur avec les fonctions HTTP WordPress. Les villes sont résolues par son géocodage ; les coordonnées saisies sont validées séparément.

Endpoint : https://api.open-meteo.com/v1/forecast

Documentation : https://open-meteo.com/en/docs

Paramètres : `models=best_match`, `timezone=auto`, coordonnées et dates de début/fin.

| Groupe | Variables demandées |
|---|---|
| hourly | cloud_cover, shortwave_radiation, diffuse_radiation_instant |
| daily | sunrise, sunset, daylight_duration, sunshine_duration, shortwave_radiation_sum |
| current | is_day |

## Graphiques et conventions

1. `shortwave_radiation` : rayonnement global horizontal, composantes directe sur l’horizontale et diffuse ; W/m², moyenne sur l’heure précédente.
2. `diffuse_radiation_instant` : rayonnement diffus instantané à l’heure indiquée ; W/m². La convention temporelle diffère du global horaire.
3. `cloud_cover` : couverture nuageuse ; %.
4. `shortwave_radiation_sum` : énergie solaire globale quotidienne sur une surface horizontale ; MJ/m².

Les trois premières séries sont des courbes horaires. La quatrième est un histogramme avec une valeur par jour, sans interpolation horaire : jour précédent, jour sélectionné et jour suivant, indépendamment des filtres horaires. Les dates futures sont signalées comme prévisionnelles. Une valeur absente reste indisponible, sans conversion en zéro.

Le cumul quotidien figure aussi dans les cartes. Le tableau horaire affiche les nuages et les deux rayonnements. Les durées sont reçues en secondes puis formatées.

La 3.1.11 supprime uniquement un texte de présentation par rapport à la 3.1.10 ; aucune variable ni aucun graphique n’est retiré. Les explications techniques restent disponibles dans cette documentation.

## Fuseaux et disponibilité

Les graphiques utilisent le fuseau météo reçu. Les bornes du calendrier utilisent la date WordPress : vérifier son fuseau si la localisation est distante. La sélection J−92 à aujourd’hui ne garantit pas la disponibilité de chaque variable. Le code signale les erreurs HTTP, réponses invalides et absences de données exploitables.

## Cache

Cache météo par coordonnées et fenêtre de dates : préfixe `omw_319_`, conservé en 3.1.11. Cache initial configurable via `cache`, minimum une minute ; route REST : 15 minutes ; géocodage : 24 heures. Ces caches sont distincts des caches de page, navigateur et CDN.

## Limites photovoltaïques

Les données sont modélisées et non mesurées localement. W/m² désigne une puissance par surface ; MJ/m² une énergie par surface. Ce ne sont pas des valeurs de production électrique. Aucun calcul de panneau incliné, pertes électriques, énergie stockée, recharge ou autonomie n’est inclus. Le composant batterie/tension MeshCore et son iframe sont distincts.
