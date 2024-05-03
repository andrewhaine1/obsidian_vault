f you deleted a file from the working tree, then commit the deletion:

```
git commit -a -m "A file was deleted"
```

And push your commit upstream:

```
git push
```

1. f you want to push a deleted file to remote

> `git add 'deleted file name'`
> 
> `git commit -m'message'`
> 
> `git push -u origin branch`

2. If you want to delete a file from remote and locally

> `git rm 'file name'`
> 
> `git commit -m'message'`
> 
> `git push -u origin branch`

3. If you want to delete a file from remote only

> `git rm --cached 'file name'`
> 
> `git commit -m'message'`
> 
> `git push -u origin branch`


A simpler way

```
git add . -A
git commit -m "Deleted some files..."
git push origin master
```

**-A** Update the index not only where the working tree has a file matching but also where the index already has an entry. This adds, modifies, and removes index entries to match the working tree. Taken from ([http://git-scm.com/docs/git-add](http://git-scm.com/docs/git-add))