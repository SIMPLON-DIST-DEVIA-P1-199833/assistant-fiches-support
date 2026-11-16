# Besoin : assistant des fiches support

## Questions et réponses retenues
Qui à accès aux fiches ? 
*Les techniciens valident et ont accès aux fiches. Tous les techniciens ont accès. Pour générer les réponses, le service d'IA aussi*
Lors d'une réponse, le technicien doit-il donner la fiche source ?
*Oui, un technicien doit pouvoir se référer précisément à une fiche*
Quelle forme de réponse ? 
*Mot-clés si c'est pertinent, sinon texte complet*
Format des fiches ? 
*Markdown*
Quelle(s) règle(s) pour la nomenclature ? 
*kebab-case : **des-mots-separes-par-tiret-du-six***
Accessibilité ? 
*L'outil doit pouvoir être lu par un logiciel de lecteur d'écran*
Temps de réponse maximum ? 
*30 sec*
Opération(s) interdite(s) ? 
*Modifier et écraser les fiches*
Taille maximum d'une fiche ? 
*20 ko*
Consommation de token ? 
*Oui, à raison de 60000 token/session et 10 appels/session*
Heures de service ? 
*9h à 17h*
## Parcours

| Étape | Qui | Fait quoi |
| :---: | --- | --- |
| 1 | Technicien | questionne l'agent IA |
| 2 | Agent IA | Vérifie la liste de fiche actuel en fonction de la demande du technicien |
| 3 | LiteLLM | Expose une API IA afin de répondre au demande de agent IA  |
| 4 | Responsable du support | encadre les techniciens sur l'utilisation de l'agent IA et les bonnes pratiques  |


## User story

**En tant que** techniciens, **je veux**  retrouver rapidement les fiches et les informations par une barre de recherche, **afin de** répondre corectement et rapidement aux clients ou en cas d'absence de fiche la possibiliter de la crée de manière assiter.

**En tant que** techniciens, **je veux**  être informer des erreur de recherche, **afin de** ne pas attendre plus de 30 secondes après la recherche avec un client en ligne.

**En tant que** responsable du support, **je veux** que les fiches crée respect une même mise en forme, une convention de nomamage kebab-case **afin de** garder une uniformiter des fiches et une meilleur lisibilité.

**En tant que** responsable du support, **je veux** que les fiches ne soit crée, modifier ou supprimer que sur validation d'un technicien, **afin de** garder que des fiches correct et utilisable.

**En tant que** responsable du support, **je veux** que les appel a l'outil IA soit surveiller et limiter, **afin de** limiter les erreur et les surcout éventuel limite 60000 tok.

## Critères d’acceptation

**Étant donné** il y a 1 fiche correspondant a la recherche,<br>
**quand** le technicien effectue une recherche via l'agent IA,<br>
**alors** l'agent lui donne une  réponse avec le lien vers la fiche concerner.

**Étant donné** il y a pluisieurs fiches correspondant a la recherche,<br>
**quand** le technicien effectue une recherche via l'agent IA,<br>
**alors** l'agent lui répond avec le noms des fiches concerner et lui donne les liens vers les fiches.

**Étant donné** il n'y a pas de fiche correspondant a la recherche,<br>
**quand** le technicien effectue une recherche via l'agent IA,<br>
**alors** l'agent lui propose un brouillon de fiche partielement completer et propose de la modifier et de l'enregistrer.

**Étant donné** une erreur de fonctionnement de l'agent,<br>
**quand** le technicien effectue une recherche via l'agent IA,<br>
**alors** le système retourne une erreur en max 30 seconde.

**Étant donné** une fiche et crée par l'agent,<br>
**quand** le technicien effectue une recherche via l'agent IA sans correspondance,<br>
**alors** la fiche respect les conditions de nommage et de mise en forme et n'est crée que sur validation d'un technicien.

**Étant donné** une demande non comforme par un technicien (taille, nombre de requete),<br>
**quand** le technicien effectue une recherche via l'agent IA,<br>
**alors** le système retour une erreur avec les détails qui ne sont pas comforme.


## Objectifs d’accessibilité
