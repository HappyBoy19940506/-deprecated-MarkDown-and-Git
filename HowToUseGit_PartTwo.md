## Let's recall what we have learnt recently.

> git init     创建一个git仓库
>
> git add <filename>  把某个文件上传到stage区，如果是修改文件，则显示modified，如果是新文件，则显示untracked files
>
> git commit -m  "xxx" 把stage暂存区的文件commit到repository里面
>
> git diff <filename> 注意，比较的是 缓存区的文件和 目前工作区文件的差别， 如果你add完直接diff的话，肯定是没区别的。
>
> git log  查看所有当前commit的树结构的操作，一般用来做回溯操作。
>
> git reflog 查看所有 add，commit，新建，reset等操作的记录，一般用做reset之后再reset的操作，因为你reset了之后你commit的head之前就已经不在树结构里面了。
>
> git status 查看工作区+暂存区+repository三个分区的所有状态，比如有没有新文件被创建，文件有没有更改，add完了之后有没有文件留在暂存区等等
>
> git reset -- hard  <commit ID>  回溯到特定的版本号。



## Next Part

### more about the diff command

- `git diff <filename>` is to check the difference between files  in the workspace and in the stage.

  >in other words, it compares the `files now in the workspaces` vs `files in the stage`

- `git diff HEAD -- <filename>` is to compare the difference  between the HEAD commit file with the workpspaces.

  > file in the workspaces    vs   the commited file in the repository

- >***file now in the workspace***   vs  stage ----- git diff <filename>
  >
  >***file now in the workspace***   vs  repository   -- git diff  HEAD -- <filename>



### git restore

+ > (use "git restore <file>..." to discard changes in working directory)

  git restore <filename>  can put the files in the working space area back to the past which means, the files will return to the states which was in the last `add`  or`commit` command.

+ > use "git restore --staged <file>..." to unstage)

   git restore --staged <filename> can put the files in the stage area back to the working spaces. which means clean the files in the stage area. If you need to restore the changes forever, you need to do one more the `git restore <filename>` to let the files go back to the last checkpoint.
  
  > git restore --staged: it can only clean the stage spaces, but didnt change anything of content in files.



### delete (git rm)

>git  rm   the same level operation as `git add`
>
> after use this, this operation has been recorded in the staged area, waiting for being committed.

***vs***

> rm   == same as you right click and use the "move to bin".

+ if you want to delete/remove somthing, use `git rm filename`, and use `git stauts`check, you can find it can detect that you delelted somethings.

+ Then, if you have confirmed that, you can use `commit` , the same as after you `git add` something.

+ Otherwise, if you changed your mind, regret deleting it, you can use`git restore filename` to withdraw the delete operation.

  ------

  TIPS:

  :star:  **if you already commit it after you delete, which means it has been recorded in the repository, so  you can simply use `git reset ` to get back to the status which the file has not been removed. the git add and git rm are on the same level**

  :star: :star: ***remember, there is a special circumstance , i.e. you use the rm to remove the file, at the same time you also add OTHER FILES. and then you `commit` in one time to put all of them to the repository , Afterwards, you again make some changes in file b thats say add more lines in B. and then you change your mind , you use`git reset` .  BUT This `reset` will discard all your changes of  OTHER files, because it will go back to the status when you commit it. Thus, the changes you made in OTHER FILES will be gone.***

  For example:   File A and File B (working directory)  ----> delete File A and add a line in File B ------> commit , so the file in repository is deleted A and changed B ,right ?

  But now, you make some changes in B again, and even you commit it . but you want recovery this file A and  then you use `reset` . so what will happen is the file will go back to Status A, so the changes in Status B will be eaten! 

  > **So keep in mind. everytime,  be careful with using reset + Commit ID. especially for there are more than one files, because the reset command will get your back to the status of ALL FILES, not only the specific file . when you use reset --hard + commit ID**
  >
  > **because the commit ID maybe contains more than one file.**

  :star::star::star: ***This is the most important***

  > **If a file is created and never to be commited before deleted, it can  not be recovered, because it was not added to the stages, so there is no record for it !**
  >
  > **So everytime think carefully before you competely delete a file espcailly you never submitted it before to the repository.**

  :star::star::star::star:

  >if YOU use rm not the git rm. you have do one more `git add` or `git rm` before you commit, 
  >
  >because it will say your changes not staged for commit !

### GitHub-Connected!

+ How to create a SSH key to get linked with the github with your local directory,and why we need to do that?

> please check : [remote repository-ssh my github](https://www.liaoxuefeng.com/wiki/896043488029600/896954117292416)  .To get linked between my LOCAL and REMOTE,
>
> 占坑回填
>
> Once you SSH successfully with remote repository , you can do with the distrubuted system
>
> In real life, company may not use github, they have their own "github".

+ Scenario 1:  I have my repo locally and I want to push it to a remote and empty repo in GitHub.

  >```
  >$ git remote add origin git@github.com:HappyBoy/notes.git
  >--linked my local repo with the remote repo. the name is origin, the link is xxxx.
  >$ git push -u origin master
  >-- push my local files to the remote and empty repo
  >--- push -u +repo name + branch name. I push this local repo to which branch of which repo.
  >```
  >
  >After this, we have bound the branch between local and remote.  next time. we can simply do:
  >
  >>git push origin master
  >>
  >>-- to push our commited files to remote repo. automatically to the "origin" and "master" branch.

+ Scenario 2: If my local is empty, I need to copy one repo from remote repo from the Github.

  >```
  >$ git clone git@github.com:michaelliao/gitskills.git
  >```
  >
  >Done !  now you can find there is a folder which is the repo in your current directory!









### Branch

[Understand different branches](https://blog.csdn.net/ShuSheng0007/article/details/80791849)

非常有用，帮助你了解真正企业开发中如何使用branch来进行迭代开发

![jaja](https://img-blog.csdn.net/20180624174835949?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1NodVNoZW5nMDAwNw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)





+  New a branch: `dev`

  > git branch dev

+ Switch our current branch to `dev` branch:

  > git checkout dev

+ Check how many branches now we have in this repo:

  > git branch

  ```
  $ git branch
  * dev    --* current branch we are in
    master
  ```

+ When things done, merge our branch back to our `master` branch.

  >git merge dev
  >
  >***Make sure to check what branch you are in. if you want to merge dev and master, you should first checkout to master and then go `git merge dev` ***

+ OK, we can delete dev branch now, its useless.

  > git branch -d dev (you must be in master branch)
  >
  > * you cannot in the branch which you are going to delete it. 

+ ```
  GO check branch list, now, only one branch.
  $ git branch
  * master
  ```

+  **Conflict**

  > For example, if two people work on the same file, and they all create a sub-branch for their work, and when both finish work, they need to merge back to the master branch.
  >
  > Things happen: both of them edit the first line of this file, so the confict occur when merge, because git can not merge the words together.

  ```
  ➜  notes git:(master) git merge dev
  Auto-merging haha.md
  CONFLICT (content): Merge conflict in haha.md
  Automatic merge failed; fix conflicts and then commit the result.
  ```

  ```
  ➜  notes git:(master) ✗ git status 
  On branch master
  Your branch is ahead of 'origin/master' by 2 commits.
    (use "git push" to publish your local commits)
  
  You have unmerged paths.
    (fix conflicts and run "git commit")
    (use "git merge --abort" to abort the merge)
  
  Unmerged paths:
    (use "git add <file>..." to mark resolution)
  	both modified:   haha.md
  
  no changes added to commit (use "git add" and/or "git commit -a")
  ```

  

  - When this happen, we need to fix the conflict by ourselves. Remember, the git merge +BRANCH, means the BRANCH overlap the current branch, the things BRANCH will not be chaged.

  - So, we just edit the `haha.md` in our current branch. If you dont solve the merge problem, the git wont let you go back the `dev` branch.

  ```
  Git is a distributed version control system.
  Git is free software distributed under the GPL.
  Git has a mutable index called stage.
  Git tracks changes of files.
  <<<<<<< HEAD
  Creating a new branch is quick & simple.
  =======
  Creating a new branch is quick AND simple.
  >>>>>>> feature1
  ```

  - Dont forget to `add`  and `commit ` when things done:

    ```
    $ git add readme.txt 
    $ git commit -m "conflict fixed"
    [master cf810e4] conflict fixed
    ```

  - > now we can use `git log --graph` to check the commit status. like:
    >
    > ```
    > *   commit ca9d673332c9862d788e06e44f09af7426c536f5 (HEAD -> master)
    > |\  Merge: 7ce62c2 861d6d1
    > | | Author: HappyBoy19940506 <HappyBoy19940506@users.noreply.github.com>
    > | | Date:   Thu May 28 04:15:32 2020 +1000
    > | | 
    > | |     merge conflict
    > | | 
    > | * commit 861d6d1b660b4a3f0a23be11e5830ba0dd5931eb (dev)
    > | | Author: HappyBoy19940506 <HappyBoy19940506@users.noreply.github.com>
    > | | Date:   Thu May 28 04:08:02 2020 +1000
    > | | 
    > | |     change the haha.md
    > | | 
    > * | commit 7ce62c2ee608aecfb92e86ac9b083d034cfd8b19
    > |/  Author: HappyBoy19940506 <HappyBoy19940506@users.noreply.github.com>
    > |   Date:   Thu May 28 04:08:44 2020 +1000
    > |   
    > |       i changed the 1st line
    > | 
    > 
    > ```

  - ```
    ➜  notes git:(master) git branch -d dev  
    Deleted branch dev (was 861d6d1).
    ```

    Cya!   dev  branch  !  :)

+ Fast-Forward vs No Fast-Forward

  - `git merge dev`  vs  `git merge --no-ff -m "merge" dev`

  - If we directly use `git merge dev`:

    > ```
    > commit 227496b211da2e1ff1eb41502fd19b07ab22d1f1 (HEAD -> master, dev)
    > Author: HappyBoy19940506 <HappyBoy19940506@users.noreply.github.com>
    > Date:   Thu May 28 07:26:55 2020 +1000
    > 
    >     new ccc.md  ---这是我在dev banch下commit的信息
    > 
    > commit ceb6c92a2bbfaf1aaeecf19f9fc0763b94910b70
    > ```

  - If we use `git merge --no-ff -m "merge dev" dev`

    >```
    >commit c351a54a99c78a02ea8472f0c7e678086f0977cb (HEAD -> master)
    >Merge: 227496b 4ecee08
    >Author: HappyBoy19940506 <HappyBoy19940506@users.noreply.github.com>
    >Date:   Thu May 28 07:31:40 2020 +1000
    >
    >    merge   -----这是我在merge的时候commit的信息
    >
    >commit 4ecee08d5936a1846bc46e332406c38fac5aa74d (dev)
    >Author: HappyBoy19940506 <HappyBoy19940506@users.noreply.github.com>
    >Date:   Thu May 28 07:30:23 2020 +1000
    >
    >    add ddd.md   ---这是我在dev banch下commit的信息
    >
    >commit 227496b211da2e1ff1eb41502fd19b07ab22d1f1
    >
    >```

  - When we use`git log --graph --pretty=oneline --abbrev-commit`

    > ```
    > *   c351a54 (HEAD -> master) merge
    > |\  
    > | * 4ecee08 add ddd.md   ----- ***USE --NO-FF MERGE*** 禁用fastforward模式
    > |/  
    > * 227496b new ccc.md  ------***NO USE --NO-FF MERGE***启用fastforward模式
    > 
    > 
    > 所以，合并分支时候，加上`--no-ff`参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。
    > 另外， 一定要用`git log --graph --pretty=oneline --abbrev-commit`才看的出效果。
    > ```





### When BUG happens

+ When the BUG happens, normally we can fix it on the master branch, we do:

  >1. Create a new branch from the master branch, called Hotfix.
  >2. Changes the bug and then merge the hot fix branch back to the master branch.

+ But when you do the bug, you are in the Dev branch. so you have to switch the branch.

  >1. If you are doing somethings on the Dev branch, which are not `commit` yet.
  >
  >2. you have to save the progress on this branch and then `switch master`
  >
  >3. why? if you dont save without `commit`, 
  >
  >   >you will see the files which are editing in the `git status` even you are in the `master`
  >   >
  >   >branch !!
  >   >
  >   >this is because, every branch shares the same working directory and stage area.
  >   >
  >   >so if you do the commit, you will also upload the files which are not completed.

+ How to save the progress?

  >```
  >git stash
  >
  >we can use this to save the progress in the current branch.
  >So we can safely switch the branch to our bug-fix branch.
  >
  >If we need do a git status.
  >we can find it will say: nothing to added and commited. 
  >So it's OK to do the changes in this branch. wont commit the files in the `dev` branch.
  >```
  >
  >

+ Retrive the progress?

  >1. use the `git stash list` to check all the stash list currently saving.
  >2. use the `git stash pop` to get the saved progress back !

+ 移植 一个单独的commit 从一个 branch 到另一个branch。

  If the bug has been fixed on the master branch, and the fix has to been fixed on the dev branch,

  what can we do to fix this bug on the dev branch without entirely merge the master branch.

  >`git cherry-pick + commit ID`
  >
  >copy this commit in that branch to the current branch.

  同样的bug，要在dev上修复，我们只需要把4c805e2 fix bug 101这个提交所做的修改“复制”到dev分支。注意：我们只想复制4c805e2 fix bug 101这个提交所做的修改，并不是把整个master分支merge过来。

  为了方便操作，Git专门提供了一个cherry-pick命令，让我们能复制一个特定的提交到当前分支：Git自动给dev分支做了一次提交，注意这次提交的commit是`1d4b803`，它并不同于master的`4c805e2`，因为这两个commit只是改动相同，但确实是两个不同的commit。用`git cherry-pick`，我们就不需要在dev分支上手动再把修bug的过程重复一遍.

+ 开发一个新feature，最好新建一个分支；

  如果要丢弃一个没有被合并过的分支，可以通过`git branch -D <name>`强行删除.

  ```
  $ git branch -d feature-vulcan
  error: The branch 'feature-vulcan' is not fully merged.
  If you are sure you want to delete it, run 'git branch -D feature-vulcan'.
  
  $ git branch -D feature-vulcan
  Deleted branch feature-vulcan (was 287773e).
  ```

  

  如果合并了分支，要返回，没关系，用`git reset --hard commitID`

  



### PUSH and PULL

[cooperation work ---using git push and git pull](https://www.liaoxuefeng.com/wiki/896043488029600/900375748016320)



### Rebase

### Tag Management 

### More about GitHub (pull request)

### Git alias

### GUI Git



