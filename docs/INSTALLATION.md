# Installation et utilisation — 3.1.11

## Utiliser sans installation

[Ouvrir l’outil sur CLOUX.NET](https://www.cloux.net/rayonnement-solaire-couverture-nuageuse/)

## Installer ou mettre à jour

[Télécharger le ZIP 3.1.11](../cloux-net-suivi-solaire-3.1.11.zip?raw=true)

PHP 7.4 minimum. Sauvegarder l’existant et tester en préproduction. L’accès au téléchargement dépend des droits et de la visibilité du dépôt. Ne pas installer l’archive Code > Download ZIP.

1. Télécharger le ZIP de l’extension sans le décompresser.
2. Dans WordPress : Extensions > Ajouter une extension > Téléverser une extension.
3. Sélectionner `cloux-net-suivi-solaire-3.1.11.zip` et remplacer la version existante.
4. Vérifier la version 3.1.11 et conserver une seule copie active.
5. Utiliser `[suivi_solaire]` dans un bloc Code court.
6. Purger les caches de page/CDN si un ancien rendu persiste.

Dossier : `cloux-net-suivi-solaire`. PHP principal : `cloux-net-suivi-solaire.php`. Pour une installation manuelle, placer ce dossier dans `wp-content/plugins/`, sans double niveau de dossier.

## Attributs

| Attribut | Défaut | Usage |
|---|---|---|
| location | vide | Ville ou latitude, longitude ; prioritaire sur lat/lon |
| lat | 48.7649 | Latitude si location est vide |
| lon | 1.9292 | Longitude si location est vide |
| label | vide | Libellé initial personnalisé |
| charts | 1 | 0 masque les quatre graphiques |
| cache | 15 | Cache initial en minutes, minimum 1 |
| start | vide | Début initial YYYY-MM-DD ; défaut hier |
| end | vide | Fin initiale YYYY-MM-DD ; défaut demain |

```text
[suivi_solaire location="Versailles" charts="1" cache="15"]
```

Alias : `[openmeteo_weather]`. Fenêtre initiale limitée à cinq jours et aux bornes gérées par le code. Le jour initial est aujourd’hui s’il est inclus, sinon start ; il doit être autorisé.

## Navigation et vérifications

Le calendrier permet de sélectionner de J−92 à aujourd’hui selon la date WordPress. La carte du lendemain ne rend pas demain sélectionnable. Les changements de ville/date passent par `/wp-json/cloux-solaire/v1/widget`, avec un cache météo de 15 minutes non personnalisé par l’attribut initial `cache`.

Ordre attendu :

1. Rayonnement global horizontal — W/m².
2. Rayonnement diffus instantané — W/m².
3. Couverture nuageuse — %.
4. Énergie solaire quotidienne — MJ/m², histogramme.

Les filtres horaires concernent les trois courbes ; l’histogramme garde les trois jours autour de la sélection. Vérifier les deux colonnes de rayonnement du tableau et l’énergie des cartes.

Les paragraphes explicatifs sous le titre de l’histogramme et avant les courbes sont supprimés respectivement en 3.1.10 et 3.1.11. Les graphiques et les données sont conservés.

## Retour arrière

[ZIP 3.1.10](../cloux-net-suivi-solaire-3.1.10.zip?raw=true)

Restaurer la copie sauvegardée et purger les caches concernés. Publier un ZIP sur GitHub ne met pas WordPress à jour. Le renommage du dépôt ne nécessite pas de changer les shortcodes, fonctions, route REST ou URL des articles.
