# Contrôles et historique

## Distribution de la version 3.1.7

Le fichier cloux-net-suivi-solaire-3.1.7.zip a été ajouté manuellement à la racine du dépôt. Sa présence a été vérifiée via GitHub : taille déclarée 15 429 octets.

Les trois fichiers fournis séparément pour cette version sont le PHP de l’extension, le fichier de présentation et les notes de contrôle. Les sources sont distribuées dans le ZIP ; elles ne sont pas encore présentes comme fichiers séparés dans l’arborescence du dépôt.

Le ZIP distant n’a pas été extrait et comparé aux pièces jointes lors de cette mise à jour documentaire. Sa présence sur GitHub ne constitue pas une validation de son contenu ni un test d’installation.

## Empreinte du PHP fourni

Nom d’installation : cloux-net-suivi-solaire.php.

SHA-256 du fichier PHP fourni et contrôlé précédemment :

```text
588dfc9ebc338be309e4849c091bfcc24fd15f69224b3becdd606e2a3b052f9e
```

Cette empreinte concerne le PHP joint, pas le ZIP distant.

## Contrôles réalisés le 29 octobre 2026

- Version 3.1.7 vérifiée dans l’en-tête du PHP fourni.
- JavaScript extrait du PHP : node --check réussi dans l’environnement de préparation.
- PHP indisponible : aucun php -l ni test d’exécution PHP réalisé.
- Aucun test navigateur, WordPress complet ou appel API réel validé lors de la préparation documentaire.

Les notes jointes antérieures annoncent une comparaison des fonctions de rendu et une vérification du ZIP préparé à ce moment-là. Elles ne constituent pas un nouveau contrôle du ZIP téléversé manuellement sur GitHub. Les scripts de test ne sont pas versionnés dans le dépôt.

## Historique de présentation

- 3.1.4 : localisation sur la ligne du libellé et calendrier à droite.
- 3.1.5 : suppression d’Afficher, changement automatique de date et alignement d’Aujourd’hui sur le début du champ de localisation.
- 3.1.6 : police du calendrier reprise du champ de localisation et fin du groupe calendrier alignée sur la fin de ce champ.
- 3.1.7 : champ date de 118 px, flèches de 10 px dans des boutons de 26 × 26 px, espacement de 4 px et marge de l’icône native ajustée sur les moteurs compatibles.

## Recette à effectuer

1. Extraire le ZIP téléchargé et contrôler les trois fichiers ainsi que le dossier d’installation.
2. Comparer l’empreinte du PHP à celle indiquée ci-dessus.
3. Exécuter php -l sur ce PHP.
4. Installer sur préproduction et contrôler les deux shortcodes.
5. Tester ville valide, ville inconnue et coordonnées invalides.
6. Tester Aujourd’hui, flèches, calendrier, borne J−92 et dates hors bornes.
7. Vérifier graphiques, tableau et valeurs absentes.
8. Vérifier heures, fuseaux et changements d’heure.
9. Tester mobile et ordinateur ; l’apparence du calendrier dépend du navigateur.
10. Simuler une indisponibilité Open-Meteo et contrôler les erreurs REST sans désactiver globalement les protections du site.

## Sécurité et publication

Ne pas déposer de jeton GitHub, cookie, mot de passe WordPress ou sauvegarde contenant des secrets. La présence du ZIP ne change pas la visibilité du dépôt. Le passage en public et toute mise en production WordPress restent des actions distinctes. Cette mise à jour documentaire ne modifie ni le ZIP, ni le PHP, ni WordPress.
