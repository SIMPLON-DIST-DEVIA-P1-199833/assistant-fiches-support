# Besoin : assistant des fiches support
 * un outil de commande a qui des techniciens pose des questions pour répondre aux clients qui font la requète (appel, ou autre)
 * il lit les fiches de procédures existants et se base dessus pour répondre
 * il peut aussi créer des brouillons de nouvelles fiches de procédures
 * il ne doit pas toucher, ecraser, supprimer les fichiers existant sans demander.
 * le dossier fiche ne doit contenir aucune données personnelles
 

## Questions et réponses retenues

* Quand l'assistant rédige un brouillon de fiche, où est-il enregistré, et qui le relit avant qu'il devienne une vraie fiche?
    * le technicien relit et valide les brouillons

* Quand l'utilisateur pose question qui ne sont pas dans le fiche que fait le service?
    * l'application créer une nouvelle fiche brouillon

* Qui sont les utilisateurs et quelles sont les niveaux de sécurité ou d'accès.
    * tous les utilisateurs ont le même niveau d'accès ce sont les techniciens

* Comment l'application doit répondre? 
    * Il répond en expliquant la procédure et en donnant ces sources : nom du ou des fiches + passage dan les fiches

* Que se passe t-il si le service extérieur IA est inaccessible?
    * Si pas de réposne au bout de 30 sec. L'application doit avertir l'utilisateur

* Quelles sont les limites ou budjets?
    - 20 ko par fiches
    - 60 ko tokken par conversation
    - 10 appels outils

## Parcours

### Parcours 1 : retrouver une procédure pendant un appel
| Étape | Qui | Fait quoi |
| :---: | --- | --- |
| 1 | Technicien support | Tape sa question dans le terminal, par exemple `"Réinitialiser le mot de passe d'un client"`. |
| 2 | Assistant | Lit les fiches du dossier `fiches/` et retient celles qui correspondent. |
| 3 | Assistant | Prépare la requète pour le service extérieure(LiteLLM) aux formats définis |
| 4 | Service extérieur (via LiteLLM) | Reçoit la question et les extraits de fiches, puis renvoie une réponse. |
| 5 | Assistant | Affiche la réponse et cite le ou les noms des fiche utilisées. |
| 6 | Technicien support | Suit les étapes de la fiche pendant l'appel. |

### Parcours 2 : rédiger un brouillon de fiche
| Étape | Qui | Fait quoi |
| :---: | --- | --- |
| 1 | Technicien support | Décrit la procédure à l'assistant, puis donne un nom de fichier. |
| 2 | Assistant | Prépare une requète pour le service extérieure(LiteLLM) avec le format de creation de fiche et le scope de la demande |
| 3 | Service extérieur (via LiteLLM) | Reçoit la demande et prépare une fiche brouillon sur le modèle de procédure fournit  |
| 4 | Assistant | Affiche le brouillon à l'utilisateur et attend sa validation. |
| 5 | Technicien support | Il relit le brouillon apporte des modifications si besoin et valide |
| 6 | Assistant | Crée la nouvelle fiche dans `fiches/`


## User story

> **En tant que** technicien support, **je veux** retrouver la procédure à suivre en posant ma question en ligne de commande, **afin de** répondre au client sans chercher la bonne fiche.

> **En tant que** technicien support, **je veux** obtenir un brouillon de nouvelle fiche et empêcher tout écrasement sans mon accord, **afin de** rédiger plus vite sans perdre de fiche existante.

## Critères d’acceptation

| Situation<br>*Étant donné…* | Action<br>*Quand…* | Résultat attendu<br>*Alors…* |
| --- | --- | --- |
| Le dossier `fiches/` contient `reinitialiser-mot-de-passe.md` | Le technicien lance `"Réinitialiser le mot de passe d'un client"` | La réponse cite `reinitialiser-mot-de-passe.md` et contient l'étape « Envoyer un lien de réinitialisation ». |
| L'utilisateur a besoin de créer un nouvelle fiche | Assistant prépare une request et envoie au service IA pour créer un brouillon | Une fiche brouillon au bon format prêt pour le review


## Objectifs d’accessibilité

| Objectif | Commande de vérification | Résultat attendu |
| --- | --- | --- |
| Une aide consultable sans connexion à la passerelle | `assistant --aide` | La commande affiche l'aide, sans appel réseau. |