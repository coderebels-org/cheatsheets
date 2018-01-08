# Git Create and Add Remote Repository

## Precondition

You have a local Git-Repository and maybe did some work there (commits and so on).

## Aim

Create and add a Remote-Repository for your local Repo.

## Step 1: on Server (Location of Remote)

```
SERVER:/directory/of/remote/repo$ git init --bare
```

## Step 2: add Repo on Client (your local Repo location)

```
CLIENT:/directory/of/local/repo$ git remote add origin <TARGET>
```

where TARGET can be for example:
/path/to/directory/of/$SERVER (e.g. if Remote-Repo is locally mounted)
ssh://user@$SERVER/path/of/remote

## Step 3: Push your commits

```
CLIENT:/VerzeichnisDesLokalenProjekts$ git push origin master
```