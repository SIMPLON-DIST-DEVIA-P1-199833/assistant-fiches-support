# Besoin : assistant des fiches support

## Questions et réponses retenues

- Le technicien valide les propositions de l’assistant IA.
- L’assistant cite le titre de la fiche source utilisée pour répondre.
- Si plusieurs fiches correspondent, l’assistant laisse le technicien choisir la bonne.
- Si aucune fiche ne correspond, l’assistant crée une fiche en brouillon.
- La recherche doit permettre de retrouver une fiche rapidement. Aucun délai précis n’a été indiqué dans tes notes.
  Rédaction et format des fiches
- Les fiches sont au format Markdown.
- La rédaction doit suivre les exemples fournis : titre, Symptôme, Étapes numérotées, Vérification.
- Tu as indiqué une convention « en minuscules, sans espaces, avec des tirets - ». Il reste à préciser si elle concerne les noms de fichiers, car tes notes mentionnent les « conventions de message ».
  Accessibilité et disponibilité
- L’assistant doit être utilisable avec un lecteur d’écran.
- Le service doit fonctionner du lundi au samedi, de 9 h à 17 h.
  Gestion des erreurs
- En cas d’erreur ou de problème du système, le technicien doit être averti dans un délai maximal de 30 secondes.
- Le message doit lui demander de réessayer ultérieurement.

## Parcours

1. Parcours
   Consulter une procédure
   Étape Qui Fait quoi
   1 Technicien Saisit sa question dans le terminal.
   2 Assistant Recherche les fiches correspondantes uniquement dans le dossier autorisé.
   3 Assistant Si plusieurs fiches correspondent, affiche leurs titres et demande au technicien de choisir.
   4 Technicien Sélectionne la fiche correspondant à son problème, si un choix est demandé.
   5 Assistant Transmet la question et le contenu utile des fiches au service d’IA, via la passerelle LiteLLM imposée.
   6 Service d’IA Produit une proposition de réponse à partir des fiches transmises.
   7 Assistant Affiche la proposition et le titre de chaque fiche utilisée.
   8 Technicien Vérifie et valide la proposition avant de l’utiliser auprès du client.

Si aucune fiche ne correspond : l’assistant signale cette absence et propose de préparer un brouillon selon le parcours suivant.
Rédiger et enregistrer un brouillon
Étape Qui Fait quoi
1 Technicien Demande un brouillon et fournit les informations disponibles sur le problème et sa résolution.
2 Assistant Demande les informations manquantes nécessaires à la rédaction.
3 Technicien Complète les informations demandées.
4 Assistant Transmet les informations et la structure attendue au service d’IA via LiteLLM.
5 Service d’IA Rédige une proposition comprenant un titre, un symptôme, des étapes numérotées et une vérification.
6 Assistant Affiche le brouillon pour relecture.
7 Technicien Demande des corrections ou valide le brouillon et son enregistrement.
8 Assistant Propose un nom de fichier conforme aux conventions et vérifie si ce fichier existe déjà.
9 Technicien Si le fichier existe, confirme explicitement son remplacement ou le refuse.
10 Assistant Enregistre le brouillon dans le dossier autorisé si les validations nécessaires sont obtenues, puis affiche son nom et son statut de brouillon.

## User story

US1 — Consulter une procédure
En tant que technicien du support Batifact,
je veux obtenir une proposition de réponse fondée sur les fiches de procédure, avec leurs titres comme sources,
afin de vérifier la procédure et guider le client pendant son appel.

US2 — Choisir la fiche adaptée
En tant que technicien du support Batifact,
je veux choisir parmi les fiches proposées lorsqu’il existe plusieurs correspondances,
afin de retenir celle qui correspond au problème du client.

US3 — Créer un brouillon
En tant que technicien du support Batifact,
je veux obtenir et relire un brouillon de fiche lorsqu’aucune fiche ne répond à ma question,
afin de compléter la documentation à partir des informations dont je dispose.

## Critères d’acceptation

Consultation des fiches — US1 et US2
ID Étant donné… Quand… Alors…
CA1 Une fiche répond à la question Le technicien pose sa question L’assistant affiche une proposition de réponse fondée sur cette fiche et cite son titre.
CA2 Plusieurs fiches correspondent à la question Le technicien pose sa question L’assistant affiche leurs titres et attend son choix avant de produire la réponse.
CA3 Plusieurs fiches ont été proposées Le technicien sélectionne une fiche L’assistant produit une proposition à partir de la fiche sélectionnée et cite son titre.
CA4 Une proposition de réponse est disponible L’assistant l’affiche Le texte indique qu’elle doit être validée par le technicien.
CA5 Aucune fiche ne répond à la question Le technicien pose sa question L’assistant indique l’absence de fiche et demande les informations nécessaires pour préparer un brouillon.

Rédaction et enregistrement — US3
ID Étant donné… Quand… Alors…
CA6 Le technicien a fourni les informations sur le problème et sa résolution L’assistant produit le brouillon Celui-ci comporte un titre et les rubriques « Symptôme », « Étapes » et « Vérification », avec des étapes numérotées.
CA7 Un brouillon est produit L’assistant le présente au technicien Son statut de brouillon est explicitement indiqué et son contenu est affiché pour relecture.
CA8 Un brouillon est affiché Le technicien ne valide pas son enregistrement Aucun fichier n’est créé ou modifié.
CA9 Le technicien a validé l’enregistrement et le nom du fichier est disponible L’assistant enregistre le brouillon Un fichier .md est créé dans le dossier autorisé et un message indique son nom et confirme l’enregistrement.

Protection des fichiers — Toutes les user stories
ID Étant donné… Quand… Alors…
CA10 Un fichier se trouve hors du dossier autorisé Une demande tente de le lire L’assistant refuse l’accès et n’affiche pas son contenu.
CA11 Un emplacement se trouve hors du dossier autorisé Une demande tente d’y créer ou modifier un fichier L’assistant refuse l’opération et aucun fichier n’est créé ou modifié à cet emplacement.
CA12 Une fiche existe déjà sous le nom demandé Le technicien demande l’enregistrement L’assistant affiche le nom du fichier et demande confirmation avant de le remplacer. Le fichier reste inchangé en attendant.
CA13 Une confirmation de remplacement est demandée Le technicien refuse ou interrompt l’opération La fiche existante reste inchangée.
CA14 Le contenu du brouillon est validé et une confirmation de remplacement est demandée Le technicien confirme explicitement

## Objectifs d’accessibilité

Accessibilité et erreurs — Toutes les user stories
ID Étant donné… Quand… Alors…
CA15 Un lecteur d’écran est actif dans le terminal utilisé pour l’essai Le technicien consulte une réponse Le lecteur d’écran restitue la réponse et les titres des sources.
CA16 Un lecteur d’écran est actif L’assistant propose un choix de fiche ou demande une confirmation Le lecteur d’écran restitue les options et les instructions permettant de répondre.
CA17 Une erreur du système ou du service d’IA empêche le traitement Le technicien lance une demande Au plus tard 30 secondes après son lancement, un message indique l’échec et demande de réessayer ultérieurement.
