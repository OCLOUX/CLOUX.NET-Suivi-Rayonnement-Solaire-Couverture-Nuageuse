# Contrôles et historique

## Version source

Version 3.1.7, fichier joint nommé cloux-net-suivi-solaire-2.php, à installer sous le nom cloux-net-suivi-solaire.php. Le renommage local du fichier ne change pas son contenu.

SHA-256 du fichier fourni :

```text
588dfc9ebc338be309e4849c091bfcc24fd15f69224b3becdd606e2a3b052f9e
```

## Contrôles réalisés le 29 octobre 2026

- Version 3.1.7 vérifiée dans l’en-tête du fichier joint.
- JavaScript extrait du PHP : node --check réussi dans l’environnement de préparation.
- PHP indisponible dans cet environnement : aucun php -l ni test d’exécution PHP réalisé.
- Aucun test navigateur, WordPress complet ou appel API réel validé lors de cette préparation documentaire.

Les notes jointes antérieures annoncent également une comparaison des fonctions de rendu et une vérification du ZIP. Ces notes ne constituent pas une nouvelle validation de production. Le présent commit contient uniquement la documentation, pas les sources ni les scripts de test.

## Changements de présentation documentés

- 3.1.4 : champ de localisation sur la ligne du libellé et calendrier à droite.
- 3.1.5 : suppression du bouton Afficher, changement automatique de date et alignement du bouton Aujourd’hui sur le début du champ de localisation.
- 3.1.6 : police du calendrier reprise du champ de localisation et alignement de la fin du groupe calendrier sur la fin de ce champ.
- 3.1.7 : champ date de 118 px, flèches de 10 px dans des boutons de 26 × 26 px, espacement de 4 px. La marge de l’icône native est ajustée sur les moteurs compatibles.

## Recette à effectuer

1. Exécuter php -l sur le fichier source.
2. Installer sur préproduction et contrôler les deux shortcodes.
3. Tester ville valide, ville inconnue et coordonnées invalides.
4. Tester Aujourd’hui, flèches, calendrier, borne J−92 et date hors bornes.
5. Vérifier les graphiques, les tableaux et les valeurs absentes.
6. Vérifier les heures, les fuseaux et le passage heure d’été/heure d’hiver.
7. Tester la mise en page sur mobile et ordinateur ; l’apparence du calendrier dépend du navigateur.
8. Simuler une indisponibilité Open-Meteo et vérifier le message d’erreur.
9. Contrôler la console et les requêtes REST sans désactiver globalement les protections du site.

## Sécurité et publication

Ne pas ajouter de jeton GitHub, cookie, mot de passe WordPress ou sauvegarde contenant des secrets. Publier un commit dans ce dépôt privé ne le rend pas public et ne déploie pas l’extension sur WordPress. Toute modification de visibilité ou mise en production nécessite une action distincte.
