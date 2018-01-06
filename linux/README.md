# Linux useful commands Cheatsheet

## chmod 666 / 777 recursively

You can use this to chmod files and directories differently:

for folders(directories):

    find . -type d -exec chmod 777 {} \;

for files:

    find . -type f -exec chmod 666 {} \;
    
## Search for File contents

```
grep -l -i searchtext *.txt
```
```
grep -l -i -r searchtext *
```
```
find . -type f -name *.txt -exec grep -l -i searchtext '{}' \;
```

## Find open ports and applications with netstat and lsof

```
netstat -npl
```
```
lsof -i | grep -e LISTEN
```

## Delete Directories with same name recursively (e.g. ".svn")

```
find . -type d -name ".svn" -exec rm -rf {} \;
```

