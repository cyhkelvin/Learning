# vim

## shortcut
 - V (select) -> zf (first define area to be zipped) -> zo (open zipped lines) -> zc (close zipped lines)
 - ctrl + v (mutli-adjacent-line select) -> shift i (insert) -> esc (close insert mode and insert words in all selected lines)
 - v (select) -> y (copy) -> d (cut) -> p (paste)

## command
 - :set mouse=a 命令、輸入、導航都啟用滑鼠的使用

## package
 - manually install package [ref](https://danishpraka.sh/2018/06/09/vim-plugin-install.html)

## vimrc setting
```
write infomation in vimrc (set runtime path and source plugin file)
:set rtp+=~/.vim/plugins/vimport
:source ~/vim/plugins/vimport/plugins/vimport.vim
```
 - use personal vimrc  `vim -u vimrc_personal <text file>`
 - automatically start package from start: write `autocmd vimenter * NERDTree` in vimrc