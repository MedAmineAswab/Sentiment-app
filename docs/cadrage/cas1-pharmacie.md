## Besoin en une phrase (obligatoire)

Repérer automatiquement les ordonnances auxquelles il manque une information obligatoire (posologie, durée, date, signature) avant la délivrance.

## Utilisateur final (obligatoire)

Le pharmacien ou le préparateur au comptoir, qui doit vérifier chaque ordonnance rapidement.

## Approche retenue (obligatoire)

Cocher une seule case :

- [x] Règles métier
- [ ] Machine learning
- [ ] RAG
- [ ] Modèle génératif seul

## Justification (obligatoire, citer au moins deux critères de la grille : (a) données étiquetées, (b) vérifiabilité, (c) coût par requête, (d) conséquence d'une erreur)

(b) Les champs obligatoires d'une ordonnance sont définis par la réglementation : une règle est vérifiable et explicable. (d) Une erreur peut mettre en danger le patient, donc le résultat doit être prévisible et auditable. (a) Nous n'avons pas de corpus d'ordonnances étiquetées.

## Données nécessaires et leur origine (obligatoire)

Ordonnances numérisées ou saisies sous forme structurée, avec la liste des champs obligatoires fournie par la réglementation pharmaceutique en vigueur.

## Métrique de succès et seuil d'acceptation (obligatoire)

Rappel d'au moins 95 % sur les ordonnances réellement incomplètes (on veut en laisser passer le moins possible), avec un taux de fausses alertes acceptable pour ne pas ralentir le comptoir.

## Conséquence d'une erreur et validation humaine prévue (obligatoire)

Une ordonnance incomplète non détectée peut causer une erreur de dosage. Le pharmacien valide toujours la délivrance : l'outil signale seulement, il ne décide pas.

## Risques éthiques ou de confidentialité (obligatoire)

Les ordonnances sont des données de santé : accès restreint, pas de stockage inutile, et aucun envoi vers un service externe sans cadre légal.

## Approche écartée et pourquoi (facultatif)

Le machine learning, faute de données étiquetées et parce qu'une décision non explicable est risquée en santé.