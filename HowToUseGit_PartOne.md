# Git introduction

***git*** is a tool that helps to manage your files more effectively and clearly.

In some cases, you have to recall what you code in your last version but it has been covered, or you need to rectify some changes of current versions but just in case need to save it, or you change your mind ,want to discard current changes then go back to last version. In all, it helps to record every-time change into a independent copy.

> git ---> a management tool
>
> GitHub---> a community who can share everyone's artifact

## Git vs SVN

**Git is a distribution system**. Everyone in this system has a full copy of the whole repository, so even without the network connection, people still can make changes on files regardless of others' working. When it needs to be intergrated, then go mix them up.

**SVN is a centralised system**.In contrast, the whole respository is saved in one server on the network. we can say the host. And if you want to change anything, you tackle specific pages of files you want and put back to it after finishing refine. 

***so the advantage is obvious***, it does not need a connection at any time, and it can avoid many collisions and confilct regarding the version control because everyone can edit the same responsitory in different and individual ways on their own computers. And if we use SVN then the host crashed, all gone. GG.

> let me recall the concept of Bitcoin also mentioning the de-centraliztion.   :smiley:

## Restrictions

Git is not suitable for PPT and some files with too many pictures.

Because all git doing is to record the things, especially for codes, into binary things. But the picture or videos contains too complex things when it converted into binary. So if you want to manage your normal colorful or vivid things, go pick another one. Git is born for storing codes.

---

# Install Git

### Windows   Bash

* Throw far away your computer and buy a Mac for God sake, I'm done with the Bash and cmd, soz guys.

### Mac OS

+ use `homebrew` , you can test it whether it already there in your toy by typing `brew help` in your terminal, go  check for details at <https://brew.sh>

+ if it does, you can get some like

  > **➜** **~** brew help
  >
  > Example usage:
  >
  >  brew search [TEXT|/REGEX/]
  >
  >  brew info [FORMULA...]
  >
  >  brew install FORMULA...
  >
  >  brew update
  >
  >  brew upgrade [FORMULA...]
  >
  >  brew uninstall FORMULA...
  >
  >  brew list [FORMULA...]

  That means that your mom has already install homebrew for you.

+ if it shows, like `command not found`, see below, you have to install homebrew. by using

  > ```c
  > /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
  > ```



+ Done? now you have homebrew, you can use it to install the `git`. by this command in terminal

  > ```c
  > $ brew install git
  > ```

+ Here we go, now after installation, if you go check `git --version`, the script should look like:

  > **➜** **~** git --version 
  >
  > git version 2.23.0

+ **Recommended to have the macOS Sierra or above, or you may encounter the version mismatch.**

  see  <https://apple.stackexchange.com/questions/93002/how-to-use-the-homebrew-installed-git-on-mac>



### Linux

+ go check whether you already have one:

  >```c
  >$ git
  >The program 'git' is currently not installed. You can install it by typing:
  >sudo apt-get install git
  >```

+ then you can go for install one, by:

  > `sudo apt-get install git`

+ after that, use `git --version`    to check

# New a repository

### Initalization

+ create a nomarl folder to be your repository , I will show you and explain to you step by step.

  1. > `$mkdir  my_repository_name`

     here, I call my repository as git_test

     > `$mkdir git_test`

     *this means i created a folder in current folder, remember to check whether folder you are in when you type this, it is a simply **`linux`** command.*                         			

  2. ***important***: **remember to go into your folder !!!!!** , by

     > `$cd git_test`

  3. you can use **`pwd`** as well as **`-ls`** to confirm you are ***in*** your folder already.

+  Convert it into a `git` repository

  > `$git init`

  if it works, it will show like 

  > ```c
  > Initialized empty Git repository in /Users/michael/learngit/.git/
  > ```

# Local Operations

### add

+ for testing, we created couples of testing files in our folder.

  >test_1.txt
  >
  >test_2.txt
  >
  >test_3.txt

+ use the ***add*** to put your files into the [stage area](https://blog.csdn.net/qq_22337877/article/details/73249912)

  you can memorize by this: 

  ![pic](https://img-blog.csdn.net/20170614164914194?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMjIzMzc4Nzc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

  

  > **$git add test_1.txt**
  >
  > note: if script shows nothings means it worked

### commit



+ now, you have some work done and store in the stage area, next, we need to push it into the working area, use `commit` .

  > `$git commit  -m "give some description about this commit"`
  >
  > here, lets say: `$git commit -m create a new test_file_1`

  it will show response like this:

  > **➜** git commit -m "create a new file_text_1"
  >
  > [master (root-commit) f8064db] create a new file_text_1
  >
  >  1 file changed, 2 insertions(+)
  >
  >  create mode 100644 test_1.txt

  - ***notes***: remember that the descriptions have double quotes for it \"description"
  - But the `add` command witht the filename does not have the quotes marks\" xx"

###  status

+ we can use `git status` to check this repository you are in to show the current status:

  and here first if we assume that we have done some changed on the previous file.

  and it will show like this:

  > ➜  git_test git:(master) git status 
  > On branch master
  > Changes not staged for commit:
  >   (use "git add <file>..." to update what will be committed)
  >   (use "git restore <file>..." to discard changes in working directory)
  > 	**modified:   test_1.txt**
  >
  > no changes added to commit (use "git add" and/or "git commit -a")

+ Above shows that it can tell you `i can find **modified:   test_1.txt**` , but still not add or commit

+ If you see something about `untracked files` which means you create some new files that never occur in the git system, you have to do `add` and then `commit`  commnad.

  >➜  git_test git:(master) git status 
  >On branch master
  >Untracked files:
  >  (use "git add <file>..." to include in what will be committed)
  >	i'm just a demo.txt
  >
  >nothing added to commit but untracked files present (use "git add" to track)



### diff

+ ok, now we have found that the `text_1` has been modified and how do we find the details of changes.

+ we can go `$git diff <filename>` to do it

+ Here, we type ``` $git diff test_1.txt ``` , then we got: 

+ > ```diff --git a/test_1.txt b/test_1.txt
  > index d8036c1..7cd6d52 100644
  > --- a/test_1.txt
  > +++ b/test_1.txt
  > @@ -1,2 +1,2 @@
  > -Git is a version control system.
  > +Git is a very good system.
  >  Git is free software.
  > \ No newline at end of file
  > (END)```
  > ```

+ > - *** it clearly showed you the difference bewteen alterd and previous one.***
  > - **you can use `Q` on keyboard to quit this.**
  > - "+++   b" means changed one
  > - "---  a" means previous one

+  OK, everything done. Now we can safely `add` and `commit` them:

  > ```nginx
  > ➜  git_test git:(master) ✗ git add test_1.txt 
  > ➜  git_test git:(master) ✗ git status 
  > On branch master
  > Changes to be committed:
  >   (use "git restore --staged <file>..." to unstage)
  > 	modified:   test_1.txt
  > 
  > ➜  git_test git:(master) ✗ git commit -m "i changed the text_1_file the first line"
  >   [master 46bd97b] i changed the text_1_file the first line q q
  >  1 file changed, 1 insertion(+), 1 deletion(-)
  > ```

+ If everything is fine, it will return:

  > ```nginx
  > ➜  git_test git:(master) git status                                               
  > On branch master
  > nothing to commit, working tree clean
  > ➜  git_test git:(master) 
  > 
  > ```

  :star: ***remember***: the `git diff <filename> `can only use  **for the files which are modified during the working space, which means if you have `add` or `commit ` already , **  **you can not  use `diff`  to see any changes **.

  

### log & reset

+  lets recall what we have learnt now: 

  > 1. add and commit , if we new a file, the script by using status also shows `modified`
  > 2. status and diff ,always use these it check the status.
  > 3. so in common: add -commit - "change somewhere"- diff -status - add - commit

+ Now you have know how to make changes and submit, now if we have to reset somethings:

  > since everytime we do the commit, the `commit` is like we saved the status everytime when we commit, and we'v got the commit ID each time, if we want to go back any status, just take the commit ID token to let the git find the sepcfic timepoints.

  - we use *** `git log`***. firstly, to check all the logfile of the `commit` operations.

    > ```nginx
    > commit 4c0311e236dab543c76025dc8436bfb23aa43f84 (HEAD -> master)
    > Author: HappyBoy19940506 <HappyBoy19940506@users.noreply.github.com>
    > Date:   Sat May 2 14:28:32 2020 +1000
    > 
    >     append GPL
    > 
    > commit 46bd97b188dbb54b130a23021f1aefdaca143033
    > Author: HappyBoy19940506 <HappyBoy19940506@users.noreply.github.com>
    > Date:   Sat May 2 14:19:07 2020 +1000
    > 
    >     i changed the text_1_file the first line
    >   
    > commit f8064db51c9335b0f041a495a99d6ff6239e1496
    > Author: HappyBoy19940506 <HappyBoy19940506@users.noreply.github.com>
    > Date:   Sat May 2 13:53:35 2020 +1000
    > 
    >     create a new file_text_1
    > ```

  - we can use "Q" to quit this script.
  - this obvisouly show commits everytime, thanks for the descriptions we wrote, we can easily understand what we did each point of save.

+  ***OK, now, we need to go back to the commit of "i changed the text"*** . lets lauch our time machine.

  >  `HEAD` means the current status you are in, for example , look at last the `git log` , you can find the `HEAD` in the first line, which means i am in the status of the point wichi is append GL

  -  `HEAD^`  means the last commit
  - `HEAD^^` means the one before the last commit
  - `HEAD~100` means the 100 last one

+ > `$git reset ***--***hard HEAD^`
  >
  >  Remember : use the hard with two dashes.

+ NOW we have successfully go back to last commit, and "add GPL" changes are gone if go `git log`.

  > commit 46bd97b188dbb54b130a23021f1aefdaca143033 (HEAD -> master)
  > Author: HappyBoy19940506 <HappyBoy19940506@users.noreply.github.com>
  > Date:   Sat May 2 14:19:07 2020 +1000
  >
  >     i changed the text_1_file the first line
  >
  > commit f8064db51c9335b0f041a495a99d6ff6239e1496
  > Author: HappyBoy19940506 <HappyBoy19940506@users.noreply.github.com>
  > Date:   Sat May 2 13:53:35 2020 +1000
  >
  >     create a new file_text_1

  ```ascii
  ┌────┐
  │HEAD│
  └────┘
     │
     │    ○ append GPL
     │    │
     └──> ○ add distributed
          │
          ○ wrote a readme file
  ```



 *** change our head to any commit***

```ascii
┌────┐
│HEAD│
└────┘
   │
   └──> ○ append GPL
        │
        ○ add distributed
        │
        ○ wrote a readme file
```

### reflog





+ OK ! if i CHANGED my mind again, i need to go back to GPL status again! what i need to do?

+ first, we need `git relog` to show all the commit id, and we have to find the GPL commit id in it:

+ > 46bd97b (**HEAD ->** **master**) HEAD@{0}: reset: moving to HEAD^

  > 4c0311e HEAD@{1}: commit: append GPL

  > 46bd97b (**HEAD ->** **master**) HEAD@{2}: commit: i changed the text_1_file the first line

  > f8064db HEAD@{3}: commit (initial): create a new file_text_1

+  Now we find the second lines said: the append GPL part ID is 4c0311e

+ Lets take this with `reset` to get back:

  > `$git reset --hard 4c0311`

  We get it ! 

  > **➜** **git_test** **git:(****master****)** git reset --hard 4c0311e
  >
  > HEAD is now at 4c0311e append GPL

  ---

  

  *** Summrize***

  1.  `HEAD` use it to change the head to point the specific commit ID to go back
  2. `git log`  ---*check the current commit in the respository (committed)*
  3. `git stauts --` *check the status of three parts : working area, stage area, repository*
  4. `git reflog -- *check all operation logs bewteen stage and repo, nomrally to find the commit ID to reset*`





# Remote Operations

:star:  More skills please stick on to \<How TO USE GIT > Part 2. 

# Cooperative Work

:star:  More skills please stick on to \<How TO USE GIT > Part 2. 

# Important Notes

:star:  More skills please stick on to \<How TO USE GIT > Part 2. 



# Command List in Part One

> git init



>git add  <filename>



> git commit  -m  "description"



> git status  [check this out ,useful](https://blog.csdn.net/tecsunwong/article/details/73604111?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.nonecase)



> git diff <filename>



> git log   ---get everytime the commit 每次commit操作的记录，记得看到他们的ID

# More skills please stick on to \<How TO USE GIT > Part 2







 