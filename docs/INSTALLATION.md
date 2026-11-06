# Installation et utilisation — 3.1.10

## Sans installation

[Utiliser l’outil sur CLOUX.NET](https://www.cloux.net/rayonnement-solaire-couverture-nuageuse/)

## Télécharger et installer

[Télécharger cloux-net-suivi-solaire-3.1.10.zip](../cloux-net-suivi-solaire-3.1.10.zip?raw=true)

PHP 7.4 minimum. Sauvegarder l’existant et privilégier un essai en préproduction. Ne pas installer l’archive générale Code > Download ZIP. L’accès au téléchargement dépend de la visibilité du dépôt et des droits du visiteur.

1. Télécharger le ZIP sans le décompresser pour le téléversement WordPress.
2. Ouvrir Extensions > Ajouter une extension > Téléverser une extension.
3. Sélectionner `cloux-net-suivi-solaire-3.1.10.zip` et remplacer la version existante.
4. Vérifier qu’une seule copie de CLOUX.NET Suivi solaire est active et que sa version est 3.1.10.
5. Ajouter `[suivi_solaire]` dans un bloc Code court.
6. Purger les caches de page/CDN si un ancien rendu persiste.

Dossier : `cloux-net-suivi-solaire`. Fichier principal : `cloux-net-suivi-solaire.php`. En installation manuelle, placer ce dossier dans `wp-content/plugins/` sans double niveau de dossier.

## Attributs

| Attribut | Défaut | Usage |
|---|---|---|
| location | vide | Ville ou latitude, longitude ; prioritaire sur lat/lon |
| lat | 48.7649 | Latitude si location est vide |
| lon | 1.9292 | Longitude si location est vide |
| label | vide | Libellé initial personnalisé |
| charts | 1 | 0 masque tous les graphiques, y compris le quotidien |
| cache | 15 | Cache initial en minutes, minimum 1 |
| start | vide | Début initial YYYY-MM-DD ; défaut hier |
| end | vide | Fin initiale YYYY-MM-DD ; défaut demain |

```text
[suivi_solaire location="Versailles" charts="1" cache="15"]
```

Alias : `[openmeteo_weather]`. La fenêtre initiale est limitée à cinq jours et aux bornes gérées par le code. Le jour initial est aujourd’hui s’il est inclus, sinon start ; il doit être autorisé.

## Navigation et contrôle visuel

Le calendrier permet de choisir de J−92 à aujourd’hui selon la date WordPress. La carte du lendemain ne rend pas demain sélectionnable. Les changements de ville/date rechargent les résultats via `/wp-json/cloux-solaire/v1/widget`, avec un cache météo de 15 minutes non personnalisé par l’attribut initial `cache`.

Vérifier cet ordre :

1. Rayonnement global horizontal — W/m².
2. Rayonnement diffus instantané — W/m².
3. Couverture nuageuse — %.
4. Énergie solaire quotidienne — MJ/m², histogramme.

Les filtres horaires portent sur les trois courbes ; l’histogramme garde les trois jours autour de la sélection. Vérifier aussi les deux colonnes de rayonnement du tableau et l’énergie dans les cartes. En 3.1.10, le paragraphe explicatif sous le titre du graphique quotidien est supprimé ; les données et l’ordre sont inchangés.

## Retour arrière

Restaurer la copie sauvegardée, puis purger les caches concernés. Publier le ZIP sur GitHub ne déclenche pas sa mise à jour dans WordPress. Le renommage du dépôt ne nécessite pas de changer les shortcodes, les fonctions, la route REST ou les URL des articles.
