![Suivi du rayonnement solaire sur CLOUX.NET](docs/cloux%20-%20rayonnement%20solaire.png)

# Suivi du rayonnement solaire et de la couverture nuageuse

Extension WordPress CLOUX.NET utilisant Open-Meteo pour suivre le rayonnement solaire d’une ville ou d’une position GPS et éclairer l’analyse de la recharge solaire. Aucun calcul de production électrique, de recharge ou d’autonomie de batterie n’est inclus.

![Suivi du rayonnement solaire sur CLOUX.NET](docs/cloux%20-%20rayonnement%20solaire.png)

## Utilisation en ligne

[Ouvrir l’outil sur CLOUX.NET](https://www.cloux.net/rayonnement-solaire-couverture-nuageuse/)

## Télécharger et installer

Version disponible : 3.1.11 — PHP 7.4 minimum.

[Télécharger le ZIP installable 3.1.11](cloux-net-suivi-solaire-3.1.11.zip?raw=true)

Sauvegarder l’existant, puis téléverser ce ZIP dans WordPress : Extensions > Ajouter une extension > Téléverser une extension. Remplacer la copie existante et conserver une seule extension active. Ajouter `[suivi_solaire]` dans un bloc Code court. Ne pas utiliser Code > Download ZIP : cette archive contient le dépôt entier.

## Graphiques, dans l’ordre d’affichage

1. Rayonnement global horizontal : `shortwave_radiation`, W/m², moyenne sur l’heure précédente.
2. Rayonnement diffus instantané : `diffuse_radiation_instant`, W/m².
3. Couverture nuageuse : `cloud_cover`, %.
4. Énergie solaire quotidienne : `shortwave_radiation_sum`, MJ/m², histogramme journalier.

Les trois courbes horaires disposent de filtres de période et d’infobulles. L’histogramme quotidien présente le jour précédent, le jour sélectionné et le jour suivant, indépendamment des filtres horaires.

## Fonctions

- Localisation par ville ou GPS.
- Cartes journalières : lever, coucher, durée du jour, ensoleillement et énergie solaire.
- Tableau horaire : nuages et deux rayonnements, global et diffus.
- Calendrier de J−92 à aujourd’hui, flèches et bouton Aujourd’hui ; disponibilité des données dépendante de l’API.
- Rechargement au changement de date ou de localisation.
- Distinction des données passées modélisées et des prévisions.

## Exemples

```text
[suivi_solaire]
[suivi_solaire location="Versailles"]
[suivi_solaire location="48.7649, 1.9292"]
[suivi_solaire charts="0"]
```

L’alias `[openmeteo_weather]` reste accepté.

## Changements récents

- 3.1.9 : rétablissement du diffus et ajout de l’histogramme quotidien.
- 3.1.10 : suppression du paragraphe sous le titre du graphique quotidien.
- 3.1.11 : suppression du paragraphe « Courbe principale… » avant les graphiques ; les données, les quatre graphiques et leur ordre sont conservés.

## Aperçu

[![Capture historique du suivi solaire](docs/cloux%20-%20rayonnement%20solaire.png)](https://www.cloux.net/rayonnement-solaire-couverture-nuageuse/)

Capture historique non actualisée pour la 3.1.11 : elle peut ne pas montrer les quatre graphiques. Ses valeurs ne sont pas en temps réel.

## Documentation

- [Installation et utilisation](docs/INSTALLATION.md)
- [Données, API et limites](docs/DONNEES.md)
- [Contrôles et historique](docs/CONTROLES.md)

## Distribution et limites

Les sources sont distribuées dans le ZIP, pas séparément dans l’arborescence du dépôt. La présence du ZIP distant a été vérifiée ; son contenu n’a pas été extrait et comparé lors de cette mise à jour documentaire.

Les données sont modélisées, pas mesurées par un capteur local. Le rayonnement horizontal ne décrit pas directement la production d’un panneau incliné. Le tableau de bord batterie/tension MeshCore et son iframe constituent un composant distinct. Publier le ZIP sur GitHub ne met pas WordPress à jour et ne change pas la visibilité du dépôt.

## Licence et attribution

Le PHP déclare GPLv2 ou ultérieure. Conserver l’attribution Open-Meteo et la mention CC BY 4.0 de l’extension ; vérifier les conditions du service pour l’usage envisagé.
