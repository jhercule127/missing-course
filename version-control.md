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
