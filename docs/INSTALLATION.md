# Installation et utilisation

## Télécharger la version 3.1.7

[Télécharger cloux-net-suivi-solaire-3.1.7.zip](../cloux-net-suivi-solaire-3.1.7.zip?raw=true)

Le paquet est disponible à la racine du dépôt. Les sources sont distribuées dans cette archive, et non encore comme fichiers séparés dans l’arborescence Git. Ne pas installer l’archive générale obtenue par Code > Download ZIP. L’accès au paquet dépend de la visibilité du dépôt et des droits du visiteur.

Prérequis déclaré : PHP 7.4 minimum. Sauvegarder l’extension existante et tester sur préproduction.

## Installation du paquet

1. Télécharger le ZIP de l’extension sans le décompresser pour le téléversement.
2. Ouvrir Extensions > Ajouter une extension > Téléverser une extension dans WordPress.
3. Sélectionner cloux-net-suivi-solaire-3.1.7.zip.
4. Installer, ou remplacer la copie existante si WordPress le propose.
5. Activer si nécessaire, sans activer deux copies déclarant les mêmes fonctions.
6. Ajouter [suivi_solaire] dans un bloc Code court et contrôler le résultat.

Le dossier de l’extension doit rester cloux-net-suivi-solaire et le fichier principal cloux-net-suivi-solaire.php. Le renommage du dépôt GitHub ne nécessite pas de renommer les fonctions, les shortcodes ou la route REST.

Pour une installation manuelle après extraction, copier le dossier de l’extension dans wp-content/plugins/, puis l’activer dans WordPress. Vérifier que le PHP n’est pas enfoui dans un second dossier de même nom.

## Attributs

| Attribut | Valeur par défaut | Usage |
|---|---|---|
| location | vide | Ville ou latitude, longitude ; prioritaire sur lat et lon |
| lat | 48.7649 | Latitude si location est vide |
| lon | 1.9292 | Longitude si location est vide |
| label | vide | Libellé initial personnalisé |
| charts | 1 | Mettre 0 pour masquer les graphiques |
| cache | 15 | Cache initial en minutes, minimum 1 |
| start | vide | Début initial YYYY-MM-DD ; défaut hier |
| end | vide | Fin initiale YYYY-MM-DD ; défaut demain |

```text
[suivi_solaire location="Versailles" charts="1" cache="15"]
```

L’alias [openmeteo_weather] reste accepté. Les attributs start/end décrivent la fenêtre initiale ; ils n’étendent pas les bornes du calendrier. La fenêtre demandée est limitée à cinq jours et aux bornes de l’API gérées par le code. Le jour sélectionné initial est aujourd’hui s’il est inclus, sinon start ; il doit rester dans les bornes autorisées.

## Navigation

Le calendrier permet de sélectionner de J−92 à aujourd’hui, selon la date WordPress, avec validation serveur. La carte du lendemain n’autorise pas à sélectionner demain. La disponibilité effective des variables dépend d’Open-Meteo.

Le changement de localisation et de date recharge cartes, graphiques et tableau via /wp-json/cloux-solaire/v1/widget. La navigation utilise une fenêtre centrée sur le jour choisi, adaptée à la borne minimale. Le cache de contenu de cette route est fixé à 15 minutes ; l’attribut cache du shortcode ne personnalise pas ce paramètre AJAX.

## Retour arrière

Restaurer la copie sauvegardée puis purger les caches concernés. Ne pas modifier les URL des articles ni les shortcodes pour un renommage du dépôt GitHub. Le téléchargement ou la publication du ZIP ne déclenche aucune mise à jour automatique de WordPress.
