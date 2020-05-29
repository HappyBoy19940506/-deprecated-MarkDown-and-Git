# Git 常见问题大杂烩！

1. How to delete a remote branch in remote repo:

   >git push origin --delete dev

2. How to check the remote branch list in origin/git hub:

   >git branch -r

3. Git restore filename VS Git restore --staged filename 

   前者：把当前文件（在工作区)回退到最近一次add或者commit的状态，因为add和commit肯定是一样的修改

   后者：把缓存区的文件退回到工作区。内容没有变化，仅仅是退回。所以要回退，需要再restore+filename一次。

