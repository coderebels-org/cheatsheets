# Git sync a fork

## Precondition

You have a local Git-Repository with a Remote-Repository which is a fork
from somebody else's Repository.

## Aim

Sync your fork with the original repository to get all the updates that
happened there.

## Step 1: add a remote for the original repository

```
$ git remote add upstream https://URL-TO-ORIGINAL-REPO/ORIG-REPO.git
```

Typically you should have now two remotes: origin (fork) and upstream (original)

## Step 2: fetch all from upstream

```
$ git fetch upstream
```

## Step 3: if not done already, switch to master (from your fork)

```
git checkout master
```

## Step 4: merge upstream changes (master branch)

```
git merge upstream/master
```

## Step 5: push changes to your fork

```
git push
```
