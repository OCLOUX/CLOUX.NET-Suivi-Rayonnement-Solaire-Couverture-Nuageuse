# Données, API et limites — 3.1.10

## Fournisseur

L’extension appelle Open-Meteo côté serveur avec les fonctions HTTP WordPress. Les noms de ville sont résolus par le géocodage Open-Meteo ; les coordonnées saisies sont validées séparément.

Endpoint météo : https://api.open-meteo.com/v1/forecast

Documentation : https://open-meteo.com/en/docs

Paramètres : `models=best_match`, `timezone=auto`, coordonnées et dates de début/fin.

| Groupe | Variables demandées |
|---|---|
| hourly | cloud_cover, shortwave_radiation, diffuse_radiation_instant |
| daily | sunrise, sunset, daylight_duration, sunshine_duration, shortwave_radiation_sum |
| current | is_day |

## Ordre des graphiques

1. `shortwave_radiation` : rayonnement global horizontal, composantes directe sur l’horizontale et diffuse ; W/m², moyenne sur l’heure précédente.
2. `diffuse_radiation_instant` : rayonnement diffus instantané à l’heure indiquée ; W/m². Sa convention temporelle diffère de celle du global horaire.
3. `cloud_cover` : couverture nuageuse ; %.
4. `shortwave_radiation_sum` : énergie solaire globale quotidienne sur une surface horizontale ; MJ/m².

Les trois premières séries sont des courbes horaires. La quatrième est un histogramme avec une valeur par jour, sans interpolation horaire : jour précédent, jour sélectionné et jour suivant. Il reste indépendant des filtres horaires. Une date future est signalée comme prévisionnelle. Une donnée absente reste indisponible, sans conversion en zéro.

La somme quotidienne est aussi affichée dans les cartes. Le tableau horaire contient les nuages et les deux rayonnements. Les durées de jour et d’ensoleillement sont reçues en secondes puis formatées pour l’affichage.

## Fuseaux et disponibilité

Les graphiques utilisent le fuseau de la réponse météo. Les bornes du calendrier reposent sur la date WordPress : vérifier le fuseau du site si la localisation est distante. La sélection va de J−92 à aujourd’hui ; cette plage ne garantit pas la disponibilité de chaque variable. Les erreurs HTTP, réponses invalides et absences de données exploitables sont signalées.

## Cache

Cache météo par coordonnées et fenêtre de dates : préfixe `omw_319_`, conservé en 3.1.10. Cache initial configurable par l’attribut `cache`, minimum une minute. Le rechargement via la route REST utilise 15 minutes. Géocodage : 24 heures. Ces caches sont distincts des caches de page, du navigateur ou du CDN.

## Limites photovoltaïques

Les données sont modélisées et non des mesures locales. W/m² désigne une puissance par surface ; MJ/m² une énergie par surface. Ces grandeurs ne sont pas la production électrique d’un panneau. Aucun calcul de panneau incliné, de pertes électriques, d’énergie stockée, de temps de recharge ou d’autonomie n’est inclus. Le composant batterie/tension MeshCore et son iframe sont distincts.
