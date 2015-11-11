# The Lifars Git Process
## Set Up
First things first, we have to do some basic configuration.

* Get [git](https://help.github.com/articles/set-up-git/)!
* [Fork](https://help.github.com/articles/fork-a-repo/) the main repository 
* Clone using ssh
	* You need to [set up ssh](https://help.github.com/articles/generating-ssh-keys/) first
	* In a terminal, navigate to the destination directory and do: 
		* ```git clone git@github.com:[YourUsername]/[RepositoryName].git```
		* Where [YourUsername] is your username on Github and [RepositoryName] is the name of the repository you forked
* Configure your [upstream remote](https://help.github.com/articles/configuring-a-remote-for-a-fork/)

Now you can work locally on your own fork!
    

## Syncing with the Main Branch
If there is work on the main repository that you'd like to pull in you'll need to sync!

* Fetch the upstream changes:
	* ```git fetch upstream```
*  Rebase upstream ontop of your fork
	* ```git rebase upstream/[branch]```
	* Where [branch] is the upstream branch your are rebasing in
	* [More info on rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing/)  

## Saving Work
After you've made changes locally, you're going to want to keep your fork up to date.

[Commit early and commit often](https://sethrobertson.github.io/GitBestPractices/#commit)!

* First we need to *add* any new files we've made
	* ```git add -p```
	* This will allow you to add in an interactive fashion
* Next we need to stage our work in a *commit*
	* ```git commit -m "This is our message"```
	* The string following ```-m``` is our commits message, a short description of the work done
* Finally we *push* the work to our remote repository
	* ```git push origin [branch name]```
	* Where [branch name] is the name of the branch you are pushing to 	    

## Submitting Work
Alright cool, you have some finished features tested and working! Let's get that in the main repository!

* Rebase with the main repository first!
* Navigate to the main repository
* [Submit a pull request](https://help.github.com/articles/creating-a-pull-request/)
* Wait for your code to be reviewed
	* Sometimes, your PR might not be accepted on the first try! Make necessary amends and [squash your commits](http://stackoverflow.com/questions/5189560/squash-my-last-x-commits-together-using-git) 
* When it's good to go, a maintainer will merge your work into master! 
