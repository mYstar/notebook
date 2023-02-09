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
