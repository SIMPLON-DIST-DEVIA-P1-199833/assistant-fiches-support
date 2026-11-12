# Modèle de user story et de critères d’acceptation

## 1. User story

Une user story décrit un besoin du point de vue de la personne qui utilise l’application.

> **En tant que** ‹ qui ›, **je veux** ‹ quoi ›, **afin de** ‹ pourquoi ›.

| Partie | Ce que tu y écris |
| --- | --- |
| **En tant que** | Un type d’utilisateur précis, pas « l’utilisateur » en général |
| **je veux** | Ce que la personne veut faire, sans décrire la solution technique |
| **afin de** | Le bénéfice attendu pour elle |

---

## 2. Critères d’acceptation

Un critère d’acceptation précise quand la user story est satisfaite. Chacun se vérifie par un essai, décrit en trois parties selon la méthode Gherkin (en anglais : « Given… When… Then… »).

| Situation<br>*Étant donné…* | Action<br>*Quand…* | Résultat attendu<br>*Alors…* |
| --- | --- | --- |
| L’état de départ | Ce que fait l’utilisateur | Ce qu’il constate, sans lire le code |

> [!TIP]
> Un résultat attendu se constate : « un message indique que… », « le fichier n’est pas modifié ». « Ça marche bien » ou « c’est rapide » ne se vérifient pas.

---

## 3. Exemple : la salle de réunion de la médiathèque

La mairie prête la salle de réunion de sa médiathèque (19 places, usage administratif) à la demi-journée ou à la journée. Aujourd’hui, la réservation se fait par un formulaire papier déposé en mairie.

| Demandeur | Demi-journée | Journée |
| --- | :---: | :---: |
| Habitant ou association de la commune<br>Personne morale dont le siège est dans la commune | Gratuit | Gratuit |
| Habitant ou association hors commune<br>Personne morale dont le siège est hors commune | 50 € | 80 € |

### Parcours

| Étape | Qui | Fait quoi |
| :---: | --- | --- |
| 1 | Responsable d’association | Choisit un créneau et indique la commune du siège de l’association |
| 2 | Application | Vérifie que la salle est libre et calcule le tarif |
| 3 | Service de paiement en ligne | Encaisse le montant, seulement si la réservation est payante |
| 4 | Application | Enregistre la réservation et envoie la confirmation |
| 5 | Responsable d’association | Reçoit la confirmation |

### User story

> **En tant que** responsable d’association, **je veux** réserver la salle de réunion de la médiathèque en ligne, **afin de** préparer nos réunions sans me déplacer en mairie.

### Critères d’acceptation

| Situation<br>*Étant donné…* | Action<br>*Quand…* | Résultat attendu<br>*Alors…* |
| --- | --- | --- |
| Une association dont le siège est dans la commune ; la salle est libre le samedi matin | Le responsable réserve la demi-journée | La réservation est confirmée sans paiement et un courriel de confirmation est reçu |
| Une association dont le siège est hors de la commune ; la salle est libre le samedi matin | Le responsable réserve la demi-journée | Un paiement de 50 € est demandé ; la réservation est confirmée une fois le paiement accepté |
| La salle est déjà réservée le samedi matin | Le responsable tente de réserver ce créneau | Un message indique que la salle est occupée et propose les créneaux libres de la semaine |

Le deuxième critère d’acceptation, rédigé en phrases :

> **Étant donné** une association dont le siège est hors de la commune et une salle libre le samedi matin,<br>
> **quand** son responsable réserve la demi-journée,<br>
> **alors** un paiement de 50 € est demandé, et la réservation est confirmée une fois le paiement accepté.
