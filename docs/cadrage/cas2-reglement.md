## Besoin en une phrase (obligatoire)

Permettre aux étudiants de poser une question en langage naturel sur le règlement intérieur et d'obtenir une réponse fiable, avec l'article concerné.

## Utilisateur final (obligatoire)

L'étudiant, qui cherche une règle précise (absences, retards, examens, usage du matériel) sans lire tout le document.

## Approche retenue (obligatoire)

Cocher une seule case :

- [ ] Règles métier
- [ ] Machine learning
- [x] RAG
- [ ] Modèle génératif seul

## Justification (obligatoire, citer au moins deux critères de la grille : (a) données étiquetées, (b) vérifiabilité, (c) coût par requête, (d) conséquence d'une erreur)

(b) Chaque réponse s'appuie sur un extrait du règlement et cite l'article, donc l'étudiant peut la vérifier. (d) Une fausse information peut conduire à une sanction injuste, donc on ne peut pas laisser un modèle inventer. (c) Le coût par requête reste faible car on n'envoie au modèle que quelques extraits pertinents.

## Données nécessaires et leur origine (obligatoire)

Le texte officiel du règlement intérieur de l'établissement, découpé en articles, avec sa date de version.

## Métrique de succès et seuil d'acceptation (obligatoire)

Sur un jeu de 30 questions de test, au moins 90 % de réponses correctes avec la bonne source citée, et aucune règle inventée.

## Conséquence d'une erreur et validation humaine prévue (obligatoire)

Une réponse erronée peut induire l'étudiant en erreur sur ses droits ou obligations. Pour tout cas litigieux, l'outil renvoie vers l'administration, qui garde la décision finale.

## Risques éthiques ou de confidentialité (obligatoire)

Le règlement est public en interne, mais les questions peuvent révéler la situation personnelle d'un étudiant : ne pas conserver les questions avec son identité, et prévenir que l'outil ne remplace pas l'administration.

## Approche écartée et pourquoi (facultatif)

Le modèle génératif seul : il peut inventer des règles plausibles mais fausses et ne cite aucune source.