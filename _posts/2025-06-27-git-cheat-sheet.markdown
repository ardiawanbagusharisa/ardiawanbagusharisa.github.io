---
layout: post
title: "Git cheat sheet"
date: 2025-06-27 06:00:00 +0800
categories: Programming 
tags: ["Git", "Programming"] 
---

A few git command for daily use. 

A few terms need to know:  
* **Local**: work files in your computer (local repository). 
* **Remote**: work files in your remote repository. 
* **Add**: add current works to be saved. 
* **Commit**: save current work, before being pushed. 
* **Pull**: like download, update your local files from remote repository. 
* **Push**: like upload, update your remote files from local repository. 
* **Branch**: a duplicate to isolate your work for more safety. 

---

### Using GitHub for the first time

**Clone an existing repository** 
1. Download [Git bash ](https://git-scm.com/)
2. Config SSH (use ssh for best experience)
3. Clone the repository in GitHub `> git clone <SSH address>`

**or, Create a new repository**  


> echo "<name of repository>" >> README.md  
> git init  
> git add README.md  
> git commit -m "first commit"  
> git remote add origin <your-git-address.git>  
> git push -u origin main  

--- 

### Using GitHub after the first time

**Update your local**  

If you have updated your local and want to `push`, make sure to update your local first by pulling from main (remote).  

To know the update on remote:  
> git fetch  

then  
> git pull  

then you can check the current status  
> git status 

**Push to remote**  

Let's say you want to `push` your update. If you are working alone and made no other branch before, then simply 
add all updated files you want to add  
> git add  

or to add all files   
> git add .  

then save the added files with a message for information  
> git commit -m "Your message here"  

then   
> git push 

Tips: always do `> git status` for each stage is not a sin.  

**Push to remote with branch**  

If you want to create a new branch for your task before push,  
> git branch (to check the existing branch)  
> git branch <branch_name>  

this will check a branch. Then, switch to your branch if exists, and will create a new one if not   
> git checkout <branch_name>  

similarly, do these  
> git add <your_files>
> git status
> git commit -m "Your comment for this upload."  

and if this is your first time to push using this branch,   
> git push -u <yourgitaddress.git> <branch_name> 

if not the first time, use this instead    
> git push origin <branch>   

You can ignore to write the `<branch>` after the first push or if it is connected already (upstreamed).  

--- 

**Keep updated**  

Check where the remote is fetched from  
> git remote show origin

To keep updated with remote branch (including main):  
> git checkout <local branch>  
> git pull origin <branch>  

or just `git pull` if you only have main.  

--- 

**Branch**  

To merge local branch with specific branch 
> git checkout <mylocalbranch> //checkout to mybranch  
> git merge <otherbranch> //merge someone's branch to mine  

To delete branch (please checkout to another branch first) 
> git branch -D <remote or not> <branch>  

To create new branch from remote branch 
> git checkout -b <your_branch> <origin/remote branch>  

or  
> git checkout --track origin/daves_branch  

`--track` is shorthand for `git checkout -b <branch> <remotename>/<branch>`,  where `<remotename>` is origin in this case and `<branch>` is twice the same, `daves_branch` in this case. 

--- 

**Set the local branch tracks remote branch**  

If the branch is not checked out  
> git branch -f --track my_local_branch origin/my_remote_branch

OR (if my_local_branch is currently checked out):  
> $ git branch --set-upstream-to my_local_branch origin/my_remote_branch

Then pull to update local branch according to the remote
> git pull

---

**Recovering uncommited changes ovewrote by commit**

Ref: http://effectif.com/git/recovering-lost-git-commits
> git reflog  
> git checkout  <branch you want to change>   
> git reset --hard <reflog ID>  

Discard/ cancel local unstagged/ untracked changes  
> git stash -u  

--- 

**Update forked repo from original** 

Ref: https://gist.github.com/CristinaSolana/1885435
https://help.github.com/articles/syncing-a-fork/

> git clone git@github.com:YOUR-USERNAME/YOUR-FORKED-REPO.git  
> cd into/cloned/fork-repo  
> git remote add upstream git://github.com/ORIGINAL-DEV-USERNAME/REPO-YOU-FORKED-FROM.git  
> git fetch upstream  
> git pull upstream main  

--- 

**Git Submodule** 

If you have a git inside another git project  
Ref: https://gist.github.com/gitaarik/8735255 

--- 


[post]: https://ardiawanbagusharisa.github.io/blog

<p><strong>Categories:</strong> 
  {% for category in page.categories %}
    <a href="/category/{{ category | slugify }}/">{{ category }}</a>{% unless forloop.last %}, {% endunless %}
  {% endfor %}
</p>

<p><strong>Tags:</strong> 
  {% for tag in page.tags %}
    <a href="/tag/{{ tag | slugify }}/">{{ tag }}</a>{% unless forloop.last %}, {% endunless %}
  {% endfor %}
</p>