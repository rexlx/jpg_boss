# jpg_boss
organize photos by year with python. requires the pillow module. to install:

```$ python -m pip install --user pillow```

works on windows *(tested with python 3.7.2)* and linux *(tested on fedora python 2.7.15 and 3.7.3)* not tested on mac.

# Usage
```
$ python jpg_boss.py -h
usage: jpg_boss.py [-h] [-t] [-s SOURCE] [-d DEST] [-b BDIR] [-v VDIR]
                   [-l LOGFILE] [-n] [-k]

This script organizes photos by year

optional arguments:
  -h, --help  show this help message and exit
  -t          dry run, output to log file
  -s SOURCE   source dir
  -d DEST     destination dir
  -b BDIR     dir to store images without year data
  -v VDIR     dir to store videos in
  -l LOGFILE
  -n          do not make directories for months
  -k          dont remove files from source dir
```

# Command Examples
1. dry run(-t) with source(-s), destination(-d), and bastard directory(-b) arguments. The bastard directory is for jpgs that do not have metadata and cannot therefore be organized. It will create the target directories if they dont exist and further organize the photos by month. All source files will be removed in this example. Simply remove the -t to run for real.<br/><br/>

**ON LINUX**<br/>
```$ python jpg_boss.py -t -s /home/rxlx/Pictures/ -d /home/rxlx/Mstor/Pictures/ -b /home/rxlx/Mstor/Pictures/loose/```

**ON WINDOWS** (on windows the paths can get kind of tricky, i suggest always doing a dry run first :) )<br/>
```>python jpg_boss.py -t -s "E:\TEMP\src\\" -d "E:\TEMP\dst\\" -b "E:\Pictures\loose\\"```

2. dry run with the keep at source(-k) and no month(-n) args, followed by source, destination, bastard and video directory(-v) args. this will copy the files to the new destination instead of removing them from the source. the no month option will only create the year directory at the target destination ( so all photos will be in say 2019/ instead of 2019/May, 2019/Jan ...etc)<br/>
```
$ python jpg_boss.py -tkn -s /home/rxlx/Pictures/ -d /storage/Pictures/ -b /storage/Pictures/loose/ -v /home/rxlx/Mstor/Videos/
```

## I dont like all those args id rather edit the script...
thats cool, here's how you do it. using you're second favorite text editor, open the file and look for these lines:
```
# --USER--VARIABLES-- #
home = os.path.expanduser("~")
user_vdir = os.path.join(home, 'Videos')
user_source = os.path.join(home, 'Pictures')
user_bdir = os.path.join(user_source, 'loose')
user_dest = os.path.join(user_source, 'Phone')
test_file = 'jpg_boss_dryrun.txt'
# --USER--VARIABLES-- #
```

**DONT** modify the variable names, just their values. options -tkn will still work as intended, now you just dont need -sdbv

# System Impacts
are minimal, here are some real world cases:
```
results of moving about 15.5 GiB around using this tool in various scenarios

HDD on linux: (same disk for source and dest)
--------------------------------------------------------------------------------
found 3858 jpgs, 2 pngs, 0 mp4s, and the following other types:
13 .jpeg 1 .gif 7 .dng

took 315.18 seconds

SDD on linux: (same disk for source and dest)
--------------------------------------------------------------------------------
found 3858 jpgs, 2 pngs, 0 mp4s, and the following other types:
13 .jpeg 1 .gif 7 .dng

took 104.04 seconds


SSD on windows: (same disk for source and dest)
--------------------------------------------------------------------------------
found 3858 jpgs, 2 pngs, 0 mp4s, and the following other types:
1 .gif 13 .jpeg 7 .dng

took 125.79 seconds

SSD as source to usb3 flash drive as destination on windows (with keep files at
source option)
--------------------------------------------------------------------------------
found 3858 jpgs, 2 pngs, 0 mp4s, and the following other types:
1 .gif 7 .dng 13 .jpeg

took 572.86 seconds
```
