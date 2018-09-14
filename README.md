# BTRFS Disk Usage check with basic system dependencies.

Simple btrfs disk usage check with minimal dependancies (btrfs tools, bash, optional numfmt).

```
$ ./check_disk_btrfs --help
usage: ./check_disk_btrfs [options...] <mount point>
check_disk_btrfs plugin
https://github.com/koshatul/check_disk_btrfs

Usage: ./check_disk_btrfs <options>
  -s            Use sudo
  -w <warn>     Percent free to trigger warning (default 10)
  -c <crit>     Percent free to trigger critical (default 5)
```

Example:
```
$ ./check_disk_btrfs /data -s
OK - /data 252.94G (99%) Free /data = 3.07G;252.94G;256.00G | /data=136867835904;1019904;274877906944;3288334336;0;1
$ echo $?
0
```

Example Warning Output:
```
$ ./check_disk_btrfs /data -s -w 100
WARNING - /data 252.94G (99%) Free /data = 3.07G;252.94G;256.00G | /data=136867835904;1019904;274877906944;3288334336;0;1
$ echo $?
1
```

Example Critical Output:
```
$ ./check_disk_btrfs /data -s -c 100
CRITICAL - /data 252.94G (99%) Free /data = 3.07G;252.94G;256.00G | /data=136867835904;1019904;274877906944;3288334336;0;1
$ echo $?
2
```
