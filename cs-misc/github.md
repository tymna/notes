- global ~/.gitconfig
- repository, contains .git

- file:
	- untracked
	- staged
	- committed
- `git status` - current repo state
- `git add .`
- `git commit -m "message"`

- `git --no-pager log --oneline`

- tree - storing a dir
- blob - storing a file

- commit stores entire history (with pointers to the files)
- tree -> blob -> blob

git see everything as objects, 4 types:
- Blobs - file content
- Trees ~ directory - list of filenames, permissions and pointers to Blobs or Trees
- Commits - pointer to a Root Tree (repo snapshot)
- Tags - commit pointer (versioning) 
[[git scheme]]
When doing commit, we create a new tree, in which we store pointers to hashes of files that were not changed. We are creating Merkle Trees {blockchain-kinda logic, but mutable (rebase/force push)}.

GitHub Merkle Tree:
Root Tree -> Trees (with children: Trees & Blobs) & Blobs

branching
- `git branch`
- `git branch -m oldname newname`
- `git switch -c new_branch`
- `git log --oneline`

merge:
- merge commit - commit with 2 parents
    A -> B -> C
      \          > G
        D -> E
