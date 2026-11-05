# Compte rendu de la semaine 3 : API FastAPI

## 1. Pourquoi l'API refuse-t-elle de démarrer sans modèle plutôt que de répondre 503 ?

Quand j'ai renommé models/sentiment.joblib puis lancé uvicorn, l'API s'est arrêtée au démarrage avec « FileNotFoundError: models/sentiment.joblib absent : lancez python src/train.py », suivie de « Application startup failed ». Une API sans modèle ne peut jamais répondre correctement à /predict : la panne est permanente tant que le fichier manque. En refusant de démarrer, elle rend le problème visible tout de suite, au déploiement, avec un message qui indique la correction, au lieu de s'afficher « en ligne » tout en échouant à chaque requête. Le code 503 convient mieux à une indisponibilité passagère, par exemple si le modèle disparaît en cours de fonctionnement.

## 2. Le double refus du texte vide est-il redondant ?

Pas complètement. Le contrat Pydantic refuse déjà le texte vide : mes essais avec {"text": ""}, {} et {"text": 42} ont tous donné 422, avec une liste d'erreurs détaillée (champ concerné, type d'erreur). Mais un texte fait seulement d'espaces passe ce contrôle (il contient au moins un caractère) et c'est predict() qui le refuse ensuite, avec un 422 dont le detail est une simple chaîne : « texte vide ». Le second contrôle est donc utile, car il protège le modèle même si l'appel ne passe pas par l'API. En revanche, le résultat n'est pas cohérent : le même refus a deux formes de réponse différentes. Il vaudrait mieux appliquer la même règle dans le schéma, pour que l'API renvoie un seul format d'erreur.