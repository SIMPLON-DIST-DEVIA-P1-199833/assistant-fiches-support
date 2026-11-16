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

- on ne fait que de la recherche et lecture seule de fiches,
- p99 < 30 secondes pour retrouver la fiche pertinente (anciennement 1h30),
- tout ce qui est écriture de nouvelles fiches n'est pas traité,
- pas de collecte de statistiques d'usage,
- possiblité de créer un brouillon de réponse, si rien de pertinent ; mais la validation de ce brouillon est une action dépendant de la DSI et non des techniciens.

Conversation avec la DSI :
- LLM derrière LLMLite: Claude ou OpenAI sans contrôle dessus.
- l'interface est en ligne de commande, python cf. diagramme [schema-cadre-technique.md](schema-cadre-technique.md)

## Interactions end-to-end
La console envoie les requêtes utilisateur à une API REST ou MCP (worker) laquelle interroge une LLM pré-approvisionnées avec les fiches et renvoie à l'utilisateur la liste et le contenu de ces dernières. La création de brouillon correspond à l'insertion d'une fiche supplémentaire dans la mémoire de ce même LLM, avec une mention d'état brouillon. L'édition de brouillon (titre, corps, statut impertinent) suit ce même flux terminal => worker => IA.

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
| US1| Première requête : obtention résumé et listing fiches pertinentes |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | J'ai ouvert la console de l'application |
| **Lorsque** | j'écris des mots clés ou une question et appuie sur entrée |
| **Alors** | Je vois un résumé optionnel de réponse, un nombre de fiches pertinentes, et numérotées : une liste de fiches pertinentes (brouillon ou publiées) à ma demande, par ordre décroissant de pertinence |

| US2 | Obtention résumé & listing fiches vide |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | J'ai ouvert la console de l'application |
| **Lorsque** | J'écris des mots clés ou une questions sans fiche pertinente |
| **Alors** | Je vois une réponse : aucune fiche pertinente trouvée. Je peux créer un brouillon en appuyant sur entrée |

| US3 | Création brouillon |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | Je suis tombé sur un listing sans résultats |
| **Lorsque** | J'appuie sur entrée une seconde fois |
| **Alors** | J'entre dans un mode de création de brouillon, avec des champs titre (première question), et un champs corps (seconde question). Quand je fais le raccourci Ctrl+C je sors du brouillon en l'enregistrant. Quand je fais Echap, je sors du brouillon en l'annulant. |

| US4 | Edition brouillon |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | J'ai choisi d'ouvrir un brouillon pré-créé, parmi un listing de résultats |
| **Lorsque** | Je fais le raccourci Ctrl+E |
| **Alors** | J'entre dans un mode de modification de ce brouillon, avec la première question pour le titre, la seconde question pour le corps. Quand je fais le raccourci Ctrl+C je sors du brouillon en l'enregistrant. Quand je fais Echap, je sors du brouillon en annulant mes changements. Si je fais Ctrl+I, je peux notifier le brouillon comme impertinent, à la fois en tant que statut et indiquer la raison de l'impertinence. |

| US5 | Ouverture fiche à partir de listing |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | J'ai déjà une liste de résultats non vide |
| **Lorsque** | J'entre un numéro de fiche et appuie sur entrée |
| **Alors** | Je vois la fiche en plein écran et peux quitter pour revenir au listing précédent |

| US6 | Nouvelle requête |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | J'ai déjà fait une requête |
| **Lorsque** | Je fais le raccourci Ctrl+C |
| **Alors** | J'entre dans une nouveau prompt juste après l'ancien |

| US7 | Sortie de la console |
| --- | --- |
| **En tant que** | Technicien support |
| **Etant donné que** | J'ai déjà fait une requête |
| **Lorsque** | Je fais le raccourci Ctrl+D |
| **Alors** | Je sors de l'application | 

| US8 | Acessibilité audio |
| --- | --- |
| **En tant que** | Technicien support malvoyant |
| **Etant donné que** | J'ai tapé le mot AUDIO en prompt ou que le terminal est configuré pour mon handicap |
| **Lorsque** | Je fais quoi que ce soit |
| **Alors** | Alors, le prompt d'invite, le listing des documents, les commandes disponibles à mon contexte, etc... me sont lues et je peux faire répéter l'item précédent avec Ctrl+flèche haut, et suivant avec Ctrl+flèche bas, ou actuel avec Ctrl+flèches gauche & droite en même temps| 



## Critères d’acceptation
- La récupération de listing à partir de mots clés ou d'une phrase prend moins de 30 secondes
- Même les mots clés ou phrases plutôt mal orthographiés ou avec grammaire pauvre doivent donner lieu à des résultats : la recherche doigt être à la frontière full-text search et LLM : 
  - full-text search : des mots-clés purs, stemisation, recherche de synonyme,
  - LLM, réponse sur sens sémantique de ce qui est recherché
- Quand on enregistre un brouillon, il est directement accessible dans les résultats de recherche, sans temps d'attente perceptible pour réindexation/vidage de cache


## Objectifs d’accessibilité
- Expérience utilisateur générale (UX) : L'interface utilise des couleurs contrastantes pour toutes visisons et un surlignage des zones des fiches pertinentes à la requête de l'assistant support. Il ne doit pas avoir à trop lire pour trouver sa réponse.
- Expérience pour malvoyants : lecture textuelle & instructions audio : ceux-ci doivent pouvoir lire différentes zones textuelles de l'écran, se voir expliquer quels raccourcis adopter pour les différentes actions contextuelles. 