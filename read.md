
#### Required Commands
Heads up! We'll be using the following terminal commands in this lesson:

>* <code style="color:red"> ls </code> - used to list files and directories ==notice== its `L` letter not `i`
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
####Create  Directories

>* create a directory called `testCommand`
>* inside that, create another directory called `new-git-project`
#####or
just run this command on the terminal - `mkdir -p udacity-git-course/new-git-project && cd $_`

#### Git Init
Use the `git init` command to create a new, empty repository in the current directory.

Running this command creates a hidden `.git` directory. This `.git` directory is the brain/storage center for the repository. It holds all of the configuration files and directories and is where all of the commits are stored.



####todo:  git clone


my new repo is **mac-git-and-commandline**
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


























<br><br><br><br><br><br><br><br><br><br><br><br>
#####Helpful Links
[settup repository](https://www.atlassian.com/git/tutorials/setting-up-a-repository)
[get init doc](https://git-scm.com/docs/git-init)
[get init tutorial](https://www.atlassian.com/git/tutorials/setting-up-a-repository)



<!-- 
| Title                   | Author            | Price  |
| ----------------------- | ----------------- | -----: |
| Meditations             | Marcus Aurelius   | $10.00 |
| Rational Optimist       | Matt Ridley       | $12.00 |
| Poor Charlie's Almanack | Charles T. Munger | $16.50 |

==anything== 
 ~~this paragraph deleted~~ 

 -->