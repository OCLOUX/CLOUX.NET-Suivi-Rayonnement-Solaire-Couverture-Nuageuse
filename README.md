# Suivi du rayonnement solaire et de la couverture nuageuse

Extension WordPress CLOUX.NET utilisant Open-Meteo pour afficher le rayonnement diffus, la couverture nuageuse et les horaires solaires d’une localisation.

## État du dépôt

Ce commit publie la documentation de la version 3.1.7 fournie. Le fichier PHP et les archives installables ne sont pas encore ajoutés au dépôt. Télécharger le dépôt seul ne permet donc pas encore d’installer l’extension. Le dépôt reste privé ; aucune mise à jour de WordPress n’est déclenchée.

## Fonctions de la version documentée

- Localisation par ville ou coordonnées GPS.
- Cartes du jour précédent, du jour sélectionné et du lendemain.
- Lever, coucher, durée du jour et durée d’ensoleillement.
- Graphiques SVG du rayonnement diffus et de la couverture nuageuse, avec infobulles.
- Tableau horaire et filtres de période.
- Navigation par calendrier, flèches et bouton Aujourd’hui ; chargement automatique au changement de date.
- Distinction graphique des données passées modélisées et des prévisions.

## Utilisation

```text
[suivi_solaire]
[suivi_solaire location="Versailles"]
[suivi_solaire location="48.7649, 1.9292"]
[suivi_solaire charts="0"]
```

L’alias historique [openmeteo_weather] reste accepté.

## Documentation

- [Installation et utilisation](docs/INSTALLATION.md)
- [Données, API et limites](docs/DONNEES.md)
- [Contrôles et historique](docs/CONTROLES.md)

## Périmètre

Le tableau de bord HTML batterie/tension MeshCore et son iframe constituent un autre composant. Ils ne sont pas inclus dans ce commit. Le calcul de production photovoltaïque et le temps de recharge d’une batterie ne sont pas implémentés dans la version 3.1.7.

## Licence et attribution

Le fichier PHP fourni déclare GPLv2 ou ultérieure. Les données affichées sont attribuées à Open-Meteo, avec la mention CC BY 4.0 présente dans l’extension. Conserver cette attribution et vérifier les conditions applicables au service pour l’usage envisagé.
