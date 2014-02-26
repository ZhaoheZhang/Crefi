
#Crefi 
Crefi is a Python command-line tool to create files and do file operations on created data.
It provides basic operations to create files of differrent
sizes, in different layout, along with other options.

Typical use involves creating large number of files of different sizes,
over different layout.

####Following are the different options available in crefi.py

  | Options      |Descriptions|
  | -------------| ------------------------------------------------|
  |-n FILES      |    number of files in each level [default: 100] |
  |--size = SIZE |  size of the files to be used [default: 100k] |
  |--random      | random size of the file between --min and --max [default: True] default random sizes of the files will be between 10k and 500K.Options --max and --min option are used with only this option.|
  | --max = MAX  |maximum size of the files, if random is True [default: 500K]|
  |--min = MIN   |minimum size of the files, if random is True [default: 10K]|
  |--single      |create files in single given directory [default: True]|
  |--multi       |create files in multiple directories.This option is used to create files in different directory layouts. There can be different types of directory layouts, but right now, the tool supports rectangular layout with given breadth and depth. In each directory it create -n number of files. Total number of files created with muclti options will be , No of files = n * b * d|
  |-b BRDTH      | number of directories in one level [default: 5]|
  |-d DEPTH      |number of levels of directories [default: 5]
  |-l FLEN       | number of bytes for filename [default: 10]. First 10 bytes will be current time, next bytes will be the value given. Default value will be 10 bytes. If no value is given, all the filenames will be of 10+10=20 bytes. Otherwise it will be (10+ l)bytes.|
  |-t --type     | type of the file to be created.(text, sparse, binary). |
  |-I INTER      | print number files created of interval. [defailt: 100] |
  |--fop = FOP   | fop to be performed on the files (create, rename, chmod, chown, chgrp, symlink, hardlink, truncate) [default:create] |
  |  -R          | To disable random file name [default: Enabled] |

####EXAMPLES:
####
  ```python crefi.py MNT_PT```

            Creates 100 text files in the directory MNT_PT of random size
            between 10K and 500K [Filename length will be 20 bytes
            first 10 bytes will be current time, next 10 bytes will be
            combination of letters(A-Z) and numbers(1-9)]
####
  ```python crefi.py --multi -b 10 -d 10 -n 1000 --type=sparse --size=100 MNT_PT```

            Create files in directory MNT_PT in the directory
            layout of 10 directories in each level, and 10 directories
            depth and in each directory, create 1000 sparse files of size 100K.