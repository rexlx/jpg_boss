# jpg_boss
organize photos by year with python. requires the pillow module. to install:

```$ python -m pip install pillow```

works on windows *(tested with python 3.7.2)* and linux *(tested on fedora python 2.7.15 and 3.7.3)* not tested on mac.

**ON LINUX**
```$ python jpg_boss.py -t -s /home/rxlx/Pictures/ -d /home/rxlx/Mstor/Pictures/ -b /home/rxlx/Mstor/Pictures/loose/```

**ON WINDOWS**
```E:\bin\scripts>python jpg_boss.py -t -s "E:\TEMP\src\\" -d "E:\TEMP\dst\\" -b "E:\Pictures\loose\\"```

```
$ python jpg_boss.py -h
usage: jpg_boss.py [-h] [-t] [-s SOURCE] [-d DEST] [-b BDIR] [-v VDIR]
                   [-l LOGFILE]

This script organizes photos by year

optional arguments:
  -h, --help  show this help message and exit
  -t          dry run, output to log file
  -s SOURCE   source dir
  -d DEST     destination dir
  -b BDIR     dir to store images without year data
  -v VDIR     dir to store videos in
  -l LOGFILE
```
