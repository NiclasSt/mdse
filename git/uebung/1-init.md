---
title: Übung 1 Git Setup
theme: solarized
revealOptions:
    transition: 'fade'
center: true
---
# Übung 1 Git Setup

--- 
## Initiales Setup eines Git Repository

---
### Download Git Client
Laden Sie Git von:

https://git-scm.com/downloads

---
### Installation

[X] Use git and optional Unix tools from the Windows Command Prompt
[X] Checkout as-is, commit as linux
[X] Start MINGW

---
### Generate SSH Key
In MINGW:
<iframe src="https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/#generating-a-new-ssh-key" width="1280" height="580"></iframe>

---
### Add SSH Key to your SSH Agent
<iframe src="https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/#adding-your-ssh-key-to-the-ssh-agent" width="1280" height="580"></iframe>

---
### Setup Git

```
git config --global user.name "Mona Lisa"
git config --global user.email "mona.lisa@example.com"
```


---
### Projekt anlegen
```
mkdir myfirstrepo
cd myfirstrepo
ls -lrta
git init
```

---
### Was ist passiert angelegt?
```
git status
ls -lrta
cd .git
ls -lrt
cat config
cat HEAD
```
Damit ist das Repository eigentlich fertig, allerdings ist es nur lokal

---
### Erster Commit
```
vim readme.md
git status
git add readme.md
git commit -m "Mein erster Commit"
```

---
### Create Github Account
 Erstellung eines Account auf [GitHub](www.github.com)

---
### Public SSH key hinzufügen
1. Gehen Sie auf [github.com]
2. Gehen Sie auf "Your profile", rechts oben
3. Edit Profile
4. SSH and GPG keys
5. New SSH Key
6. Kopieren Sie den .pub key aus dem .ssh Ordner in ihrem Home Verzeichnis 

---
### Connect to GitHub
1. Erstellen Sie ein leeres Repository of Github.com (New Repository), vergeben Sie lediglich einen Namen, z.B. myfirstrepo
2. Verbinden der Repositories
```
git remote add origin git@github.com:<YourUser>/myfirstrepo.git
git push --set-upstream origin master
```



