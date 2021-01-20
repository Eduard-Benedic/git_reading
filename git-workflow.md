# Branching Workflows

## Long Running Branches
- longer
- more suitable for large projects

# Topic branches
- shorter
- for projects of any size

To push to a branch
**git push (remote) (branch)**
e.g **git push origin serverfix**
You can also work on a different named branch and push to the same remote branch
**git push origin (name-of-branch):(where to push to the remote)**
git push origin serverfix:serverix
git push origin serverfix:great-remote-branch
This commands pushes from the serverfix branch to the "great-remote-branch"


## Tracking branches
Tracking branches are local branches that have a direct relationsip to a remote branch.

**git checkout --track origin/serverfix**

To set up a local branch with a different name than the remote branch, you can type:
**git checkout -b [branch] [remotename]/[branch]**

If you already track a remote branch with your local branch you can push upstream with:

**git merge @{upstream} || git merge @{u}**