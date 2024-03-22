# Copy whole repository

## Add new remote
```bash
git remote add gitlab git@new_git_adress.git
```
## fetch all
```bash
git fetch origin  --all
```
## Track checkout and track all remote branches
### Linux
Optional: Filter for master and Head
```bash
for remote in $(git branch -r | grep -v master | grep -v HEAD); do git checkout --track $remote ; done
```
### Windows
Substring(2) filters unwanted whitespace. Remove if necessary 
```powershell
$remotes=git branch -r
forEach($remote in $remotes){git checkout --track $remote.Substring(2)}
```
## push all commits
```bash
git push --all gitlab
```
## push all tags
```bash
git push --tags gitlab
```
## remove old remote repository
```bash
git remote remove origin
```
## rename new remote repository 
```bash
git remote rename gitlab origin
```