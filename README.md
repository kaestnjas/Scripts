# Scripts

Collection of my little helpers...

## My 2 top most often used "onliners" for Git via several shell's

    https://github.com/kaestnjas/Scripts.git

Carefully (!), its only working with simple urls like above. 

Urls containing additional directories or dots like below wont work:

    https://github.com/kaestnjas/projects/Scripts.git;  
    https://github.com/kaestnjas/Scripts.wiki.git;

## Windows GitBash from GitForWindows

### 1. First time clone a new repository (like this one)

    url=https://github.com/kaestnjas/Scripts.git;
    dir=$USERPROFILE'\source\repos\'"$(cut -d'/' -f3 <<<$url)"'\'"$(cut -d'/' -f4 <<<$url)";mkdir -p "$dir" && cd "$dir" && git clone $url && cd "$dir"/"$(cut -d'.' -f1 <<<$(cut -d'/' -f5 <<<$url))" && git config credential.helper store && git fetch --all && git pull

### 2. Update all my local cloned repositories to the latest version

    cd "$dir"/"$(cut -d'.' -f1 <<<$(cut -d'/' -f5 <<<$url))" && git config credential.helper store && git fetch --all && git reset --hard origin/master && git pull;cd $USERPROFILE'\source\repos\' && find . -type d -name .git -not -wholename "*kaestnjas/Scripts*" -not -wholename "*kaestnjas/Scripts.wiki*" -execdir sh -c "pwd && git config credential.helper store && git stash && git fetch --all && git clean -d -f && git pull" \;

## Windows WSL Ubunutu Bash

### 1. First time clone a new repository (like this one)

    url="https://github.com/kaestnjas/Scripts.git" 
    dir=~/source/repos/"$(cut -d'/' -f3 <<<$url)"/"$(cut -d'/' -f4 <<<$url)";mkdir -p "$dir" && cd "$dir" && git clone $url && cd "$dir"/"$(cut -d'.' -f1 <<<$(cut -d'/' -f5 <<<$url))" && git config credential.helper store && git fetch --all && git pull

### 2. Update all my local cloned repositories to the latest version

    cd "$dir"/"$(cut -d'.' -f1 <<<$(cut -d'/' -f5 <<<$url))" && git config credential.helper store && git fetch --all && git reset --hard origin/master && git pull;cd ~/source/repos/ && find . -type d -name .git -not -wholename "*kaestnjas/Scripts*" -not -wholename "*kaestnjas/Scripts.wiki*" -execdir sh -c "pwd && git config credential.helper store && git stash && git fetch --all && git clean -d -f && git pull" \;

## not ready ! dont use ! Windows Powershell GitForWindows

### 1. First time clone a new repository (like this one)

    PS:
    $url="https://github.com/kaestnjas/Scripts.git"  
    $dir = "$env:USERPROFILE\source\repos\"

todo: how to cut the url to pieces with PS

    PS:
    dir=$USERPROFILE'\source\repos\'"$(cut -d'/' -f3 <<<$url)"'\'"$(cut -d'/' -f4 <<<$url)";mkdir -p "$dir" && cd "$dir" && git clone $url && cd "$dir"/"$(cut -d'.' -f1 <<<$(cut -d'/' -f5 <<<$url))" && git config credential.helper store && git fetch --all && git pull

### 2. Update all my local cloned repositories to the latest version

    PS:
    cd "$dir"/"$(cut -d'.' -f1 <<<$(cut -d'/' -f5 <<<$url))" && git config credential.helper store && git fetch --all && git reset --hard origin/master && git pull;cd $USERPROFILE'\source\repos\' && find . -type d -name .git -not -wholename "*kaestnjas/Scripts*" -not -wholename "*kaestnjas/Scripts.wiki*" -execdir sh -c "pwd && git config credential.helper store && git stash && git fetch --all && git clean -d -f && git pull" \;
