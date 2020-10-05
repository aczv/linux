## Switch from Bitbucket to Github

```bash

# Add new remote repository
git remote add github git@github.com:foo/bar.git

# Push to github
git push --porcelain --progress --tags --recurse-submodules=check github refs/heads/master:refs/heads/master

# Set Tracked Branch
git branch --set-upstream-to=github/master master

# Delete old remote Repository
git remote rm origin

# Rename new remote to 'origin'
git remote rename github origin

```
