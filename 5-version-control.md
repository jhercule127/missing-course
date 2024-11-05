## Version Control (Git)

Version control systems (VCS) are tools used to track changes to source code. Help maintain a history of changes

Why is version control? Even when you’re working by yourself it can let you look at old snapshots of a project, keep a log of changes, work on parallel branches of development


### Git’s data model

**Snapshots**
Git models the history of a collection of files and folders within some top-level directory as a series of snapshots
- Blob - a file in Git
- Tree - a directory in Git (maps names to blobs or trees)

Snapshot is the top-level tree that is being tracked

Modeling history: relating snapshots
In Git, a history is directed acyclic graph of snapshots, every snapshot has a set of parents
Commits in Git are immutable, “edits” to commit history are actually creating entirely new commits

**Objects and content-addressing**
An “object” is a blob, tree or commit, In Git data store all objects are content-addressed by their SHA-1 hash

**References**
References are pointers to commits. Gives human-readable names fro SHA-1 hashes
To have a notion of “where we currently are” in the history of- In Git that “where we currently are”
Is a special reference called “HEAD”

Repositories
A repository is the data objects and references



## Staging Area
This is a way you might imagine of implementing snapshotting , to have a 
“Create snapshot” command
- Git accommodates scenarios by allowing you to specify which modifications should be included

Helpful commands
`git log --all --graph --decorate`: visualizes history as a DAG
`git diff <filename>`: show changes you made relative to the staging area

**Remote**
`git branch --set-upstream-to=<remote>/<remote branch>`: set up correspondence between local and remote branch

**Advanced**
`git blame`: show who last edited which line
`git stash`: temporarily remove modifications to working directory

For deleting sensitive data from git history
- https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository



### Exercises
2. Clone the repository
  -  git log --all --graph --decorate (SHOWS GRAPH)
  -  Answer: Author: j-s-ashley <jashley6@vols.utk.edu>
  -  cmd: git blame _config.yaml to get line
  -  git show - shows the commit
3. Sensitive info removal
4. Git stash can be used to make changes, save them away the put them on a new branch
5. Add GIT ALIASES TO ~/.gitconfig
6. ~/.gitignore_global can be used to ignore specific temporary files
