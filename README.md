# AES Crypt brute force tool (multithread)

> This is a branch of the soure repository for the AES Crypt software available from www.aescrypt.com
> Forked from https://github.com/paulej/AESCrypt

### About

AES Crypt file format brute force tool with multithread support (ncpu), works only for Linux, file loaded once into memory to speed up tool.

Input dictionary of possible passwords must be zero determinated text file:
```
123465
111111
qwerty
```

#### Usage:
Compile:
```
autoreconf -ivf
./configure
make
```
Run example:
```
./src/aescrypt -b <in_file.aes> <in_dict.txt>
```

Bash script for iterate over many dicts:

```bash
#!/bin/bash

FILES=`ls ./dicts`
for f in $FILES
do
    echo "Processing dict: $f"
    ./aescrypt -b <in_file.aes> <dict_directory>/$f"
    RESULT=$?
    if [ $RESULT -eq 0 ]; then
        echo "PASSWORD FOUND!"
        exit
    fi
done
```
