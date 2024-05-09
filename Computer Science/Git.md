Git is a version control system that tracks changes made to software during the development period. Git operates as a distributed model and therefore has a remote and local copies. These remote copies are commonly held by a service such as GitHub or Gitlab.

The most basic element of Git is the repository. A **repository** is the folder that is being tracked by Git. These repositories are modified with actions called commits. **Commits** function to change specific files in the repository. A common aspect of git is the hosting onto an outside server. This allows users to keep their own copies of the git which they are able to commit too without affecting the main copy. Initially to get the main copy a **clone** request must first be issued. To modify this main copy the commits need to be **pushed**. Commonly the central copy is modified and thus needs to be updated with the changes of other uses. To achieve this a **pull** request is done as to apply all changes.

Due to its version history capabilities a git repository is usually represented as a [[Abstract Datatypes#Stack|stack]] with a *head* representing the latest version of the repo.

A **branch** is a copy of the repository that is being modified independently from the main branch. Changes to this branch won't affect other branches and as a result changes from other branches won't affect this branch. A branches can be **merged** together. This process attempts to update changes from files as to get a final result.

Git can be used from the command line. The commands that can be used are:
- `git add` which adds the selected file.
- `git commit` which adds a new version change to the git history. Use the `-m "..."` flag as to put a message into the commit.
- `git push` which pushes changes to the remote copy of the repository.
- `git branch` which creates a new branch with a name.
- `git switch` which switches the currently used branch.
- `git merge` which merges branches together.
- `git rebase` which rebases the entire repository.
