# Commandes Git

Git enregistre l’historique de tes fichiers sur ton poste et l’échange avec GitHub. Le fork et la demande de fusion se font sur le site GitHub : voir [Fork et demande de fusion sur GitHub](github-demande-de-fusion.md).

## Vérifie ta configuration

Dans un terminal :

```sh
git --version
git config --global user.name
git config --global user.email
```

Si le nom ou le courriel ne s’affiche pas, renseigne-les. Utilise le courriel de ton compte GitHub :

```sh
git config --global user.name "Prénom Nom"
git config --global user.email "ton-courriel@exemple.fr"
```

## Clone ton fork

Sur la page de ton fork, clique sur **Code** et copie l’adresse HTTPS. Dans un terminal, place-toi dans le dossier de tes projets :

```sh
git clone https://github.com/<ton-compte>/assistant-fiches-support.git
cd assistant-fiches-support
git status
```

`git status` indique la branche courante, `main`, et les fichiers modifiés. Utilise-la avant chaque commit.

## Commite et pousse

Après avoir enregistré `docs/besoin.md` :

```sh
git status
git add docs/besoin.md
git commit -m "Rédige le besoin de l’assistant"
git push
```

- `git add` choisit les fichiers à inclure dans le prochain commit.
- `git commit` enregistre ces fichiers dans l’historique local, avec un message qui décrit le changement.
- `git push` publie tes commits dans ton fork. Au premier `git push`, GitHub te demande de te connecter.

Ouvre ton fork sur GitHub et vérifie que `docs/besoin.md` contient ton travail.

## Compare deux versions

```sh
git log --oneline
git diff <commit-avant> <commit-après> -- docs/besoin.md
```

`git log --oneline` affiche l’identifiant court de chaque commit, du plus récent au plus ancien. `git diff` montre les lignes retirées (`-`) et ajoutées (`+`) entre les deux commits. Appuie sur `q` pour quitter l’affichage.
