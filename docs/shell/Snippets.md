## execute command, detach it from console, and redirect output to null/void:
```bash
nohup command >/dev/null 2>&1 &
```

## execute command, endless command and detach it
```bash
nohup sh -c 'while true; do ./.....; done' &
```

## remove duplicate lines from file
```bash
awk '!seen[$0]++' /path/to/file
```

## generate a ssh key
```bash
ssh-keygen -b 4096 -t rsa -C first.last@company.com
```