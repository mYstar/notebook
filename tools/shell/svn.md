# svn

## create a repo

1. create repo on server and set **permissions**
    * permissions set in: `<repo folder>/conf/svnserve.conf`
    * passwords configured in: `<repo folder>/conf/passwd`
2. `svn import <folder> svn://<url>/<reponame>`
3. write commit message
4. login

## working
* checkout: `svn co svn://<url>/<repo>`
* commit: 
    1. (`svn add <files>`)
    2. `svn commit <optional: files -- when no add> -m '<message>'`
* branch: `svn copy svn://<url>/<repo>/trunk/ svn://<url>/<repo>/branches/<branchname>`
* update local copy: `svn up`

## organization

* `trunk/`: main code
* `branches/`: holds working copies of trunk, merged later
* `tags/`: holds ready versions of trunk

## merging

* classical workflow:
```
cd <branch>
svn up  
svn merge ^/trunk
svn commit
cd <trunk>
svn merge --reintegrate ^/branches/<branchname>
svn commit
```
* afterwards perhaps delete the branch: `svn delete <branchfolder>`

## resolve conflicts

* conflicts happen on `svn up`
* there are multiple options:
    * **p**ostpone: creates 4 files on every conflict 
        * conflict version (original name), your version, last checked out version, new version 
        * change the conflict version 
        * `svn resolved <filename>`
    * **e**dit file:
    * **m**y side of **c**onflict:
    * **t**heir side of **c**onflict:

## tagging

* gives a name to a specific revision
* used to name versions
* create tag with: `svn copy`
    * remote: `svn copy svn://<remote>/trunk svn://<remote>/tags/v1.1.`
    * or working copy:  `svn copy <path/to/working/copy/> svn://<remote>/tags/v1.1.`

## ignore

* is set on a directory basis
    * for every folder only one regex
* with: `svn propset svn:ignore 'file.txt' .`
    * and for all subdirectories: `--recursive`
    * `*?[]` are usable
