# Contrôles et historique

## Distribution actuelle

Le 6 novembre 2026, GitHub déclare à la racine :

- `cloux-net-suivi-solaire-3.1.11.zip` : 16 158 octets.
- `cloux-net-suivi-solaire-3.1.10.zip` : 16 205 octets, conservé pour retour arrière.

Les sources sont distribuées dans les ZIP, pas séparément dans l’arborescence du dépôt. Le ZIP distant 3.1.11 n’a pas été extrait et comparé lors de cette mise à jour documentaire ; sa présence ne valide ni son contenu ni son installation.

## Contrôles de préparation

La 3.1.11 a été préparée à partir du PHP 3.1.9 fourni en conservant les deux suppressions de texte successives.

- Suppression des paragraphes de présentation demandés en 3.1.10 et 3.1.11.
- Présence des quatre fonctions graphiques vérifiée.
- JavaScript extrait : `node --check` réussi.
- ZIP généré : contenu PHP relu et intégrité CRC vérifiée.
- PHP indisponible : aucun `php -l` ni test d’exécution PHP.
- Aucun test d’installation WordPress de la 3.1.11 effectué par l’assistant.

Ces contrôles concernent les fichiers préparés, pas une nouvelle extraction du ZIP distant. La lecture de la page en 3.1.8 n’est pas une recette de la 3.1.11. Les scripts de test ne sont pas versionnés.

## Historique

- 3.1.4 : localisation sur la ligne du libellé et calendrier à droite.
- 3.1.5 : suppression du bouton Afficher, changement automatique de date, alignement d’Aujourd’hui.
- 3.1.6 : police et alignement du calendrier.
- 3.1.7 : champ date de 118 px, flèches de 10 px, boutons de 26 × 26 px, espacement de 4 px.
- 3.1.8 : remplacement du diffus par le global horaire et énergie quotidienne dans les cartes ; pas de graphique quotidien.
- 3.1.9 : diffus rétabli, histogramme quotidien ajouté, colonne diffus ajoutée au tableau ; cache `omw_319_`. Ordre : global, diffus, nuages, énergie quotidienne.
- 3.1.10 : suppression du paragraphe sous le titre du graphique quotidien.
- 3.1.11 : suppression du paragraphe « Courbe principale… » avant les graphiques. Données, quatre graphiques et ordre conservés.

## Recette à effectuer

1. Extraire le ZIP ; contrôler dossier, PHP, readme.txt et CONTROLES.txt.
2. Exécuter `php -l`, puis installer en préproduction.
3. Vérifier version, deux shortcodes, villes valides/inconnues et coordonnées invalides.
4. Tester calendrier, flèches, Aujourd’hui, borne J−92 et rejets hors bornes.
5. Vérifier ordre et unités des quatre graphiques, cartes et tableau.
6. Tester filtres horaires, infobulles et indépendance de l’histogramme.
7. Tester valeurs nulles, zéros, prévisions, fuseaux et changements d’heure.
8. Vérifier `charts=0`, mobile/ordinateur et erreurs API/REST.
9. Confirmer l’absence des deux paragraphes sans disparition des graphiques.

## Sécurité et périmètre

Ne pas déposer de jeton, cookie, mot de passe ou sauvegarde contenant des secrets. Cette mise à jour documentaire ne modifie ni les ZIP, ni le PHP, ni WordPress. Publication GitHub et mise en production restent distinctes.
