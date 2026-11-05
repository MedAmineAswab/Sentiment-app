# Compte rendu de la semaine 2 : modèle de sentiment

## 1. Quelles erreurs le modèle commet-il ?

Le modèle TF-IDF + régression logistique obtient un F1 macro de 0,879 sur les 58 avis de test du jeu de démonstration. Sa matrice de confusion est [[27, 2], [5, 24]] : il commet 7 erreurs, dont 2 avis négatifs classés positifs et 5 avis positifs classés négatifs. Toutes ces erreurs concernent des avis mitigés, qui mélangent une partie négative et une partie positive. Exemple : « Commande jamais reçue et remboursement en attente au début, sauf que ensuite je recommande sans hésiter » est un avis positif, mais le modèle le prédit négatif.

## 2. Pourquoi ces erreurs ?

Le modèle fonctionne comme un sac de mots : il additionne les poids des mots et des paires de mots, sans tenir compte de leur ordre dans la phrase. Il ne comprend donc pas qu'un connecteur comme « sauf que », « avant que » ou « mais finalement » renverse le sens de ce qui précède. Dans les sept cas, la prédiction suit le début de l'avis, alors que c'est la fin qui donne le vrai verdict.

## 3. Comment l'améliorer ?

Il faudrait une représentation qui tient compte de l'ordre des mots et du contexte, comme les embeddings de phrase (semaine 9) ou un modèle de langue. Les bigrammes ne suffiraient pas, car le vectoriseur en utilise déjà.