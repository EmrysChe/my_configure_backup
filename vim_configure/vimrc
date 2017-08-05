" All system-wide defaults are set in $VIMRUNTIME/debian.vim and sourced by
" the call to :runtime you can find below.  If you wish to change any of those
" settings, you should do it in this file (/etc/vim/vimrc), since debian.vim
" will be overwritten everytime an upgrade of the vim packages is performed.
" It is recommended to make changes after sourcing debian.vim since it alters
" the value of the 'compatible' option.

" This line should not be removed as it ensures that various options are
" properly set to work with the Vim-related packages available in Debian.
runtime! debian.vim

" Uncomment the next line to make Vim more Vi-compatible
" NOTE: debian.vim sets 'nocompatible'.  Setting 'compatible' changes numerous
" options, so any other options should be set AFTER setting 'compatible'.
"set compatible

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
if has("syntax")
  syntax on
endif

" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
"set background=dark

" Uncomment the following to have Vim jump to the last position when
" reopening a file
"if has("autocmd")
"  au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif
"endif

" Uncomment the following to have Vim load indentation rules and plugins
" according to the detected filetype.
"if has("autocmd")
"  filetype plugin indent on
"endif

" The following are commented out as they cause vim to behave a lot
" differently from regular Vi. They are highly recommended though.
"set showcmd		" Show (partial) command in status line.
"set showmatch		" Show matching brackets.
"set ignorecase		" Do case insensitive matching
"set smartcase		" Do smart case matching
"set incsearch		" Incremental search
"set autowrite		" Automatically save before commands like :next and :make
"set hidden		" Hide buffers when they are abandoned
"set mouse=a		" Enable mouse usage (all modes)

" Source a global configuration file if available
if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif
"新建.c,.h,.sh,.java文件，自动插入文件头
autocmd BufNewFile *.cpp,*.[ch],*.sh exec ":call SetTitle()"
""定义函数SetTitle，自动插入文件头
function! SetTitle()
	"如果文件类型为.sh文件
	if &filetype == 'sh'
		call setline(1,"\##################################################")
		call append(line("."), "\# Filename: ".expand("%"))
		call append(line(".")+1, "\# Author: Emrys")
		call append(line(".")+2, "\# E-mail: emrysche@qq.com")
		call append(line(".")+3, "\# Created Time: ".strftime("%c"))
		call append(line(".")+4, "\##################################################")
		call append(line(".")+5, "\#!/bin/bash")
		call append(line(".")+6, "")
	endif

	if &filetype == 'c'
		call setline(1, "/*")
		call append(line("."), " * ==================================================")
		call append(line(".")+1, " *")
		call append(line(".")+2, " *Filename:  ".expand("%"))
		call append(line(".")+3, " *")
		call append(line(".")+4, " *Description:  ")
		call append(line(".")+5, " *")
		call append(line(".")+6, " *Version:   0.01")
		call append(line(".")+7, " *Created:   ".strftime("%c"))
		call append(line(".")+8, " *Author:    Emrys")
		call append(line(".")+9, " *E-mail:    emrysche@qq.com")
		call append(line(".")+10, " *")
		call append(line(".")+11, " * ==================================================")
		call append(line(".")+12, " */")
		call append(line(".")+13, "#include <stdio.h>")
		call append(line(".")+14, "")
		call append(line(".")+15, "int main()")
		call append(line(".")+16, "{")
		call append(line(".")+17, "	return 0;")
		call append(line(".")+18, "}")
	endif
	if &filetype == 'cpp'
		call setline(1, "/*")
		call append(line("."), " * ==================================================")
		call append(line(".")+1, " *")
		call append(line(".")+2, " *Filename:  ".expand("%"))
		call append(line(".")+3, " *")
		call append(line(".")+4, " *Description:  ")
		call append(line(".")+5, " *")
		call append(line(".")+6, " *Version:   0.01")
		call append(line(".")+7, " *Created:   ".strftime("%c"))
		call append(line(".")+8, " *Author:    Emrys")
		call append(line(".")+9, " *E-mail:    emrysche@qq.com")
		call append(line(".")+10, " *")
		call append(line(".")+11, " * ==================================================")
		call append(line(".")+12, " */")
		call append(line(".")+13, "#include <iostream>")
		call append(line(".")+14, "using namespace std;")
		call append(line(".")+15, "int main()")
		call append(line(".")+16, "{")
		call append(line(".")+17, "	return 0;")
		call append(line(".")+18, "}")
	endif
	"新建文件后，自动定位到文件末尾
	autocmd BufNewFile * normal G

endfunction

set autoindent
set tabstop=4
set softtabstop=4
set shiftwidth=4
set smarttab
" 显示行号
set number

:inoremap ( ()<ESC>i
:inoremap ) <c-r>=ClosePair(')')<CR>
:inoremap { {<CR>}<ESC>O
:inoremap } <c-r>=ClosePair('}')<CR>
:inoremap [ []<ESC>i
:inoremap ] <c-r>=ClosePair(']')<CR>
:inoremap " ""<ESC>i
:inoremap ' ''<ESC>i
function! ClosePair(char)
    if getline('.')[col('.') - 1] == a:char
        return "\<Right>"
    else
        return a:char
    endif
endfunction
filetype plugin indent on 
