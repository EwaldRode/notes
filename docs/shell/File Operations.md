# File operations

## find and delete empty directories 
```bash
find /path/to/folder -type d --empty -delete
```

## move and merge directories
```bash
rsync -a --remove-source-files /source/directory/ /target/directory/
```