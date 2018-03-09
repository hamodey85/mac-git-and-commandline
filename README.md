
#### Required Commands
Heads up! We'll be using the following terminal commands in this lesson:

>* `ls` -or `-l` used to list files and directories **notice** its `L` letter not `i`
>*  `mkdir`  - used to create a new directory
>* ` cd `  - used to change directories
>* ` rm `  - used to remove files and directories
>* ` pwd ` - used to print working directory
----------


## First Time Git Configuration


##### sets up Git with your name

```bash
git config --global user.name "<Your-Full-Name>"
```

##### sets up Git with your email

```bash
git config --global user.email "<your-email-address>"
```

##### makes sure that Git output is colored

```bash
git config --global color.ui auto
```

##### displays the original state in a conflict

```bash
git config --global merge.conflictstyle diff3
```

```bash
git config --list
```






## Git & Code Editor
----------
The last step of configuration is to get Git working with your code editor. Below are three of the most popular code editors. If you use a different editor, then do a quick search on Google for "associate X text editor with Git" (replace the X with the name of your code editor).


##### VSCode Setup

```bash
git config --global core.editor "code --wait"
```

##### Atom Editor Setup

```bash
git config --global core.editor "atom --wait"
```

##### Sublime Text Setup

```bash
git config --global core.editor "'C:/Program Files/Sublime Text 2/sublime_text.exe' -n -w"
```







## Create A Repo From Scratch

----------
Before you can make commits or do anything else with a git repository, the repository needs to actually exist. To create a new repository with Git, we'll use the ` git init ` command.
The ` init ` subcommand is short for **"initialize"**

#### Required Commands
Heads up! We'll be using the following terminal commands in this lesson:

>* ` ls ` - used to list files and directories ==notice== its `L` letter not `i`
>* ` mkdir `  - used to create a new directory
>* ` cd `  - used to change directories
>* ` rm `  - used to remove files and directories
>* ` pwd ` - used to print working directory


#### Create  Directories

>* create a directory called `testCommand`
>* inside that, create another directory called `new-git-project`
##### or
just run this command on the terminal - `mkdir -p udacity-git-course/new-git-project && cd $_`

#### Git Init
Use the `git init` command to create a new, empty repository in the current directory.

Running this command creates a hidden `.git` directory. This `.git` directory is the brain/storage center for the repository. It holds all of the configuration files and directories and is where all of the commits are stored.



#### todo:  git clone
The git clone command is used to create an identical copy of an existing repository.
```
git clone https://github.com/username/repo_name <optional newFileName>
```

my  repo is **mac-git-and-commandline**
create a new repository on the command line
```
echo "# mac-git-and-commandline" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/hamodey85/mac-git-and-commandline.git
git push -u origin master
```

…or push an existing repository from the command line
```
git remote add origin https://github.com/hamodey85/mac-git-and-commandline.git
git push -u origin master
```

#### git status
The `git status` is our key to the mind of Git. It will tell us what Git is thinking and the state of our repository as Git sees it. When you're first starting out, you should be using the git status command all of the time! Seriously. You should get into the habit of running it after any other command. This will help you learn how Git works and it'll help you from making (possibly) incorrect assumptions about the state of your files/repository.





#### The Git Log Command
The `git log` command is used to display all of the commits of a repository.
By default, this command displays:

* the SHA
* the author
* the date
* and the message


Git uses the command line pager, Less, to page through all of the information. The important keys for Less are:

* to scroll down by a line, use j or ↓
* to scroll up by a line, use k or ↑
* to scroll down by a page, use the spacebar or the Page Down button
* to scroll up by a page, use b or the Page Up button
* to quit, use q



Let's think about some of these questions:
* **the SHA **- git log will display the complete SHA for every single commit. Each SHA is unique, so we don't really need to see the entire SHA. We could get by perfectly fine with knowing just the first 6-8 characters. Wouldn't it be great if we could save some space and show just the first 5 or so characters of the SHA?

* **the author** - the git log output displays the commit author for every single commit! It could be different for other repositories that have multiple people collaborating together, but for this one, there's only one person making all of the commits, so the commit author will be identical for all of them. Do we need to see the author for each one? What if we wanted to hide that information?

* **the date **- By default, git log will display the date for each commit. But do we really care about the commit's date? Knowing the date might be important occasionally, but typically knowing the date isn't vitally important and can be ignored in a lot of cases. Is there a way we could hide that to save space?
* **the commit message** - this is one of the most important parts of a commit message...we usually always want to see this

What could we do here to not waste a lot of space and make the output smaller? We can use a **flag**.


>TIP: This isn't a course on the command line, but a `flag` is used to alter how a program functions. For example, the `ls` command will list all of the files in the current directory. The `ls` command has a `-l` flag (i.e. `ls -l`) that runs the same ls command but alters how it works; it now displays the information in the long format (the `-l` for long).
>Flags can be used to alter how a program functions and/or what is displayed.

### git log --oneline
To recap, the `--oneline` flag is used to alter how git log displays information:

```
$ git log --oneline
```
This command:
* lists one commit per line
* shows the first 7 characters of the commit's SHA
* shows the commit's message

ex:`a3dc99a      ......  added new componant to index.html `



#### git log --stat

 the `--stat` flag is used to alter how `git log` displays information:

```
$ git log --stat
```
This command:
* displays the file(s) that have been modified
* displays the number of lines that have been added/removed
* displays a summary line with the total number of modified files and lines that have been added/removed

#### git log  --patch 

the `-p` flag (which is the same as the `--patch` flag) is used to alter how `git log` displays information:
```
git log -p
```
This command adds the following to the default output:
* displays the files that have been modified
* displays the location of the lines that have been added/removed
* displays the actual changes that have been made

#### Annotated git log -p Output

![Annotated](git-log-p-lines-removed-annotated.png)
Using the image above, let's do a quick recap of the `git log -p` output:

* 🔵 - the file that is being displayed
* 🔶 - the hash of the first version of the file and the hash of the second version of the file
    * not usually important, so it's safe to ignore 
* ❤️ - the old version and current version of the file
* 🔍 - the lines where the file is added and how many lines there are
    * `-15,83` indicates that the old version (represented by the `-`) started at line 15 and that the file had 83 lines.
    * `+15,85 `indicates that the current version (represented by the `+`) starts at line 15 and that there are now 85 lines...these 85 lines are shown in the patch below
* ✏️ - the actual changes made in the commit
    * lines that are red and start with a minus (`-`) were in the original version of the file but have been removed by the commit
    * lines that are green and start with a plus (`+`) are new lines that have been added in the commit


we can run both --stat and --patch

###### Here we run both --stat and --patch
it will display both with stat info above patch info
```
git log -p --stat
```
this -w will ignore white spaces change
```
git log -p -w
```

######Further Research
[General paches with -p](https://git-scm.com/docs/git-diff#_generating_patches_with_p
) from the Git docs


#### Too Much Scrolling !!

>Wouldn't it be super handy if you could just display a specific commit's details without worrying about all of the others in the repo?

There are actually two ways to do this!
* providing the SHA of the commit you want to see to `git log`
* use a new command `git show`

They're both pretty simple, but let's look at the `git log `way and then we'll look at `git show`.

You already know how to "log" information with:

* `git log`
* `git log --oneline`
* `git log --stat`
* `git log -p`

But did you know, you can supply the **SHA** of a commit as the final argument for all of these commands? For example:

```bash
$ git log -p fdf5493
```





The `git log` command is extremely powerful, and you can use it to discover a lot about a repository. But it can be especially helpful to discover information about a repository that you're collaborating on with others. You can use `git log` to:

- group commits by author with


  ```bash
  $ git shortlog
  ```

  ```bash
  $ git shortlog
  ```

- filter commits with the `--author` flag

  ```bash
  $ git log --author="Richard Kalehoff"
  ```

- filter commits using the `--grep` flag

  ```bash
    $ git log --grep="border radius issue in Safari"
  ```







#### git show

The other command that shows a specific commit is ` git show `:

```bash
$ git show
```
```bash
$ git show fdf5493
```
The `git show` command will show only one commit. So don't get alarmed when you can't find any other commits - it only shows one. The output of the `git show` command is exactly the same as the `git log -p` command. So by default, `git show` displays:
* the commit
* the author
* the date
* the commit message
* the patch information

However, `git show ` can be combined with most of the other **flags** we've looked at:

* `--stat` - to show the how many files were changed and the number of lines that were added/removed
* `-p` or -`-patch` - this the default, but if `--stat` is used, the patch won't display, so pass `-p` to add it again
* `-w` - to ignore changes to whitespace.




##### Git add

-----------

The `git add` command is used to move files from the Working Directory to the Staging Index.

```bash
$ git add <file1> <file2> … <fileN>
```

This command:

- takes a space-separated list of file names
- alternatively, the period `.` can be used in place of a list of files to tell Git to add the current directory (and all nested files)




##### Git unstage/ remove files from stage area

------

```bash
git rm  -r --cache  <filename>
```

* If you added files by mistake you can remove them from stage area by using `git rm` 







##### Git Commit

----------------------

The `git commit` command takes files from the Staging Index and saves them in the repository.

```bash
$ git commit
```

This command:

- will open the code editor that is specified in your configuration
  - (check out the Git configuration step from the first lesson to configure your editor)

Inside the code editor:

- a commit message must be supplied
- lines that start with a `#` are comments and will not be recorded
- save the file after adding a commit message
- close the editor to make the commit

Then, use `git log` to review the commit you just made!

```bash
$ git commit -m "Initial commit"
```

### Further Research

- [Associating text editors with Git](https://help.github.com/articles/associating-text-editors-with-git/) from GitHub Help Docs
- [Getting Started - First-Time Git Setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup) from Git book









## Good Commit Messages

Let's take a quick stroll down Stickler Lane and ask the question:

> How do I write a *good* commit message? And why should I care?

These are *fantastic* questions! I can't stress enough how important it is to spend some time writing a *good* commit message.

Now, what makes a "good" commit message? That's a great question and has been [written about](https://chris.beams.io/posts/git-commit/) [a number](https://medium.com/@preslavrachev/what-s-with-the-50-72-rule-8a906f61f09c#.jwprsco0n) [of times](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html). Here are some important things to think about when crafting a good commit message:

**Do**

- do keep the message short (less than 60-ish characters)
- do explain *what* the commit does (not *how* or *why*!)

**Do not**

- do not explain *why* the changes are made (more on this below)
- do not explain *how* the changes are made (that's what `git log -p` is for!)
- do not use the word "and"
  - if you have to use "and", your commit message is probably doing too many changes - break the changes into separate commits
  - e.g. "make the background color pink *and* increase the size of the sidebar"

The best way that I've found to come up with a commit message is to finish this phrase, "This commit will...". However, you finish that phrase, use *that* as your commit message.



## `git diff`

The `git diff` command can be used to see changes that have been made but haven't been committed, yet.

```bash
$ git diff
```

This command displays:

- the files that have been modified
- the location of the lines that have been added/removed
- the actual changes that have been made

## Git Ignore

 the `.gitignore` file is used to tell Git about the files that Git should not track. This file should be placed in the same directory that the `.git` directory is in.

If you want to keep a file in your project's directory structure but make sure it isn't accidentally committed to the project, you can use the specially named file, `.gitignore` (note the dot at the front, it's important!). Add this file to your project in the same directory that the hidden `.git` directory is located. All you have to do is list the *names* of files that you want Git to ignore (not track) and it will ignore them.



## Globbing Crash Course

[globbing](https://en.wikipedia.org/wiki/Glob_(programming)) lets you use special characters to match patterns/characters. In the `.gitignore` file, you can use the following:

- blank lines can be used for spacing
- `#` - marks line as a comment
- `*` - matches 0 or more characters
- `?` - matches 1 character
- `[abc]` - matches a, b, *or* c
- `**` -  matches nested directories - `a/**/z` matches
  - a/z
  - a/b/z
  - a/b/c/z











## Git Tag Command

 the `git tag` command is used to add a marker on a specific commit. The tag does not move around as new commits are added.

```bash
$ git tag -a beta
```

```bash
$ git tag -a v1.0
```

This command will:

- add a tag to the most recent commit
- add a tag to a specific commit *if a SHA is passed*



CAREFUL: In the command above (`git tag -a v1.0`) the `-a` flag is used. This flag tells Git to create an *annotated*flag. If you don't provide the flag (i.e. `git tag v1.0`) then it'll create what's called a *lightweight* tag.

Annotated tags are recommended because they include a lot of extra information such as:

- the person who made the tag
- the date the tag was made
- a message for the tag

Because of this, you should always use annotated tags.

## Verify Tag

After saving and quitting the editor, nothing is displayed on the command line. So how do we know that a tag was actually added to the project? If you type out just `git tag`, it will display all tags that are in the repository.

So we've verified that it's in the repository, but let's actually see *where* it is inside the repository. To do that, we'll go back to our good old friend, `git log`!



## Git Log's --decorate Flag

As you've learned, `git log` is a pretty powerful tool for letting us check out a repository's commits. We've already looked at a couple of its flags, but it's time to add a new one to our toolbelt. The `--decorate` flag will show us some details that are hidden from the default view.

Try running `git log --decorate` now!



## 💡 `--decorate` Flag Changes in Git 2.13 💡

In the 2.13 update to Git, the `log` command has changed to automatically enable the `--decorate` flag. This means that you do not need to include the `--decorate` flag in your command, since it is automatically included, anyway! So the following commands result in the exact same output:

```bash
$ git log --decorate
$ git log
```



## Deleting A Tag

What if you accidentally misspelled something in the tag's message, or mistyped the actual tag name (`v0.1` instead of `v1.0`). How could you fix this? The easiest way is just to delete the tag and make a new one.

A Git tag can be deleted with the `-d` flag (for *delete*!) and the name of the tag:

```bash
$ git tag -d v1.0
```



## Adding A Tag To A Past Commit

Running `git tag -a v1.0` will tag the most recent commit. But what if you wanted to tag a commit that occurred farther back in the repo's history?

All you have to do is provide the SHA of the commit you want to tag!

```bash
$ git tag -a v1.0 a87984
```







## The `git branch` command

 the `git branch` command is used to manage branches in Git:

```bash
# to list all branches
$ git branch

# to create a new "footer-fix" branch
$ git branch footer-fix

# to delete the "footer-fix" branch
$ git branch -d footer-fix

# It creates a new branch called footer-fix and has it pointing at the commit with the SHA 42a69f
$ git branch footer-fix 42a69f
```



This command is used to:

- list out local branches
- create new branches
- remove branches



## The `git checkout` Command

Remember that when a commit is made that it will be added to the current branch. So even though we created the new `sidebar`, no new commits will be added to it since we haven't *switched to it*, yet. If we made a commit right now, that commit would be added to the `master` branch, *not* the `sidebar` branch. We've already seen this in the demo, but to switch between branches, we need to use Git's `checkout` command.



```bash
$ git checkout sidebar

```





It's important to understand how this command works. Running this command will:

- remove all files and directories from the Working Directory that Git is tracking
  - (files that Git tracks are stored in the repository, so nothing is lost)
- go into the repository and pull out all of the files and directories of the commit that the branch points to

So this will remove all of the files that are referenced by commits in the master branch. It will replace them with the files that are referenced by the commits in the sidebar branch. This is very important to understand, so go back and read these last two sentences.

The funny thing, though, is that both `sidebar` and `master` are pointing *at the same commit*, so it will look like nothing changes when you switch between them. But the command prompt will show "sidebar", now:







## 💡 Switch and Create Branch In One Command💡

The way we currently work with branches is to create a branch with the `git branch` command and then switch to that newly created branch with the `git checkout` command.

But did you know that the `git checkout` command can actually create a new branch, too? If you provide the `-b`flag, you can create a branch *and* switch to it all in one command.

```bash
$ git checkout -b richards-branch-for-awesome-changes

#Let's use this new feature of the git checkout command to create our new footer branch and have this footer branch start at the same location as the master branch:
$ git checkout -b footer master

```

It's a pretty useful command, and I use it often.



## Branches In The Log

The branch information in the command prompt is helpful, but the clearest way to see it is by looking at the output of `git log`. But just like we had to use the `--decorate` flag to display Git tags, we need it to display branches.

```bash
$ git log --oneline --decorate
```



## Delete A Branch

A branch is used to do development or make a fix to the project that won't affect the project (since the changes are made on a branch). Once you make the change on the branch, you can combine that branch into the `master` branch (this "combining of branches" is called "merging" and we'll look at shortly).

Now after a branch's changes have been merged, you probably won't need the branch anymore. If you want to delete the branch, you'd use the `-d` flag. The command below includes the `-d` flag which tells Git to *delete* the provided branch (in this case, the "sidebar" branch).

```
$ git branch -d sidebar

```

One thing to note is that you can't delete a branch that you're currently on. So to delete the `sidebar` branch, you'd have to switch to either the `master` branch or create and switch to a new branch.

Deleting something can be quite nerve-wracking. Don't worry, though. Git won't let you delete a branch if it has commits on it that aren't on any other branch (meaning the commits are unique to the branch that's about to be deleted). If you created the `sidebar` branch, added commits to it, and then tried to delete it with the `git branch -d sidebar`, Git wouldn't let you delete the branch because you can't delete a branch that you're currently on. If you switched to the `master` branch and tried to delete the `sidebar` branch, Git *also* wouldn't let you do that because those new commits on the `sidebar`branch would be lost! To force deletion, you need to use a capital D flag - `git branch -D sidebar`.





## See All Branches At Once

We've made it to the end of all the changes we needed to make! Awesome job!

Now we have multiple sets of changes on three different branches. We can't see other branches unless in the `git log`output unless we switch to a branch. Wouldn't it be nice if we could see *all* branches at once in the `git log` output.

As you've hopefully learned by now, the `git log` command is pretty powerful and *can* show us this information. We'll use the new `--graph` and `--all` flags:

```bash
$ git log --oneline --decorate --graph --all
```

The `--graph` flag adds the bullets and lines to the leftmost part of the output. This shows the actual *branching* that's happening. The `--all` flag is what displays *all* of the branches in the repository.



## The Merge Command

The `git merge` command is used to combine Git branches:

```bash
$ git merge <name-of-branch-to-merge-in>

```

- There are two types of merges:
  - Fast-forward merge – the branch being merged in must be *ahead* of the checked out branch. The checked out branch's pointer will just be moved forward to point to the same commit as the other branch.
  - the regular type of merge
    - two divergent branches are combined
    - a merge commit is created



### Fast-forward Merge

In our project, I've checked out the `master` branch and I want *it* to have the changes that are on the `footer` branch. If I wanted to verbalize this, I could say this is - "I want to merge in the `footer` branch". That "merge in" is important; when a merge is performed, the *other* branch's changes are brought into the branch that's currently checked out.

Let me stress that again - When we merge, we're merging some other branch into the current (checked-out) branch. We're not merging two branches into a new branch. We're not merging the current branch into the other branch.

Now, since `footer` is directly ahead of `master`, this merge is one of the easiest merges to do. Merging `footer` into `master`will cause a **Fast-forward merge**. A Fast-forward merge will just move the currently checked out branch *forward* until it points to the same commit that the other branch (in this case, `footer`) is pointing to.

To merge in the `footer` branch, run:

```bash
$ git merge footer
```



## undo change 

 if you make a merge on the wrong branch, use this command to undo the merge:

```bash
git reset --hard HEAD^
```





## Merge Conflict 

A merge conflict happens when the same line or lines have been changed on different branches that are being merged. Git will pause mid-merge telling you that there is a conflict and will tell you in what file or files the conflict occurred. To resolve the conflict in a file:

- locate and remove all lines with merge conflict indicators
- determine what to keep
- save the file(s)
- stage the file(s)
- make a commit

Be careful that a file might have merge conflicts in multiple parts of the file, so make sure you check the entire file for merge conflict indicators - a quick search for `<<<` should help you locate all of them.





## Merge Conflict Indicators Explanation

The editor has the following merge conflict indicators:

- `<<<<<<< HEAD` everything below this line (until the next indicator) shows you what's on the current branch
- `||||||| merged common ancestors` everything below this line (until the next indicator) shows you what the original lines were
- `=======` is the end of the original lines, everything that follows (until the next indicator) is what's on the branch that's being merged in
- `>>>>>>> heading-update` is the ending indicator of what's on the branch that's being merged in (in this case, the `heading-update` branch)

## Resolving A Merge Conflict

Git is using the merge conflict indicators to show you what lines caused the merge conflict on the two different branches as well as what the original line used to have. So to resolve a merge conflict, you need to:

1. choose which line(s) to keep
2. remove all lines with indicators



## Changing The Last Commit

You've already made plenty of commits with the `git commit` command. Now with the `--amend` flag, you can alter the *most-recent* commit.

```bash
$ git commit --amend

```

If your Working Directory is clean (meaning there aren't any uncommitted changes in the repository), then running `git commit --amend` will let you provide a new commit message. Your code editor will open up and display the original commit message. Just fix a misspelling or completely reword it! Then save it and close the editor to lock in the new commit message.

## Add Forgotten Files To Commit

Alternatively, `git commit --amend` will let you include files (or changes to files) you might've forgotten to include. Let's say you've updated the color of all navigation links across your entire website. You committed that change and thought you were done. But then you discovered that a special nav link buried deep on a page doesn't have the new color. You *could*just make a new commit that updates the color for that one link, but that would have two back-to-back commits that do practically the exact same thing (change link colors).

Instead, you can amend the last commit (the one that updated the color of all of the other links) to include this forgotten one. To do get the forgotten link included, just:

- edit the file(s)
- save the file(s)
- stage the file(s)
- and run `git commit --amend`

So you'd make changes to the necessary CSS and/or HTML files to get the forgotten link styled correctly, then you'd save all of the files that were modified, then you'd use `git add` to stage all of the modified files (just as if you were going to make a new commit!), but then you'd run `git commit --amend` to update the most-recent commit instead of creating a new one.



## Revert 

 the `git revert` command is used to reverse a previously made commit:

```bash
$ git revert <SHA-of-commit-to-revert>

```

This command:

- will undo the changes that were made by the provided commit
- creates a new commit to record the change



## Reset 

 the `git reset` command is used erase commits:

```bash
$ git reset <reference-to-commit>

```

It can be used to:

- move the HEAD and current branch pointer to the referenced commit
- erase commits with the `--hard` flag
- moves committed changes to the staging index with the `--soft` flag
- unstages committed changes `--mixed` flag

Typically, ancestry references are used to indicate previous commits. The ancestry references are:

- `^` – indicates the parent commit
- `~` – indicates the first parent commit



## Git Reset's Flags

The way that Git determines if it erases, stages previously committed changes, or unstages previously committed changes is by the flag that's used. The flags are:

- `--mixed`
- `--soft`
- `--hard`

Reference 

https://www.youtube.com/watch?time_continue=104&v=UN7ki2G2yKc

## Reset vs Revert

At first glance, *resetting* might seem coincidentally close to *reverting*, but they are actually quite different. Reverting creates a new commit that reverts or undos a previous commit. Resetting, on the other hand, *erases* commits!

> ## ⚠️ Resetting Is Dangerous ⚠️
>
> You've got to be careful with Git's resetting capabilities. This is one of the few commands that lets you erase commits from the repository. If a commit is no longer in the repository, then its content is gone.
>
> To alleviate the stress a bit, Git *does* keep track of everything for about 30 days before it completely erases anything. To access this content, you'll need to use the `git reflog` command. Check out these links for more info:
>
> - [git-reflog](https://git-scm.com/docs/git-reflog)
> - [Rewriting History](https://www.atlassian.com/git/tutorials/rewriting-history)
> - [reflog, your safety net](http://gitready.com/intermediate/2009/02/09/reflog-your-safety-net.html)





## Relative Commit References

You already know that you can reference commits by their SHA, by tags, branches, and the special `HEAD` pointer. Sometimes that's not enough, though. There will be times when you'll want to reference a commit relative to another commit. For example, there will be times where you'll want to tell Git about the commit that's one before the current commit...or two before the current commit. There are special characters called "Ancestry References" that we can use to tell Git about these relative references. Those characters are:

- `^` – indicates the parent commit
- `~` – indicates the *first* parent commit

Here's how we can refer to previous commits:

- the parent commit – the following indicate the parent commit of the current commit
  - HEAD^
  - HEAD~
  - HEAD~1
- the grandparent commit – the following indicate the grandparent commit of the current commit
  - HEAD^^
  - HEAD~2
- the great-grandparent commit – the following indicate the great-grandparent commit of the current commit
  - HEAD^^^
  - HEAD~3

The main difference between the `^` and the `~` is when a commit is created *from a merge*. A merge commit has *two*parents. With a merge commit, the `^` reference is used to indicate the *first* parent of the commit while `^2` indicates the *second* parent. The first parent is the branch you were on when you ran `git merge` while the second parent is the branch that was merged in.



It's easier if we look at an example. This what my `git log` currently shows:

```bash
* 9ec05ca (HEAD -> master) Revert "Set page heading to "Quests & Crusades""
* db7e87a Set page heading to "Quests & Crusades"
*   796ddb0 Merge branch 'heading-update'
|\  
| * 4c9749e (heading-update) Set page heading to "Crusade"
* | 0c5975a Set page heading to "Quest"
|/  
*   1a56a81 Merge branch 'sidebar'
|\  
| * f69811c (sidebar) Update sidebar with favorite movie
| * e6c65a6 Add new sidebar content
* | e014d91 (footer) Add links to social media
* | 209752a Improve site heading for SEO
* | 3772ab1 Set background color for page
|/  
* 5bfe5e7 Add starting HTML structure
* 6fa5f34 Add .gitignore file
* a879849 Add header to blog
* 94de470 Initial commit

```

Let's look at how we'd refer to some of the previous commits. Since `HEAD` points to the `9ec05ca` commt:

- `HEAD^` is the `db7e87a` commit
- `HEAD~1` is also the `db7e87a` commit
- `HEAD^^` is the `796ddb0` commit
- `HEAD~2` is also the `796ddb0` commit
- `HEAD^^^` is the `0c5975a` commit
- `HEAD~3` is also the `0c5975a` commit
- `HEAD^^^2` is the `4c9749e` commit (this is the grandparent's (`HEAD^^`) *second parent* (`^2`))



## Git remote

A remote repository is a repository that's just like the one you're using but it's just stored at a different location. To manage a remote repository, use the `git remote` command:

```bash
$ git remote

```

- It's possible to have links to multiple different remote repositories.
- A shortname is the name that's used to refer to a remote repository's location. Typically the location is a URL, but it could be a file path on the same computer.
- `git remote add` is used to add a connection to a new remote repository.
- `git remote -v` is used to see the details about a connection to a remote.



### Git Push

The `git push` command is used to send commits from a local repository to a remote repository.

```bash
$ git push origin master

```

The `git push` command takes:

- the shortname of the remote repository you want to send commits to
- the name of the branch that has the commits you want to send





## Git Pull

If there are changes in a remote repository that you'd like to include in your local repository, then you want to *pull* in those changes. To do that with Git, you'd use the `git pull` command. You tell Git the shortname of the remote you want to get the changes from and then the branch that has the changes you want:

```bash
$ git pull origin master

```

When `git pull` is run, the following things happen:

- the commit(s) on the remote branch are copied to the local repository
- the local tracking branch (`origin/master`) is moved to point to the most recent commit
- the local tracking branch (`origin/master`) is merged into the local branch (`master`)



## Git Fetch

You can think of the `git pull` command as doing two things:

1. fetching remote changes (which adds the commits to the local repository and moves the tracking branch to point to them)
2. merging the local branch with the tracking branch

The `git fetch` command is just the first step. It just retrieves the commits and moves the tracking branch. It *does not*merge the local branch with the tracking branch. The same information provided to `git pull` is passed to `git fetch`:

- the shorname of the remote repository
- the branch with commits to retrieve

```bash
$ git fetch origin master
```



[Explanation Video](https://www.youtube.com/watch?time_continue=62&v=jwyQUfE1Eqw)





## Fork

Forking is an action that's done on a hosting service, like GitHub. Forking a repository creates an identical copy of the original repository and moves this copy to your account. You have total control over this forked repository. Modifying your forked repository does not alter the original repository in any way.





## Pull request

A pull request is a *request* for the source repository to pull in your commits and merge them with their project. To create a pull request, a couple of things need to happen:

- you must *fork* the source repository
- clone your fork down to your machine
- make some commits (ideally on a topic branch!)
- push the commits back to *your fork*
- create a new pull request and choose the branch that has your new commits








## stay in sync with source project

When working with a project that you've forked. The original project's maintainer will continue adding changes to their project. You'll want to keep your fork of their project in sync with theirs so that you can include any changes they make.

To get commits from a source repository into your forked repository on GitHub you need to:

- get the cloneable URL of the source repository

- create a new remote with the


  ```bash
  git remote add
  ```

   

  command

  - use the shortname `upstream` to point to the source repository
  - provide the URL of the source repository

- fetch the new `upstream` remote

- merge the `upstream`'s branch into a local branch

- push the newly updated local branch to your `origin` repo



## Git rebase

The `git rebase` command is used to do a great many things.

```bash
# interactive rebase
$ git rebase -i <base>

# interactively rebase the commits to the one that's 3 before the one we're on
$ git rebase -i HEAD~3

```

Inside the interactive list of commits, all commits start out as `pick`, but you can swap that out with one of the other commands (`reword`, `edit`, `squash`, `fixup`, `exec`, and `drop`).

I recommend that you create a `backup` branch *before* rebasing, so that it's easy to return to your previous state. If you're happy with the rebase, then you can just delete the `backup` branch!



## Rebase Commands

Let's take another look at the different commands that you can do with `git rebase`:

- use `p` or `pick` – to keep the commit as is

- use `r` or `reword` – to keep the commit's content but alter the commit message

- use


  ```
  e
  ```

   

  or

   

  ```
  edit
  ```

   

  – to keep the commit's content but stop before committing so that you can:

  - add new content or files
  - remove content or files
  - alter the content that was going to be committed

- use `s` or `squash` – to combine this commit's changes into the previous commit (the commit above it in the list)

- use `f` or `fixup` – to combine this commit's change into the previous one but drop the commit message

- use `x` or `exec` – to run a shell command

- use `d` or `drop` – to delete the commit

## When to rebase

As you've seen, the `git rebase` command is incredibly powerful. It can help you edit commit messages, reorder commits, combine commits, etc. So it truly is a powerhouse of a tool. Now the question becomes "*When* should you rebase?".

Whenever you rebase commits, Git will create a new SHA *for each commit*! This has drastic implications. To Git, the SHA is the identifier for a commit, so a different identifier means it's a different commit, *regardless if the content has changed at all.*

So you should not rebase if you have already pushed the commits you want to rebase. If you're collaborating with other developers, then they might already be working with the commits you've pushed. If you then use `git rebase` to change things around and then force push the commits, then the other developers will now be out of sync with the remote repository. They will have to do some complicated surgery to their Git repository to get their repo back in a working state...and it might not even be possible for them to do that; they might just have to scrap all of their work and start over with your newly-rebased, force-pushed commits.





### Force Pushing

In the video, I had to force push the branch. I had to do this because GitHub was trying to prevent me from accidentally deleting commits. Because I used the `git rebase` command, I effectively *erased* the three separate commits that recorded my addition of Florida, Paris, and Scotland. I used `git rebase` to combine or *squash* all of these commits into one, single commit.

Using `git rebase` creates a new commit with a new SHA. When I tried using `git push` to send this commit up to GitHub, GitHub knew that accepting the push would erase the three separate commits, so it rejected it. So I had to *force push* the commits through using `git push -f`.

> ### ⚠️ Force Pushing ⚠️
>
> In this instance, force pushing my commits was necessary. But if you try to push commits and GitHub rejects them, it's trying to help you, so make sure to review what commits you're pushing *and* the commits that are on GitHub to verify you're not about to overwrite content on your remote repository accidentally!