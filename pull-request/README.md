# Creating a Pull Request
This tutorial will walk you through how to request that someone else pulls your changes to their code into their project.
This is called a **pull request**, usually abbreviated to PR.
It is assumed that you are comfortable with using the fundamental git commands (`git add`, `git commit`, etc.) at a command prompt, and that you are familiar with pushing and pulling repositories to and from GitHub.
If you are completely new to git, you may want to first find and go through a tutorial to learn these fundamental commands before continuing with this one. 
https://try.github.io/ and https://git-scm.com/book/en/v1/Git-Basics are two such tutorials, but there are plenty of others out there.

These are the steps necessary to make a PR, each of which will be described in more detail below:
- Fork a repository
- Clone your fork of the repo
- Create a new branch in your local repo
- Make some changes to your local branch
- Push the changes to your fork
- Create PR

## Fork a repo
Find and click the '**Fork**' button in the top-right of a GitHub repo that belongs to someone else - e.g.: https://github.com/PlasmaPy/PlasmaPy-Tutorials.
This will make a copy of that repo, and that copy belongs to you.

## Clone your fork of the repo
On your fork of the repo (<_your-github-username_>/PlasmaPy-Tutorials), use the '**Clone or Download**' button to download the repo.
Alternatively you can do this manually at the command line with the syntax `git clone https://github.com/<_your-github-username_>/<_name-of-repo_>.git` or `git clone <git@github.com:<_your-username_>/<_name-of-repo_>.git`.
This is the same as you've done before with any of your other repos.

#### Remotes
If you run the command `git remote -v` in your newly-cloned repo, you should see that you have one remote called **'origin'**.
Again, this is the same as when you've pushed and pulled a repo to and from your GitHub account before.

When your repo is a fork of someone else's, it's often useful to deal with that version as well as your own, in which case you may need to add it as another remote.
By convention, that remote is called **'upstream'**.
To do this, you can run `git remote add upstream <_url-of-remote-repo_>`.
In this case the URL for the upstream remote would be https://github.com/PlasmaPy/PlasmaPy-Tutorials.

## Create a new branch in your local repo
This step is not strictly necessary to make a PR, but is highly recommended as part of the git workflow in general, so we shall take the time to go through it here.
You can do this with the command `git branch new_contributor` and then `git checkout new_contributor`.
These commands are explained below.

#### Branches
Branches are a vital feature of git that allow different development tasks to be self-contained.
For instance, to add some new major functionality to a project, you will often want to create a separate branch of your repo.
Splitting off in this way allows you to work on the new feature without affecting the original code at all until you are ready to merge them together.
This means you can return to the original version if you need a clean working environment, or make other updates to that code.
You can also have many different branches at once, so several different features can be developed at the same time without interfering with each other.

#### Working with branches
To see what branches exist locally in your repo, run `git branch`.
At the moment, this should just show 'master', which is the usual main branch and is the one branch created when you make a new repo.
You can also give this command an argument which is the name of a new branch to create.
So in this repo, run `git branch new_contributor` to make a new branch called 'new_contributor'.
This creates a branch but if you run `git branch` again, you will see that you are still working in the master branch.
To switch to your new branch, run `git checkout new_contributor`.
Similarly, from there you can return to your original branch with `git checkout master`.

## Make some changes to your local branch
Make some changes to some document on your local branch of the repo.
For this example, add your name and GitHub username to the contributors list at the bottom of this file (pull-request/README.md).
Commit your changes with `git add` and `git commit`.

Once you've done this you can see the separation of branches by checking out your master branch again and inspecting it.
If you look at the commit history (`git log`) and open the file again, you will see that the commit you just made and the corresponding changes are no longer there.
Returning to the new_contributor branch restores the commit and the changes.
Don't forget to do this before moving on with the tutorial.

### Update your local branch
This is also not strictly necessary but is often a good idea.

It is important to remember that while we are making changes in our branch of our fork, it is very likely that the main project branch (`upstream/master`) is also changing.
If we don't to anything to account for this, it may cause merge conflicts when we make our PR, which will delay our contribution.
It therefore often makes things easier (particularly for the maintainer of the main code project) for you to pull in any changes to upstream and resolve any conflicts with your changes locally.
Doing this means that when you make your PR, the only differences between your branch and the original are the changes you wish to submit, which is as it should be.
You can do this with `git pull upstream master`.
Note that this pulls the master branch of the upstream repo and merges it into _your current local branch_ - don't make the common mistake of thinking this will update your local master branch, unless that is the branch you have checked out when you run the command.
See below for a bit more on this syntax, which is the same as for `git push`.

## Push the changes to your fork
This is very similar to pushing you will have done before, but now you need to take branches into account.

#### `git push` syntax
Up until now you have likely been doing `git push origin master`.
What this actually does is tell git to push your current branch of the local repo (which is master by default) to the 'master' branch of the 'origin' remote.

In this case we've been working in a different branch, `new_contributor`, so we don't want to push to the master branch.
Instead we should push to the `new_contributor` branch on origin, if it exists.
If not, we should push to it anyway and git will create it for us, so the command is the same either way: `git push origin new_contributor`.

## Create PR
On the GitHub page for your fork of the repo, you should see drop-down menu that says '**Branch: master**' and a button next to it saying '**New pull request**'.
Select the `new_contributor` branch from the drop-down menu and then click the button.
You should then get a page telling you what the base fork and branch are (into which you want your code to be merged), and what the fork and branch are (that you're trying to merge).
For this example those should be `PlasmaPy/PlasmaPy-Tutorials master` and `<_your-username_>/PlasmaPy-Tutorials new_contributor`.
This page also lets you give your PR a title and a description, which you should use to make clear to other developers what the purpose of the PR is.

When you've added these, click the big green '**Create pull request**' button and you're done!
Now I, or another maintainer of the original repo, have the option to accept or refuse the changes you've made to the code.

## Contributors

- Drew Leonard (SolarDrew)
- Felipe Nathan de Oliveira (felipenathan)
