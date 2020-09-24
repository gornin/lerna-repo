# github thing

create a new repository on the command line

```bash
echo "# lerna-repo" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin git@github.com:buzingar/lerna-repo.git
git push -u origin master
```

or push an existing repository from the command line

```bash
git remote add origin git@github.com:buzingar/lerna-repo.git
git branch -M master
git push -u origin master
```
