# Commandes Git

## Remote

gh auth login +token
- Authentification GitHub CLI avec un token

git push --set-upstream origin master
- Pousse la branche master vers origin et configure le suivi

git remote -v
- Affiche la liste des dépôts distants avec leurs URLs

git remote set-url origin https://github.com/laurentcoufinal/mincursor.git
- Modifie l'URL du dépôt distant origin

git push origin master
- Pousse la branche master vers le dépôt distant origin

git push origin branch-name
- Pousse une branche spécifique vers origin

git pull origin master
- Récupère et fusionne les modifications de origin/master dans la branche locale

git fetch origin
- Récupère les modifications du dépôt distant sans les fusionner

git clone https://github.com/user/repo.git
- Clone un dépôt distant dans un nouveau dossier

git remote add origin https://github.com/user/repo.git
- Ajoute un nouveau dépôt distant nommé origin

git remote remove origin
- Supprime le dépôt distant origin

## Local

git init
- Initialise un nouveau dépôt Git dans le répertoire courant

git add .
- Ajoute tous les fichiers modifiés de l'arborescence courante à l'index

git add file.txt
- Ajoute un fichier spécifique à l'index

git add -A
- Ajoute tous les fichiers modifiés, nouveaux et supprimés à l'index

git commit -m "message"
- Crée un commit avec le message spécifié

git commit -am "message"
- Ajoute tous les fichiers modifiés et crée un commit en une seule commande

git commit --amend
- Modifie le dernier commit (message ou fichiers)

git commit --amend -m "nouveau message"
- Modifie le message du dernier commit

## Status et Information

git status
- Affiche l'état des fichiers (modifiés, ajoutés, supprimés)

git log
- Affiche l'historique des commits

git log --oneline
- Affiche l'historique en une ligne par commit

git log --graph --oneline --all
- Affiche l'historique avec un graphique pour toutes les branches

git log -p
- Affiche l'historique avec les différences de chaque commit

git show commit-hash
- Affiche les détails d'un commit spécifique

git diff
- Affiche les différences entre les fichiers modifiés et la version indexée

git diff --staged
- Affiche les différences entre l'index et le dernier commit

git diff file.txt
- Affiche les différences pour un fichier spécifique

git blame file.txt
- Affiche qui a modifié chaque ligne d'un fichier et quand

git show HEAD
- Affiche les détails du dernier commit

## Branches

git branch
- Liste toutes les branches locales

git branch -a
- Liste toutes les branches (locales et distantes)

git branch branch-name
- Crée une nouvelle branche sans y basculer

git branch -d branch-name
- Supprime une branche (sécurisé, échoue si non fusionnée)

git branch -D branch-name
- Force la suppression d'une branche

git checkout branch-name
- Bascule vers une branche existante

git checkout -b new-branch
- Crée une nouvelle branche et y bascule

git switch branch-name
- Bascule vers une branche (commande moderne)

git switch -c new-branch
- Crée une nouvelle branche et y bascule (commande moderne)

git merge branch-name
- Fusionne une branche dans la branche courante

git merge --no-ff branch-name
- Fusionne en créant toujours un commit de fusion

## Historique et Navigation

git log --oneline -10
- Affiche les 10 derniers commits en une ligne

git log --author="name"
- Affiche les commits d'un auteur spécifique

git log --since="2 weeks ago"
- Affiche les commits depuis une date

git log --grep="search term"
- Recherche des commits contenant un terme dans le message

git reflog
- Affiche l'historique de toutes les actions Git (même les commits supprimés)

git checkout commit-hash
- Bascule vers un commit spécifique (mode détaché)

git reset --soft HEAD~1
- Annule le dernier commit en gardant les modifications dans l'index

git reset --mixed HEAD~1
- Annule le dernier commit et retire les fichiers de l'index

git reset --hard HEAD~1
- Annule le dernier commit et supprime toutes les modifications

git reset --hard origin/master
- Réinitialise la branche locale pour correspondre à origin/master

## Stash

git stash
- Sauvegarde temporairement les modifications non commitées

git stash save "message"
- Sauvegarde avec un message descriptif

git stash list
- Liste toutes les sauvegardes stash

git stash apply
- Applique la dernière sauvegarde stash sans la supprimer

git stash pop
- Applique la dernière sauvegarde stash et la supprime

git stash drop
- Supprime la dernière sauvegarde stash

git stash clear
- Supprime toutes les sauvegardes stash

## Tags

git tag
- Liste tous les tags

git tag v1.0.0
- Crée un tag léger pour la version 1.0.0

git tag -a v1.0.0 -m "Release version 1.0.0"
- Crée un tag annoté avec un message

git push origin v1.0.0
- Pousse un tag spécifique vers le dépôt distant

git push origin --tags
- Pousse tous les tags vers le dépôt distant

git tag -d v1.0.0
- Supprime un tag local

## Configuration

git config --global user.name "Name"
- Configure le nom d'utilisateur globalement

git config --global user.email "email@example.com"
- Configure l'email globalement

git config --list
- Affiche toute la configuration Git

git config --global core.editor "code --wait"
- Configure l'éditeur par défaut pour les commits

git config --global init.defaultBranch main
- Configure la branche par défaut lors de l'initialisation

## Ignore et Clean

git clean -n
- Affiche les fichiers qui seraient supprimés (dry-run)

git clean -f
- Supprime les fichiers non suivis

git clean -fd
- Supprime les fichiers et dossiers non suivis

git rm file.txt
- Supprime un fichier du dépôt et de l'index

git rm --cached file.txt
- Retire un fichier de l'index sans le supprimer du disque

## Submodules

git submodule add https://github.com/user/repo.git path
- Ajoute un sous-module à un chemin spécifique

git submodule update --init --recursive
- Initialise et met à jour tous les sous-modules

git submodule update --remote
- Met à jour les sous-modules depuis leurs dépôts distants

## Autres Utiles

git cherry-pick commit-hash
- Applique un commit spécifique sur la branche courante

git rebase branch-name
- Rejoue les commits de la branche courante sur une autre branche

git rebase -i HEAD~3
- Rebase interactif des 3 derniers commits

git revert commit-hash
- Crée un nouveau commit qui annule les modifications d'un commit

git bisect start
- Démarre une recherche binaire pour trouver le commit problématique

git bisect good
- Marque le commit courant comme bon

git bisect bad
- Marque le commit courant comme mauvais

git bisect reset
- Termine la recherche binaire et retourne à la branche originale

## Commandes Supplémentaires Utiles

git pull --rebase origin master
- Récupère et rebase les modifications au lieu de fusionner

git fetch --prune
- Récupère les modifications et supprime les références aux branches distantes supprimées

git fetch --all
- Récupère les modifications de tous les dépôts distants

git remote show origin
- Affiche des informations détaillées sur le dépôt distant origin

git add -p
- Ajoute les modifications de manière interactive (patch)

git restore file.txt
- Restaure un fichier à sa version du dernier commit

git restore --staged file.txt
- Retire un fichier de l'index sans modifier le fichier

git checkout -- file.txt
- Restaure un fichier à sa version du dernier commit (ancienne syntaxe)

git status -s
- Affiche le statut en format court

git status -sb
- Affiche le statut en format court avec les informations de branche

git log --stat
- Affiche l'historique avec les statistiques des fichiers modifiés

git log --decorate
- Affiche l'historique avec les références (branches, tags)

git diff HEAD~1 HEAD
- Compare deux commits spécifiques

git diff branch1..branch2
- Compare deux branches

git branch -r
- Liste uniquement les branches distantes

git branch -m old-name new-name
- Renomme une branche

git branch --merged
- Liste les branches qui ont été fusionnées

git branch --no-merged
- Liste les branches qui n'ont pas été fusionnées

git merge --abort
- Annule une fusion en cours

git merge --squash branch-name
- Fusionne une branche en créant un seul commit

git cherry-pick commit1..commit2
- Applique une plage de commits

git cherry-pick --abort
- Annule un cherry-pick en cours

git rebase --abort
- Annule un rebase en cours

git rebase --continue
- Continue un rebase après résolution de conflits

git rebase --skip
- Ignore le commit courant lors d'un rebase

git revert --no-commit commit-hash
- Annule un commit sans créer de commit (modifications dans l'index)

git ls-files
- Liste tous les fichiers suivis par Git

git grep "search term"
- Recherche un terme dans tous les fichiers du dépôt

git grep -n "search term"
- Recherche avec affichage des numéros de ligne

git archive --format=zip HEAD > archive.zip
- Crée une archive ZIP du dépôt à un commit spécifique

git clone --depth 1 https://github.com/user/repo.git
- Clone un dépôt avec un historique limité (clone superficiel)

git worktree add ../path branch-name
- Ajoute un nouvel espace de travail pour une branche

git worktree list
- Liste tous les espaces de travail

git worktree remove ../path
- Supprime un espace de travail
