

# Git


## git states


files have three state: 1. committed 2. staged 3. modified and untracked

if you create a file but did not add it to stage ===> untracked
if you add a file into staged and edited it after that ===> modified


## commands
git add 5.js != git restore --staged 5.js ===>You can't undo a git restore
create a file but 

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