Hello all,
Before going deeper let's understand in big picture.

**BLOB :**
- BLOB stands for binary large object.
- It is a binary representation of a file. This is the object type which is used to store the contents of each file in a directory.These are most basic datatypes in git.

**Tree objects :**
- These are bit like directories. Tree objects can contain pointers to blobs and any other tree objects.
**Commit objects :**
- These points to a single tree object. And contain some meta data including the commit author and any parent commits.
**Tag objects :**
- which points to a single commit object and contain some meta data.
**References :**
- which are points to a single object(usually a commit or a tag object)

Git repository exists entirely in a single ".git" directory.


- Git is distributed version control system. Which means everybody has their own self contained repository.
- version controlling system is a system which involves in the process of tracking modifications of a previous versions of present code.
version controlling systems are basically divided into 2 types. They are 1. centralised version conrol system 2. Distributed version control system.

|centralised version control system| Distributed version control system|
|------------------|------------------------------|
|It is a single repository| It is a multirepository |
|Internet connection always needed | No need of internet connection |
|Made conflicts between the developers | Don't made the conflicts between the developers. Since, each developer has their own repository |
|It is having a high risk of losing data | It has a less risk of losing data |

**Difference between git and github**

|GIT | GITHUB |
|------|------|
|It was started in 2005 | It was started in 2008 |
|It is a software & CLI| It is a website, GUI & Service|
|It was developed by linux foundation | It was developed by Microsoft |
|It is user independent | It is user dependent |
|It is installed locally on the system | It is hosted in the web |
|It can manage source code history | It is a hosting service for git repo |
|It is focussed on the code sharing & version controlling | It is focussed on the centralised source code hosting |

The working process of git as follows : 
working area ---> staging area --> local repository ---> remote repository.


- we can initiate a empty git repository anywhere by using `$ git init` command
image.png

image.png
image.png
- The important directories are ./objects where we store all objects and ./refs where we store all references

**Tree objects :**
- Tree objects in git can be though as a directory. It contains a list of files(blobs) and another tree objects(sub-directories)
- root tree object is essentially a snapshot of your repository at a given time. When git refers to the tree it means it is root tree object.
**commits:**
- commit objects is essentially a pointer that contains few pieces of important meta data. the commit itself has a hash which built from a metadata that it contains.
- Even if we give partial hash, it gives us complete hash value because it's unique.
**References :**
- A reference is a file stored in somewhere else ./git/ref containing hash of commit object.

`$ ls -l .git/refs/heads`
`$ cat .git/refs/heads/master`
`$ git show --oneline master`
`$ git rev-parse master`

**Branches :**
- git branches is a strong feature. It is lightweight. It is entire clone of the repository.
`$ cat .git/HEAD`
`$ git branch </branch-name>`
`$ cat .git/refs/heads/</branch-name>`
`$ cat .git/HEAD`
`$ git checkout </branch-name>`
`$ cat .git/HEAD`

**Tags:**
- There are 2 types of tags in git they are 1. annotated tags and 2. lightweight tag
`$ git checkout master`
`$ git tag 1.0-lightweight`
`$ cat .git/refs/tags/1.0-lightweight`
`$ git cat-file -p 1.0-lightweight`

- lightweight tag and commit are the same object. light weight tag is only reference to the commit object
- let's create annotated tag
`$ git tag -a -m "taged 1.0" 1.0`
we have passed -a(annotated) to git tag to create annotated tag, It is also created a reference tag just like lightweight tag but reference is not pointing to same object as the lightweight tag.
`$ git cat-file` to inspect the object

Tag objects can also be signed with GPG keys to prevent commit or email spoofing.
`$ cat .git/refs/tags/1.0`
`$ git cat-file -p 1.0`

Reasons why we prefer annotated tag rather than lightweight tag :
> GpG keys
> Owner authorization
> These are timestamped, Apart from telling when the last commit was made. It also tells us about the last version release date.

**Merging :**
- Merging in git is the process of joining two histories(branches)together.
- let's say you have created new feature branch from master, and done some work on it.
`$ git checkout -b </branch-name>`
`$ git commit -am "finished the new feature"`
`$ git checkout master`
At the same time, you need to fix an urgent bug . so you created a hotfix branch from master and do some work in there.
Now you want to bring the bug fix into master. so that you can tag it and release it.

`$ git checkout -b hotfix`
`$ git commit -am "fixed some wording"`

- Notice how git mentions **fast-forwarding** during the merge. what this means is that all of the commits in hotfix were directly upstream from master. This allows git to simply move the master pointer up the tree to hotfix.

let's try and merge feature-branch into master.
`$ git branch hotfix`
`$ git merge hotfix`
`$ git merge feature-branch`
`$ git log --oneline`
`$ git show --format=raw </commit-id>`

- This time, Git wasn't able to perform a fast-forwarding. This is because feature-branch isn't directly upstream from master. This is clear on the above above, where master is at commit **D** which is in  a different history tree to feature-branch at commit **C**
so, how did git handle this merge ? Taking a look at the log, we see that git has actually created a new "merge" commit, as well as bringing the commit from feature-branch.

upon closer inspection, we can see that this is a special kind of commit object- It has **two parent commits** this is refered to as **merge commit**

**cherry-picking :**

![image](https://user-images.githubusercontent.com/89054489/218244876-691578c1-e3c1-438d-becd-38bfe4192cd3.png)

- if you are on commit **D** and you run git cherry-pick **F**, Git will take that changes that are introduced in commit **F** and replay them as new commit(shown as 'F`') on top of commit **D**
 ![image](https://user-images.githubusercontent.com/89054489/218245440-2e306048-0a61-4caf-81e1-56467b952111.png)

- The reason why we end up with a copy of commit **F** rather than commit **F** itself is due to the way commits are constructed. Recall the parent commit is part of a commit's hash.so, despite containing the same changes, author information and timestamp. **F`** will have a different parent to **F**, giving it a different hash.

- A common workflow in git is to develop feature on small branches and merge the features one at a time into the masters branch.
![image](https://user-images.githubusercontent.com/89054489/218246806-08a20b41-183a-4dbc-b734-e83a8f80e77f.png)

- As you can see, master has been updated since, "foo" was created. To avoid potential conflicts when "foo" is merged with "master", we want to bring master's changes into "foo". Because master is the base branch, we want to play foo's commits on top of master. Essentially, we want to change commit **C's** parent from **B**to**F**
it's not going to be easy. But, we can achieve this with git cherry-pick.First, we need to create a temporary branch at commit F

`$ git checkout master`
`$ git checkout -b foo-tmp`
Now that we have a base on commit **F**, we can cherry-pick all of foo's commits on top of it.
`$ git cherry-pick C D`

- Now all that's left to do is point "foo" at commit **D`**  and delete temporary branch "foo-temp". We do this with the reset command, which points HEAD(and therefore the current branch) at a specified commit. The --hard flag ensures our working tree is updated as well.

`$ git checkout foo`
`$ git reset --hard foo-temp`
`$ git branch -D foo-temp`

- This gives the desired result of foo's commits being upstream of master. Note that the original **C**and**D** commits are no longer reachable because no branch points to them.

![image](https://user-images.githubusercontent.com/89054489/218247808-426a42ec-8015-41da-a191-d39ddba359d3.png)


![image](https://user-images.githubusercontent.com/89054489/218248215-e83029c0-635e-4fa9-b447-ac4c09af505f.png)

**Rebasing :**
`$ git rebase <base> <target>`
- with the format git rebase <base> </target> , the rebase command will take all of the commits from <target> and play them on top of <base> one by one. It does this without actually modifying <base> , so the end result is a linear history in which <base> can be fast-forwarded to <target>
- In a sense, performing a rebase is like telling git **"Hey, i want to pretend that <target> was actually branched from <base> Take all of the commits from <target>, and pretend that they happened after <base>"**.

- All we have to do to enable fast-forward merge of feature-branch into master is run git rebase master feature branch before performing the merge. This has brought feature-branch directly upstream of master.

![image](https://user-images.githubusercontent.com/89054489/218262135-7530d9e1-ec21-47b5-aee0-5bc4b3d5f0f0.png)

- **Rebase flatterns the history, removing unwanted entries**. Git merge on the other hand, only changes the target branch and creates a commit, preserving the history of the source branch.
-**cherry picking in git means to choose a particular commit from one branch and apply it onto another branch**. In contrast merge or rebase apply normally many commits onto another branch.

**Remotes :**

- It is therefore possible to have a repository which can store your project's history without actually having a working tree. this is called **bare repository**.Bare repositories are most commonly used as a "central" repository where collaborators can share changes. the mechanism for sharing these changes will be explained in detail in the **pushing**and**pulling**sections. For now, let's look at creating a bare repository.

`$ git init --bare`
- Notice here instead of creating a .git folder, the above command simply treats the current directory as .git directory.

- Notice how rather than creating a .git directory for the repository. git init --bare simply treats the current directory as the .git repository.
There's really not much to this repository. The only interesting things it contains are HEAD reference. which points to the master branch(which doesn't exist yet) and a config file which has the bare flag set to true. The other files aren't of much interest of us.

`$ cat HEAD`
`$ cat config`
`$ find. -type f`

**Cloning :**
- the git clone is really just a shortcut which does a few things for you. with its default configuration, it will:<br>
1. create remote-tracking branches for each branch in the remote.<br>
2. checkout the branch which currently active(HEAD) on the remote.<br>
3. perform a git pull to bring the current branch and working tree up-to-date with the remote.

the clone command takes a url and supports a number of transport protocols including HTTP, SSH, and Git's own protocol. It also supports plain old file paths, which is what we'll use.

`$ cd ..`
`$ git clone bare-repo/clone-of-bare-repo`
let's inspect this cloned repository to see how git has set it up.

`$ cd clone-of-bare-repository`
`$ find. -type f`
`$ cat .git/HEAD`
`$ ls -l .git/refs/heads`
`$ cat .git/config`

- This is quite literally a clone of bare-repo the only difference is that this repository contains a few extra lines in .git/config
<br>First, it contains a remote listing for "origin"  which is the default name given to a repository's main remote. This tells git the URL of the repository and which reference it should retrieve when performing a **git-fetch**.

**pushing :**
- we just now cloned a completely empty repository, and we want to start working on it.
`$ echo 'project v1.0'>README`
`$ git add README`
`$ git commit -m "Add readme"`
- Now that we've completed some work, we need to share this with our collaborators who have also cloned this repository. Git makes this really easy.

`$ git push origin master`
- As expected, the remote repository now contains a master branch which points to the commit that we just created.
- Essentially, what happened when we ran git push, is GIT updated the remote's references, and sent it any objects required to build those references. In this case, git push updated the remote's master to a point at <commit-id> and sent it to <commit-id> commit object as well as any tree and blob objects related to that commit.

`$ remote-tracking branches`
- As we saw in cloning, a remote-tracking branch is essentially just a few lines in .git/config.
**[branch "master"]<br>
        remote = "origin"<br>
        merge = refs/heads/master

The line [branch "master"] denotes that the following configuration applies to the local **master** branch.
The rest of the configuration specifies that when this remote-tracking branch is fetched. Git should fetch the **master** branch from the **origin** remote.
Besides storing this configuration, git also stores a local copy of the remote branch.This is simply stored as a reference in .git/refs/remotes/<remote>/<branch>

**fetching :**
- **git fech** command is fairly simple. It takes the name of a remote (unless used with -all flag, which fetches all remotes) and retrieves any new references and all objects necessary to complete them.
- This fetch parameters here specifies a mapping of <remote-refs>:<local-refs>
<br>
The example above simply states that the references found in origin's refs/heads/* should be stored locally in /refs/remote/origin/*

`$ git fetch origin`
This has done a couple of things. First, it has created a reference for the remote branch in .git/refs/remote/origin
`$ cat .git/refs/remotes/origin/feature-branch`
it has updated a specific file .git/FETCH_HEAD with some important information.

- But, what if we do want a local branch which tracks the remote feature-branch ? Git makes this easy. if we run git checkout feature-branch rather than failing because no local feature branch exists, git will see that there is a remote feature-branch available and create a local branch for us.
`$ git checkout feature-branch`
branch feature-branch set up to track remote branch feature-branch from origin.

git has done couple of things for us here. first, it has created a local feature-branch reference which points to the same commit as the remote feature-branch.

`$ cat .git/refs/remotes/origin/feature-branch`
It has also created a remote-tracking branch entry in .git/config
`$ cat .git/config`

**pulling :**
- the git pull command is, like git clone, a nice shortcut which essentially just runs a few lower-level commands. In short, with the format `$ git pull<remote> <branch>, the git pull command does the following :<br>
1. Runs git fetch <remote>
2. Reads .git/FETCH_HEAD to figureout if <branch> has a remote-tracking branch which should be merged.
3. Runs git merge if required, otherwise quits with an appropriate message.

At this point, it helps to understand git's FETCH_HEAD. Everytime you run git fetch, git stores information about the fetched branches in .git/FETCH_HEAD. This is refered as short-lived reference, because by default git will override the contents of FETCH_HEAD everytime you run git fetch.

**Toolkit :**
 **git-reflog**:
- git records information about the changes in so called "reflog"
- git log is no help, since the commits are no longer reachable from HEAD.
In these cases, we use reflog
`$ git reflog`
- the reflog shows a list of all changes to HEAD in reverse chronological order.
- the hash in the first column is the value of HEAD after the action on the right was performed.

- if we want to recover commits we follow different methods depends upon situation. In this particular example, we can simply do `$ git reset --hard <commit-id>` to restore HEAD to its original position.However, if we have introduced new commits since, the destructive change, we may need to do something like **cherry-pick** all the commits that are lost.

**note:** git's reflog is only a record of chages for your repository. if your local repository becomes corrupt or deleted. the reflog won't be of any use(if the repository is deleted the reflog won't exist at all)
- depends upon the situation, you may find **git fsck** more suitable for recovering lost commits.
- git's object storage works like a primitive file system--objects are like files on harddrive and hashes are object's physical address on the disk. the git index is exactly like the index of a file system in that it contains references which point at an object's physical location.
- In `$ git fsck` fsck(file system check) this tool is able to check git's database and verify the validity and reachability of every object that it finds.
- when a reference(like branch) is deleted from git's index. the object(s) they refer to usually aren't deleted. even if they are no longer reachable by any other references. if we delete **feature-branch(ex)** the commit will no longer be reachable.<br>
At this point, commit<commitid> still exist in our repository. but there are no references pointing to it. By searching through the database, git fsck is able to find it.
`$ git fsck --lost found`
- An example of this is when you delete a remote branch through interfaces like github. Assuming the object haven't been garbage-collected, you can clone the remote repository and use git fsck to recover the deleted branch.
**git stash:**
- it takes all changes to your working tree and index and "stashes" them away, giving you a clean working tree. you can then retrieve those changes from your stash and reapply them to the working tree at anytime with `$ git stash apply`
- A common usecase of git stash command is to save some half finished changes inorder to checkout another branch.
- stashes in git are put onto a stack. with the most recently stashed on top. you can list all current stashes with `$ git stash list`
-**stash commit is a merge commit**
- to find path of git merge commit , we use `$ git show-ref`
#### why does git creates a merge commit for stash ?
- Recording the stat of working tree, and record the state of index(also known as "staging area")
- since, its possible for the index and the working tree to contain changes to a same file. Git needs to store the states repeatedly.
This gives us a history that looks a little like this :

![image](https://user-images.githubusercontent.com/89054489/218262227-765b9b2c-6700-4c9a-9e6c-005c9c729082.png)

- In this history graph, the tree of commit C contains the changes to the working tree. commit C's first parent is the commit that HEAD pointed to when the stash was created (commit A). The second parent (commit B) contains the changes to the index. It is with these two commits that Git is able to re-apply your stashed changes.

**git describe:**
- git describe show the most recent tag that is reachable from a commit.
- git describe will take any reference or commit hash, and return the name of the most recent tag.if the tag points at the commit you gave it.
- git describe will return only the tag name. otherwise, it will suffix the tag name with some information including the number of commits since the tag and an abbreviation of the commit hash.
`$ git describe <commit-id>`
- if you want to ensure that only the tag name is returned. you can force git to remove the suffix by parsing --abbrev=0
`$ git describe --abbrev=0 </commitid>`
**git rev-parse**
- it is an ancillary plumbing command which takes a wide range of inputs and returns one or more commit hashes. The most common use case is figuring out which commit a tag or branch point to.
`$ git rev-parse --short v1.2.15`
**git bisect :**
- git bisect is an indispensible tool when you need to figure out which commit introduced a breaking change. the **bisect** command does a binary serach through your commit history to help you find the breaking change as quickly as possible.
To get simply started, simply run `$ git bisect start `
To tell git that commit your'e currently on is broken `$ git bisect bad`
then give git a commit that you know is working with `$ git bisect good <commit>`
once bisect is finished( or when you want to abort it) be sure to run git bisect reset HEAD to where it was before the bisect.

find which commit a reference points at `$ git rev-parse HEAD` `$ git rev-parse --short HEAD`
find which branches a commit is in `$ git branch --contains HEAD`
find commits that are in one branch but not another `$ git log --oneline --right-only master..hotfixed-1`
exclude commits that are cherry-picked `$ git log --oneline--cherry-pick --right-only master..hotfixed-1`
To view details of an object `$ git cat-file -p HEAD`
To shown an object's type `$ git cat-file -t HEAD`
to show an object's size `$ git cat-file -s HEAD`
print the tree of a given reference `$ git ls-tree-t-r HEAD`
find  the first tag that contains the reference `$ git describe HEAD`




`git config --global user.name "Nagacharan g"`   To provide global user name
`$ git config --global user.email "nagacharan4286@gmail.com"` To provide global user email id
`$ git config --global user.name` To check the name of the user
`$ git config --global user.email` To check the name of the email id
`$ git config --list`      To check all the list of configurations
`$ git config --global --list` To check only the global configurations.
`$ git config --global --edit` To edit the global configuration settings.

`$ git init`    To create a new empty local repository.

`$ git status`  To check the status of untracked files



