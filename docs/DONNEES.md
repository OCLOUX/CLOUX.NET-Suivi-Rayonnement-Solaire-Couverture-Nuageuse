# Données, API et limites

## Sources du code fourni

L’extension appelle Open-Meteo côté serveur via les fonctions HTTP WordPress. La géolocalisation par nom utilise le service de géocodage Open-Meteo ; les coordonnées saisies sont validées séparément.

Variables demandées par le code :

| Groupe | Variables |
|---|---|
| hourly | cloud_cover, diffuse_radiation_instant |
| daily | sunrise, sunset, daylight_duration, sunshine_duration |
| current | is_day |

Le fournisseur météo est https://api.open-meteo.com/v1/forecast avec models=best_match et timezone=auto. La documentation du fournisseur est https://open-meteo.com/en/docs.

## Lecture des résultats

- cloud_cover : couverture nuageuse en pourcentage.
- diffuse_radiation_instant : rayonnement diffus instantané en W/m² à l’heure indiquée, échantillonné dans la série horaire.
- daylight_duration et sunshine_duration : durées en secondes converties pour l’affichage.
- Les données passées sont des valeurs modélisées, pas les mesures d’un capteur local.
- Une valeur absente doit rester absente, sans conversion en zéro.

Le fuseau météo est obtenu dans la réponse de l’API. Le code construit le contexte temporel utilisé pour les graphiques et leurs horodatages. Les bornes du calendrier utilisent la date WordPress : vérifier le fuseau configuré sur le site, notamment si la localisation météo est distante.

## Cache et disponibilité

Le contenu météo est mis en cache par coordonnées et fenêtre de dates. Le géocodage est mis en cache 24 heures. La route AJAX utilise un cache de contenu de 15 minutes. Une modification de code ne signifie pas que des données plus récentes sont immédiatement disponibles.

La plage autorisée par l’interface ne garantit pas la disponibilité effective de toutes les variables Open-Meteo. Le code signale les erreurs HTTP, les réponses invalides et l’absence de données exploitables pour le jour choisi.

## Photovoltaïque : hors périmètre de la 3.1.7

Ne pas assimiler le rayonnement diffus seul à la production totale d’un panneau. Aucun calcul de production d’un panneau de 5 W, d’énergie stockée ou de temps de recharge n’est inclus. Les paramètres de panneau incliné discutés séparément ne sont pas présents dans cette version.

## Télémétrie et iframe

Le HTML batterie/tension, ses données JSON et son code iframe à hauteur automatique ne font pas partie de l’extension documentée ici. Leur intégration doit être versionnée séparément et ne doit pas être annoncée comme une fonction incluse dans le PHP.
