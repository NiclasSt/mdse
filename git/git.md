---
title: Methoden und Werkzeuge des Software Engineering
theme: solarized
revealOptions:
    transition: 'fade'
center: false
---
<style type="text/css">
  .reveal {
   font-size: 30px;
  }
  .reveal p {
    text-align: left;
  }
  .reveal ul {
    display: block;
  }
  .reveal ol {
    display: block;
  }
  img {
   display: block ! important;
   width: auto ! important;
   margin: auto ! important;
   border: 0px;
  }
</style>

# Grundlagen der Versionskontrolle <!-- .element style="font-size: 80pt;" -->
### mit Git
---
## Inhalte
1. Ziele
2. Datensicherung
3. Git
 * Web UI
 * Grundlegende Befehle
 * Lifecycle
 * Branching
 * Paralleles Arbeiten

---
### Am Ende dieses Moduls ...
 ... kennen Sie die Vorteile von Versionskontrollsystemen    
 ... haben Sie Git eingerichtet                           
 ... können Sie Git Projekte anlegen                    
 ... können Sie Konflikte auflösen

---
## Warum?
<img style="border: 0;" src="https://svgsilh.com/svg/2154830-4caf50.svg" height="450px"/>

---
### Ziele der Versionskontrolle
1. Eindeutigkeit bzgl. der aktuellen Version
2. Austausch von Daten
3. Datensicherung
4. Nachvollziehbarkeit 
5. Wiederherstellung eines Softwarestandes

---
## Verteilte Versionskontrolle

---
### Lokale Versionskontrolle

<img src="https://github.com/progit/progit2/raw/master/images/local.png" height="450px"/>

---
### Zentrale Versionskontrolle
<img src="https://github.com/progit/progit2/raw/master/images/centralized.png" height="450px"/>

---
### Verteilte Versionskontrolle
<img src="https://github.com/progit/progit2/raw/master/images/distributed.png" height="550px"/>


---
# Git


---
## Web UI

| Produkt        | Hersteller           | Features  |
| ---------- |:----------:| ----:|
| **Gerrit**      | Google       | Review System, Changesets, Outdated  |
| **GitHub**      | Microsoft    | Marktführer, Issues, Wiki, Editor, Pull Requests |
| **GitLab**     | Open-Source / GitLab Inc.   | CI, Container Registry, Issues, WebIDE, Wiki, Merge Requests  |

---
## Lifecycle einer Datei
<img src="https://github.com/progit/progit2/raw/master/images/lifecycle.png" height="570px"/><!-- .element height="80%" width="100%" -->

---
## Git Arbeitsbereiche 
<img src="https://github.com/progit/progit2/raw/master/images/areas.png" height="570px"/><!-- .element height="80%" width="100%" -->

---
## Git Befehle

---
### `git --help`
**`--help`** am Ende eines Befehls zeigt die Hilfe an. Unter anderem werden die möglichen Parameter aufgelistet und erläutert. 

---
### `git config` 
Ermöglicht die Konfiguration von Git, dabei gibt es:
* Lokale Einstellungen (je Repository)
* Globale Einstellungen 

```
git config --global user.name "Mona Lisa"
git config --global user.email "mona.lisa@example.com"
```

---
### `git init`
Initialisiert ein neues lokales Repository im angegebenen Ordner. 

---
### `git status`
Zeigt den Status des lokalen Repositories an:
* Aktueller Branch
* Status veränderter Dateien
* Inhalt des Staging Bereichs
```
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   Readme.md
```
---
### `git add`
Fügt eine Datei dem Staging Bereich des Versionskontrollsystems hinzu. 
```
git add Readme.md
```
---
### `git commit`
Sichert den aktuellen Stand des Staging Bereichs ins Repository. Dabei wird für diesen eine eindeutige ID generiert. Der Staging Bereich wird geleert.
```
git commit -m "My first commit"
[master (root-commit) 562fbb8] My first commit
 1 file changed, 2 insertions(+)
 create mode 100644 Readme.md
 ```
---
### `git remote`
Ermöglicht den Umgang mit Remote Repositories, indem es einen Alias hinzufügt.  Dadurch kann leicht auf diesen verwiesen werden.
#### **`git remote add <alias> <URL>`** 
```
git remote add origin https://github.com/<Nutzer>/myfirstrepo.git
```

---
### `git push`
Aktualisiert das angegebene Remote Repository, sodass dort die Referenzen ebenfalls vorhanden sind. 
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
---

<iframe src="./demo/1-init.md" width="1280" height="560"></iframe>

---
## Basics: Shell Commands
* ***`mkdir <folder>`***

	Legt einen neuen Ordner an.
	
* ***`cd <folder>`***

	Navigiert in das angegeben Verzeichnis.
	
	Sonderfall: **"`cd ..`"** verlässt den Unterordner.

* ***`ls -al`*** 

	Listet alle Dateien und Ordner im aktuellen Verzechnis.

* ***`cat <file>`*** 

	Gibt den Inhalt der Datei auf die Konsole aus.

---
## Basics: VIM
* `i` für interactive mode
* `esc` für normal mode
* `:wq!` beenden *mit* speichern
* `:q!` beenden *ohne* speichern

---
## Übung 1: Git Setup

---
## Wiederholung: Lifecycle einer Datei
<img src="https://github.com/progit/progit2/raw/master/images/lifecycle.png" height="570px"/><!-- .element height="80%" width="100%" -->

---
## Wiederholung: Git Arbeitsbereiche 
<img src="https://github.com/progit/progit2/raw/master/images/areas.png" height="570px"/><!-- .element height="80%" width="100%" -->

---
#### `git clone`
Erstellt eine lokale Kopie eines bestehenden Repositories in einem neuen Verzeichnis.
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
In Git gibt es Branches, die auf Commits bzw. Snapshots verweisen. Ein Branch verweist auf einen Commit. Allerdings können auch mehrere Branches auf den gleichen Commit verweisen. Der momentan aktive Branch wird durch den HEAD bestimmt.

---
### `git checkout`
Ermöglicht es, einen Branch auszuchecken. 
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

---
### Branch testing ist aktiv
```
git checkout -b testing
```
<img src="https://github.com/progit/progit2/raw/master/images/head-to-testing.png" height="400px"/>

Wie würde ein Commit im Branch `testing` aussehen?

---
### Commit in Branch testing
```
vim neuedatei.txt
git add neuedatei.txt
git commit -m 'Added neuedatei.txt'
```
<img src="https://github.com/progit/progit2/raw/master/images/advance-testing.png" height="400px"/>

Was würde bei einem Checkout des Branches `master` passieren?

---
### Checkout master
```
git checkout master
```
<img src="https://github.com/progit/progit2/raw/master/images/checkout-master.png" height="400px"/>

Wie würde ein Commit im Branch `master` aussehen?

---
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
Der Befehl fügt mehrere Historien zusammen. So können z.B. Branches zusammengeführt werden. Je nach Situation verhält sich der Befehl unterschiedlich:

* Eine der Historien hat keine Änderung: Fast Forward
* Beide Historien haben Änderungen: Merge Commit
    * In unterschiedlichen Dateien: Automatisch
    * In gleicher Datei: Manuell

---
#### `git merge` - Fast-Forward
```
git merge hotfix
Updating f42c575..3a0874d
Fast-forward
```
<img src="https://github.com/progit/progit2/raw/master/images/basic-branching-5.png" height="400px"/>  

---
#### `git merge`
<img src="https://github.com/progit/progit2/raw/master/images/basic-branching-6.png" height="400px"/> 

In dieser Situation muss der Merge einen Commit durchführen, der die Änderungen zusammenführt.

---
#### `git merge`
```
git checkout master
git fetch 
git merge iss53
```
<img src="https://github.com/progit/progit2/raw/master/images/basic-merging-2.png" height="400px"/> 

---
#### `git merge` - Konflikt
Falls Git nicht in der Lage ist die Änderungen selbständig zusammenzuführen erhalten Sie einen Konflikt. Die Meldung sieht dann wie folgt aus: 
```
git merge
Auto-merging helloWorld.bat
CONFLICT (content): Merge conflict in helloWorld.bat
Automatic merge failed; fix conflicts and then commit the result.
```
Diesen Konflikt müssen Sie selbst auflösen.

---
##### `git merge` - Konflikt 
Git hat Ihnen in den betreffenden Dateien Kommentare hinzugefügt. Diese sehen wie folgt aus:
```
echo Hello World 
<<<<<<< HEAD
echo Zusaetzlicher Commit aus meiner Branch
=======
echo Zusaetzlicher Commit aus einer anderen Branch
>>>>>>> 
```
* **"`<<<<<<< HEAD`"** bis **"`=======`"**: Änderungen aus der lokalen Branch.
* **"`=======`"** bis **"`>>>>>>>`"**:  Änderungen aus der entfernten Branch. 

---
##### `git merge` - Konflikt
1. Führen Sie die Änderungen zusammen.
2. Entfernen Sie die Sonderzeichen von Git.
3. Fügen Sie die Änderung mit `git add` hinzu.
4. Überprüfen Sie den Status mit `git status`.

Wenn alle Dateien mit Konflikten zusammengeführt sind beenden Sie den Vorgang mit 
```
git merge --continue
```

---
#### `git merge` vs `git rebase`
Wie würde das Ergebnis eines Merge bei folgenden Ausgangszustand aussehen?

<img src="https://github.com/progit/progit2/raw/master/images/basic-rebase-1.png" height="400px"/> 

---
##### `git merge` - Ergebnis
<img src="https://github.com/progit/progit2/raw/master/images/basic-rebase-2.png" height="400px"/> 

---
##### `git rebase`
`git rebase` wendet die Veränderung eines Commits auf einen anderen Softwarestand an. 

<img src="https://github.com/progit/progit2/raw/master/images/basic-rebase-3.png" height="400px"/> 

---
##### `git rebase` Vorsicht!!!
`git rebase` verändert die Historie. D.h. Sie sollten Git Rebase niemals auf Commits anwenden, die Sie bereits mit anderen geteilt haben. 

---
#### `git fetch`
Empfängt Informationen aus dem Remote Repository. Folgenden Entitäten (refs) werden abgeholt:
* Branch
* Tag
* Commit

Der HEAD wird noch nicht verändert.

---
## Übung 2 & 3 - Paralleles Arbeiten (mit Konflikt)

---
### .gitignore

In dieser Datei können Dateien aufgenommen werden, sodass diese bei Änderungen nicht berücksichtigt werden. Auch Dateiendungen bzw. Wildcard Patterns sind möglich.
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
Zeigt die Historie von Git an. Die Option **`--graph --oneline`** verbessert die Lesbarkeit.
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

---
#### `git reset`
<img src="https://github.com/progit/progit2/raw/master/images/reset-start.png" height="570px"/> 

---
#### `git reset --soft`
Setzt lediglich HEAD zurück, Index und Arbeitsbereich bleiben gleich.
<img src="https://github.com/progit/progit2/raw/master/images/reset-soft.png" height="470px"/> 

---
#### `git reset --mixed`
Setzt HEAD und Index zurück, der Arbeitsbereich bleibt gleich.

<img src="https://github.com/progit/progit2/raw/master/images/reset-mixed.png" height="470px"/> 

---
#### `git reset --hard`
Setzt HEAD, Index und Arbeitsbereich (Vorsicht!) zurück.
<img src="https://github.com/progit/progit2/raw/master/images/reset-hard.png" height="470px"/> 

---
#### `git reset` squash commits
Wenn man Commits wie "WIP", "noch nicht fertig" oder "Buggy" hat, möchte man diese in der Regel zusammenführen. 

<img src="https://github.com/progit/progit2/raw/master/images/reset-squash-r1.png" height="370px"/> 

---
#### `git reset` squash commits
<img src="https://github.com/progit/progit2/raw/master/images/reset-squash-r2.png" height="570px"/> 

---
#### `git reset` squash commits
<img src="https://github.com/progit/progit2/raw/master/images/reset-squash-r3.png" height="570px"/>

---
## THE END

---
## Links
* [Git Cheat Sheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)
* [Git Book](https://git-scm.com/book/)
* [Source Tree](https://www.sourcetreeapp.com/) (Git GUI)