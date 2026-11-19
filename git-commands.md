# git commands

## staging and commit
### stage files to "index"

	git add filename

### commit staged files

	git commit -m "Initial Commit"

### stage changes and deletions (no new files), then commit staged files

	git commit -a -m "Initial Commit"     

### show commit log

	git log      # chronological descend

### diff between staged and working
	
	git diff filename

### git stash
```
# Save tracked changes and clean the working tree
git stash

# Save changes with a message
git stash push -m "message"

# Also include untracked files
git stash push -u

# List saved stashes
git stash list

# Inspect latest stash
git stash show -p

# Reapply latest stash and keep it saved
git stash apply

# Reapply a specific stash and keep it saved
git stash apply stash@{n}

# Reapply latest stash and remove it from the list
git stash pop

# Remove a specific stash
git stash drop stash@{n}
```


## backtrack commands
### git restore
Default: copy index to working tree
```
# Index → working tree

	git restore <path>

# HEAD → index

	git restore --staged <path>

# HEAD → index and working tree

	git restore --staged --worktree <path>

# Commit → working tree

	git restore --source=<commit> <path>

# Commit → index and working tree

	git restore --source=<commit> --staged --worktree <path>
```
	
### git reset
Default: copy HEAD to index
```
# Copy HEAD → index; working tree unchanged

	git reset

# Copy HEAD → index for selected path (unstage); working tree unchanged

	git reset <path>

# Move HEAD → commit; index and working tree unchanged

	git reset --soft <commit>

# Move HEAD → commit and reset index; working tree unchanged

	git reset <commit>

# Move HEAD → commit and reset index and working tree

	git reset --hard <commit>

# Copy commit → index for selected path; working tree unchanged

	git reset <commit> -- <path>      # '--': end-of-options marker
```

## branches and teamwork

Workflow
1. Make a branch to commit subtask-changes without disturbing the "teamwork" on the main branch.
2. Commit (tested) changes.
3. Open a pull request.
4. Review the pull request.
5. Merge the branch with main when the subtask is finished.
6. Delete the branch.

### git branch
```
# Show current branch

	git branch

# Create a branch

	git branch NEW_BRANCH

# Switch to another branch

	git checkout BRANCH

# Merge branch to main

	# add and commit changes on BRANCH
	git checkout main   # switch to main
	git merge BRANCH

# Merge conflict

A file contains a changed line on BRANCH and on main

	<<<<<<< HEAD
	# this is a PRO file on branch "main"
	=======
	# this is a MED file on branch "fences"
	>>>>>>> fencing

# Delete branch

	git branch -d BRANCH
```
