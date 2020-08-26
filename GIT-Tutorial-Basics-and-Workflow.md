# GIT Tutorial : Basics and Workflow

### Introduction

<p>Git is the most basic technology that probably every developer needs irrespective of his/her field of expertise. It has become a central infrastructure for every Open Source Software and workflow. Today we are going to discuss just about how you can get started with git and integrate it with your project's workflow.</p>

<p>Git is a <em>distributed Version Control System</em>, which means you can keep track of the changes in your codebase seamlessly along with your team and you don't even need a centralized server.</p>

<p>The way this software works is that it records and time stamps the snapshots of your file-system/codebase.</p>

<p>This article is all about using git confidently for your day to day needs. And by the end of this article-tutorial, you will know enough of git that you will be able to contribute to an open source project with confidence.</p>

<p>Let's look at some basic and frequent git terms.</p>

#### Terminology
<ul>
<li><p> <strong>Repository</strong> : The directory containing all the sub-directories, files and source code. </p></li>

<img alt="Github repository" align="center" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598340509753/oRMIB4wLO.png" />

<li><p> <strong>Local and Remote</strong> : Your home computing device is the local device and the repository it contains is called the local repository. The device you communicate with over the internet is the remote device and the repository it contains is called the remote repository. </p></li>

<li> <strong>Cloning</strong> : Copying a remote repository to your local device. </li>

<img alt="Git clone output" align="center"  src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598343360515/aEPSeTHCq.png" />

<li><p><strong> Branch </strong> : Think of it as a road diverging from a highway and reuniting with it later. It is the roads where all the changes to your codebase will take place. The main highway or the default branch is called `master`. That is, you diverge from `master`, make changes to your codebase in a new branch, and when you are done with the changes you will reunite the development branch back with the `master` branch. </p></li>

<img alt="Git Branches" align="center"  src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598347889153/4BHGUuEz9.jpeg" />

<li><p> <strong>Commit</strong> : Changes are done to the codebase in discrete steps called a commit i.e. a commit is a basic unit of change in git. A commit contains the following information : Changes done, change message, change description, the author (the person who made the changes), the committer (the person who committed the changes to the codebase), the timestamp of the change, information about the parent branches and a hash value associated with the change. Here is an screenshot of a commit : </p></li>

<img alt="Git commit output" align="center"  src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598342490464/f6tXpuJgA.jpeg" />

<li><p> <strong>Log</strong> (commit history) : Git maintains the history of commits in a chronological way called the log. Here is an example of the commit history of [MinimalOS](https://github.com/MrSquanchee/MinimalOS/commits/master) : </p></li>

<img alt="Git log output screenshot" align="center"   src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598346297411/Oa9x2AbOJ.png" />

<li><p> <strong>Merge</strong>: The reunion of a branch with another branch (usually, master) is called merging. This is when all the changes form different branches are brought together. </p></li>

<li><p> <strong>Rebase</strong> : It is basically redefining and revising the commit history or log. Rebasing is a smart way to clean the history of your branch up to the standards 
 of a project before submitting it for a merge with the `master` branch.</p></li>

<li><p> <strong>Pull Request</strong> : Requesting a remote party to merge your changes or branch with their local branch. </p></li>
</ul>
<hr>

### Git Commands

<p><b>NOTE</b>: Having a github account is recommended</p>

<p>For the sake of understanding the commands better we will make a new repository on github and name it `git-tutorial`, clone it into our local device, make some changes and <em>use git for real</em>. You can also fork [this](https://github.com/MrSquanchee/git-tutorial) repository and follow along the tutorial. We will follow the standard workflow of contributing to an Open Source software.</p>

<b>Step 1</b> :  Clone a repository

~ <strong>git clone</strong> `<location>`

<p>Description : Copies the repository present at `<location>`. Where `<location>` can be any string specifying a git repository's location, for e.g. an [internet URL](https://en.wikipedia.org/wiki/URL) or a directory location of any repository in your local system.
For this tutorial, we will use the [github repository](https://github.com/MrSquanchee/git-tutorial) that I created just for this purpose.</p>

E.g.
```
git clone "https://github.com/MrSquanchee/git-tutorial.git"
cd git-tutorial/
```
<br>
<b>Step 2</b> : Setup the git repository

~ <strong>git config</strong> `[--global] user.name <name>`
<br>~ <strong>git config</strong> `[--global] user.email <email>`

<p>
Description : The above commands will configure the repository with your name and email. Replace the `<name>` and `<email>` with your own name and email.
It is important to do this step as this information will be used by git to add the author field to your commits. And optionally, you can use the `--global` flag in the command to set your information globally for the whole system.
</p>

E.g.

```
git config --global user.name "YourNameHere"
git config --global user.email "abc@example.com"
```

~ <strong>git remote</strong> `add <var-name> <location>`
<br>~ <strong>git remote</strong> `remove <var-name>`

<p>
Description : With the command line option `add`, this adds a remote variable specified by `<var-name>` with a value of `<location>` and with the option `remove`, it removes the variable specified by `<var-name>`.
</p>
<p>
Remote variables are generally used as pointers to forks and remote clones of the repository. These are used so that you don't have to type the long URL again and again.
</p>

E.g.

```
git remote add upstream <your-forked-repository-url>
```

<p>All the configuration information is stored in the `config` file under the `.git` directory. That is, you can see the configuration changes you have made so far with the command :</p>

```
cat .git/config
```

The output will look something like this :

<img alt="Git Configuration Setup ScreenShot" align="center" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598364409484/I-bTGZbe9.png" />

<br>
<b> Step 3</b> : Branches

~ <strong>git branch</strong> `[-a]`
<br>~ <strong>git branch</strong> `-D <branch-name>`

<p>
Description  : This command shows the branches in your local repository and if used with the command line option `-a`, it shows all the branches of the local repository + remote repository.<br>
The second command with the option `-D` will delete the branch with the name `<branch-name>`.
</p>

E.g.

```
git branch
git branch -a
```

The output will look something like this :

<img alt="Output of git branch and git branch -a" align="center" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598373140196/eDi7SMXVf.png"/>

~ <strong>git checkout</strong> `[-b] <branch-name>`

<p>
Description : Using this command you can switch between different branches.
And with the optional flag `-b`, this will create a new branch and switch to it.
</p>

E.g.

```
git checkout -b new-branch
git checkout master
git branch
git branch -D new-branch
git branch
```

The above commands will create a new branch named "new-branch" and will switch to it, switch back to master, display the branches, delete "new-branch" and then display the branches again.

The output will look something like this :

<img alt="Output of git branch and git branch -a" align="center" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598373885777/Vc-CRBWAR.png"/>

<br>
<b> Step 4</b> : Make Changes and Commit

<p>
Now, it's time you make some changes in the repository.<br>
Open the README.md file, in the editor of your choice, and add your name to it at the end of the file and write a review of this articles. And for the sake of making changes, create a new branch for your changes and name it anything you like.
</p>

E.g.
(I am doing this via the `cat` command line utility and adding my name.)

```
$ cat >> README.md
Hello I am Suraj Upadhyay and I am the author of this article. <Cntrl-d>
```
<p>Save and Exit.</p>

The output will look something like this :

<img alt="Usage of cat command" align="center" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598375328192/4Bb0E19FS.png"/>

~ <strong>git status</strong>

<p>Description : This command reports which files have been changed, deleted and/or created. It is a simple command with is generally used after making all the changes.</p>

E.g.

```
git status
```

The output will look something like this :

<img alt="Usage of cat command" align="center" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598376129445/CkvkPGnNg.png"/>

<p>Now, if you want to see what changes you have made on the command line probably before committing, you would use the following command</p>

~ <strong>git diff</strong> `[file-name]`

<p>
Description : This command outputs the diff between the previous <b>HEAD</b> (the last commit) and the current state of the codebase and defaults to all files unless a particular file-name is specified. It shows the diff in the git format i.e. all the added lines are shown with (+) sign and all the removed line are shown with (-) sign and each modified line is shown as a couple of removal and addition.
</p>

E.g.

```
git diff ./README.md
```
The output will look something like this :

<img alt="Output of git diff" align="center" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598376968848/QY99Q2XAB.png"/>

~ <strong>git add</strong> `[file1[,file2,[...]]]`

<p>
Description : This command adds `git diff` of all the files, given as an argument, to the staging-index. The `diffs` in the staging area are logically the next to be committed changes.
</p>

~ <strong>git diff</strong> `--cached`

<p>
Description : When the `git diff` is used with the `--cached` option, it shows the diff of the files added to the staging-index.
</p>

E.g.

```
git add ./README.md
git diff --cached
```

Output will look something like this :

![gitAddSS.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598377834150/UV5wVCSVe.png)

~ <strong>git stash</strong> `[file1[,file2,[...]]]`
<br>~ <strong>git stash pop</strong> `[file1[,file2,[...]]]`

<p>
Description : In git, the stash is like a stack, you can push changes into it and pop the changes into existence. Also, you get to specify the file-names in the argument.
</p>

```
git stash
git status
git stash pop
```

Output will look something like this :

<img alt="Output of git stash and git stash pop" align="center" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1598382891475/wtVKzjijs.png"/>

~ <strong>git commit</strong>

<p>
Command line options : There are many options with this command as with others, but for regular usages you will just need these: 
<li> `-a` : it will commit everything that is chagned if used with the command line option `-a`</li>
<li>`-m <commit-description>` : used to set the commit-description to `<commit-description>`, this is used only if you don't want to specify a commit message</li>
<li>`--amend`: If you changed your mind after committing something, you can make your changes again and amend the commit with the `--amend` option</li>
<li> `-s` : used to append a "Signed-off-by: <your-name>" string to the commit message.<br>
All of this options can also be used alongside each other</li>
</p>

<p>
Description : This command commits all your changes which are staged with `git add` or the command line option `-a` and will prompt you to specify commit description and commit message in your default editor.
</p>

E.g.

Let's commit our changes to the repository.

If you remember the previous example, we used `git stash` and `git stash pop` which destaged our changes, so now we should use the `-a` command line option, to automatically add every change to the staging index :

```
git commit -a
```

And you will be prompted to enter a commit description and message.

![gitCommitSS.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598424545212/Rk_vu7tTM.png)

![gitCommitPromptSS.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598424530084/sO0WXKfcc.png)

<br>
<b>Step 5</b> : Commit history

~ <strong>git log</strong> `[file-name]`

<p>
Description : This command shows all the commits that changed the file given as the argument. If a file argument isn't given to `git log`, it will show all the commits which changed whole codebase in reverse-chronological order.
</p>

E.g.

```
git log ./README.md
git log
```

The output of the above commands will look something like this :

![gitLogFileSS.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598424817707/5wUkkCeoW.png)

![gitLogSS.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598424861928/epYPXxAnZ.png)

~ <strong>git show</strong> `<commit-hash>`
<br>~ <strong>git reset</strong> `[--soft|--hard] <commit-has>`

<p>
Description : These two commands are used to interact with the commit history.
<br>1. The first command shows the commit passed as the argument `<commit-hash>` i.e. It shows the commit-description, message, author, timestamp, hash and the diff it committed.
<br>2. The second command can travel back to the specified commit. If used with the `--hard` option it will delete every change made after the specified commit. And if used with the `--soft` option it will preserve all the changes after the specified commit i.e. you will be able to see these changes via `git diff` and `git status`.
</p>

E.g.

```
git show HEAD
git reset --soft HEAD^
```

Now, obviously after the second command you will need to recommit your changes.

```
git log
git commit -s -a -m "Tutorial : Add Information"
git log
```

The output of the above commands will look something like this :


![gitShowHEADScreenShot.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598425524464/n62xZ4_Ye.png)

![gitResetScreenShot.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598425609688/fvDw0Ts8A.png)

![gitLogCommitLogScreenShot.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598425682832/aDBpjyf4K.png)

<br>
<b> Step 5</b> : Update remote and local repositories

<p>
When you make your changes locally, the remote/forked repository goes out of sync, similarly when changes are made in the remote/origin repository your local repository can go out of sync. To avoid this, you should regularly update your local copy and whenever you finish doing your work you should update the remote repository too. In this step, you will learn how to do the same.
</p>

~ <strong>git push</strong> '<remote-var> [+]<branch-name>'

<p>
Description : This command pushes your local changes in `<branch-name>` to the repository pointed to by `<remote-var>`. If the you are pushing a new branch, you have to use the (+)-plus sign before the branch's name.<br>
After entering this command you will be prompted for your github username and password, if `<remote-var>` is hosted on github.
</p>

E.g.

```
git push upstream master
```

The output will look something like this :

![gitPushSS.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598432534752/1wjB6if0y.png)

~ <strong>git fetch</strong> `<remote-var> [<branch-name>]`

<p>
Description : This command downloads all the branches and changes from the repository `<remote-var>`. If a `<branch-name>` is specified, the changes form the particular branch is downloaded.
</p>

E.g.

```
git fetch upstream new-branch
```
You can copy and run the above command.

The output will look something like this :

![gitFetchSS.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598433320016/tcKf6D8v6.png)

~ <strong>git merge</strong> `<branch-name>`

<p>
Description : This command merges the branch `<branch-name>` to the current branch. Don't forget to check your current branch with `git branch` before entering this command.
</p>

E.g.

```
git merge upstream/new-branch
```

~ <strong>git pull</strong> `<remote-var> <branch-name>`

<p>
Description : This command is used to update your local repository's branch with the remote repository's (`<remote-var>`) branch (`<branch-name>`). It is a compound command of `git fetch` and `git merge`. That is, under the hood it executes as follows :
```
git fetch <remote-var> <branch-name>
git merge <remote-var>/<branch-name>
```
</p>

<b>Step 6</b> : You can optionally send my a pull request.

<p>
If you have followed along this tutorial you would have a forked repository with some changes to the README.md file. Now, you should head directly to you github forked repository and you will see a compare and pull request prompt, you can follow the prompts on github and send me a pull request. I know there aren't any significant changes and mean nothing but I will be glad to guide you with the pull request and review process, which is one of the most important steps while engaging in any Open Source Community.
</p>

### Conclusion

<p>Git is a huge software and you can do things beyond this tutorial has done. To know more about git, I would recommend you to head out to the official git documentation [here](https://git-scm.com/doc).</p>

<p>You have now learnt enough of git now that you can contribute to any open source project with confidence. Please do comment, if you have any queries regarding the basics and workflow of git.</p>

Thanks for reading.

