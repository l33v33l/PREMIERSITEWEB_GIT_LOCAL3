# Configurer GitHub

## Table des matières

1. [Mettre à jour courriel ou nom d'utilisateur](#Si-avoir-changé-le-nom-d'utilisateur-et-le-courriel)
1. [Clef SSH](#2---créer-une-clef-ssh-et-lassocié-au-compte)
   - [Étapes pour MAC](#21---étapes-pour-mac)
     <!--- Ajouter - pour inclure un niveau inférieur dans la table des matières -->
     <!--- Commentaire https://www.jamestharpe.com/markdown-comments/ -->
1. [À partir d'un repo local](#3---à-partir-dun-repo-local)
1. [À partir d'un repo en ligne](#4---à-partir-dun-repo-en-ligne)
1. [Créer une nouvelle branche](#5---créer-une-nouvelle-branche)
1. [Sources](#5---sources)

## 1 - Si avoir changé le nom d'utilisateur et le courriel

- git config --global user.email "nouveau courriel"
- git config --global user.name "nom d'utilisateur"

## 2 - Créer une clef SSH et l'associé au compte

- Source : https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
- Source : https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

### 2.1 - Étapes POUR MAC

- 1 : eval "$(ssh-agent -s)"
- 2 : open ~/.ssh/config
- 3 : SI LE FICHIER N'EXISTE PAS, alors faire ceci
  - 3.1 : touch ~/.ssh/config
  - 3.2 : open ~/.ssh/config
- 4 : AJOUTER DANS LE FICHIER (SANS LES GUILLEMETS)
  "Host \"
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519

- 5 : ssh-keygen -t ed25519 -C "your_email@example.com"
  - 5.1 : APPUYER SUR ENTER ET NE RIEN RENTRER (À MOINS QUE VOULOIR ENTRER UN MOT DE PASSE)
- 6 : ssh-add -K ~/.ssh/id_ed25519
  - ON PEUT ENLEVER -K SI PAS METTRE DE MOT DE PASSE) (DEPUIS MAC 12 -K et -A est remplacé par --apple-use-keychain et --apple-load-keychain)
- 7 : AJOUTER LA CLEF AU COMPTE GIT : https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account
- 8 : pbcopy < ~/.ssh/id_ed25519.pub

## 3 - À partir d'un repo local

https://docs.github.com/en/get-started/importing-your-projects-to-github/importing-source-code-to-github/importing-a-git-repository-using-the-command-line

- 1 : Créer dossier
- 2 : cd dans le dossier dans la ligne de commandes
- 3 : git init
- 4 : git status
- 5 : git add nomDuFichier
- 6 : git commit -m "" -m ""

<u> Créer le lien entre le dossier et le repo <u>

- 7 : Créer un repo sur git
- 8 : git remote add origin "lien ssh ou https sur github une fois qu'avoir créé le dépôt"
- 9 : git remote -v
  - Pour vérifier si l'url est ajouté.
- 10 : git push origin main
  - On peut aussi utiliser git push -u origin master. Ça permet après de juste faire "git push" les fois d'après

## 4 - À partir d'un repo en ligne

1 : Créer dossier
2 : cd dans le dossier dans la ligne de commandes
git status

git commit . = commit tous les fichiers

git commit - m "text" -m "autre message"

    Premier ""  = commentaires après le commit
    Deuxième "" = pour la description

git push = envoyer sur la base de données.

puis, besoin d'utiliser un clef ssh

~ ssh-keygen -t rsa -b 4096 -C "mettre son adresse courriel"

~ ls | grep testkey
alors on va voir la clef publique et privée
.pub = clef publique
sans .pub, alors garder privé.

~ cat testkey.pub

- copier coller. ou ~ pbcopy < ~ >

Puis aller sur SSH and GPG keys dans le compte + add new.

~ vim ~/.ssh/config

Puis copier-coller à la fin

Host \*
AddKeysToAgent yes
UseKeychain yes
IdentityFile ~/.ssh/id_ed25519

ET ÇA

ssh-add -K ~/.ssh/id_ed25519

ET ÇA

git push origin main

## 5 - Créer une nouvelle branche

- 1 : git branch
  Pour savoir quels sont les branches disponibles
- 2 : git checkout -b nom_de_la_nouvelle_branche
  Exemple : feature-...-...
  Exemple 2 : feature*...*...
  ** Ça doit être le plus descriptif possible et utiliser les conventions **
- 3 : git checkout main
  Pour changer de branche

## 6 - Sources

- Vidéo qui couvre en général le sujet : https://www.youtube.com/watch?v=RGOj5yH7evk

Test Test Test Test
