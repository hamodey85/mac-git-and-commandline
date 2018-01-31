
#### Required Commands
Heads up! We'll be using the following terminal commands in this lesson:

>* `ls` -or `-l` used to list files and directories **notice** its `L` letter not `i`
>* <code style="color:red"> mkdir </code>  - used to create a new directory
>* <code style="color:red"> cd </code>  - used to change directories
>* <code style="color:red"> rm </code>  - used to remove files and directories
>* <code style="color:red"> pwd </code> - used to print working directory
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
<br><br><br><br><br><br><br><br>
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

<br><br><br><br><br><br><br>

## Create A Repo From Scratch

----------
Before you can make commits or do anything else with a git repository, the repository needs to actually exist. To create a new repository with Git, we'll use the <code style="color:red"> git init </code> command.
The <code style="color:red"> init </code> subcommand is short for **"initialize"**
<br><br>
#### Required Commands
Heads up! We'll be using the following terminal commands in this lesson:

>* <code style="color:red"> ls </code> - used to list files and directories ==notice== its `L` letter not `i`
>* <code style="color:red"> mkdir </code>  - used to create a new directory
>* <code style="color:red"> cd </code>  - used to change directories
>* <code style="color:red"> rm </code>  - used to remove files and directories
>* <code style="color:red"> pwd </code> - used to print working directory

<br><br><br><br>
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

<br><br><br><br>
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

```
$ git log -p fdf5493
```

#### git show
The other command that shows a specific commit is ` git show `:

```
$ git show
```
```
$ git show fdf5493
```
The `git show` command will show only one commit. So don't get alarmed when you can't find any other commits - it only shows one. The output of the `git show` command is exactly the same as the `git log -p` command. So by default, `git show` displays:
* the commit
* the author
* the date
* the commit message
* the patch information

However, `git show `can be combined with most of the other **flags** we've looked at:

* `--stat` - to show the how many files were changed and the number of lines that were added/removed
* `-p` or -`-patch` - this the default, but if `--stat` is used, the patch won't display, so pass `-p` to add it again
* `-w` - to ignore changes to whitespace



<br><br><br><br><br><br><br><br><br><br><br><br>
##### Helpful Links
[git basic](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)
[git init doc](https://git-scm.com/docs/git-init)
[git init tutorial](https://www.atlassian.com/git/tutorials/setting-up-a-repository)



<!-- 
| Title                   | Author            |  Price |
| ----------------------- | ----------------- | -----: |
| Meditations             | Marcus Aurelius   | $10.00 |
| Rational Optimist       | Matt Ridley       | $12.00 |
| Poor Charlie's Almanack | Charles T. Munger | $16.50 |

==anything== 
 ~~this paragraph deleted~~ 

 -->