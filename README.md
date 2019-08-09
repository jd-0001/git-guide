# git-guide
This repo is created to list common git actions

## Branch

**Q: How to create new branch?**
  
Use `git branch <branch_name>` to create new branch locally. Make commit in this branch and push changes to new branch using `git push origin <feature_branch>`. This will add remote branch with your changes.

**Q: How to remove local branch & remote branch?**
  
Remove local branch using `git branch -d {the_local_branch}` command. (use -D instead to force deleting the branch without checking merged status)
  
Remove remote branch using `git push origin --delete {the_remote_branch}` command.
