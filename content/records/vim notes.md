---
title: vim notes
date: 2024-03-15
description: "Vim settings and notes."
tags: tools
---

Vim settings and notes.

1. Swapping Esc with Caps
	-  Mac OS [Karabiner-Elements (pqrs.org)](https://karabiner-elements.pqrs.org/)
1. Key bindings I use
	1. `cw` to change current word in insert mode
	2. `jk` move cursor to end of line in insert mode
	3. `kj` move cursor to beginning of line in insert mode
	4. `K` == `C` in normal mode
	5. swap gj/j and gk/k in normal mode
	6. swap v and ctr-v in normal mode
	7. ctr-y yank to system clipboard (though I am hating this setting in obsidian now)

vimrc
---

```
" absolute number for current line and relavetive numbers for everywhere else
set nu rnu

set updatetime=150
" map jj, kk, jk, kj to backspace in insert mode
imap cw <Esc>ciw
imap jk <Esc>A
imap kj <Esc>I

" swap gj/gk and j/k
nnoremap j gj
nnoremap gj j
nnoremap k gk
nnoremap gk k

" Ctrl+y to yank to system clipboard under visual mode
vnoremap <C-y> "+y

syntax enable
syntax on

" cursors
set cursorline
set cursorcolumn
" steady block for visual mode, bar for insert
let &t_SI = "\e[6 q"
let &t_EI = "\e[2 q"

" don't let cursor go below the last 5 lines
set scrolloff=5

" fix tab behaviors
filetype plugin indent on
" show existing tab with 4 spaces width
set tabstop=4
" when indenting with '>', use 4 spaces width
set shiftwidth=4
" On pressing tab, insert 4 spaces
set expandtab

" incrementally highlight as searchring
set incsearch
" case smart insensitive search, still check caps if explicity search caps
set ignorecase smartcase

"intall plug-ins with vim-plug
call plug#begin()
Plug 'morhetz/gruvbox'
call plug#end()

" comment out these 2 lines for the first time
" run :PlugInstall in vimrc and remove comment
autocmd vimenter * nested colorscheme gruvbox
set bg=dark
```