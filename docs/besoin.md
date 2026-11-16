# Besoin : assistant des fiches support
## Qui ?
Agents techniques répondant au téléphone
## Quoi ?
Console de recherche et ouverture de documents par mots clés, basée sur l'IA avec LLM. 
## Où ?
Terminal
## Comment ?
L'utilisateur tape des mots clés du problème au téléphone, et une IA donne un sous-ensemble pertinent de fiches par ordre décroissant. Elle affiche aussi le contenu de la fiche la plus pertinente, s'il y a une quasi-certitude qu'elle correspond exactement au problème évoqué et une synthèse brève de celle-ci.
## Pourquoi ?
Les utilisateurs prennent trop de temps à chercher les fiches.

## Questions et réponses retenues
cf. e-mail [demande-initiale.md](demande-initiale.md) et entretien téléphonique Mme Nadia Ferrand :

- on ne fait que de la recherche et lecture seule de fiches
- tout ce qui est écriture de nouvelles fiches n'est pas traité
- pas de collecte de statistiques d'usage.

Conversation avec la DSI :
- LLM derrière LLMLite: Claude ou OpenAI sans contrôle dessus.
- l'interface est en ligne de commande, python cf. diagramme [schema-cadre-technique.md](schema-cadre-technique.md)

## Parcours
Le technicien support ouvre un terminal, il saisit des mots clés de l'appel, voit la liste des notes relatives et peut les consulter. Il peut faire cela à la chaîne.

| Étape | Qui | Fait quoi |
|-------|-----|------------|
| 1 | Technicien support | Ouvre un terminal |
| 2 | Technicien support| Saisit des mots clés ou une question |
| 3 | Technicien support | Il voit la liste de notes pertinentes et un résumé d'une réponse directe, si évidente |
| 4 | Technicien support | Il peut ouvrir la note qu'il souhaite |
| 5 | Technicien support | Retour à 2 |

## User stories
| User story | Obtention résumé et listing fiches pertinentes |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | J'ai ouvert la console de l'application |
| **Lorsque** | j'écris des mots clés ou une question et appuie sur entrée |
| **Alors** | Je vois un résumé optionnel de réponse, un nombre de fiches pertinentes, et numérotées : une liste de fiches pertinentes à ma demande, par ordre décroissant de pertinence |

| User story | Obtention résumé & listing fiches vide |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | J'ai ouvert la console de l'application |
| **Lorsque** | J'écris des mots clés ou une questions sans fiche pertinente |
| **Alors** | Je vois une réponse : aucune fiche pertinente trouvée. |

| User story | Ouverture fiche à partir de listing |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | J'ai déjà une liste de résultats non vide |
| **Lorsque** | J'entre un numéro de fiche et appuie sur entrée |
| **Alors** | Je vois la fiche en plein écran et peux quitter pour revenir au listing précédent |

| User story | Nouvelle requête |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | J'ai déjà fait une requête |
| **Lorsque** | Je fais le raccourci Ctrl+C |
| **Alors** | J'entre dans une nouveau prompt juste après l'ancien |

| User story | Sortie de la console |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | J'ai déjà fait une requête |
| **Lorsque** | Je fais le raccourci Ctrl+D |
| **Alors** | Je sors de l'application | 


## Critères d’acceptation

## Objectifs d’accessibilité
