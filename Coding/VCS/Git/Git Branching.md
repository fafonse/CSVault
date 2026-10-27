Whenever you are developing on a [[Repository|repository]] with others, you should make a new branch to minimize any conflicts.

- After cloning a repository, use the command `git checkout -b [branch name]`
	- This creates a new branch that's local to your computer
- When pushing, you need to do `git push --set-upstream [main branch] [your branch]`
	- This sets your branch in the cloud, and you need to set it because it needs to know where your branch is branching off of
- To delete a branch use `git -d [branch name]`
- Switch branches with `git switch [branch name]`

That's all the setup. All [[Commit|commits]] made are now made to your branch, instead of the parent branch.

After setting up a branch, you can create pull requests to merge your changes onto the main repository. That way you can go over conflicts file by file, instead of pushing and hoping you don't fuck someone over.

>[!warning] After [[Merging Changes|merging]] a branch, make sure to pull on your local repository to make sure that your local clone is up to date

## Git Flow
Git flow is a branching method that keeps your work nice and tidy.

- When making any changes, create a branch for that part of the repo you're touching
- When you merge that branch, don't delete it
	- You can come back to it later to "reverse" your state back to that point

> Technically good commit messages and tagging can do the same thing, but that's harder to maintain