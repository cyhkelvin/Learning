# shell


## file header
1. `# -*- coding: utf-8 -*-`
2. `#!/bin/bash` 
3. `#!/usr/bin/python`

## ssh to server
 - remotecommand -rcfile (for setting environment with given .bashrc)

## open gnome terminal
 - gnome-terminal \-\- \<command\> (\-\-working-directory=\<path\>)
    **開新 terminal 並執行指令**

## commands
 - `unset variable`
 - `comm file1 file2 > file3` (-1 except f1, -2 except f2, -3 except both)
 - `unix2dos<${unix_file}|iconv -f UTF-8 -t UTF-16 >${dos_file}`
 - `trap 'rm -rf "$tmpdir"' EXIT (similar try catch)`
 - `ps -a` and `ps aux`
 - `est -e` Exit immediately if a command exits with a non-zero status.
 - date_var=$(date +%Y%m%d)
 - [ps command](https://www.uj5u.com/caozuo/254249.html)
 - [ubuntu system cmds](https://jasminmin.com/2019-05-03-ubuntu-commands/)
### tar 
1. tar zcvf \<file_name\>.tar.gz -C \<execute_path\> \<dir_name\> 
   (tar:打包, gz:壓縮, 將\<execute_path\>/\<dir_name\> 壓縮在 file 裡，以後解壓縮直接是 \<dir_name\> 不會變成是絕對路徑)
2. extract or unzip specific file [ref](https://hamisme.blogspot.com/2013/08/tar.html)
3. tar -tf \<tar file\> 用來檢視僅打包的 .tar 檔案內容 [ref](https://terryl.in/zh/linux-tar-command/)
4. 分割 tar 檔案`split -b 100MB demo.tar "demo_part_"`
5. 結合並解開 tar `cat demo_part_* | tar -zxvf -` [ref](https://www.jinnsblog.com/2018/03/linux-tar-and-split-cat-example.html)
### chmod and find
 since it needs to be r+w for user to browse folders but read files only
 - find <path> -type d -exec chmod 544 {} + \\;  
 [reference of exec](https://unix.stackexchange.com/questions/12902/how-to-run-find-exec)
 - find <path> -type f -exec chmod 444 {} + \\; 

## scripting skills
  - [append array](https://linuxhint.com/bash_append_array/)
    - array  arrVar=("AC" "TV" "Mobile" "Fridge" "Oven" "Blender")
    - append  arrVar+=("Dish Washer") or arrVar=(${arrVar[@]} "Jack Fruit") arrVar=(${arrVar1[@]} ${arrVar2[@]})
    - loop array  
        ```
        # 由這個例子可以知道 base array 裡面是可以包含空白字符的
        for value in "${arrVar[@]}"
        do
            echo $value
        done
        ```
  - for i in {1..10..2}; do echo i; done
  - for ((i=1;i<=10;i+=1)); do echo i; done
  - if []; then {action};fi
