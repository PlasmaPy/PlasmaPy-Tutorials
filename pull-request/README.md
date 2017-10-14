# Creating a Pull Request
This tutorial will walk you through making a pull request (often abbreviated to PR) to someone else's code project.

To make a PR:
- Fork a repo
- Clone your fork of the repo
- Create a new branch in your local repo
- Make some changes to your local branch
- Push the changes to your fork
- Create PR

## Fork a repo
Find and click the '**Fork**' button in the top-right of a GitHub repo that belongs to someone else - e.g.: SolarDrew/pyastro-my-first-PR.
This will make a copy of that repo, and that copy belongs to you.

## Clone your fork of the repo
On your fork of the repo (<_your-username_>/pyastro17-my-first-PR), use the '**Clone or Download**' button to download the repo.
This is the same as you've done before with any of your other repos.

#### Remotes
If you run `git remote -v` in your newly-cloned repo, you should see that you have one remote called 'origin'.
Again, this is the same as when you've pushed and pulled a repo to and from your GitHub account before.

When your repo is a fork of someone else's, it's often useful to deal with that version as well as your own, in which case you may need to add it as another remote.
By convention, that remote is called 'upstream'.

## Create a new branch in your local repo
#### Branches
Branches are a vital feature of git that allow different development tasks to be self-contained.
For instance, to add some new major functionality to a project, you will often want to create a separate branch of your repo.

Splitting off in this way allows you to return to the original version if you need a clean working environment, or make other updates to that code.
You can also have many different branches at once, so several different features can be developed at the same time without interfering with each other.

#### Working with branches
To see what branches exist in your repo, run `git branch`.
At the moment, this should just show 'master', which is the usual main branch and is the one branch created when you make a new repo.
You can also give this command an argument which is the name of a new branch to create.
So in this repo, run `git branch new_contributor` to make a new branch called 'new_contributor'.
This creates a branch but you are still working in the master branch.
To switch to your new branch, run `git checkout new_contributor`.

## Make some changes to your local branch
Make some changes to some document on your local branch of the repo.
For this example, add your name and GitHub username to the contributors list at the bottom of this file (README.md).
Commit your changes with `git add` and `git commit`.

## Push the changes to your fork
This is very similar to pushing you've done before, but now you need to take branches into account.

#### `git push` syntax
Up until now we have been doing `git push origin master`.
What this actually does is tell git to push your current branch of the local repo (which has been master until this example) to the 'master' branch of the 'origin' remote.

In this case we've been working in a different branch, 'new_contributor', so we don't want to push to the master branch.
Instead we should push to the new_contributor branch on origin, if it exists.
If not, we should push to it anyway and git will create it for us, so the command is the same either way:
`git push origin new_contributor`

## Create PR
On the GitHub page for your fork of the repo, you should see drop-down menu that says '**Branch: master**' and a button next to it saying '**New pull request**'.
Select the new_contributor branch from the drop-down menu and then click the button.
You should then get a page telling you what the base fork and branch are (into which you want your code to be merged), and the fork and branch are (that you're trying to merge).
For this example those should be SolarDrew/pyastro17-my-first-PR master and <_your-username_>/pyastro17-my-first-PR new_contributor.
This page also lets you give your PR a title and a description.

When you've added these, click the big green '**Create pull request**' button and you're done!
Now I, as the owner of the original repo, have the option to accept or refuse the changes you've made to the code.

## Contributors

- Drew Leonard (SolarDrew)
- Benjamin Winkel (bwinkel)
- Esteban Morales (eztean)