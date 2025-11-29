# How to Git

## Reference
<https://gitimmersion.com/lab_01.html>

<https://learngitbranching.js.org/>

<https://git-scm.com/book/en/v2>

Unlike other version control system, which are delta-based version control, git thinks about its data more like a stream of snapshots.

Git has three main states that your file can reside in.
* `modified` - you have changed the file but have not committed it to your database yet
* `staged` - you have marked a modified file in its current version to go into your next commit snapshot
* `committed` -data is safely stored in your local database

## Installing Git
```bash
sudo apt install git-all # Debian-based distro
brew install git # MacBook
```
For other platform:[Installation Guide](https://git-scm.com/install/windows) 

### First-Time Git Setup
There are few things to consider after installation of Git. I would suggest you to go through Page 21, 22 and 23 of [Pro Git](https://git-scm.com/book/en/v2) book.

```bash
# Checking your settings
git config --list
```
### Getting Help
```bash
git help <verb>
git <verb> --help
man git-<verb>

#Example
git help config
```
## Git Basics
### Initializing a repo
```bash
git init

git --version # Output git version 2.46.0
```
```bash
# Example of initializing git

# git init
macbook@MacMan Git-to-know % git init 
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint:   git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint:   git branch -m <name>
Initialized empty Git repository in /Users/macbook/Library/CloudStorage/OneDrive-Personal/Repos/Git-to-know/.git/

# list the files created
macbook@MacMan Git-to-know % ls -a
.               ..              .git            how-to-git.md

# changed the brach name to main
macbook@MacMan Git-to-know % git branch -m main

# checking the current git status
macbook@MacMan Git-to-know % git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        how-to-git.md

nothing added to commit but untracked files present (use "git add" to track)
macbook@MacMan Git-to-know % 
```
On the above example I changed the branch name to `main` because GitHub changed the default branch name from `master` to `main`. However, Git itself still uses `master` as the default.

```bash
# Tracking new file - means staged
macbook@MacMan Git-to-know % git add how-to-git.md

# Check status - it is staged i.e tracked
macbook@MacMan Git-to-know % git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   how-to-git.md
```

### Cloning a repo
```bash
git clone https://github.com/satishkarki/satishkarki.github.io.git # uses https protocol

git:// or user@server:path/to/repo.git # uses SSH protocol, more on this later
```
### `git status`
```bash
# Long status
macbook@MacMan Git-to-know % git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   how-to-git.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   how-to-git.md

# Short status
macbook@MacMan Git-to-know % git status -s
AM how-to-git.md
```
### Ignoring Files
Setting up a `.gitignore` file for your new repository is a good idea so you don't accidentally commit files that you don't want in your repo.  

GitHub maintains a fairly comprehensive list of good .gitignore file examples for dozens of projects and languages at https://github.com/github/gitignore if you want a starting point for your project.

```bash
# Example of .gitignore file

# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```
### `git diff`
The `git diff` shows you the exact lines added and removed- the patch, as it were.

```bash
git diff
git diff --staged
git difftool # Git Diff is an External tool
git difftool --tool-help # To check what is available on your system
```
### `git commit`
```bash
git commit # this will open an editor like vim, :q to quit (pro tip)

git commit -m "My First Commit" # using -m flag

git commit -a -m "Skipped Staging Area" # Skip Staging Area with -a flag

```
### `git rm`





