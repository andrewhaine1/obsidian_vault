Show what's consuming disk space
```
du -cha --max-depth=1 / | grep -E "M|G"
```
```
du -cha --max-depth=1 /var/lib/docker | grep -E "M|G"
```

Delete all folders in dir except 2
```
ls | grep -v -e live -e stream | xargs sudo rm -rf
```
List folders newest first
```
ls -t
```
or
```
ll -t
```
List all folders from December
```
ls -lt | awk '$6 == "Dec" && $7 >=01 && $7 <= 31 {print $9}'
```

Delete all folders from December
```
ls -lt | awk '$6 == "Dec" && $7 >=01 && $7 <= 31 {print $9}' | xargs sudo rm -rf
```
Find largest 10 directories
```
du -a /var | sort -n -r | head -n 10
```

find file and silence errors
```
find / -type f -name sqlpackage 2>/dev/null
```

To create a new symlink (will fail if symlink exists already):
```
ln -s /path/to/file /path/to/symlink
```

To create or update a symlink:
```
ln -sf /path/to/file /path/to/symlink
```
List directory contents - biggest first
```
du -sh * | sort -hr
```
