## Personal daily tips and tricks around git

### "Pulling is not possible because you have unmerged files"

- status:

```bash
git pull
# error: Pulling is not possible because you have unmerged files.
# hint: Fix them up in the work tree, and then use 'git add/rm <file>'
# hint: as appropriate to mark resolution and make a commit.
# fatal: Exiting because of an unresolved conflict.
```

- quick solution, either add new local file and commit, or just revert with
  upstream changes

```bash
# update origin/<branch> to latest
git fetch --all
git branch backup-master
```

## Fetch upstream changes

```bash
# i.e. in master/main branch
git fetch upstream
git status
```

### Pull new changes if fast-forward only is possible

All is fine.

```bash
git pull upstream main --ff-only
```

### Pull changes if fast-forward not possible

Probably touched the main branch. Read more why not do do so and how
to resolve in chapter
[32.5 Um, what if I did touch main](https://happygitwithr.com/upstream-changes.html#touched-main)
of [happy git with R](https://happygitwithr.com/)

1. Save changes accidentally made in main branch

```bash
git checkout -b my-great-innovations
```

2. Go back to main/master branch

3. Reset hard with tip at source repo of the repository owner

```bash
git reset --hard upstream/master
```