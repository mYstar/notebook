# merge remote branch into working branch 

1. (git checkout <working>)
2. git pull origin <remote>
3. resolve conflicts
4. commit
5. git push origin HEAD

# commands
- `fetch`: updates all local branches to remote (also `update` for single branch)
- `pull`: integrates changes into working copy (`fetch` + `merge`)
    - `--rebase` setzt eigene Commits an die Spitze von remote HEAD 

## undo
- `git log`: shows the last commits and their hashes
- `git revert <hash1> <hash2>`: undoes the last commits in a new commit
  - `-m 1`: reverts a merge (1 stands for the first parent)
  - `git reset --hard <hash>`: removes the commit with <hash> and all following from the branch (use: `git push --force`)
  - git reset alters the branch, it should be the last resort, when revert is not possible  