# CheatSheet - Git Commands

## Table of Content
| Topic                                      | Commands                                             |
|--------------------------------------------|------------------------------------------------------|
| [Basic Git commands](#basic-git-commands)  | init; clone; commit; config; log;                    |
| [Branching](#branching)                    | branch; status; checkout; branch -dbm;               |
| [Merging](#merging)                        | checkout; merge; mergetool;                          |
| [Remotes & Pushing](#remotes-and-pushing)  | Pusing local branches to remote repositories         |
| [Remotes & Pulling](#remotes-and-pulling)  | Updating our local branches from remote repositories |
| [Versioning](#versioning)                  | How to manage tags and versioning our projects       |
| [Changelog](#changelog)                    | CHANGELOG Definitions                                |



## Basic Git Commands
<div>
<details>
<summary>Expand...</summary>


#### Creating new Repo
```sh
> git init 
```

#### Cloning an existing Repo
```sh
> git clone <git-url>
```

#### Turns Color on
```sh
> git config color.ui true
```

#### Adding files to the Staging
```sh
> git add .
```

#### Open editor to add a comment about your changes
```sh
> git commit
```

#### Adding a comment without opening an editor
```sh
> git commit -m "comment for commit"
```

#### Adding our credentials
```sh
> git config --local user.name dany 
> git config --local user.email email@email.com 
```

#### Check Logs history

```sh
> git log  

> git log --oneline     # See the log comments in a single line
```
</details>
            </div>

## Branching

<div>
<details>
<summary>Expand...</summary>


#### Branch Listing
```sh
> git branch 

* master   # Indicates the branch that you currently in
```

#### Get Status of the branch you are in.
```sh
> git status
```

#### Create a Branch
```sh
> git branch test  
```

#### Move to a Branch
```sh
> git checkout test  
```

#### Get History Log
*As a Branch is a copy of the master branch, you get the history of the project*
```sh
> git log
```

#### Delete a Branch
```sh
> git branch -d test
```
#### Create a Branch and move to it immediatelly
```sh
> git checkout -b test
```

#### Rename a branch
*You have to be in the branch for rename it*
```sh
> git branch -m newname
```
</details>
</div>


## Merging

<div>
<details>
<summary>Expand...</summary>


#### Fast Forward Merge
This will merge our branch into the master branch in a fast-paced.
A fast forward merge will only happen when the branch that was branched away from hasn't changed
in the time that the new branch has changed and in every other merge scenario a brand-new commit
would be generated from the merge except for in a fast-forward merge where no new commits are needed
because it's essentially that catching up with what is missed.
```sh
> git checkout master
> git merge branchname
```

#### True Merge
After running `git merge` command we will go to the editor to confirm the merge by adding a comment.
```sh
> git checkout master
> git merge branchname
```

### Merge Conflict
If we have a conflict when merging, we can cancel the merge we requested by running `git merge --abort`.

#### Solving conflicts:
- [Manually Edit File]: Go to the file in conflict and manually fix the lines involved. Then, add the files, commit them and merge them.
- [Use Git mergetool (VimDiff)]: Use this tool to help you solve merging conflicts you may be facing, by running `git mergetool`.
. [Using a GUI (eg. Sourcetree]: You can see and correct the conflicts by using a Graphical Interface.
```sh
> git checkout master

> git merge branchname

Auto-mergin file.txt
CONFLICT (context): Merge conflict in file.txt
Automatic merge failed; fix conflicts and then commit the result


> git merge --abort

> git mergetool  # Tool used for fixing merges.


:diffg RE   # 'RE' represents the first letters of the code you are seeing in the screen 
            # (in this case it is related to REMOTE), running this command you can move 
            # between those files.

:wqall      # It saves the changes and closes all of the involved files.
```
</details>
</div>


## Remotes and Pushing

<div>
<details>
<summary>Expand...</summary>


### Git Remote
We use remote repositories to work with external source of code instead our local machine's code.

   | Command         | Description                                          |
   |-----------------|------------------------------------------------------|
   | `git remote`    | List all remote repositories we have added           |
   | `git remote -v` | List all remote repositories with its alias and url. |


```sh
> git remote   
repository

> git remote -v
repository    http://github.com/username/repository.git

```


*Pushing an existing repository.*
```sh

> git remote add origin http://github.com/username/repository.git

> git push -u origin master

```

#### Git Push
Upload code to the remote repository.

| Command                         | Description                                                                                                         |
|---------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `git push [WHERE] [WHAT]`       | Syntax of *'push'* command. Where to Push? What to Push?                                                            | 
| `git push [remote] [branch]`    | You can push your branches to the remote repository by running this command.                                        |
| `git push -u [remote] [branch]` | Set an upstream tracking branch. After this you can do your push only typing `git push` without specify the branch. |
| `git push --all`                | It will push all of your branches                                                                                   |

```sh

> git push origin master

```


</details>
</div>


## Remotes and Pulling

<div>
<details>
<summary>Expand...</summary>


#### Git Pull and Fetch
Get changes from the remote repository.

| Command                  | Description                                                    |
|--------------------------|----------------------------------------------------------------|
|`git pull [FROM] [WHAT] ` | Get the files up to date from the remote repository            |
|`git pull origin master ` | Get the files from the origin and pull them into master branch |



```sh

> git pull origin master

```


#### Git fetch
Get files into your remote tracking branches.

|Command        | Description                                                                                                                    |
|---------------|--------------------------------------------------------------------------------------------------------------------------------|
| `git fetch `  | Update all of the branches in the local machine                                                                                |
| `git fetch -p`| Check what the remote tracking branch has now and if there is not in the server, it will remove it from the tracking branches. |


```sh

> git fetch

> git fetch -p

```
</details>
</div>


## Versioning

<div>
<details>
<summary>Expand...</summary>

### Versions types

| Version type        | Description                                                                              |
|---------------------|------------------------------------------------------------------------------------------|
| `v1.0.0-pre-alpha`  | Requirements analysis, software design, software development, unit testing.              |
| `v1.0.0-alpha`      | Software testing; may not contain all of the features planned for final version.         |
| `v1.0.0-beta`       | Feature complete with likely known/unknown bugs. Useful for demonstrations and previews. |
| `v1.0.0-rc`         | (Release Candidate) - All product features have been designed, coded and tested.         |
| `v1.0.0-stable`     | Last 'rc' which has passed all verification/tests.                                       |


### Version Number Updating

```
Version   v1.0.0
           ^ ^ ^
           | | |
           X Y Z
```

| Version Name | ID | Description                                                                                                                |
|--------------|----|----------------------------------------------------------------------------------------------------------------------------|
| Patch        |`Z` |Backwards compatible bug fixes are introduced.                                                                              |
| Minor        |`Y` |Backwards compatible functionality is introduced, any functionality is marked as deprecated. Substantial new functionality or improvements                                                                                                                                     |
| Major        |`X` |Any backwards incompatible changes are introduced. Patch and Minor must be reset to 0 when major is incremented.            |


Fast example about how to create a tag and push it to the server.

```sh
> git tag -a -m "Comment about the Tag" v1.0.0-alpha

> git push origin v1.0.0-alpha
```

</details>
</div>


## Changelog


<div>
<details>
<summary>Expand...</summary>


- [ConventionalCommits](https://www.conventionalcommits.org/en/v1.0.0/)
- [git-commit-msg-linter - NPM](https://www.npmjs.com/package/git-commit-msg-linter)

| Type     | Means         | Description                                                                                            |
|----------|---------------|--------------------------------------------------------------------------------------------------------|
| feat     | feature       | A new feature.                                                                                         |
| fix      | fixes         | A bug fix.                                                                                             |
| docs     | docs          | Documentation only changes.                                                                            |
| style    | style         | Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).|
| refactor | refactor      | A code change that neither fixes a buf nor adds a feature.                                             |
| test     | test          | Adding missing tests or correcting existing ones.                                                      |
| chore    | chore         | Changes to the build process or auxiliary tools and libraries such as documentation generation.        |
| perf     | performance   | A code change that improves performance.                                                               |
| ci       |ci             | Changes to your CI configuration files and scripts.                                                    |
| build    |build          | Changes that affects the build system or external dependencies (example scopes: gulp, broccoli, npm)   |
| temp     |temp           | Temporary commit that won't be included in your CHANGELOG.                                             |


#### Install Commit Msg Linter
            
```sh
> npm install git-commit-msg-linter --save-dev
```

#### Example of commit with comment

```sh
> git commit -m"chore: add typescript"

> git commit -m"feat: added a new feature that will allow the system to do something really cool"
```
</details>
</div>

