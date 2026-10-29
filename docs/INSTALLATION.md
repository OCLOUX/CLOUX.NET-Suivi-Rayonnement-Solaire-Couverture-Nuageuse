# Installation et utilisation

## Prérequis et disponibilité

La version documentée est la 3.1.7. PHP 7.4 minimum selon l’en-tête fourni. Les sources ne sont pas encore importées dans ce dépôt ; utiliser le paquet préparé séparément, pas une archive du dépôt documentaire. Sauvegarder l’extension existante et tester sur préproduction.

## Installation du paquet

1. Ouvrir Extensions > Ajouter une extension > Téléverser une extension.
2. Sélectionner le ZIP de l’extension.
3. Remplacer la copie existante si WordPress le propose.
4. Ne pas activer deux copies déclarant les mêmes fonctions.
5. Ajouter [suivi_solaire] dans un bloc Code court et contrôler le résultat.

Conserver le dossier cloux-net-suivi-solaire et le fichier principal cloux-net-suivi-solaire.php. Le renommage du dépôt GitHub ne nécessite pas de renommer les fonctions, les shortcodes ou la route REST.

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

Exemple :

```text
[suivi_solaire location="Versailles" charts="1" cache="15"]
```

Les attributs start/end décrivent la fenêtre initiale ; ils n’étendent pas les bornes du calendrier. La fenêtre demandée est limitée à cinq jours et aux bornes de l’API gérées par le code. Le jour sélectionné initial est aujourd’hui s’il est inclus, sinon start ; il doit rester dans les bornes autorisées.

## Navigation

Le calendrier permet de sélectionner de J−92 à aujourd’hui, selon la date WordPress, avec validation serveur. La carte du lendemain n’autorise pas à sélectionner demain dans le calendrier. L’API peut néanmoins ne pas fournir toutes les variables sur toute cette plage.

Le changement de localisation et de date recharge ensemble les cartes, les graphiques et le tableau via la route REST publique de lecture /wp-json/cloux-solaire/v1/widget. La navigation dynamique utilise une fenêtre centrée sur le jour choisi, avec adaptation à la borne minimale. Le cache de contenu utilisé par cette route est fixé à 15 minutes dans le code actuel ; l’attribut cache du shortcode ne personnalise pas ce paramètre AJAX.

## Retour arrière

Restaurer la copie sauvegardée puis purger les caches concernés. Ne pas modifier les URL des articles ni les shortcodes pour un simple renommage du dépôt GitHub. Aucun déploiement automatique n’est configuré par ce commit.
