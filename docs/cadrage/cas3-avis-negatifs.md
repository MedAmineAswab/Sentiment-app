## Besoin en une phrase (obligatoire)

Repérer automatiquement les avis clients négatifs pour que le service client les traite en premier.

## Utilisateur final (obligatoire)

Le conseiller du service client, qui reçoit beaucoup d'avis et doit traiter d'abord les clients mécontents.

## Approche retenue (obligatoire)

Cocher une seule case :

- [ ] Règles métier
- [x] Machine learning
- [ ] RAG
- [ ] Modèle génératif seul

## Justification (obligatoire, citer au moins deux critères de la grille : (a) données étiquetées, (b) vérifiabilité, (c) coût par requête, (d) conséquence d'une erreur)

(a) Des jeux d'avis déjà étiquetés positif ou négatif existent, ce qui permet d'entraîner un classifieur. (c) Un modèle léger de type TF-IDF avec régression logistique coûte presque rien par requête et répond en quelques millisecondes. (d) Une erreur est peu grave : un avis mal classé sera simplement relu plus tard par un humain.

## Données nécessaires et leur origine (obligatoire)

Des avis clients en français avec leur étiquette (positif ou négatif) : un jeu de démonstration généré pour les tests, puis le jeu public Allociné (20 000 avis) pour l'entraînement final.

## Métrique de succès et seuil d'acceptation (obligatoire)

F1 macro d'au moins 0,85 sur un jeu de test jamais vu pendant l'entraînement, avec un bon rappel sur la classe négative pour ne pas rater les clients mécontents.

## Conséquence d'une erreur et validation humaine prévue (obligatoire)

Un avis négatif classé positif risque d'être traité trop tard. Pour limiter ce risque, un avis dont la confiance est faible est marqué « indéterminé » et renvoyé à un conseiller, qui garde la décision.

## Risques éthiques ou de confidentialité (obligatoire)

Les avis peuvent contenir des noms ou des coordonnées : les anonymiser avant tout stockage. Le modèle peut aussi être moins fiable sur l'ironie ou sur des avis mitigés, donc il ne doit pas servir à évaluer des personnes.

## Approche écartée et pourquoi (facultatif)

Les règles métier à base de mots-clés : elles ratent les négations et les tournures variées, et deviennent vite ingérables.