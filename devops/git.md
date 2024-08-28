1. Why VCS:
   - COLLABORATION
   - MANAGE VERSIONS
   - ROLL BACKS
   - REDUCE DOWNTIME
   - ANALYSE PROJECT
1. Git:
   Git is a Distributed Version Control tool that supports distributed non linear work flows by providing data assurance for developing quality software

   1. Features:

      1. Economical - Open source & License free
      2. Speed - Faster than other VCS
      3. Non-Linear - Branchig and Merging
      4. Robustness - Nearly everything can be undo
      5. Snapshots - Easy recovery from local repo (SHA1)
      6. Integrity - Every change is recorded
      7. Distributed - Every user has a own copy of repo locally
      8. Branching - Every user (Developer) will be working on different branch (Feature branch)

   2. Git Operations:

      1. Set up repo:
         1. git init - initializes git with .git
         2. git colne - Create a copy of repo locally (git clone <url>)
         3. git config - configuring git
         4. `git alias` -
      2. Save changes:
         1. git add <file name> - adding changes to working dir and staging area
            ----> git add -A (adds all the files)
         2. git commit -m "<message>" - Describes what are the changes done
      3. Inspect repo:
         1. git status - displays the state of working dir and staging area and untracked files by git
         2. git log - displays commited snapshots
         3. <file name> - used to capture a point in history
         4. git blame <file name> - displays authors metadata what changes made at what time along with commit id respectively
         5. git branch -vv - displays current working branch
         6. git remote add origin <url> - to set up a remote and git pull origin main - which updates the local repo with remote repo
         7. git remote set url origin <url>
         8. git remote -v - to check remote repo
         9. git pull origin main - updates the local repo with remote repo - imports commits from remote
         10. git push origin main - updates the remote repo with local repo - exports commits from remote
      4. Parallel development:
         1. git branch <branch name> - creates new branch
         2. git checkout <branch name> - switches to a branch
         3. git merge <base> - combines two branches
         4. git rebase <base> - moves all work from current branch to main branch
      5. Git push and pull:
         - Create a dir and initialize with git and add a repo in github as well
           ----> git remote add origin <linn of the repo created on githib>
           ----> git pull origin <branch name>
         - To do pull operation create a file locally in the same above repo
         - Then add and commit changes
           ----> git push origim master

      - Additional commands:
        - git archive master --format=zip -output=.<name of file>.zip
          `* git bundle create ../repo.bundler master`
        - git stash
      - REPOSITORY:
        - A repository is a directory or storage space where projects live. It can be local folder or folder on host (GITHUB)

   3. SSH KEYS:
      - An SSH key is an access credential for the secure shell network protocol. This authenticated and encrypted secure network protocol is used for remote communication between machines on an unsecured open network. SSH is used for remote file transfer, Network management and remote operating system access
        1. Remote file transfer
        2. Netwoek Management
        3. Remote OS access

           1. CREATING SSH KEYS:
              ----> ssh-keygen
              - prompted to save the key
              - leave the pass phrase empty
              - ass the ssh key to shh-agent
           2. Setting up SSH:
              - ssh-keygen -t rsa b 4096 -C "<email adress>"
              - Select the file location or enter to set default location
              - Use enter and use the empty pass phrase
              - To check ssh agent is enabled:
                ----> eval "$(ssh-agent -s)"
              - Adding shh agent:
                ----> ssh-add <location of id_rsa key>
              - To add ssh key to github account
                ----> cat ~/.ssh/id_rsa.pub
              - copy the above key and in github settings SSH and GPG keys paste the key
              - To test the key
                ----> ssh -T git@github.com
              - Colour of key turns in to green (test is sucessfull)

1. Installation:

   1. Install is different from one operating system to another check the online procedure and follow
   2. Configuration:
      ----> git config user.name "<name>"
      ----> git config user.email "<email id>"
      ----> git config --list

1. Commands:
   1. git init - This turns a dir in to empty git repo
   2. git add <file name> - add the files to the staging area
   3. git rm --cached <file name> - to unstage the changes
   4. git commit -m ""<message> - Records the changes made to the files in a local repo
   5. git status - This command returns the current state of the repo
   6. git config
      ----> git config user.name "<name>"
      ----> git config user.email "<email id>"
      ----> git config --list
   7. Branching:
      - Branches are used for create another line of development, features and the deafult branch is `master`
      - To create a branch:
        ----> git branch <branch name>
        ----> git checkout -b <branch name>
        ----> git checkout -b <branch name> <commit id>
      - To del branch
        ----> git branch -d <branch name to be deleted> - to del merged branches
      - Force del
        ----> git branch -D <branch name to be deleted> - to del unmerged branches
        * To del a remote branch
        ----> git push -d <remote name> <branch name>
        ----> git push <remote name>:<branch name>
      - To create and checkout a branch
        ----> git checkout -b <give a branch name>
      - Comparing local branch with remote
        ----> git diff <master brach> <remote branch>
      - To check all branches
        ----> git branch -a

   - Working with remote repos:

     - To connect to a remote repo from local repo
       ----> git remote add origin <link of the repo from github>
     - To make a copy or copy of an existing repo
       ----> git clone <link of the repo>
     - To pull the changes made remotely
       ----> git pull origin master
     - Add and commit changes then only we can push the changes
       ----> git push origim master

     - Scenario: We have a local repo we want to add it to GitHub
       ----> git remote
       ----> git remote add <remote name> <url of repo>
       ----> git rename rename origin <name>
       ----> git remote rm - to remove a remote repo
       ----> git push origin <branch name> default branch -> master
       ----> git push origin --delete <branch name>
     - Renaming a branch on remote repo:
       ----> git branch -m <branch name> <rename> (rename or move a branch) (cureent branch is considered and renames if not given a branch name)
       ----> git push origin :<old name> <new namw>
     - Deleting a remote branch:
       ----> git push -delete <remote name> <branch name> (here default: remote:origin, branch: master)
     - Force (-f) push flag in Git:
       - This flag is used to push changes forcefully
       - This must be avoided because it might override other peoples changes
         ----> git push -f <remote name> <branch name>
       - Only the pushed changes from local repo will appear
     - Comparing remote repos:
       - Commit a file, then make changes
         ----> git diff <file name>
     - Comparing two commits:
       ----> git diff <commit id1> <commit id2>
     - We can aslo compare file with commitid
       ----> git diff <commit id> <file name>
     - fork
     - Setting up Upstream:
     - To check remote repos
       ----> git remote -v
     - git remote add upstream
     - Pull request:

   - Advanced commands:

     1. git stash - to save changes made when they are not in a state to commit them to a repo

        - git add <file name>
        - git stash -u
        - git status
        - git stash list
        - git shash show
        - git stash apply (after completion of clean work)

     2. got log - this helps give you context and history of repo
        - git log - shows logs
        - git log -before="<date>"
        - git log --author="<author name>" (hint: no need to give exact name)
        - git log --oneline - gives one line response
     3. git rebase - take a set of commits, copies them and stores them out side your repo
     4. git revert - it helps in roll back previous version of the file
        - git revert <commit id>
        - git revert HEAD - roll backs to the old version

1. Basics:

   - NEED FOR GITHUB:
     - Developers need a web/cloud based hosting platform
     - Useful for version control
     - Enables effective collaboration
     - Downloads files and projects in one go
     - Easy evaluation each others work
       1. GITLAB
       2. MICROSOFT TEAM FOUNDATION
       3. BITBUCKET
   - ADVANTAGES OF GITHUB:

     - Powerful community
     - The largest shared repos
     - East version cintrol
     - Secure cloud storage

   - WHAT IS GITHUB
     - Web based git repo hosting service
     - Easy management of code
     - Open source software for version control
     - Effective collaboration
     - Bug tracker (issues feature)

1. Github workflow:

   - Git flow:
     - Works with each phase of the software development
     - It is perfect when one or two developers are working on the same project
   - GitHub:
     - Lightweight, Branching workflow
     - Supports team that deploy often
     - Centered around small changes
   - GitHub flow:
     1. Creating a branch:
        - Branches help work on features and bug fixes
        - Do not effect master branch
        - Anything in master branch is deployable
     2. Add commits:
        - Keep tracks of changes in feature branch
        - More transparent history of work
        - A seperate unit of change
     3. Open a pull request:
        - Discussion about commits
        - Open it during any point of development process
        - We can ask feedback from any of the team members

1. Git bash: (Bourne again shell)
   - It is an application which provides git command line experience on the operating system
1. Git repo:

   - Storage space for project
   - GitHub is avery popular central repo that allows to share files
   - Push local repo to GitHub and share it with other collaborators via central repo

1. Gitlab CI/CD

1. Branching and stashing:

BENIFITS OF BRANCHING
---------------------
   1. Revolutionary feature of Git - Distinguishes from other VCS
   2. Lightweight, Operations over git branches are very fast - Switching back and forth
   3. Faciliates faster Development and code merging

GIT STORAGE STRATEGY - OBJECTS
------------------------------

1. BLOB
2. TREE
3. COMMIT
4. TAG

   - Branches allows us to work on other features
   - They can be included with the main line of the project
   - The mian branch - the one where all the changes eventually get merged back into, and is called master
     (we can create branches from github)

- Pull requests:
  - Notifies developers about changes you have pushedto a branch repo
  - Acknowledge and reviews changes
  - This can be created in two ways

10. Git merge
11. Git rebase
12. Git merge vs git rebase
13. Jenkins git integration
14. Web hooks Jenkins

* CICD :

INRRODUCTION TO CICD
--------------------

* Cons:
    1. Reduce errors in code
    2. Speeds up coding process
    3. Integrates code steamlessly

* CI - Continous Integration
* CD - Continous Delivery
* Continous Deployment

* Why CICD?
    1. Increase speed of operation
    2. Communication between teams
    3. Regular feedback
    4. Frequent Development Cycles
    5. Easier Detection of errors
    6. Quicker recovery
    7. Better efficiency

* CICD - pipeline:
    1. Initiates code builds
    2. Run tests
    3. Staging Production Environments

1. Commit - New codes are integrated to the base code
2. Build - Source code is converted in to an executable form
3. Test - Checks the interaction between builds and if app is working
4. Deploy - Deploys the app to production environment

GIT-LAB:

* To use GITLAB we need:
    1. Application codebase hosted on GITHUB
    2. Sequentially defined scripts in YAML file
    3. YAML file in the path of root repo
    4. Name of file `.gitlab-ci.yml`
