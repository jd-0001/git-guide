# git-guide
This repo is created to list common git actions

## Branch

**Q: How to create new branch?**
  
Use `git branch <branch_name>` to create new branch locally. Make commit in this branch and push changes to new branch using `git push origin <branch_name>`. This will add remote branch with your changes.

**Q: How to remove local branch & remote branch?**
  
Remove local branch using `git branch -d {the_local_branch}` command. (use -D instead to force deleting the branch without checking merged status)
  
Remove remote branch using `git push origin --delete {the_remote_branch}` command.

**Q: How to delete commit from branch?**
1. Move to branch from which you want to remove commit
2. Use `git log` command to list all commits
3. Copy the commit hash from log
4. Run `git reset --hard <commit>` to delete commit in that branch
5. Run `git log` again to confirm
6. Make changes to branch(if you want to) and finally push your changes using `git push origin <branch_name>`
