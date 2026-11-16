
# Besoin : assistant des fiches support

## Questions et réponses retenues


Question 1 : Comment l'assistant doit-il rechercher les fiches ?

Il doit rechercher dans les titres et le contenu des fiches existantes pour retrouver celle qui correspond à la demande.

Question 2 : Le technicien peut-il utiliser quelques mots-clés ?

Oui. Nadia considère cette possibilité comme pratique, car ses techniciens n'ont pas tous des compétences techniques avancées.

Question 3 : L'assistant doit-il indiquer la source de ses réponses ?

Oui, à chaque fois. Nadia insiste sur la nécessité d'afficher le titre exact de la fiche utilisée.

Question 4 : Pourquoi faut-il indiquer le titre exact ?

Pour que le technicien puisse retrouver la fiche dans le système déjà utilisé par l'entreprise et éventuellement la compléter.

Question 5 : Faut-il afficher toute la fiche ?

Nadia souhaite surtout obtenir les informations utiles à la question.

Question 6 : Que faire si plusieurs fiches correspondent ?

Proposer plusieurs possibilités lorsque l'assistant ne peut pas déterminer avec certitude quelle fiche convient.

Question 7 : Que faire si aucune fiche ne correspond ?

Signaler l'absence de fiche. La création d'une nouvelle fiche et la préparation d'un brouillon ont été évoquées.

Question 8 : Peut-on demander la liste des fiches disponibles ?

Cette possibilité a été évoquée pendant l'entretien, sans confirmation claire de son fonctionnement exact.

Question 9 : Quel format utilisent les fiches ?

Nadia pense qu'elles sont au format Markdown, mais elle exprime une incertitude sur ce point.

Question 10 : Comment nommer les fichiers ?

Les noms doivent être en minuscules, sans espaces, avec des tirets entre les mots.

Question 11 : Quelle structure utilisent les fiches ?

Nadia indique que les exemples comportent un titre, des étapes de résolution et une vérification finale.

Question 13 : Quelles sont les limites techniques ?

Une limite qui pourrait correspondre à 20 Ko par fiche est évoquée, ainsi que des limites de jetons.


## Parcours

### Parcours 1 : rechercher une fiche existante

Étape 1 - Technicien support :
Saisit une question ou quelques mots-clés concernant le problème rencontré par un client.

Étape 2 - Assistant :
Recherche les informations correspondantes dans les titres et le contenu des fiches existantes.

Étape 3 - Service d'IA :
Aide à préparer une réponse à partir des informations retrouvées.

Étape 4 - Assistant :
Affiche les informations utiles et le titre exact de la fiche utilisée.

Étape 5 - Technicien support :
Consulte la réponse et peut retrouver la fiche complète dans son système habituel.


### Parcours 2 : plusieurs fiches correspondantes

Étape 1 - Technicien support :
Saisit une demande qui peut correspondre à plusieurs fiches.

Étape 2 - Assistant :
Recherche les fiches correspondantes.

Étape 3 - Assistant :
Présente plusieurs possibilités au technicien.

Étape 4 - Technicien support :
Consulte les propositions pour identifier la fiche adaptée.


### Parcours 3 : aucune fiche correspondante

Étape 1 - Technicien support :
Recherche une procédure qui n'existe pas encore dans les fiches disponibles.

Étape 2 - Assistant :
Recherche dans les fiches existantes.

Étape 3 - Assistant :
Signale qu'aucune fiche correspondante n'a été trouvée.

Étape 4 - Technicien support :
Demande la préparation d'une nouvelle fiche.

Étape 5 - Service d'IA :
Propose un brouillon de procédure.

Étape 6 - Technicien support :
Consulte le brouillon proposé.


## User story

En tant que technicien du support,

je veux pouvoir retrouver les fiches de procédure à partir d'une question ou de mots-clés, obtenir le titre exact de la source utilisée et disposer d'un brouillon lorsqu'une procédure manque,

afin de retrouver plus facilement les informations nécessaires pour répondre aux demandes des clients.


## Critères d'acceptation

### Critère 1 : recherche dans les fiches

Étant donné qu'une fiche existante contient des informations correspondant à la recherche,

Quand le technicien saisit les mots-clés de cette recherche,

Alors l'assistant propose la fiche correspondante.


### Critère 2 : recherche dans le contenu

Étant donné qu'une information recherchée apparaît dans le contenu d'une fiche,

Quand le technicien recherche cette information,

Alors l'assistant peut retrouver cette fiche même si les mots recherchés ne figurent pas dans son titre.


### Critère 3 : indication de la source

Étant donné que l'assistant utilise une fiche pour répondre à une question,

Quand il affiche sa réponse,

Alors il affiche également le titre exact de cette fiche.


### Critère 4 : informations utiles

Étant donné qu'une fiche contient une procédure correspondant à la question du technicien,

Quand l'assistant répond,

Alors il présente les informations de la fiche en rapport avec la question.


### Critère 5 : plusieurs fiches correspondantes

Étant donné que plusieurs fiches correspondent à une demande,

Quand le technicien effectue sa recherche,

Alors l'assistant propose plusieurs fiches correspondantes avec leurs titres.


### Critère 6 : absence de fiche

Étant donné qu'aucune fiche existante ne correspond à la recherche,

Quand le technicien effectue sa demande,

Alors l'assistant affiche un message indiquant qu'aucune fiche correspondante n'a été trouvée.


### Critère 7 : préparation d'un brouillon

Étant donné qu'une nouvelle procédure doit être documentée,

Quand le technicien demande un brouillon de fiche,

Alors l'assistant présente une proposition de nouvelle fiche.






