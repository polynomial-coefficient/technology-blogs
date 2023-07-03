neovim配置文件位置: ~/.config/nvim/init.vim

<hr>

``````

" 隐藏空格and回车符号
set nolist

" 忽略大小写
set ic    

" 高亮当前行
set cursorline

" 高亮当前列
set cursorcolumn                
highlight CursorLine   cterm=NONE ctermbg=NONE ctermfg=white guibg=NONE guifg=NONE
highlight CursorColumn cterm=NONE ctermbg=NONE ctermfg=white guibg=NONE guifg=NONE
  
" Pmenu :所有项的配色,PmenuSel:选中项的配色
" guibg / guifg 分别对应背景色/前景色
highlight Pmenu guibg=#b0b8a3
highlight PmenuSel ctermfg=7 ctermbg=4 guibg=#101f42 guifg=#ffffff

"显示文件名：总行数，总的字符数
set statusline=[%F]%y%r%m%*%=[Line:%l/%L,Column:%c][%p%%] 

" 关闭兼容旧版本vi模式
set nocompatible              

" 自动保存,防止突发情况致使内容丢失,如断电时
set autowriteall

" 每五秒自动将内容输出至swpfile
set updatetime=5000

" 必须
filetype off      

" 搜索模式里忽略大小写
set ignorecase 

" 如果搜索模式包含大写字符,不使用 'ignorecase' 选项.只有在输入搜索模式并且打开 'ignorecase' 选项时才会使用.
"set smartcase 

" 设置自动对齐(缩进):即每行的缩进值与上一行相等; 使用 noautoindent 取消设置
set autoindent 

" 智能对齐方式
"set smartindent 

" 设置制表符(tab键)的宽度
set tabstop=4 

" 设置软制表符的宽度
set softtabstop=4 

"(自动)缩进使用的4个空格
set shiftwidth=4 
set cindent " 使用 C/C++ 语言的自动缩进方式
set cinoptions={0,1s,t0,n-2,p2s,(03s,=.5s,>1s,=1s,:1s "设置C/C++语言的具体缩进方式
"set backspace=2 " 设置退格键可用

" 设置匹配模式,显示匹配的括号
set showmatch 

" 整词换行
set linebreak 

" 光标从行首和行末时可以跳到另一行去
set whichwrap=b,s,<,>,[,] 
"set hidden " Hide buffers when they are abandoned

" 启用鼠标
set mouse=a 

"显示行号
set number 

" 标识预览窗口
"set previewwindow   

"状态行设置
set laststatus=2 

"标尺,用于显示光标位置的行号和列号,逗号分隔.每个窗口都有自己的标尺.如果窗口有状态行,标尺在那里显示.否则,它显示在屏幕的最后一行上
set ruler 

" 命令行显示输入的命令
set showcmd 

" 命令行显示vim当前模式
set showmode 

" 输入搜索内容就显示搜索结果
set incsearch 

" 搜索时高亮匹配内容
set hlsearch

if has("syntax")
" 语法高亮
syntax on 
endif

" elflord ron peachpuff default 设置配色方案,vim自带的配色方案保存在/usr/share/vim/vim72/colors目录下
colorscheme ron 

" detect file type
filetype on

" If using a dark background within the editing area and syntax highlighting turn on this option as well
set background=dark


"创建某些类型的文件时,自动添加一些内容
"注意此处的文件类型(*.*,*.*)之间不能有空格
autocmd BufNewFile,BufRead *.h,*.c,*.cpp,*.cc exec ":call SetTitle()" 

""定义函数SetTitle，自动插入文件头 
func SetTitle() 
if expand("%:e")== 'c'
    call setline(1,"#include<stdio.h>")
    call append(line("."),   "#include<stdlib.h>")
    call append(line(".")+1, "#include<string.h>")
    call append(line(".")+2, "")
    call append(line(".")+3, "")
    call append(line(".")+4, "int main(int argc, char *argv){ ")
    call append(line(".")+5, "")
    call append(line(".")+6, "")
    call append(line(".")+7, "    return 0;")
    call append(line(".")+8, "}")
    call append(line(".")+9, "")
endif

if expand("%:e")== 'cpp'
    call setline(1,"#include<iostream>")
    call append(line("."),   "#include<string>")
    call append(line(".")+1, "#include<fstream>")
    call append(line(".")+2, "using namespace std;")
    call append(line(".")+3, "")
    call append(line(".")+4, "")
    call append(line(".")+5, "int main(int argc, char *argv){ ")
    call append(line(".")+6, "")
    call append(line(".")+7, "")
    call append(line(".")+8, "    return 0;")
    call append(line(".")+9, "}")
    call append(line(".")+10, "")
endif

if expand("%:e")== 'cc'
    call setline(1,"#include<iostream>")
    call append(line("."),   "#include<string>")
    call append(line(".")+1, "#include<fstream>")
    call append(line(".")+2, "using namespace std;")
    call append(line(".")+3, "")
    call append(line(".")+4, "")
    call append(line(".")+5, "int main(int argc, char *argv){ ")
    call append(line(".")+6, "")
    call append(line(".")+7, "")
    call append(line(".")+8, "    return 0;")
    call append(line(".")+9, "}")
    call append(line(".")+10, "")
endif

if expand("%:e")== 'h'
    call setline(1,"#ifndef __".expand("%:r")."_H__")
    call append(line("."),"#define __".expand("%:r")."_H__")
    call append(line(".")+1, "")
    call append(line(".")+2, "")
    call append(line(".")+3, "")
    call append(line(".")+4, "")
    call append(line(".")+5, "")
    call append(line(".")+6, "")
    call append(line(".")+7, "#enif")
endif

"新建文件后，自动定位到文件末尾
"autocmd BufNewFile * normal G
endfunc 


"补全括号和花括号（换行四次）   
":inoremap ( ()<ESC>i
":inoremap ) <c-r>=ClosePair(')')<CR>

:inoremap { {<CR>}<ESC>O
":inoremap } <c-r>=ClosePair('}')<CR>

":inoremap [ []<ESC>i
":inoremap ] <c-r>=ClosePair(']')<CR>

:inoremap " ""<ESC>i
:inoremap ' ''<ESC>i

``````