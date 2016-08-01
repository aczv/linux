## Switch from Bitbucket to Github

### Add Remote Repository

```
git remote add github git@github.com:foo/bar.git
```

### Push

```
git push --porcelain --progress --tags --recurse-submodules=check github refs/heads/master:refs/heads/master
```

### Set Tracked Branch

```
git branch --set-upstream-to=github/master master
```

### Delete Remote Repository

```
git remote rm origin
```

### Rename Remote Repository

```
git remote rename github origin
```

