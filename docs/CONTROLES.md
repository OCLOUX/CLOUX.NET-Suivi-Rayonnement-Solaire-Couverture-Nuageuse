# Contrôles et historique

## Distribution actuelle

Le 6 novembre 2026, GitHub déclare `cloux-net-suivi-solaire-3.1.10.zip` à la racine : 16 205 octets. Les sources sont distribuées dans l’archive et non séparément dans l’arborescence du dépôt. Le ZIP distant n’a pas été extrait et comparé lors de cette mise à jour documentaire ; sa présence ne valide ni son contenu ni son installation.

## Contrôles de préparation de la 3.1.10

- Base : PHP 3.1.9 fourni.
- Suppression du paragraphe explicatif du graphique quotidien et mise à jour de version.
- JavaScript extrait : `node --check` réussi.
- ZIP généré : contenu PHP relu et intégrité CRC vérifiée.
- PHP indisponible : aucun `php -l` ni test d’exécution PHP.
- Aucun test d’installation WordPress de la 3.1.10 effectué par l’assistant.

Ces contrôles concernent les fichiers préparés, pas une nouvelle extraction du ZIP distant. La vérification de la page en 3.1.8 ne constitue pas une recette de la 3.1.10.

## Historique

- 3.1.4 : localisation sur la ligne du libellé et calendrier à droite.
- 3.1.5 : suppression du bouton Afficher, changement automatique de date, alignement d’Aujourd’hui.
- 3.1.6 : police et alignement du calendrier.
- 3.1.7 : champ date de 118 px, flèches de 10 px, boutons de 26 × 26 px, espacement de 4 px.
- 3.1.8 : remplacement du diffus par le global horaire, ajout de l’énergie quotidienne dans les cartes ; pas encore de graphique quotidien.
- 3.1.9 : rétablissement du diffus, ajout de l’histogramme quotidien et de la colonne diffus du tableau ; cache météo `omw_319_`. Ordre : global, diffus, nuages, énergie quotidienne.
- 3.1.10 : suppression du paragraphe explicatif sous le titre du graphique quotidien ; graphiques et ordre inchangés.

## Recette à effectuer

1. Extraire le ZIP et contrôler le dossier, le PHP, readme.txt et CONTROLES.txt.
2. Exécuter `php -l`, puis installer en préproduction.
3. Vérifier version, deux shortcodes, ville valide/inconnue et coordonnées invalides.
4. Tester calendrier, flèches, Aujourd’hui, borne J−92 et rejets hors bornes.
5. Vérifier l’ordre des quatre graphiques, les unités, les valeurs des cartes et les deux rayonnements du tableau.
6. Vérifier les filtres horaires, les infobulles et l’indépendance du graphique quotidien.
7. Tester valeurs nulles, zéros, prévisions, fuseaux et changements d’heure.
8. Vérifier `charts=0`, mobile/ordinateur et erreurs API/REST.
9. Confirmer la suppression du paragraphe demandé sans disparition de l’histogramme.

## Sécurité et périmètre

Ne pas déposer de jeton, cookie, mot de passe ou sauvegarde contenant des secrets. Cette mise à jour documentaire ne modifie ni le ZIP, ni le PHP, ni WordPress. La publication sur GitHub et la mise en production sont distinctes.
