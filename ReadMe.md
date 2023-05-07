---
 GIT CHEATSHEET
 DOCUMENTATION: https://git-scm.com/
---


# ReadMe

In this repo I want to write some notes and train git commands for myself. 

## cheat sheet
+ https://cheatography.com/itsellej/cheat-sheets/git-commands/
+ https://quickref.me/markdown.html
+ https://github.com/LeCoupa/awesome-cheatsheets/blob/master/tools/git.sh
+ https://learntheweb.courses/topics/markdown-yaml-cheat-sheet/
+ https://devhints.io/
+ https://developercheatsheets.com/
## git glassory
https://git-scm.com/docs/gitglossary
## book
https://git-scm.com/book/en/v2

# Git

-------------------------------------
## git states
1. working directory
2. staging area
3. local repository
4. github repo



## file states
files have three state: 
1. committed 
2. staged
3. modified and untracked

if you create a file but did not add it to stage ===> untracked

if you add a file into staged and edited it after that ===> modified

## state cycle
Git essentially has 4 main statuses for the files in your local repo:

+ untracked: The file is new, Git knows nothing about it. If you git add <file>, it becomes:
+ staged: Now Git knows the file (tracked), but also made it part of the next commit batch (called the index). If you git commit, it becomes:
+ unchanged: The file has not changed since its last commit. If you modify it, it becomes:
+ unstaged: Modified but not part of the next commit yet. You can stage it again with git add
+ R for renamed file

## terms
"origin" = is a shorthand name for the remote repository that a project was originally cloned from
"HEAD" = latest commit ===> cat .git/refs/heads/master ==> commit ID of the HEAD



-------------------------------------
## undo sycle

+ git clean -f -x ===> delete untracked files( do not affect on M fiels and A files) (delete just U files)
+ git restore --staged . ===> transfer from staging area to working directory  ===> (change A files and M files into U)
+ git restore . ===> change modified files into staged area ===> discard changes of modified files ==> (change M files into A)
+ git reset --hard ===> back to last commit ===>(delete M A files and not U files) 
+ git reset --soft HEAD~ ===> delete last commit and its changes from files 
+ git checkout 3ec793f72ed79503a546e4703167272ed133494c ===> back to specific commit
+ git checkout deletedfile.js ===> recover deleted file before staging (before git add .)
+ git checkout 12.js ===> discard not staged M files (just M files and no U,A files)
+ git checkout . ===> discard not staged M files for all files
+ git checkout HEAD -- 12.js ===> discard not staged M files(and no A,U files)
+ git stash &&&& git stash drop ===> discard M A U files with temporary commit



## log
+ git status
+ git status -s ===> better listing
+ git checkout ===> list of A,U,M files
+ git diff ===> find modified files (can not find U and A files)
+ git diff --staged ===> find A and M files (can not find U files)
+ git reflog ===>
+ git log ===> list of all commits
+ git log -1 ===> just latest commit ===> -2 show 2 latest commit
+ git log --oneline ===> just commit messages and no username
+ git log -p 2.js ===> log of inside changes filename
+ git log --follow 2.js ===> commits for this file
+ git show ====> last commit inside changes
+ git show -2 ===> show 2 lastedt inside changes commit
+ git show 3ec793f72ed79503a546e4703167272ed133494c ====> show changes 
+ git branch -vv || branch || branch -av ===> list of branches
+ git log --stat -M ===> summary of how much one file was changed compared to another
+ git log --pretty=oneline --graph --decorate --all ===> cool visualization





## stash

+git stash ===> save changes as a temporary commit
+git stash save "ABC" ===> save with this name

+git stash clear ===> delete all stashes
+git stash drop ===> drop 0
+git stash drop 3 ===> drop 3

+git stash pop 3 ===> pop 3
+git stash pop 0 ===> pop 0


+git stash show ===> show 0 brifely
+git stash show 2 ==> show 2 brifely
+git stash show 2 -p ==> show 2 content


## tag
Git supports two types of tags: lightweight and annotated.

A lightweight tag is very much like a branch that doesn’t change

+ git tag TAGNAME ===>  tag the current commit as a lightweght
+ git tag -a TAGNAME -m "message" ===>  tag the current commit as a annonate tag
+ git log --pretty=oneline ===> log commits and tags	
+ git tag -l ===> list of tags
+ gut tag -d TAGNAME ===> delete a tag

-------------------------------------

## restore
You can't undo a git restore ===> it is dangerous
1. 
touch 5.js then edit it and then `git add 5.js` then `git statue` ===> `git restore --staged 5.js` ===> nothing to see in vscode but you can see what happened with `git status` ===> this command (restore --staged) is an undo for `git add .`

2. 
create a file but do not use `git add .` then `git status` ===> `git restore 5.js` ===>
you can see something in vscode ===> 5.js will disappear ===> this command (`git restore`) will delete all files that they are not added to stage 

## reset 
git reset is all about moving HEAD 
default flag ==> --mixed


```js
git reset --soft HEAD~ ===> delete last commit and bring commited changes to staging area (commited to M,A)
git reset --soft HEAD~3 ===> delete 3 latest commit and bring them changes into staging area 
git reset HEAD~ ===> delete last commit and bring theme in working directory 
git reset --hard HEAD~ ===> delete last commit forever
git reset --hard HEAD~ ==> can not delete U files but M, A file will delete
```



## rm

you can not delete A,U files
+ git rm -r . ====> keep uncommitted files and delete committed files
+ git reset --hard ===> undo for `git rm -r .`


## mv (move and rename)
you can not move A,U files
other developers can see ==> 1 files changed, 0 insertions(+), 0 deletions(-)
and you can commit for this movement ===> -m "Modified directory structure"

rename ===> git mv 1.js rename.js 
move ===> git mv 1.js src/  




## clean 


git init  # aku

## commit 
+ you can not commit twice with no changes ===> get error: nothing to commit 
+ git commit -m "write your commit" ===> After commit we can view log details
+ git commit ===> open editor in terminal to write your commit
+ git commit --amend -m "edited message" ===> edit your commit (edit before push) ===>new commit ID
+ git log -1 ===> latest commit 


-------------------------------------


## vscode
1. you can use "cls" for clear terminal in vscode
2. you can create a file in cmd by ===>
    + type nul > 6.js
    + echo console.log("s") > 6.js
    + echo > 6.js and press enter
    + touch 6.js ===> in linux
    + delete a file ===> del 6.js
1. in File Explorer (hover it) : 

    + M means: Modified 
    + U means: Untracked
    + A means Index Added ==> after U
    + Nothing means: after commit


3. in Editor panel of vscode (user interface) (click it):
   
    Green means ===> new created (Untracked into file)
    Blue means ===> edit committed file (Modified into file)

4. you can  open a file from terminal into vscode ===> code . 11.js ===> open it as a new tab
5. ctrl + s ===> fwd i search ===> then press ctrl+r or esp




## git synopsis 
Utility Conventions 
this is like vim notation
ref = https://stackoverflow.com/questions/32085652/whats-the-meaning-of-in-git-command-synopsis



Placeholders are spelled in lowercase and enclosed in angle brackets:
   <file>
   --sort=<key>
   --abbrev[=<n>]

Optional parts are enclosed in square brackets:
   [<extra>]
   (Zero or one <extra>.)

   --exec-path[=<path>]
   (Option with an optional argument.  Note that the "=" is inside the
   brackets.)

   [<patch>...]
   (Zero or more of <patch>.  Note that the dots are inside, not
   outside the brackets.)

Multiple alternatives are indicated with vertical bars:
   [-q | --quiet]
   [--utf8 | --no-utf8]

Parentheses are used for grouping:
   [(<rev> | <range>)...]
   (Any number of either <rev> or <range>.  Parens are needed to make
   it clear that "..." pertains to both <rev> and <range>.)

   [(-p <parent>)...]
   (Any number of option -p, each with one <parent> argument.)

   git remote set-head <name> (-a | -d | <branch>)
   (One and only one of "-a", "-d" or "<branch>" _must_ (no square
   brackets) be provided.)

And a somewhat more contrived example:
   --diff-filter=[(A|C|D|M|R|T|U|X|B)...[*]]
   Here "=" is outside the brackets, because "--diff-filter=" is a
   valid usage.  "*" has its own pair of brackets, because it can
   (optionally) be specified only when one or more of the letters is
   also provided.
   
   
## git usage

+ you can push multiple commit at once as a one feature


