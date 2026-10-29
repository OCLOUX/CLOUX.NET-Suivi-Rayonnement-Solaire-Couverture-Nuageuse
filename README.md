# Suivi du rayonnement solaire et de la couverture nuageuse

Extension WordPress CLOUX.NET utilisant Open-Meteo pour afficher le rayonnement diffus, la couverture nuageuse et les horaires solaires d’une localisation.

## Télécharger et installer

Version disponible : 3.1.7 — PHP 7.4 minimum.

[Télécharger le ZIP de l’extension](cloux-net-suivi-solaire-3.1.7.zip?raw=true)

1. Télécharger ce ZIP, sans le décompresser pour le téléversement WordPress.
2. Dans WordPress : Extensions > Ajouter une extension > Téléverser une extension.
3. Sélectionner cloux-net-suivi-solaire-3.1.7.zip, puis installer ou remplacer la version existante après sauvegarde.
4. Activer l’extension si nécessaire et ajouter [suivi_solaire] dans un bloc Code court.

Ne pas utiliser Code > Download ZIP pour cette installation : cette commande télécharge le dépôt entier, pas seulement le paquet de l’extension.

## Contenu disponible

Le paquet installable est présent à la racine du dépôt. D’après les fichiers fournis pour cette version, il contient le PHP de l’extension, readme.txt et CONTROLES.txt. Les sources sont distribuées dans ce ZIP ; elles ne sont pas encore versionnées séparément dans l’arborescence du dépôt.

La présence du ZIP distant a été vérifiée. Son contenu n’a pas été extrait et comparé aux pièces jointes lors de cette mise à jour documentaire.

## Fonctions

- Localisation par ville ou coordonnées GPS.
- Cartes du jour précédent, du jour sélectionné et du lendemain.
- Lever, coucher, durée du jour et durée d’ensoleillement.
- Graphiques SVG du rayonnement diffus et de la couverture nuageuse avec infobulles.
- Tableau horaire et filtres de période.
- Calendrier, flèches et bouton Aujourd’hui ; chargement automatique au changement de date.
- Distinction des données passées modélisées et des prévisions.

## Exemples

```text
[suivi_solaire]
[suivi_solaire location="Versailles"]
[suivi_solaire location="48.7649, 1.9292"]
[suivi_solaire charts="0"]
```

L’alias [openmeteo_weather] reste accepté.

## Documentation

- [Installation et utilisation](docs/INSTALLATION.md)
- [Données, API et limites](docs/DONNEES.md)
- [Contrôles et historique](docs/CONTROLES.md)

## Limites et périmètre

Les données météo sont modélisées, pas mesurées par un capteur local. Le rayonnement diffus ne représente pas à lui seul la production totale d’un panneau. Aucun calcul de recharge ou d’autonomie n’est inclus. Le tableau de bord batterie/tension MeshCore et son iframe constituent un autre composant.

L’ajout du ZIP ne rend pas le dépôt public et ne déploie rien sur WordPress. L’accès au téléchargement dépend de la visibilité du dépôt et des droits du visiteur.

## Licence et attribution

Le PHP fourni déclare GPLv2 ou ultérieure. Conserver l’attribution Open-Meteo et la mention CC BY 4.0 présente dans l’extension ; vérifier les conditions applicables au service pour l’usage envisagé.
