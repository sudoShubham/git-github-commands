
# Git:
## Distributed version control system(Git can track any files in any folder i.e, it stores all history of changes that user do to the file)
#####  **Git doeesn't depends on internet connection.**
---
# Github:
## Repository hosting service for Git.
---
---
#### Basic linux commands:
```
git init                            :create new empty git repository
mkdir                               :make directory
pwd                                 :shows current directory
clear                               :clear terminal
ls                                  :list files
ls-l                                :shows files in table format 
ls-la                               :shows hidden files too
cd directoryName                    :Change directory
mkdir folderName                    :make  new directory
cd ..                               :Go to back directory
cd                                  :Go to parent/root directory
.                                   :shows current directory
cd .                                :Stays in same directory
start . (or) explorer .             :Opens file explorer in current directory
cd Desktop/my-project               :Go to nested directory
cat filename.txt                    :Reads content of the file.
nano                                :Text editor
Tab key                             :auto-complete
```
---
### Help from terminal:
```
commandName --help(Windows)					:to get information about any git command
man commandName(Mac)						:to get information about any git command
```
---
### Git fileSystem commands:
```
echo								:Outputs the all text after the command
echo -n                             :Output without ending on new line.
echo "Hello shubham" > file.txt		:rewrite the text in file.txt
echo "Welcome" >> file.txt			:Appends text to new line in file.txt
rm filename.txt                     :Removes file 
rm -rf folderName                   :Removes folder
```
---

### Git object types:
    1.Blob: stores Single file of any extension              cmd to create new object: git hash-object
    2.Tree: information about Folder/directory
    3.Commit: use to store different versios of project
    4.Annoted tag

![Git Lifecycle](https://miro.medium.com/max/438/1*cBkeiMOwIeF7OWl_rjpcHg.jpeg)
---
```
git cat-file -p hash
o/p: content of the object
```


```
git cat-file -p b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e

o/p: Hello, Git
```
```
cmd: git cat-file -t hash
o/p: type of the object

eg: 
$ git cat-file -t b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e

3.cmd: git cat-file -s hash
o/p: size of the object in bytes
```
eg:
```
$ git cat-file -s b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e
o/p: 11
```

```
cmd: echo "This is new file." > new-file.txt
o/p: create new file with given text and given name(alternative:nano,touch)
```
```
cmd: git hash-object ../new-file.txt -w
o/p: creates object of new-file.txt and stores it
```
---               
cmd to find all objects in a directory : 
```
find .git/objects -type f             (f stands for file type)
```
---
---
### **FILE DISTRIBUTION**
| Working directory | Staging area(index) |  Git repository |
|--- |--- |--- |

```
cmd: git ls-files -s 
o/p: List filesin the Staging area 
```
```
cmd: git read-tree <hash of tree object>
o/p: create files contained in a tree to Staging area.
```
```
cmd: git checkout-index -a
o/p: create files in the working directory (copy files from Staging area to working directory)
```
---
---
#### **GIT SETUP**
```
cmd: git config --global user.name "sudoShubham"
o/p: setup git user name
```     
```
cmd: git config --global user.email shubhamp2017@gmail.com
o/p: setup git email
```
```
cmd: git config --list
o/p: shows all configuration options
```
---
---
#### **GIT COMMIT**
```
cmd: git status
o/p: shows status of directory
```
```
cmd: git commit -m "msg regarding commit"
o/p: commits the changes
```



```
cmd: git ls-files -s
o/p: shows files from staging area
```

---

## **BASIC GIT COMMANDS**
---
```
cmd: git status
o/p: current state of git repository

cmd: git add
o/p: add files to staging area

cmd: git commit
o/p: write changes to git repository

cmd: git log 
o/p: history of changes(commits)

cmd: git checkout <branchName>  (or) git checkout <Commit SHA1> 
o/p: checkout commit or branch or to jump on any specific version
```

#### GIT FILE LIFECYCLES
![Git Lifecycle](https://git-scm.com/book/en/v2/images/lifecycle.png)


---

```
cmd: git add .
o/p: add all modified/new files to stage state.

cmd: git add <file name>
o/p: add specified file to stage state.

cmd: git restore --staged <file name>  (or) git rm --cached <file name>
o/p: to unstage from staged state
```
```
cmd: cat .git/HEAD
o/p: shows where HEAD is pointing now.
```
#### **BRANCH**
```
cmd: git branch
o/p: list all local branches

cmd: git branch <name>
o/p: create new branch

cmd: git checkout <branchName>
o/p: checkout specific branch

cmd: git branch -d <branchName>
o/p: delete specific branch

cmd: git branch -m <oldName> <newName>
o/p: rename specific branch

cmd: git checkout -b <branchName>
o/p: creating a branch with checkout

cmd: ls .git/refs/heads
o/p: shows total branches(heads)

cmd: cat .git/HEAD
o/p: shows current head 

cmd: git diff 
o/p: shows difference in old and modified file.

cmd: git unpack-objects < SAMPLE.pack>
o/p: Git will generate all objects inside .git/objects directory of your repository.
NOTE: Move .pack file to .git folder before executing the cmd.

cmd: git commit -m "message" -a
o/p: files will  

```

#### **MERGE**


| fast-forward merge | 3-way merge | 
|--- |--- |

> **fast-forward merge** 
fast-forward merge is possible only when there are no further commits in the recieving branch after the commit where feature-branch was created.
after merging feature-branch with master branch, we can delete the feature branch.
```cmd: git merge <branch name>```
```o/p: merge <branch name> with current head (or) master //before merging we need to checkout recieving branch(main branch)```

---
> 3 way merg 
```during 3 ways merging, MERGE_HEAD points to feature branch head which is going to merge with master.``` 
---
---
### GitHub:
```
cmd: git push
o/p: push to remote

cmd: git pull
o/p: merge changesm from remote repository

cmd: git fetch
o/p: fetch updates

cmd: git remote
o/p: lists all remote repositories for your local repository.

cmd: git remote -v
o/p: origin  https://github.com/sudoShubham/first-git-repo.git (fetch)
     origin  https://github.com/sudoShubham/first-git-repo.git (push)

cmd: git branch -a
o/p: shows all local + remote branches

cmd: git branch -r
o/p: shows all remote branches

cmd: git branch -l
o/p: shows all local branches

cmd: git branch -vv
o/p: shows tracking branches

cmd: git checkout <remoteBranchName>
o/p: add local tracking branch to remote <remoteBranchName>.

cmd: git remote show origin
o/p: shows information about tracking branches and push pull information.

cmd: git remote prune origin
o/p: removes remotely deleted branch from local repository.

cmd: git pull -v
o/p: shows inside process of pull.

.git/FETCH_HEAD contains the hash of last commit at remote branch and is used to check is locally fetched repository is upto date or not.



cmd: git push-u origin <branchName>
o/p: pushes newly created local branch to remote repository.
```

#GITHUB TOKEN: 
```
cmd: git remote update origin --prune
o/p: reflect remotely deleted branches in our local repository.

cmd: git branch -D <branchName>
o/p: delete unmerged branches.

cmd: git push origin -d <branchName>
o/p: Delete remote branch from local terminal

cmd: git show-ref
o/p: shows all remote + local references(branches)

cmd: ls .git/refs/heads
o/p: shows all local branches

cmd: ls .git/refs/remotes/origin
o/p: shows all remote branches

cmd: git show-ref <branchName>
o/p: shows references to specified branchName.(both should be same if they are consistent)

```

#PULL REQUEST
pull requst != git pull
```
cmd: git commit --amend --author = "newAuthorName <authorNewEmail>"
o/p: update last commit author information.

cmd: git remote add <newRemoteServerName> <parentRepositoryLink>
o/p: add parent origin(we can only pull and fetch allowed)
e.g" git remote add upstream https://github.com/sudoShubham/git-github-commands.git

cmd: git pull upstream master -v
o/p: pull from parent of forked branch.
```
#### **GIT TAGS**

                                                        V 4.7.2
                                                  ________| | |__________                                                   
                                                 |          |            | 
                                                 |          |            |
                                                 |          |            |
                                               MAJOR      MINOR        PATCH
                                                        

TAGS
|-----------lightweight tag
| 
|-----------Annoted tag
```
cmd: git tag
o/p: shows all tags

cmd: git tag <version>
o/p: create lightweight tag.
e.g: git tag v1.0.0

cmd: git show <version>
o/p: shows commit where tag has been set and other information.

cmd: ls .git/refs/tags
o/p: show all tags
```

```NOTE: lightweight tags are not get pushed to remote using git push cmd.```

```
cmd: git tag -a <version> -m <message>
o/p: create Annoted tag

cmd: git push --tags
o/p: push tags to remote(Annoted tags)

cmd: git push -v origin <version>
o/p: push specific version to remote.
```
#### **REBASING**
```
git checkout <featureBranch>
git rebase master
git checkout master
git merge <featureBranch>

cmd: git log --graph
o/p: shows log with tracking lines
```
---

```
.gitignore file
    new-file.txt //ignore new-file.txt
    bin/         //ignore bin folder
    *.tmt        //ignore all files with .tmt extension
```


```

cmd: git log --oneline
o/p: show log in collapse view 

cmd: git log --stat
o/p: more detailed information.

cmd: git log -4
o/p: shows last 4 commits

cmd: git shortlog
o/p: shows short log

cmd: git shortlog -n
o/p: shows shor log with most active user at the top.

cmd: git shortlog -n -s
o/p: shows all authors with number of commits that they have made. 

cmd: git shortlog -n -s -e
p/p: shows emails of all authors

cmd: git log --authors = "<authorName>"
o/p: shows all commits done by specified author.

cmd: git log --authors = "<authorName>" --oneline
o/p: shows all commits done by specified author in one line.

cmd: git log --grep = <"specificKeyword">
o/p: shows all commits containing specificKeyword.



cmd: git log --merges
o/p: show all merges

cmd: git log --no-merges
o/p: shows commits without merges.
```

```DISTRUCTIVE COMMANDS```

```cmd: git reset <comitName/hash>
o/p: unstage changes.

cmd: git reset HEAD ~ 5
o/p: unstage latest 5 changes.
```

```
cmd: git revert HEAD
o/p: it revert all changes of last commit and create new commit without that changes.

cmd: git revert <SHA1>
o/p: it revert all changes of <SHA1> commit and create new commit without that changes.

cmd: git commit --amend -m "<newMessage>"
o/p: updates last commit message.

cmd: git commit --amend --author = "newAuthorName <authorNewEmail>"
o/p: update last commit author information.

cmd: git cherry-pick <SHA1>
o/p: add <SHA1> commit to current branch commit.

cmd: git stash
o/p: saves data of staged area before changing the branch so that after coming from some other branch we can still have those unstage area data.

cmd: git stash pop
o/p: takes staged data out which we have stored before going to another branch.

cmd: git gc
o/p: does garbage collection, removes detached head commit.Removed objects gets packed in .git/objects/pack folder.

cmd: git config credential.helper ""
o/p: reset credentials.

cmd: chmod +x <fileName>
o/p: makes file executable.
```

```NOTE: hooks are local,they are not pushed to remote repository.```

HOOKS REFFERENCE: https://github.com/sudoShubham/git-hooks-nodejs
