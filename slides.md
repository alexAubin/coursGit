title: Introduction à Git
class: animation-fade
layout: true

---

<br/>

.center[
![](img/logogit.png)

# {{title}}

### Gestion du contrôle de versions 

![](img/tree.png)
]

---

class: impact

## Hello, world!

---

## À propos de moi

.col-12[
.col-4[
.center[
![](img/me.jpg)
]
]

.col-8[.center[
<br>
<br>
`https://github.com/alexAubin`
<br>
<br>
`alex.aubin@mailoo.org`
<br>
<br>
]]
]

.col-4[.center[
Ingénieur/Physicien

![](img/cern.png)
</br>
![](img/particles.jpg)
]]

.col-4[.center[
Dev / adminsys / ...

![](img/yunohost.png)
![](img/arn.png)
![](img/odoo.png)
]]

.col-4[.center[
Formateur

![](img/python_arduino_linux.png)
]]

---

## À propos de vous

---

## Organisation

- 7h de formation par jour
- 9h -> 12h30
- 13h30 -> 17h

## Évaluation (par vous) le dernier jour


---

## Plan

- 0 : Intro : pourquoi Git ?
- 1 : Les bases : dépôt, commit, état des fichiers
- 2 : Explorer un dépôt : git log, lire le graphe, ...
- 3 : Les branches : création, merge, gestion des conflits
- 4 : Les forges : remote, merge request, ...
- 5 : Bonnes pratiques et tips pour la vie quotidienne
- 6 : Intégration continue avec GitLab

---

## Méthode de travail

- Je met à disposition au fur à mesure le support
- Illustration de chaque partie par des exercices
- Distanciel : travail sur des machines guacamole

---

class: impact

## Introduction

### Les gestionnaires de version


---

## Les gestionnaires de version

La vie sans gestionnaire de version :
- versionnement "à l'arrache" (on copie / partage un .zip du code)
- on ne sait plus ce qu'on a modifié depuis le moment où ça marchait
- très compliqué (si ce n'est impossible) de travailler en parallèle et fusionner les changements

.center[
-> impossible de gérer le projet correctement sur plusieurs mois ou avec plus que 2 ou 3 personnes
]

---

## Les gestionnaires de version

**Garder un historique précis de l'évolution du code**
- pouvoir parler de manière précise d'un état du code
- retrouver quand (et idéalement pourquoi) une modification a été faite

**Permettre et structurer le travail collaboratif**
- possibilité de travailler en parallèle
- partager ses modifications, les fusionner, résoudre les conflits

**Une pièce centrale connectée aux autres aspects du travail de dev**
- suivi de bug, fusio-demandes, revue de code, ...
- intégration continue, déploiement continu (CI/CD) 

---

## Les gestionnaires de version

En pratique :
- à chaque modification de fichiers, on peut **sauvegarder un nouvel état** dans l'historique
- on peut remettre le répertoire de travail dans **un état antérieur**
- ou bien d'**inspecter les différences** entre maintenant et un état antérieur
- adapté au suivi des fichiers texte (pas forcément du code)
    - une collection de recettes ou le code pénal peut être géré avec Git ;)
    - ... on peut aussi suivre des fichiers binaires (par ex. images ou pdf ou docx) mais pas pratique
    - on évite les "gros fichiers" (supérieurs à quelques Mo)

---

## Les gestionnaires de version

Des systèmes de version historique : 
- VCS (1990)
- Subversion (2000)
- Bitkeeper (2000, propriétaire)
- **Git** (2005)
- Mercurial (2005)
- (Bazaar (2005))

Bitkeeper marque l'apparition des systèmes de version "décentralisé", c'est-à-dire qu'il n'y a plus de dépot central auquel il faut être connecté pour pouvoir travailler.

---


.center[
![](img/logogit.png)
## Git
]

Git est créé en 2005 par Linus Torvalds pour les besoins du noyau Linux, et a été pensé comme un gestionnaire **décentralisé**. La plateforme GitHub a aussi beaucoup contribué à son adoption, ce qui fait de Git le **standard de-facto**, notamment dans la communauté libriste.

>quand on lui a demandé pourquoi il avait appelé son logiciel “git”, qui est à peu près l'équivalent de “connard” en argot britannique, Linus Torvalds a répondu “je ne suis qu'un sale égocentrique, donc j'appelle tous mes projets d'après ma propre personne. D'abord Linux, puis Git.” ». 

---

## Git

Git est aussi connu pour son nommage des commandes qui n'est pas évident (typiquement `git checkout` permet de faire au moins 3 ou 4 choses différentes suivant comment on l'utilise :/)

.center[
![](img/gitxkcd.png)
]

---

.center[
![](img/gitiseasier.png)
]

---

## GitHub, GitLab : les "forges" Git

.center[
![](img/logogithubgitlab.png)
]

GitHub et GitLab sont des plateformes en ligne qui ont popularisé Git. 

Il faut néanmoins bien comprendre que ces plateformes sont indépendantes de **Git** au sens où il est tout à fait possible de construire un projet sans passer par ces plateformes ... (par ex. le développement de Linux se passe par échange de patch Git par emails !!) 

Ces « forges » sont "juste" des plateforme connues, gérée par des entreprises, sur laquelle on peut **publier son code**, et surtout qui **permet facilement de proposer ses modifications** à des projets.

On peut résumer / carricaturer en disant que **GitHub, c'est le réseau social des développeur.euse.s** (voir leurs CVs).

---

## Les intégrations Git dans les IDE

Là encore : attention à ne pas confondre Git et les extensions qui permettent d'interagir avec Git au travers d'autres outils.

Par exemple, les extensions qui intègrent Git dans VS Code (ou votre IDE favoris) ne font que "traduire" vos clics en commande Git.

---

## Pendant cette formation

- **git** : Comprendre les notions et connaître les commandes fondamentales
- **VScode**/**Eclipse** : Savoir interagir avec Git au travers des intégrations disponibles
- **GitLab** : Savoir publier / récupérer du code, et créer des merge requests
- Bonnes pratiques, méthodes de travail











---

class: impact

# 1. Les bases

## Dépôt, commit, état des fichiers

---

## 1. Dépôt, commit, état des fichiers

Pour travailler avec Git, il faut commencer par avoir un dépôt de code.

Un dépôt git c'est : 
- l'historique des états des fichiers depuis le début du projet
- d'autres méta-données : commentaire des commit, références (branches, tags, ..)
- le tout est stocké dans un dossier `.git`

---

## 1. Dépôt, commit, état des fichiers

Pour avoir un dépôt de code :
- soit on a démarre un nouveau dépôt avec `git init`
- soit on récupère un dépôt existant avec `git clone <addresse>`
    - classiquement cloner un dépôt hébergé sur GitHub via HTTP: `git clone https://github.com/yunohost/moulinette`
    - ou via SSH, par exemple avec un dépot GitLab : `git clone git@gitlab.com:coopaname/odoo.git`

Lorsqu'on travaille avec des dépôts privés, il faut potentiellement s'authentifier:
- soit avec des tokens (par exemple `git clone https://user:token@gitlab.com/org/depo`
- soit via une clef SSH, dans ce cas `git` demande interactivement le mot de passe pour déverouiller la clef


---

## 1. Dépôt, commit, état des fichiers

On manipule souvent un dépôt qui fait référence à une sorte de "dépôt central officiel" (typiquement sur GitHub ou GitLab)

NÉANMOINS, grâce au **caractère décentralisé de Git** : 
- vous n'avez absolument **pas besoin de d'abord créer un dépôt sur une forge**, vous pouvez juste faire `git init` en local et voir plus tard
- vous pouvez **travailler hors-ligne et synchroniser votre travail plus tard** (`git pull`/`push`)
- certains projets travaillent sans que tout passe par un dépôt central <small>(voir [cette page](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows))</small>
- il peut y avoir plusieurs "dépôt centraux / officiels", par exemple si le code est publié sur plusieurs forges

---

## 1. Dépôt, commit, état des fichiers

Voir l'état du dépot de code : `git status`

.center[
***C'est une des commandes les plus importantes,***

***je la tape quasiment avant et après chaque commande !!***
]

```text
$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	presentation.md
	TODOLIST
    templates/
    img/

nothing added to commit but untracked files present (use "git add" to track)
```

(Bon, ici rien de spécial, mais on y reviendra)

---

## 1. Dépôt, commit, état des fichiers

Dans notre dépôt de code, il faut maintenant ajouter des fichiers que l'on souhaite versionner à l'aide de `git add` 
<small>(eh oui, les fichiers ne sont pas automagiquement et systématiquement versionnés !)</small>

```bash
$ git add presentation.md
$ git add exercices/*.md
$ git add img/*
```

---

## 1. Dépôt, commit, état des fichiers

Les fichiers sont passés de "untracked" (non versionnés) à "staged" (prévus pour le prochain commit)

```text
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   presentation.md
	new file:   exercices/1_les_bases.md
	new file:   img/arbre_git.jpg

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	TODOLIST
```

---

## 1. Dépôt, commit, état des fichiers

On peut ensuite créer notre propre commit avec `git commit -m 'Commit initial'`

Un commit c'est :
- l'équivalent d'un "amendement" à l'assemblée nationale, ou d'une "transaction"
- l'action de "graver dans le marbre" ses changements
- l'élément fondamental de l'historique git

.center[
Idéalement, un commit est un ensemble de changements "atomiques" cohérents entre eux <small>(on essaye de pas changer d'un seul coup 15 trucs qui n'ont rien à voir)</small>
]

---

## 1. Dépôt, commit, état des fichiers

Techniquement parlant, un commit c'est :
- une date
- un commentaire (obligatoire!)
- un auteur (+ commiteur)
- 0, 1 ou 2 commit parent
- le différentiel avec le commit parent
- un identifiant unique qui est hash SHA1 des différentes métadonnées

```text
$ git log
commit c49659ebe26fd8a56495e7ef3b3ce311b2d21554 (HEAD -> main)
Author: Alexandre Aubin <alex.aubin@mailoo.org>
Date:   Fri May 26 18:10:18 2023 +0200

    Commit initial
```

---

## 1. Dépôt, commit, état des fichiers

... et maintenant l'état de notre dépôt :

```
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	TODOLIST

nothing added to commit but untracked files present (use "git add" to track)
```

---

## 1. Dépôt, commit, état des fichiers

La première fois que l'on fait un commit sur un système, git imposera que l'on définisse une identité : 

```bash
$ git config --global user.name "Camille Dupont"
$ git config --global user.email "camille@dupont.org"
```

Ces informations sont stockées dans fichier `.gitconfig` dans votre répertoire personnel:

```text
$ cat ~/.gitconfig
# This is Git's per-user configuration file.
[user]
	email = camille@dupont.org
	name = Camille Dupont
```

---

## 1. Dépôt, commit, état des fichiers

On peut déclarer que certains fichiers n'ont pas vocations à être versionné ... par exemple notre fichier `TODOLIST` ou bien les fichiers se terminant par `.bkp`, `.sav` ou `~`.

Pour cela il faut créer le fichier `.gitignore` dans le projet avec comme contenu:

```text
 TODOLIST
 *.bkp
 *.sav
 *~
```

puis effectivement versionner le fichier `.gitignore` (et le commiter) !

---

## 1. Dépôt, commit, état des fichiers

Plusieurs manière pour commiter 

```bash
$ git add .gitignore
$ git commit -m "Ajout du fichier .gitignore"
```

Commiter seulement un fichier précis (sans passer par `git add`) ... <small>mais suppose que le fichier est déjà versionné</small>

```bash
$ git commit .gitignore -m "Mise à jour de .gitignore pour ignorer d'autres fichiers"
```

Commiter tous (`-a`/`-all`) les changements listés par `git status` <small>(là aussi, seulement les fichiers déjà versionnés)</small>

```bash
$ git commit -a -m "Mon commentaire"
```

---

## 1. Dépôt, commit, état des fichiers

Pour résumer les fichiers peuvent être dans plusieurs états : 

- **staged** (prévu pour être inclu dans le prochain commit)
- **modified** (modifié)
- versionné mais pas modifié depuis le dernier commit
- **untracked** (non versionné)
- **ignored** (non versionné et ignoré par le `.gitignore`)

---

## 1. Dépôt, commit, état des fichiers

.center[
![](img/fileflow0.png)
]

---

## 1. Dépôt, commit, état des fichiers

.center[
![](img/fileflow0_min.png)
]

3 façons de voir le diff : 
- `git diff` : changements "unstaged"
- `git diff --staged` : changements "staged"
- `git diff HEAD` : changements staged+unstaged

---

## 1. Dépôt, commit, état des fichiers

.center[
![](img/fileflow0_min.png)
]



Plus rarement on peut aussi : 
- `git rm <fichier>` : supprimer et oublier (ne plus versionner) un fichier
- `git mv <fichier> <nouveau_nom>` : renommer un fichier (comme `mv` mais git-aware)

---

## 1. Dépôt, commit, état des fichiers

Les commits sont identifiés par la somme de controle SHA-1 de leur diff et méta-données (qui inclue le hash du parent)

- Par exemple `1cd11d9433f63251c9bfd0be8394b180a6dc6eb7`
- On peut toujours faire référence à ce même commit en utilisant les 7~8 premières lettres : `1cd11d94`
- On peut également faire référence au commit parent avec : `1cd11d94~`
- ... ou au parent-du-parent-du-parent avec : `1cd11d94~3`

Le fait que le hash dépends du parent empêche de pouvoir rajouter un commit dans l'historique lointain sans que ça se remarque

---

## 1. Dépôt, commit, état des fichiers

.center[
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
### Exercices
]

---

## Résumé des commandes jusqu'ici

- `git init` / `git clone <url>` : initialiser/cloner un dépôt
- `git status` : voir l'état actuel du dépôt
- `git add`, `rm`, `mv` : ajouter/supprimer/renommer des fichiers versionnés
- `git restore` ou `git reset` : remettre un fichier dans l'état initial avant modification
- `git commit` : commiter les changements 
- `git diff` : voir la différence entre le répertoire de travail et l'état initial
- `git log` : voir l'historique des commits

---

## 1. Dépôt, commit, état des fichiers

Représentation graphique des historiques Git

.center[
![](img/tree-2.png)
]

---

## Versionnement accidentel de secrets ..

- On peut avoir commité un secret (mot de passe, clef de DB ou d'API, ...) accidentellement
- Utiliser `git revert` ou faire un nouveau commit pour supprimer l'information ne suffit pas : elle est toujours présente dans l'historique ... supprimer/modifier réellement un commit passé, c'est compliqué !
   - si vous réalisez le problème tout de suite, il est possible d'annuler les `N` derniers commit avec `git reset --hard HEAD~N`
   - si c'était il y a "longtemps", il faut modifier et réecrire l'historique avec `git rebase -i` ou `git filter-repo` (commandes complexes .. voir sur Internet)

### Prévenir le problème

- La configuration d'un logiciel doit être dans un fichier à part, qui n'est PAS versionné (d'autant plus si elle contient des secrets !)
- Ajouter les fichiers de conf dans le `.gitignore` **le plus tôt possible**
- Soyez attentif à vos `git add`
- Si il y a un réel besoin de versionner des secrets, voir par ex. `ansible-vault`

---

class: impact

# 2. Explorer un dépôt

## Historique, arbre, `HEAD`, intégration IDE

---

## Parentèse technique : sous le capot

Git a été conçu un peu comme un système de fichier. Dans `.git` on trouve:
- des **blob** : le contenu des fichiers
- des **tree** : description d'une arborescence de fichier via une liste de **blob** (contenus) et méta-données comme le nom des fichiers et leur permissions
- des **commits** : un **tree** enrichi de méta-données telles que date/heure du commit, commentaire, auteur, parent, ...
- des **tags** (étiquettes) : un nom donné à un commit

Les objets sont identifiés par des sommes de contrôle SHA-1.

Le stockage des objets est optimisé en calculant parfois le différentiel entre deux objets <small>(c'est pourquoi des fois on voit git parler de "Resolving deltas (...)")</small>

Plus d'infos : https://git-scm.com/book/en/v2/Git-Internals-Git-Objects

---

## 2. Explorer un dépôt

### Rappel : `git clone`

Lorsqu'on clone un dépôt :
- on obtient une copie de tout le dépôt à l'instant T : commits, historique, références (branches, tags), ...
- tout ce qu'on fait un local ne concerne que nous jusqu'à ce qu'on fasse `git push`
- il n'y a pas de synchronisation automagique, il faut faire `git pull` (ou `git fetch`)

---

## 2. Explorer un dépôt

### Naviguer dans l'historique

- `git log` : vue "basique", éventuellement rajouter l'option `--oneline`
- `tig` : outil + pratique mais à installer (`apt install tig` sous Debian/Ubuntu)
- Personellement j'ai un alias "`logc`" (log compact) configuré dans mon `.gitconfig` (attention : il n'affiche pas l'arbre)

```
[alias]
	logc = log -n10 --pretty=format:'%Cred%h%Creset %C(bold blue)(%an) %Creset%Cgreen(%cr)%Creset - %s %C(yellow)%d%Creset' --abbrev-commit
```

---

## 2. Explorer un dépôt

### Naviguer dans l'historique

- `git show <commit_id>` montre tout le différentiel entre le commit et son parent
- `git diff <commit_id>` montre tout le différentiel entre le commit et votre espace de travail actuel

---

## 2. Explorer un dépôt

### Naviguer dans l'historique

- `git checkout <commit_id>` permet de remettre l'espace de travail dans l'état correspondant à un commit donné
- Si on fait ça, `HEAD` pointe alors vers un commit qui n'est plus le sommet d'une branche ... (on parle de "detached HEAD")

.center[
![](img/tree-2-2.png)
]

---

## 2. Explorer un dépôt

### Chercher qu'est-ce qui a causé un changement

`git blame <fichier>`
- affiche le dernier commit (+date, auteur) qui a modifié chaque ligne du fichier
- montre l'importance d'avoir des bons messages de commit qui expliquent pourquoi un changement a été fait !

Outil plus avancé : `git bisect` 
- cherche par dichotomie quel commit a introduit un problème dans les situations moins simples
- `git` va proposer successivement des versions que l'on doit marquer comme "good" ou "bad" suivant si il contient le problène ou non
- jusqu'à trouver quel commit a introduit le problème

---

## 2. Explorer un dépôt

.center[
### Exercices
]














---

class: impact

# 3. Branches, merges, conflits, tags

---

## 3. Branches, merges, conflits, tags

Jusqu'ici nous avons travaillé sur une seule branche : nos commits représentent une ligne qui va du commit le plus ancien au commit le plus récent

Mais la force du versionnement viens de son concept de branche : 
- typiquement pour séparer le développement de nouvelles fonctionnalités jusqu'à ce qu'elles soient terminées, testées, validées
- ou pour séparer l'état de la production de l'état de developpement, ou faire une branche par version
- beaucoup de modes de fonctionnement possibles (=workflow) (à rediscuter plus tard)

---

## 3. Branches, merges, conflits, tags

D'un point de vue humain/métier :
- une **séquence de commit** destinée à être intégrés dans une autre branche <small>(typiquement dans `master`/`main`/`dev`, ..)</small>

MAIS techniquement parlant : 
- une branche est uniquement une référence vers le commit au sommet de la branche
- parler de "la séquence de commit" n'a de sens que par rapport à une branche à laquelle on compare
- supprimer une branche, c'est juste supprimer la référence

.center[
cf. article [I wish people would stop insisting that Git branches are nothing but refs](https://blog.plover.com/2023/02/27/)
]


---

## Cycle de vie d'une branche (1/8)

État initial : on est sur `main`

.center[
![](img/gitbranch1.png)
]

---

## Cycle de vie d'une branche (2/8)

On créé la branche `feature-X` avec `git branch feature-X`

(attention : après cette commande on est toujours en train de travailler sur `main`)

.center[
![](img/gitbranch2.png)
]

---

## Cycle de vie d'une branche (3/8)

On passe sur la branche `feature-X` avec `git switch feature-X`

(pro-tip : on peut à la fois créer ET passer sur une nouvelle branche avec `git switch -c <branche>` (ou `git checkout -b <branche>`)

.center[
![](img/gitbranch3.png)
]

---

## Cycle de vie d'une branche (4/8)

On fait un premier commit sur la branche `feature-X`

.center[
![](img/gitbranch4.png)
]

---

## Cycle de vie d'une branche (5/8)

On fait *d'autres* commits jusqu'à être content ...

.center[
![](img/gitbranch5.png)
]

---

## Cycle de vie d'une branche (6/8)

Pendant ce temps, il y a peut-être d'autres commits qui sont apparus sur `main`

.center[
![](img/gitbranch6.png)
]

---

## Cycle de vie d'une branche (7/8)

On décide que la branche `feature-X` est OK et on décide de l'intégrer (la **merger**) dans `main` : 

```bash
git switch main      # Je reviens sur la branche main
git merge feature-X  # Je fusionne feature-X dans main
```

.center[
![](img/gitbranch7.png)
]


---

## Cycle de vie d'une branche (8/8)

Les commits de la branche `feature-X` font maintenant partie de `main` : on peut supprimer la branche `feature-X`

.center[
![](img/gitbranch8.png)
]


---

## 3. Branches, merges, conflits, tags

D'un point de vue humain/métier :
- une **séquence de commit** destinée à être intégrés dans une autre branche <small>(typiquement dans `master`/`main`/`dev`, ..)</small>

MAIS techniquement parlant : 
- une branche est uniquement une référence vers le commit au sommet de la branche
- parler de "la séquence de commit" n'a de sens que par rapport à une branche à laquelle on compare
- supprimer une branche, c'est juste supprimer la référence

.center[
cf. article [I wish people would stop insisting that Git branches are nothing but refs](https://blog.plover.com/2023/02/27/)
]

---

## Les merges et les conflits (1/5)

Lorsqu'on merge une branche dans une autre, il y a un commit spécial qui est crée : il s'agit d'un *commit de merge*

La plupart du temps, les commits des deux côtés de l'historique n'ont pas touché aux mêmes bouts de code et la fusion est triviale. Git créé un commit avec comme commentaire quelque chose comme `Merge branch 'feature' into main`

---

## Les merges et les conflits (2/5)

Lorsqu'on merge une branche dans une autre, il y a un commit spécial qui est crée : il s'agit d'un *commit de merge*

La plupart du temps, les commits des deux côtés de l'historique n'ont pas touché aux mêmes bouts de code et la fusion est triviale. Git créé un commit avec comme commentaire quelque chose comme `Merge branch 'feature' into main`

**Néanmoins**, Git n'a aucune fondamentalement aucune conscience du langage de programmation qu'il manipule et de ses implications : pour Git, c'est juste du texte !

On peut trouver des cas où une fusion perçue comme triviale par Git va créer un bug : 
- une branche `feature` est créée et utilise une variable globale `FOOBAR` qui était jusqu'ici inutilisée
- en parallèle sur `main`, quelqu'un supprime l'existence de la variable `FOOBAR` car inutilisée
- les deux historiques indépendament sont fonctionnels, mais buggés si fusionnés


---

## Les merges et les conflits (3/5)

*Des fois* la fusion des deux historiques n'est pas triviale car touche aux même bout de code : on parle de *conflit*

Git s'arrète dans un état intermédiaire et laisse les deux versions de texte concernés entre `<<<<<` et `>>>>>` : 

.center[
![](img/gitconflit.png)
]

---

## Les merges et les conflits (4/5)

Une fois les conflits résolu je dois : 
- explicitement dire que j'ai terminé de résoudre les conflits sur chaque fichier avec `git add <fichier>`
- dire à Git de finir le merge avec (juste) `git commit`

.center[
![](img/gitconflit2.png)
]


---

## Les merges et les conflits (5/5)

**Merger A dans B, ce n'est pas pareil que merger B dans A**

- Cas 1 : le travail sur `feature` est fini et validé : je merge `feature` dans `main`
   - `git switch dev` puis `git merge feature`
- Cas 2, plus rare : il y a eu un commit important dans `main` dont j'ai besoin pour mon travail sur `feature` : je merge `main` dans `feature` 
   - `git switch feature` puis `git merge dev`

.center[
![](img/gitbranch-2merge.png)
]

---

## Exemple de branches plus complexe

Dans cet exemple : il y avait besoin de `feature-X` pour commencer à travailler sur `feature-Y`

.center[
![](img/gitbranch-2branch.png)
]

---

.center[
![](img/gitflow.png)
]

---

## Les tags

- Jusqu'ici, on a utilisé les branches qui correspondent à des références "mouvantes" : à chaque fois qu'un commit est ajouté, la branche pointe vers ce nouveau commit

- Les tags correspondents à des étiquettes permanentes : elles pointent vers un commit précis et ont vocation à exister pour toujours. Typiquement pour un numéro de version

```bash
git tag v0.2   # Créer une nouvelle étiquette 'v0.2' qui pointe sur le commit actuel
git tag toto   # Créer une nouvelle étiquette 'toto' qui pointe sur le commit actuel
git checkout v0.1  # Remettre l'espace de travail dans l'état du tag v0.1
```

- Apriori on ne supprime jamais un tag ... si il y a un bug important en version `v0.1`, alors il faut faire une `v0.1.1` ou `v0.2`


---

## 3. Branches, merges, conflits, tags

.center[
### Exercices
]


---

## 3. Branches, merges, conflits, tags


Epilogue partie 3 : regarder `git log --oneline --graph`






---

class: impact

# 4. Remote et pull/merge requests

---

## 4. Remote et pull/merge requests

Le plus souvent, on travaille par rapport à un dépòt central hébergé sur GitHub ou GitLab

**GitHub**
- c'est une plateforme centralisée détenue par Microsoft
- l'hébergement de code n'est que le sommet de l'iceberg (pull request, issue, CI, ...)

**GitLab**
- c'est à la fois la plateforme GitLab.com ...
- ... ET un logiciel auto-hébergeable ! Il existe d'autres instances GitLab, par exemple Framagit
- là aussi, l'hébergement de code n'est que le sommet de l'iceberg

Il existe d'autres logiciels pour créer des forges : Gitea, Gogs, Forgejo, gitweb, ...

---

## 4. Remote et pull/merge requests

Lorsqu'on clone un dépôt, Git se souvient du dépôt d'origine : il s'agit d'un `remote` :

```
$ git remote -v
origin	https://github.com/miguelgrinberg/microblog (fetch)
origin	https://github.com/miguelgrinberg/microblog (push)
```

Rappel : tout ça ne veut pas dire qu'il y a une synchronisation automagique (ni dans un sens, ni dans l'autre) entre votre dépôt local et le dépôt distant. Il faut utiliser `git pull` / `push`

---

## 4. Remote et pull/merge requests

Démarrons dans cet état : nous avons créé une nouvelle branche en locale, et il y a deux nouveaux commits sur le dépôt distant (`Your branch is behind 'origin/main' by 2 commits`)

.center[
![](img/pullpush1.png)
]

---

## 4. Remote et pull/merge requests

À l'aide de `git push origin feature-X`, nous poussons notre branche sur le dépôt distant :

.center[
![](img/pullpush2.png)
]


---

## 4. Remote et pull/merge requests

Et à l'aide de `git pull` (depuis la branche `main`), nous récupérons les deux nouveaux commits

.center[
![](img/pullpush3.png)
]


---

## 4. Remote et pull/merge requests

AUTRE situation : il y a deux commits sur le dépôt distant, MAIS nous avons déjà fait un nouveau commit, et je ne PEUX PAS le pousser (git refusera) <small>(à moins que vous soyez *vraiment* sur de vous et que vous utilisez `--force` ...)</small>

.center[
![](img/pullpush4.png)
]


---

## 4. Remote et pull/merge requests

Ce n'est pas grave : si nous faisons `git pull`, alors Git fusionnera les deux historiques comme si il s'agissait de deux branches différentes

.center[
![](img/pullpush5.png)
]


---

## 4. Remote et pull/merge requests

Pour avoir un historique "plus propre", on aurait pu aussi faire : `git pull --rebase`

.center[
![](img/pullpush6.png)
]


---

## 4. Remote et pull/merge requests

Lorsqu'on fait `git pull` (ou plus explicitement `git pull origin main`), on effectue en réalité deux actions : 
- `git fetch` : Se contente de télécharger les nouveautés du dépôt distant, sans les intégrer
- `git merge` : Fusionne la branche `origin/main` dans `main`


---

## 4. Remote et pull/merge requests

Que ce serait-il passé si on avait mergé `feature-X` en local avant de faire `git pull` ?

---

## 4. Remote et pull/merge requests

Dans la vraie vie, on merge assez peu souvent des branches en local : on créer une pull-request (PR) / merge-request (MR) sur le dépôt distant (ou plus précisémment sur la *forge*

- En français : demande d'intégration, ou fusio-demande
- NB: c'est une fonctionnalité des forges (GitHub/GitLab/...), PAS de Git!
- L'objectif est de publier, relire, discuter des changements avant de les merger
- Une PR/MR corresponds à une branche : si d'autres commits sont poussés sur la branche, ils sont dans la PR/MR

---

## 4. Remote et pull/merge requests

Mais pour pouvoir pousser la brancher sur `origin` ... encore faut-il avoir le droit de le faire !

Néanmoins on peut également créer une merge request depuis un *fork* du dépôt !
- Un fork est un peu comme un clone, mais hébergé sur la forge
- ... par exemple : `https://gitlab.com/<votre_username>/microblogging`
- Tout comme les clones locaux : il n'y a aucune synchronisation automagique entre votre fork et le dépôt original

1. Vous devez alors dire à Git qu'il existe un nouveau "remote" : `git remote add myfork https://gitlab.com/<votre_username>/microblogging`
2. Pousser votre branche sur ce fork : `git push myfork feature-X`
3. Retrouver votre branche dans l'interface web de la forge
4. Créer une merge request à partir de cette branche

---

.center[
![](img/githubfork.png)
]

---

## 4. Remote et pull/merge requests

.center[
### Exercices
]

---

## 4. Remote et pull/merge requests

Discussion sur la revue de code, le mécanisme de suggestion, etc.












---

class: impact

# 5. Bonnes pratiques, tips pour la vie quotidienne


---

## 5. Bonnes pratiques (1/6)

### Relire le diff avant de commiter

- Idéalement avoir testé son code ...
- Faire `git status` ! Vérifiez qu'on a pas des fichiers à enlever
- Relire **attentivement** le diff <small>(généralement on oublie d'enlever un `print(..)` de debug)</small>
- On peut utiliser `git add -e` pour une relecture du diff / ajouter les blocs de modifications un par un


---

## 5. Bonnes pratiques (2/6)

### Quelle granularité pour les commits ?

Un commit est censé être une modification "atomique", qui s'explique clairement
- Trouver un juste milieu entre "je commit à chaque modification de fichier" et "je commit 30 changements qui n'ont absolument rien à voir"
- Idéalement lorsqu'on a plusieurs choses à faire, on réfléchi auparavant à comment on va s'y prendre, puis on avance/commit morceau par morceau

---

## 5. Bonnes pratiques (3/6)

### C'est quoi un bon message de commit ?

- Comme les commentaires dans le code : si ça se contente de paraphraser, ça ne sert à rien
- Prendre de la hauteur : expliquer le *pourquoi*, pas le *quoi* !
- Certaines personnes préfixent les messages de commit par `[fix]` ou `[enh]`
- ... personellement je privilégie un mot clef qui rappele le contexte
    - par exemple : `contrats: ajout de nouvelles colonnes pour améliorer la vue liste, comme demandée par le service RH`


.center[
![](img/codecomment.jpeg)
]

---

## 5. Bonnes pratiques (4/6)

### Quelle workflow pour mes branches 

Discussion : [4 branching workflows for Git](https://medium.com/@patrickporto/4-branching-workflows-for-git-30d0aaee7bf)
- GitFlow (`main` + `develop` + `release-*` + `hotfix-*` + `feature-*`)
- GitHub Flow (`main` + `feature-*`)
- GitLab Flow (`production` + `staging` + `main` + `feature-*`, tag-based releases)
- OneFlow (comme GitFlow, mais sans `develop`)

À discuter avec votre équipe en fonction des spécificités du projet
- mon exemple : fonctionnement de Coopaname
- mon autre exemple : ancien et nouveau fonctionnement de YunoHost


---

## 5. Bonnes pratiques (5/6)

### Comment fusionner les merge request

En realité il y a trois façon d'intégrer une branche dans une autre : 
- via un commit de merge (passe partout)
- rebase
- squash : [pourquoi?](https://softwareengineering.stackexchange.com/questions/263164/why-squash-git-commits-for-pull-requests)

Là encore, ça dépends de choix organisationnel pour votre projet (cf workflow). 

Généralement les commits de merge, c'est good-enough.

---

## 5. Bonnes pratiques (6/6)

### Est-ce qu'on passe toujours par une merge-request

À discuter avec votre équipe ...
- des fois c'est un peu ridicule de créer une MR pour corriger une typo dans le README

---

## 5. Tips pour la vie quotidienne (1/6)

### Git dans son `$PS1`

Si vous travaillez souvent dans un terminal Linux, il est possible d'avoir le nom de la branche ou d'autres infos dynamiquement dans le prompt

```
PS1='[\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]]`__git_ps1`\n > '
```

.center[
![](img/prompt.png)
]

---

## 5. Tips pour la vie quotidienne (2/6)

### `git commit --amend`

**Situation** : je viens tout juste de faire un commit mais j'ai oublié un tout petit détail (genre enlever un `print()` de debug), ou bien j'ai fait une typo dans mon commentaire !

Pas de panique : 
- je peux modifier les fichiers comme je veux
- et faire `git commit <mes_fichiers> --amend` : le dernier commit sera re-créé avec en plus mes changements
- je peux aussi faire juste `git commmit --amend` pour ré-éditer le message de commit

**Attention** : si le commit a déjà été poussé sur le dépôt distant, il va falloir utiliser `git push --force` qui est peut-être interdit ...


---

## 5. Tips pour la vie quotidienne (3/6)

### `git stash`

**Situation** : je voudrais récupérer les derniers changements avec `git pull`, mais Git se plaint que j'ai des changements non-commités ! Pourtant je n'ai pas envie de commiter tout de suite

Pas de panique :
- je peux mettre de côté mes changements "brouillon" avec `git stash`
- faire `git pull`
- puis immédiatement `git stash pop` pour réappliquer mes modifications dans l'espace de travail

On peut aussi utiliser `git stash` pour "transporter" un petit bout de changement qu'on aurait commencé par inadvertance sur une autre branche

---

## 5. Tips pour la vie quotidienne (4/6)

### Créer/appliquer des patchs avec `git diff` et `git apply`

La sortie de `git diff` contient toutes les informations pour recréer le même changement ailleurs !

Par exemple : 
- `git diff > mon_patch.diff` d'un côté
- je transfert le patch à un.e collègue ou dans une autre machine
- `git apply < mon_patch.diff` de l'autre
- (je peux également juste mettre la sortie de `git diff` dans mon presse-papier, et la coller dans `git apply`)


---

## 5. Tips pour la vie quotidienne (5/6)

**Situation** : j'ai commité sur `main` alors que je voulais commiter sur une nouvelle branche !

Pas de panique : 
- `git branch -c ma_branche` : créer une nouvelle branche à partir du commit actuel et se positionner dessus
- `git switch main` : revenir sur main
- `git reset --hard HEAD~1` : revenir de manière un commit en arrière (`--hard`: en modifiant vraiment les fichiers)
- `git switch ma_branche` : se repositionner sur la nouvelle branche pour continuer le travail

---

## 5. Tips pour la vie quotidienne (6/6)

**Situation** : j'ai fait un commit mais j'aimerai le séparer en deux commits distincts

Pas de panique :
- `git reset HEAD~1` : "annule" le dernier commit, sans modifier l'état des fichiers
- `git commit <fichier1> <fichier2>` : commiter une partie des changements dans un premier commit
- `git commit <fichier3> <fichier4>` : commiter l'autre partie dans un deuxième commit

---

## 5. Commandes "avancées"

### `git cherry-pick`

- Vous avez identifié un commit en particulier sur une autre branche que vous aimeriez avoir sur la votre
- ... mais vous n'avez pas envie de merger *toute* la branche .. juste ce commit
- `git cherry-pick <commit>` permet de créer un commit identique par dessus l'historique en cours !

---

## 5. Commandes "avancées"

### `git rebase`

- Les commits de merge, c'est bien mais ne pourrait-on pas s'en passer ?
- On a commencé `feature` sur un ancien commit de `main` ...
- .. recréons l'historique comme si on était parti du dernier commit actuel

.center[
![](img/rebase0.png)
]

---

## 5. Commandes "avancées"

### `git rebase`

- Les commits de merge, c'est bien mais ne pourrait-on pas s'en passer ?
- On a commencé `feature` sur un ancien commit de `main` ...
- .. recréons l'historique comme si on était parti du dernier commit actuel

.center[
![](img/rebase1.png)
]

---

## 5. Commandes "avancées"

### `git rebase`

- Les commits de merge, c'est bien mais ne pourrait-on pas s'en passer ?
- On a commencé `feature` sur un ancien commit de `main` ...
- .. recréons l'historique comme si on était parti du dernier commit actuel

.center[
![](img/rebase2.png)
]


---

## 5. Commandes "avancées"

### `git subtree` vs `git submodule`

Dans certains cas, on aimerait inclure tout un (ou des) *autre* dépôt de code dans notre projet.

Par exemple, une librairie développée par votre entreprise, utile a plein de projet

On a envie d'avoir le code de cette librairie disponible "dans le projet", et de pouvoir le mettre à jour, mais pas de gérer la vie de cette librairie depuis le projet.

- `git submodule` : présent de base dans `git`. Gère des sortes de "lien symbolique" vers un commit précis d'un autre dépôt
- `git subtree` : Intègre l'historique de la librairie *avec* celui de votre dépôt

---

# 5. Bonnes pratiques, tips pour la vie quotidienne

.center[
<br/>
<br/>
<br/>
<br/>
Exercices
]






---

class: impact

# 6. Intégration continue avec GitLab

## Et autres outils d'une forge moderne


---

# 6. Gitlab CI

## L'intégration continue (CI)

- Accélérer la livraison des nouvelles versions du logiciel.
- Des tests *systématiques* et *automatisés* pour ne pas se reposer sur la vérification humaine.
- A chaque étape le code passe dans un Pipeline de validation automatique.
- ... et même éventuellement le déploie (en test ou recette ou prod) : c'est le déploiement continu

---

.center[
![](img/cicd.png)
]

---

# 6. Gitlab CI

## L'intégration continue (CI)

La CI/CD fait partie de l’approche DevOps dont fait aussi partie les concepts de :
- cloud (Infrastructure-as-a-Service, IaaS)
- d’Infrastructure-as-Code
- les conteneurs

---

# 6. Gitlab CI

## Les pipelines de test

Découpées en "stages" puis en "jobs"

.center[
![](img/ci_yunohost.png)
]

---

# 6. Gitlab CI

## Les pipelines de test

Découpées en "stages" puis en "jobs"

.center[
![](img/ci_yunohost2.png)
]


---

## `.gitlab-ci.yml`

```yml
stages:
  - build
  - test
  - deploy

build-job:
  stage: build
  script:
    - echo "Hello, $GITLAB_USER_LOGIN!"

test-job1:
  stage: test
  script:
    - echo "This job tests something"

test-job2:
  stage: test
  script:
    - echo "This job tests something, but takes more time than test-job1."
    - echo "After the echo commands complete, it runs the sleep command for 20 seconds"
    - echo "which simulates a test that runs 20 seconds longer than test-job1"
    - sleep 20

deploy-prod:
  stage: deploy
  script:
    - echo "This job deploys something from the $CI_COMMIT_BRANCH branch."
```

---

## `.gitlab-ci.yml` : exemple proche de la vraie vie

Tester les annotations de type dans du code Python

```yml
stages:
  - linter

mypy:
  stage: linter
  script:
    - apt update
    - apt install python3-pip -y
    - pip3 install mypy
    - mypy *.py --non-interactive
```


---

## `.gitlab-ci.yml` : build d'une image Docker

```yml
stages:
  - build

variables:
  DOCKER_HOST: tcp://docker:2375/
  DOCKER_TLS_CERTDIR: ""
  IMAGE_BRANCH_TAG: $CI_REGISTRY_IMAGE:$CI_COMMIT_REF_SLUG

build:
  stage: build
  image: docker:latest
  before_script:
    - apk update && apk add git grep
    - if [ $CI_COMMIT_REF_SLUG = "main" ]; then IMAGE_BRANCH_TAG="$CI_REGISTRY_IMAGE:latest"; fi
  services:
    - docker:19.03.1-dind
  script:
    - docker login -u $SECRET_CI_LOGIN -p $SECRET_CI_PASSWORD $CI_REGISTRY
    - docker build --progress plain $(pwd)
    - echo "Pushing $IMAGE_BRANCH_TAG"
    - docker push $IMAGE_BRANCH_TAG
```


---

# 6. Gitlab CI

## Pour aller plus loin

GitLab permet d'être "docker registry"
- c'est-à-dire héberger les images docker pour votre projet

GitLab permet aussi de configurer des Webhooks
- c'est-à-dire appeler une URL web e.g `https://votre.domain.tld/my_hook/` lorsque certain type d'événements se produisent (par exemple un nouveau commit sur une PR, un merge, un tag, ...)

... et pleins d'autres choses

