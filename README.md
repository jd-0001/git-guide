# git-guide
This repo is created to list common git actions

## Commands - What They Do?

**Checkout**
  
This command is used to switch to other branch. If you get master branch as your default branch intialy when you start or clone project and you want to switch to different branch(let's say `dev`), you will use `git checkout <branch_name>`.
```bash
# switch to "dev" branch
git checkout dev
```

**merge**

Generally it is used to merge two branches. It combines commits of two branches. So, if you want to get commits of `master` branch in `dev` branch you will use.
```bash
# switch to "dev" branch
git checkout dev

# get commits from "master" branch
git merge master
```

## Resolve Conflicts

While merging branches it is common that you might get conflict. When two developers works on same file this scenarior occurs. So, when you run `git merge <branch_name>` git shows conflicts. To solve this conflict you can either use git command to take changes of yours/others or you can manually go to that file and resolve conflict as you wish.

**Using git command**
So, what's the difference between both approaches. When you use git command to resolve conflict you can only get changes of one developer. So, you will remove changes of other developer. To perfrom this operation we will use `checkout` command along with parameter `ours`/`theirs`.
  
So, if you want to take your changes then you will below command
```
git checkout --ours path/to/file/file-name.py
```
Else if you want to get changes from other developer.
```
git checkout --theirs path/to/file/file-name.py
```

So, above approach is not useful sometimes or mostly.

**Manually**
In this approach, you can get both changes. Unlike above approach where you have to chooses only one from both changes in manual approach you have to go to that conflicted file and edit that file the way you want. So, you can keep changes of both side.
  
To perform this first you have to understand how git shows conflict in files.

When you get conflict in any file and you open that file, search for `<<<<<<<`, this is called as conflict marker. Section between `<<<<<<<` and `>>>>>>> <branch_name>` is conflicted area. Between these two markers you will find `=======`, which stands as separater. Code above from this seperator is from your side(please check below example) and code below this seperator from incoming side.
  
```
# other code

<<<<<<< HEAD
I am change of yours
=======
I am changes from other/upcoming
>>>>>>> <branch_name>

# other code
```

Now, to resolve conflict just remove above mentioned threee merkers from file and make changes as you like. Conflict is resolved. But, you have to add new commit for this.

```
git commit -m "resolved conflict blah blah"
```

Conflict Solved!

## Branch

**Q: How to create new branch?**
  
Use `git branch <branch_name>` to create new branch locally. Switch to newly created branch using `git checkout <branch_name>`. Make commit in this branch and push changes to new branch using `git push origin <branch_name>`. This will add remote branch with your changes.

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
