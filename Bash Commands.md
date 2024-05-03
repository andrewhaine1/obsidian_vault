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
