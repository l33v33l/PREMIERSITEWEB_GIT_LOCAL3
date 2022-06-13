# À partir de cette vidéo https://www.youtube.com/watch?v=RGOj5yH7evk

# SI AVOIR CHANGÉ LE NOM D'UTILISATEUR OU DE COURRIEL

<br> git config --global user.email "nouveau courriel"
<br> git config --global user.name "nom d'utilisateur"

# CLEF SSH

Source : https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
Source : https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

POUR MAC :
<br>1 : eval "$(ssh-agent -s)"
<br>2 : open ~/.ssh/config
<br>3 : SI LE FICHIER N'EXISTE PAS, alors  
<br> touch ~/.ssh/config  
<br> open ~/.ssh/config

<br>4 : AJOUTER (SANS LES GUILLEMETS)
<br>"Host \"
<br>AddKeysToAgent yes
<br>UseKeychain yes
<br>IdentityFile ~/.ssh/id_ed25519

<br>5 : ssh-keygen -t ed25519 -C "your_email@example.com"
<br>5.1 : APPUYER SUR ENTER ET NE RIEN RENTRER (À MOINS QUE VOULOIR ENTRER UN MOT DE PASSE)
<br>6 : ssh-add -K ~/.ssh/id_ed25519 (ON PEUT ENLEVER -K SI PAS METTRE DE MOT DE PASSE) (DEPUIS MAC 12 -K et -A est remplacé par --apple-use-keychain et --apple-load-keychain)
<br>7 : AJOUTER LA CLEF AU COMPTE GIT : https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account
<br>8 : pbcopy < ~/.ssh/id_ed25519.pub

# SI VOULOIR UPDATE UN FICHIER DANS UN RÉPO LOCAL

https://docs.github.com/en/get-started/importing-your-projects-to-github/importing-source-code-to-github/importing-a-git-repository-using-the-command-line

1 : Créer dossier
2 : cd dans le dossier dans la ligne de commandes
2 : git init
3 : git status
4 : git add nomDuFichier
5 : git commit -m "" -m ""
--Créer le lien entre le dossier et le repo--
6 : Créer un repo sur git
7 : git remote add origin "lien ssh ou https sur github une fois qu'avoir créé le "
8 : git remote -v
#Pour vérifier si l'url est ajouté.
9 : git push origin main
#On peut aussi utiliser git push -u origin master. Ça permet après de juste faire "git push" les fois d'après

# SI VOULOIR TÉLÉCHARGER UN FICHIER D'UN RÉPO EN LIGNE (COMPLÉTER)

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
