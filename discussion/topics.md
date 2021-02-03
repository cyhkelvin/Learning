# topics
1 python
2 terminal

## python
1. six: compatible python2 and python3
2. mpdb (python command line debugger)
3. with open 
    equal to try: open(f) finally: if f: f.close()
4. a(str_list) b(str_tuple) `c = [*a, *b]` (have all elements from a and b)
5. set_A.difference(set_B) for (A - B)
6. @staticmethod [ref](https://openhome.cc/Gossip/Python/StaticClassMethod.html)
7. lambda function
8. filter(), map(), zip(), reduce()
9. [subprocess](https://www.itread01.com/content/1548457405.html)
10. [singleton](https://hackmd.io/P-tOlvwjSGaoVLVC6QFX3Q) ※包含 \_\_init\_\_, \_\_new\_\_ 的差別等等
11. expanduser() 處理路徑中 '~' 字符, splitext() 分離路徑中副檔名
### useful packages
1. pytest and flake8
2. re
3. pytube3
4. [enum package](https://blog.louie.lu/2017/08/02/%E4%BD%A0%E6%89%80%E4%B8%8D%E7%9F%A5%E9%81%93%E7%9A%84-python-%E6%A8%99%E6%BA%96%E5%87%BD%E5%BC%8F%E5%BA%AB%E7%94%A8%E6%B3%95-07-enum/) build up variable types
5. [opencc](https://github.com/BYVoid/OpenCC)
6. (有什麼想學的 python package 再加入)
### config, yaml, json, pkl, textgrid
 - configobj configparser (讀取 .ini)
### matplotlib, seaborn
 - matplotlib [cmap](https://matplotlib.org/3.1.0/tutorials/colors/colormaps.html), [heatmap](https://matplotlib.org/3.1.1/gallery/images_contours_and_fields/image_annotated_heatmap.html)
 - seaborn [heapmap](http://seaborn.pydata.org/generated/seaborn.heatmap.html?highlight=s)
### encoding
 - chinese words encoding:
    https://kknews.cc/tech/g252r48.html
    https://blog.miniasp.com/post/2019/01/02/Common-Regex-patterns-for-Unicode-characters
 - str.encode('unicode-escape') # print out unicode of string
### jupyter
 - jupyterlab 切視窗: ctrl+shift+\[(切到左方分頁)或\](切到右方分頁)
 - jupyternote cell m for markdown, y for code, esc for escape


## terminal
1. https://jasminmin.com/2019-05-03-ubuntu-commands/
2. `unset variable`
3. `comm file1 file2 > file3` (-1 except f1, -2 except f2, -3 except both)
4. `unix2dos<${unix_file}|iconv -f UTF-8 -t UTF-16 >${dos_file}`
5. `trap 'rm -rf "$tmpdir"' EXIT (similar try catch)`
6. `ps -a` and `ps aux`
7. `est -e` Exit immediately if a command exits with a non-zero status.
### file header(keyword for searching: shebang)
1. `# -*- coding: utf-8 -*-`
2. `#!/bin/bash` 
3. `#!/usr/bin/python`
### bash
1. [append array](https://linuxhint.com/bash_append_array/)
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
### tar
1. tar zcvf \<file_name\>.tar.gz -C \<execute_path\> \<dir_name\> 
   (tar:打包, gz:壓縮, 將\<execute_path\>/\<dir_name\> 壓縮在 file 裡，以後解壓縮直接是 \<dir_name\> 不會變成是絕對路徑)
2. extract or unzip specific file [ref](https://hamisme.blogspot.com/2013/08/tar.html)
3. tar -tf \<tar file\> 用來檢視僅打包的 .tar 檔案內容 [ref](https://terryl.in/zh/linux-tar-command/)
4. 分割 tar 檔案`split -b 100MB demo.tar "demo_part_"`
5. 結合並解開 tar `cat demo_part_* | tar -zxvf -` [ref](https://www.jinnsblog.com/2018/03/linux-tar-and-split-cat-example.html)
### awk, sed, gawk
1. gsub(pattern_to_replace, patter_tobe_replace, object)
2. -F, --field-separator

