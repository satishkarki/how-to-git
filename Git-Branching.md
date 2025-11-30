A branch in Git is simply a lightweight movable pointer to one of the commits. The default branch name in Git is `master`/`main`. As you start making commit, you're given a `master` branch that points to the last commit you made. Every time you commit, the `master` branch pointer moves forward automatically.

```bash
git branch testing
```
![git-branch](post/git-branching/git-branch.png)

Example
```bash
$git branch testing

$git log --oneline --decorate --graph --all
* 5df03d0 (HEAD -> main, origin/main, testing)  First commit of Git Branching
* 7034b0d Git Basic topic complete
* 98e3b1e  Beginning of Git Aliases topic
...
```
On the example above, the special pointer `HEAD` is pointing to `main`

## Switching Branches
```bash
$git checkout testing # This moves HEAD to point to testing branch

$git checkout -b <new-branch> # Create and checkout in one command

$git switch -c <new-branch> # Starting Git v2.23
```

Output
```bash
$git checkout testing
Switched to branch 'testing'

$git log --oneline --decorate --graph --all
* 5df03d0 (HEAD -> testing, origin/main, main)  First commit of Git Branching
* 7034b0d Git Basic topic complete
* 98e3b1e  Beginning of Git Aliases topic
```
### Modifying the branch
```bash
$echo "this is a test to check the branch feature" > testing-branch.md
$git add testing-branch.md
$git commit -a -m "First commit of testing branch"
$git log --oneline --decorate --graph --all 
```
output
```bash
$git log --oneline --decorate --graph --all       
* 616c359 (HEAD -> testing) First commit of testing branch
* 5df03d0 (origin/main, main)  First commit of Git Branching
* 7034b0d Git Basic topic complete
* 98e3b1e  Beginning of Git Aliases topic
* ad7d380 this is the commit after ammend
```
To check log
```bash
$git log # checks log of main branch
$git log testing # checks log of testing branch only
$git log--all #checks log of all branch
```
Output
```bash
$git log --pretty=oneline
5df03 (HEAD -> main, origin/main)  First commit of Git Branching
7034b Git Basic topic complete
98e3b  Beginning of Git Aliases topic
...

$git log testing --pretty=oneline
616c3 (testing) First commit of testing branch
5df03 (HEAD -> main, origin/main)  First commit of Git Branching
7034b Git Basic topic complete
98e3b  Beginning of Git Aliases topic
...
```
### Divergent History
You made some changes in `testing` branch and came back to `main` branch, made some changes here- your project history has diverged.
![Git-Divergent](post/git-branching/git-divergent.png)

Example
```bash
$git log --oneline --decorate --graph --all
* 3fbd727 (HEAD -> main) commit to create divergent
| * 616c359 (testing) First commit of testing branch
|/  
* 5df03d0 (origin/main)  First commit of Git Branching
* 7034b0d Git Basic topic complete
* 98e3b1e  Beginning of Git Aliases topic
```
## Basic Branching and Merging




