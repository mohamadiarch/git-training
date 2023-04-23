

# Git


## git states


files have three state: 1. committed 2. staged 3. modified and untracked

if you create a file but did not add it to stage ===> untracked
if you add a file into staged and edited it after that ===> modified


## restore
You can't undo a git restore ===> it is dangerous
1. 
touch 5.js then edit it and then `git add 5.js` then `git statue` ===> `git restore --staged 5.js` ===> nothing to see in vscode but you can see what happened with `git status` ===> this command (restore --staged) is an undo for `git add .`

2. 
create a file but do not use `git add .` then `git status` ===> `git restore 5.js` ===>
you can see something in vscode ===> 5.js will disappear ===> this command (`git restore`) will delete all files that they are not added to stage 

## vscode
1. you can use "cls" for clear terminal in vscode
2. you can create a file in cmd by ===>
    + type nul > 6.js
    + echo console.log("s") > 6.js
    + echo > 6.js and press enter
    + touch 6.js ===> in linux
    + delete a file ===> del 6.js
1. in File Explorer (hover it) : 

    M means: Modified 
    U means: Untracked
    A: means Index Added ==> after U
    Nothing means: after commit


3. in Editor panel of vscode (user interface) (click it):
   
    Green means ===> new created (Untracked into file)
    Blue means ===> edit committed file (Modified into file)

4.  