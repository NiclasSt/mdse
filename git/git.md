---
title: Methoden und Werkzeuge des Software Engineering
theme: solarized
revealOptions:
    transition: 'fade'
center: false
---
# Versionsmanagement <!-- .element style="font-size: 100pt;" -->

---
### Ziele Versionsmanagement
1. Eindeutigkeit, welches ist die aktuelle Version?
2. Austausch von Daten
3. Datensicherung
4. Nachvollziehbarkeit
5. Wiederherstellung einer alten Version

---
<section style="text-align: left;">

### Am Ende dieses Moduls ...
... kennen Sie die Vorteile von Versionierungssystemen

... haben Sie GIT eingerichtet

... sind Sie in der Lage GIT zu nutzen

... können Sie Versionskonflikte auflösen


----
### Lokale Datensicherung

<img src="https://github.com/progit/progit2/raw/master/images/local.png" height="450px"/>

----
### Zentrale Datensicherung
<img src="https://github.com/progit/progit2/raw/master/images/centralized.png" height="450px"/>

----
### Verteilte Datensicherung
<img src="https://github.com/progit/progit2/raw/master/images/distributed.png" height="550px"/>

---
# Git

---
## Web Ui's für GIT 
* Git Gerrit, von Google
* GitLab, Open Source
* Github, Microsoft

---
## Lifecycle einer Datei
<img src="https://github.com/progit/progit2/raw/master/images/lifecycle.png" height="570px"/><!-- .element height="80%" width="100%" -->

----
### Git Arbeitsbereiche 
<img src="https://github.com/progit/progit2/raw/master/images/areas.png" height="570px"/><!-- .element height="80%" width="100%" -->


---
## Git Befehle

----
### `git --help`
Mit **`--help`** am Ende eines Befehls können Sie sich in der Regel die Hilfe anzeigen lassen. Diese zeigt Ihnen die möglichen optionen auf.  

----
### `git config` 
Ermöglicht die Konfiguration von Git, dabei gibt es:
* Lokale Einstellungen (Je Repository)
* Globale Einstellungen 

```
git config --global user.name "Mona Lisa"
git config --global user.email "mona.lisa@example.com"
```

----
### `git init`
Initialisiert ein neues Repository

----
### `git status`
Zeigt den Status des lokalen Repositories an. 
* Auf welcher Branch befindet sich der HEAD
* Status Veränderter Dateien
* Was ist im Staging Bereich
```
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   Readme.md
```
----
### `git add`
Fügt eine Datei dem Staging Bereich des Versionskontrollsystems hinzu. 
```
git add Readme.md
```
----
### `git commit`
Sichert den aktuellen Stand des Staging Bereichs ins Repository. Dabei wird eine uuid generiert. Diese macht den Stand eindeutig identifizierbar. Der Staging Bereich wird geleert.
```
git commit -m "My first commit"
[master (root-commit) 562fbb8] My first commit
 1 file changed, 2 insertions(+)
 create mode 100644 Readme.md
 ```
----
### `git remote`
Ermöglicht den Umgang mit Remote Repositories. 
#### **`git remote add <alias> <URL>`** 
Fügt beispielsweise einen Alias hinzu. Dadurch kann leicht auf diesen verwießen werden.
```
git remote add origin https://github.com/<Nutzer>/myfirstrepo.git
```

----
#### `git push`
Aktualisiert das angegebene Repository sodass dort die Referenzen ebenfalls vorhanden sind. 
```
git push origin master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 279 bytes | 139.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
remote:
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/<Nutzer>/myfirstrepo/pull/new/master
remote:
To github.com:<Nutzer>/myfirstrepo.git
 * [new branch]      master -> master
```
----
<iframe src="./demo/1-init.md" width="1280" height="560"></iframe>

----
<iframe src="./uebung/1-init.md" width="1280" height="660"></iframe>

----
#### `git clone`
Erstellt eine lokale Kopie eines bestehenden Repositories in einem neuen Verzeichnis 
```
git clone https://github.com/<Nutzer>/myfirstrepo.git/
Cloning into 'myfirstrepo'...
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
```


---
## Branching
In git gibt es Branches die auf Commits bzw. Snapshots verweißen. Eine Branch verweißt auf einen Commit. Allerdings können auch mehrere Branches auf den gleichen Commit verweißen. Die momentan aktive Branch ist der sogenannte HEAD.

----
### `git checkout`
Ermöglicht es eine Branch auszuchecken. 
```
git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
```
Zudem können auch neue Branches erstellt werden z.b. mit
```
git checkout -b testing
Switched to a new branch 'testing'
```

----
### Branch testing ist aktiv
```
git checkout -b testing
```
<img src="https://github.com/progit/progit2/raw/master/images/head-to-testing.png" height="400px"/>

----
### Commit in Branch testing
```
vim neuedatei.txt
git add neuedatei.txt
git commit -m 'Add neuedatei.txt'
```
<img src="https://github.com/progit/progit2/raw/master/images/advance-testing.png" height="400px"/>

----
### Checkout master
```
git checkout master
```
<img src="https://github.com/progit/progit2/raw/master/images/checkout-master.png" height="400px"/>


----
### Commit master
```
vim readme.md
git commit -m 'Fix some minor issues'
```
<img src="https://github.com/progit/progit2/raw/master/images/advance-master.png" height="400px"/>


---
## Änderungen zusammenführen
Um Änderungen in Git zusammenzuführen gibt es die beiden Befehle **`git rebase`** und **`git merge`**. 
<img src="https://github.com/progit/progit2/raw/master/images/basic-branching-4.png" height="400px"/>

---
### `git merge`
Der Befehl fügt mehrere Historien zusammen. So können z.B. Branches zusammen geführt werden. Je nach Situation verhält sich der Befehl unterschiedlich. 
* Eine der Historien hat keine Änderung: Fast Forward
* Beide Historien haben Änderungen: Merge Commit
    * In unterschiedlichen Dateien: Automatisch
    * In gleicher Datei: Manuell

----
#### `git merge` - Fast-Forward
```
git merge hotfix
Updating f42c575..3a0874d
Fast-forward
```
<img src="https://github.com/progit/progit2/raw/master/images/basic-branching-5.png" height="400px"/>  

----
#### `git merge`
<img src="https://github.com/progit/progit2/raw/master/images/basic-branching-6.png" height="400px"/> 

In dieser Situation muss der merge einen Commit durchführen der die Änderungen zusammenführt. 

----
#### `git merge`
```
git checkout master
git fetch 
git merge iss53
```
<img src="https://github.com/progit/progit2/raw/master/images/basic-merging-2.png" height="400px"/> 

----
#### `git merge` - Konflikt
Falls git nicht in der Lage ist die Änderungen selbständig zusammenzuführen erhalten Sie einen Konflikt. Die Meldung sieht dann wie folgt aus: 
```
git merge
Auto-merging helloWorld.bat
CONFLICT (content): Merge conflict in helloWorld.bat
Automatic merge failed; fix conflicts and then commit the result.
```
Diesen Konflikt müssen Sie selbst auflösen

----
##### `git merge` - Konflikt 
 Git hat ihnen in den betreffenden Dateien Kommentare hinzugefügt. Diese sehen wie folgt aus:
```
echo Hello World 
<<<<<<< HEAD
echo Zusaetzlicher Commit aus meiner Branch
=======
echo Zusaetzlicher Commit aus einer anderen Branch
>>>>>>> 
```
* Von **`<<<<<<< HEAD`** bis **`=======`** sind die Änderungen Ihrer aktuellen Branch enthalten
* Von **`=======`** bis **`>>>>>>>`** sind die Änderungen der anderen Branch enthalten. 

----
##### `git merge` - Konflikt
1. Führen Sie die Änderungen zusammen
2. Entfernen Sie die Sonderzeichen von Git
3. Fügen Sie die Änderung mit `git add` hinzu
4. Überprüfen Sie den Status mit `git status`

Wenn alle Dateien mit Konflikten zusammengeführt sind beenden Sie den Vorgang mit 
```
git merge --continue
```

---
#### `git merge` vs `git rebase`
Eine Alternative zu `git merge` ist `git rebase`.

<img src="https://github.com/progit/progit2/raw/master/images/basic-rebase-1.png" height="400px"/> 

Wie würde das Ergebnis eines Merge aussehen?
----
##### `git merge` - Ergebnis
<img src="https://github.com/progit/progit2/raw/master/images/basic-rebase-2.png" height="400px"/> 

----
##### `git rebase`
`git rebase` wendet die Veränderung eines Commits auf einen anderen Softwarestand an. 

<img src="https://github.com/progit/progit2/raw/master/images/basic-rebase-3.png" height="400px"/> 

----
##### `git rebase` Vorsicht!!!
`git rebase` verändert die Historie D.h. Sie sollten git Rebase niemals auf Versionen anwenden die Sie mit anderen geteilt haben. 


---
#### `git fetch`
Empfängt Metainformationen aus dem Remote Repository. Informationen zu folgenden Entitäten (refs) werden abgeholt
* Branch
* Tag
* Commit

---
<iframe src="./uebung/2-paralleles-arbeiten.md" width="1280" height="660"></iframe>

---
<iframe src="./uebung/3-paralleles-arbeiten-konflikt.md" width="1280" height="660"></iframe>

---
### .gitignore

In dieser Datei können Dateien aufgenommen werden, sodass diese bei Änderungen nicht berücksichtigt werden. Auch Datei Endungen oder Reguläre ausdrücke sind möglich.
```
# ignore all .log files
*.log

# but do track lib.log, even though you're ignoring .log files above
!lib.log

# ignore the target directory
target/
```

---
#### `git log`
Zeigt die Historie von git an, besonders die Optionen **`--graph --oneline`** machen das ganze lesbar
```
git log --graph --oneline
*   92e03be (HEAD -> master, sshorigin/master) Merge remote-tracking branch 'refs/remotes/sshorigin/master'
|\
| * 02ac5df Meine Erwartungen
* | 3930dff Erwartungen 3
|/
* 1b72bf0 Meine Erwartungen 2
* 774da85 (origin/master, origin/HEAD) Feature: Contributer.md added
* 562fbb8 (newBranch) My first commit
```

---
### `git reset`
Manchmal muss man den *Arbeitsbereich*, den *Index* oder den *HEAD* verändern.
<img src="https://github.com/progit/progit2/raw/master/images/reset-workflow.png" height="400px"/> 

----
#### `git reset`
<img src="https://github.com/progit/progit2/raw/master/images/reset-start.png" height="570px"/> 

----
#### `git reset --soft`
Setzt lediglich den HEAD zurück, Index und Arbeitsbereich bleiben gleich
<img src="https://github.com/progit/progit2/raw/master/images/reset-soft.png" height="470px"/> 

----
#### `git reset --mixed`
Setzt den HEAD und Index zurück, der Arbeitsbereich bleibt gleich

<img src="https://github.com/progit/progit2/raw/master/images/reset-mixed.png" height="470px"/> 

----
#### `git reset --hard`
Setzt den HEAD, Index und den Arbeitsbereich zurück.
<img src="https://github.com/progit/progit2/raw/master/images/reset-hard.png" height="470px"/> 

----
#### `git reset` squash commits
Wenn man commits wie "WIP", "noch nicht fertig" oder "Buggy" hat, möchte man diese in der Regel zusammenführen. 

<img src="https://github.com/progit/progit2/raw/master/images/reset-squash-r1.png" height="370px"/> 

----
#### `git reset` squash commits
<img src="https://github.com/progit/progit2/raw/master/images/reset-squash-r2.png" height="570px"/> 

----
#### `git reset` squash commits
<img src="https://github.com/progit/progit2/raw/master/images/reset-squash-r3.png" height="570px"/> 

---
### END
 
---
### Mögliche ToDos
Man könnte noch:
* Eine Übung zu Squash Commits machen bzw. git rebase -i HEAD~3

---
## Externe Doku
Git Cheat Sheet: https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf
