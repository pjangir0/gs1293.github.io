<p align="center">
  <b>
  <font size="+2">vimrc</font>
  </b>
</p>

---

```vim

" Use Vim settings, rather then Vi settings (much better!).
" This must be first, because it changes other options as a side effect.
set nocompatible

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" Plugin Settings

filetype off                  " required

set rtp+=~/.vim/bundle/Vundle.vim
set rtp+=~/.fzf

" Functions list
source ~/.vim/myfunctions/Block.vim
source ~/.vim/myfunctions/Pipeline.vim
source ~/.vim/myfunctions/Always.vim

call vundle#begin()

Plugin 'VundleVim/Vundle.vim'                   " PluginInstall/Clean/Update
Plugin 'tpope/vim-commentary'                   " gc{motion}
Plugin 'godlygeek/tabular'                      " :Tab /{delimiter}
Plugin 'junegunn/vim-easy-align'                " ga{motion}{delimiter} : use <C-x> to use any delimiter
Plugin 'vim-syntastic/syntastic'                " :SyntasticCheck, :SyntasticInfo
Plugin 'ctrlpvim/ctrlp.vim'                     " <C-p> filename
Plugin 'tpope/vim-surround'                     " cs{old identifier}{new identifier}
Plugin 'flazz/vim-colorschemes'                 " :colorscheme <scheme>
Plugin 'tpope/vim-vinegar'                      " - , enhancing netrw
Plugin 'raimondi/delimitmate'                   " automatically create bracket pairs in insert mode
Plugin 'haya14busa/incsearch.vim'               " highlight all matching text while searching
Plugin 'Yggdroot/indentLine'                    " creates dotted lines to show code indentation
Plugin 'vim-scripts/VisIncr'                    " :I <increment>
Plugin 'terryma/vim-multiple-cursors'           " <C-n> to select multiple cursors
Plugin 'easymotion/vim-easymotion'              " [y|d|c]<leader><leader>{motion}{identifier}
Plugin 'luochen1990/rainbow'                    " Use different colors for nested parantheses
Plugin 'cazador481/vim-systemverilog'           " verilog plugin
Plugin 'antoinemadec/vim-verilog-instance'      " gb{motion}
Plugin 'kana/vim-textobj-user'                  " use user defined text objects
Plugin 'adriaanzon/vim-textobj-matchit'         " use am/im textobjects for matchit pairs
Plugin 'troydm/zoomwintab.vim'                  " use <C-w><C-o> to zoom in/out current buffer
Plugin 'simeji/winresizer'                      " <C-e> + h/j/k/l to resize window
Plugin 'rhysd/clever-f.vim'                     " use f/F after f{char} instead of ;/, and t/T after t{char}
Plugin 'terryma/vim-expand-region'              " Press + to expand the visual selection and _ to shrink it
Plugin 'thiagoalessio/rainbow_levels.vim'       " text color based on indentation, default off, :RainbowToggle
Plugin 'mileszs/ack.vim'                        " sudo apt-get install ack-grep; use Ack! {pattern} {directory}; check ag.vim also
Plugin 'beloglazov/vim-online-thesaurus'        " search online thesaurus, use <leader>K
Plugin 'vim-scripts/YankRing.vim'               " save the yanked data, use p <c-p>/<c-n>
Plugin 'mhinz/vim-startify'                     " fancy start screen for vim
Plugin 'SirVer/ultisnips'
Plugin 'honza/vim-snippets'
Plugin 'matze/vim-move'                         " Highlight block then Alt+j/k, Currently only works in gvim
Plugin 'rhysd/accelerated-jk'                   " accelerate up-down moving using j/k
Plugin 'danro/rename.vim'                       " rename current file
Plugin 'junegunn/goyo.vim'                      " :Goyo , Distraction-free writing in Vim
Plugin 'junegunn/limelight.vim'                 " :Limelight, Hyperfocus-writing in Vim
Plugin 'tommcdo/vim-exchange'                   " cx{motion} Easy text exchange operator for Vim
Plugin 'francoiscabrol/ranger.vim'              " <leader>f opens ranger for file navigation
" Plugin 'chrisbra/NrrwRgn'                       " :NR :h NrrwRgn.txt
" Plugin 'dominikduda/vim_current_word'           " :VimCurrentWordToggle
" Plugin 'will133/vim-dirdiff'                    " diff recursively for directories
" Plugin 'mihais/vim-mark'
" Plugin 'Valloric/YouCompleteMe'                 " very problematic, find alternative

call vundle#end()            " required
filetype plugin indent on    " required

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" Plugin Options

runtime macros/matchit.vim

" Start interactive EasyAlign in visual mode (e.g. vipga)
xmap ga <Plug>(EasyAlign)

" Start interactive EasyAlign for a motion/text object (e.g. gaip)
nmap ga <Plug>(EasyAlign)

map /  <Plug>(incsearch-forward)
map ?  <Plug>(incsearch-backward)
map g/ <Plug>(incsearch-stay)

let g:rainbow_active = 1 "0 if you want to enable it later via :RainbowToggle

let g:clever_f_smart_case = 1 " clever-f uses smart case

let g:UltiSnipsExpandTrigger           = '<tab>'
let g:UltiSnipsJumpForwardTrigger      = '<tab>'
let g:UltiSnipsJumpBackwardTrigger     = '<s-tab>'
let g:ycm_key_list_select_completion   = ['<C-j>', '<C-n>', '<Down>']
let g:ycm_key_list_previous_completion = ['<C-k>', '<C-p>', '<Up>']

let g:ctrlp_show_hidden = 1

let g:rainbow_levels = [
    \{'ctermfg': 2, 'guifg': '#a6e22e'},
    \{'ctermfg': 6, 'guifg': '#66d9ef'},
    \{'ctermfg': 4, 'guifg': '#ae81ff'},
    \{'ctermfg': 5, 'guifg': '#f92672'},
    \{'ctermfg': 1, 'guifg': '#fd971f'},
    \{'ctermfg': 3, 'guifg': '#f4bf75'},
    \{'ctermfg': 7, 'guifg': '#f8f8f2'},
    \{'ctermfg': 0, 'guifg': '#75715e'}]

nmap j <Plug>(accelerated_jk_gj)
nmap k <Plug>(accelerated_jk_gk)

let g:nrrw_rgn_vert = 1

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" Keyboard Mappings

" Mapping the SPACE key as Leader key (Backslash is still the default leader)
map <space> <leader>
map <space><space> <leader><leader>

" To stop pressing shift for getting :
nnoremap ; :
vnoremap ; :

"Mapping to open explorer
nnoremap <leader>d :Vexplore!<cr>

" `gf` command open file under cursor in a new vertical split
nnoremap gf :vertical wincmd f<CR>

"Mapping to open ~/.vimrc
nnoremap <leader>ev :vsplit $MYVIMRC<cr>

"Mapping to source ~/.vimrc
nnoremap <leader>sv :source $MYVIMRC<cr> :noh<cr>

" Saving and Quitting vim files
nnoremap <leader>q :q<cr>
nnoremap <leader>w :w<cr>
nnoremap <leader>x :x<cr>

" nnoremap <leader>f <c-w>v:Startify<cr>

" For verilog code indentation
map <leader>, :Tab /,/l0r0<cr>
map <leader>; :Tab /;/l0r0<cr>
map <leader>= :Tab / = /l0r0<cr>
map <leader>< :Tab /<=/l1r1<cr>
map <leader>( :Tab /(/l1r0<cr>
map <leader>) :Tab /)/l0r0<cr>

" Mapping Ctrl+L to remove highlighting and redraw the screen (default functionality)
nnoremap <c-l> :nohl<cr><c-l>

" Center the screen on the highlighted search result
nnoremap n nzz
nnoremap N Nzz
nnoremap * *zz
nnoremap # #zz
nnoremap g* g*zz
nnoremap g# g#zz

" To go to start/end of current line
nnoremap H ^
nnoremap L $

" To repeat last macro faster
nnoremap Q @@

" Disabling arrow keys in Vim
" noremap <Up> <Nop>
" noremap <Down> <Nop>
" noremap <Left> <Nop>
" noremap <Right> <Nop>

" Mapping arrow keys for navigating splits
nnoremap <Up> <c-w>k
nnoremap <Down> <c-w>j
nnoremap <Left> <c-w>h
nnoremap <Right> <c-w>l

"Right align and Left align a visual block
xnoremap <silent> <leader>ar :s/\v%V(\s*)(\S*)(\s*)/\1\3\2/<cr> :noh<cr>
xnoremap <silent> <leader>al :s/\v%V(\s*)(\S*)(\s*)/\2\1\3/<cr> :noh<cr>

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" Basic Settings for Vim

" Always show status line
set laststatus=2

" Enable the use of mouse
set mouse+=a

" Remove the introduction message in Vim
set shortmess=I

" Enable syntax highlighting.
syntax on

" Automatically indent when adding a curly bracket, etc.
set smartindent

" Number of spaces inserted when <TAB> is pressed
set tabstop=8
set softtabstop=4
" Number of spaces used in Auto indentation
set shiftwidth=4
" <TAB>'s are converted to spaces
set expandtab

" Show line number and cursor position
set ruler

" Display normal mode commands as you type
set showcmd

" Show editing mode
set showmode

" Show file options above the command line
set wildmenu
set wildignorecase

" Highlight the current line and column
set cursorline
"set cursorcolumn

" Break lines so that words are not broken halfway, when using set wrap
"set wrap
"set linebreak

" Don't wrap lines by default
set nowrap

" Open vertical split on the right side of the current window
set splitbelow
set splitright

" Display network directory as tree type by default
let g:netrw_liststyle=3

" Open help topics on the right side vertical split
autocmd FileType help wincmd L

" Setting backspace to work as it should
set backspace=indent,eol,start

" Manging line numbers
set number relativenumber

augroup numbertoggle
    autocmd!
    autocmd BufEnter,FocusGained,InsertLeave * set relativenumber
    autocmd BufLeave,FocusLost,InsertEnter   * set norelativenumber
augroup END

" Set color scheme that I like.
if has("gui_running")
  colorscheme molokai_dark
else
  colorscheme molokai_dark
endif

" Search Settings
" Search as you type (incremental search)
set incsearch

" Highlight your Searches.
set hlsearch

" Case settings for searching.
set ignorecase
set smartcase

" Automatically cd into the directory in which the file is present
set autochdir

" To keep cursor at middle of the screen, remove if want to use <C-e>/<C-y> to scroll up/down
" set scrolloff=999

" Stop vim from rerendering the screen after every step of the macro, only rerender at the end
set lazyredraw

" Directories for swp files
set nobackup
set noswapfile

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" Statusline settings
function! InsertStatuslineColor(mode)
  if a:mode == 'i'
    hi statusline guibg=Cyan ctermfg=6 guifg=Black ctermbg=0
  elseif a:mode == 'r'
    hi statusline guibg=Purple ctermfg=5 guifg=Black ctermbg=0
  else
    hi statusline guibg=DarkRed ctermfg=1 guifg=Black ctermbg=0
  endif
endfunction

au InsertEnter * call InsertStatuslineColor(v:insertmode)
au InsertLeave * hi statusline guibg=DarkGrey ctermfg=8 guifg=White ctermbg=15

" default the statusline to green when entering Vim
hi statusline guibg=DarkGrey ctermfg=8 guifg=White ctermbg=15

" Formats the statusline
set statusline=%f                               " file name
set statusline+=[%{strlen(&fenc)?&fenc:'none'}, " file encoding
set statusline+=%{&ff}]                         " file format
set statusline+=%y                              " filetype
set statusline+=%h                              " help file flag
set statusline+=%m                              " modified flag
set statusline+=%r                              " read only flag

set statusline+=\ %=                                                " align left
set statusline+=Line:%l/%L[%p%%]                                    " line X of Y [percent of file]
set statusline+=\ Col:%c                                            " current column
set statusline+=\ Buf:%n                                            " Buffer number
set statusline+=\ [%b][0x%B]\                                       " ASCII and byte code under cursor
set statusline+=%{strftime(\"%l:%M:%S\ \%p,\ %a\ %b\ %d,\ %Y\")}    " Display time and date

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" Managing trailing whitespaces

highlight ExtraWhitespace ctermbg=red guibg=red
augroup WhitespaceMatch
  " Remove ALL autocommands for the WhitespaceMatch group.
  autocmd!
  autocmd BufWinEnter * let w:whitespace_match_number =
        \ matchadd('ExtraWhitespace', '\s\+$')
  autocmd InsertEnter * call s:ToggleWhitespaceMatch('i')
  autocmd InsertLeave * call s:ToggleWhitespaceMatch('n')
augroup END
function! s:ToggleWhitespaceMatch(mode)
  let pattern = (a:mode == 'i') ? '\s\+\%#\@<!$' : '\s\+$'
  if exists('w:whitespace_match_number')
    call matchdelete(w:whitespace_match_number)
    call matchadd('ExtraWhitespace', pattern, 10, w:whitespace_match_number)
  else
    " Something went wrong, try to be graceful.
    let w:whitespace_match_number =  matchadd('ExtraWhitespace', pattern)
  endif
endfunction

function! <SID>StripTrailingWhitespace()
    " Preparation: save last search, and cursor position.
    let _s=@/
    let l = line(".")
    let c = col(".")
    " Do the business:
    %s/\s\+$//e
    " Clean up: restore previous search history, and cursor position
    let @/=_s
    call cursor(l, c)
endfunction

autocmd BufWritePre,FileWritePre ?* silent :call <SID>StripTrailingWhitespace()

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" Folding settings

""To save and load folds automatically
"augroup filefolding
"    autocmd!
"    autocmd BufWinLeave ?* mkview
"    autocmd BufWinEnter ?* silent loadview
"    autocmd BufWinEnter ?* :normal zM
"augroup END

set foldclose=all      "close folds automatically when moving out of them
augroup filetype_vim
    autocmd!
    autocmd FileType vim setlocal foldmethod=marker
    autocmd FileType verilog* setlocal foldmethod=marker
augroup END

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" Searching the visually selected text using * or # from visual mode directly
xnoremap * :<C-u>call <SID>VSetSearch()<CR>/<C-R>=@/<CR><CR>
xnoremap # :<C-u>call <SID>VSetSearch()<CR>?<C-R>=@/<CR><CR>
function! s:VSetSearch()
    let temp = @s
    norm! gv"sy
    let @/ = '\V' . substitute(escape(@s, '/\'), '\n', '\\n', 'g')
    let @s = temp
endfunction

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" Leaving insert mode in terminal vim
" Fix for faster visual block mode in terminal vim
" When you’re pressing Escape to leave insert mode in the terminal, it will by
" default take a second or another keystroke to leave insert mode completely
" and update the statusline. This fixes that. I got this from:
" https://powerline.readthedocs.org/en/latest/tipstricks.html#vim
set timeout " Do time out on mappings and others
set timeoutlen=2000 " Wait {num} ms before timing out a mapping

if !has('gui_running')
    set ttimeoutlen=10
    augroup FastEscape
        autocmd!
        autocmd InsertEnter * set timeoutlen=0
        autocmd InsertLeave * set timeoutlen=1000
    augroup END
endif

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" RTL snippets : use :z<TAB>

command! Zalways    :-1r ~/.vim/mysnippets/always
command! Zdivider   :-1r ~/.vim/mysnippets/divider
command! Zmodule    :-1r ~/.vim/mysnippets/module
command! Zrow       :-1r ~/.vim/mysnippets/row
command! Zcolumn    :-1r ~/.vim/mysnippets/column
command! Zpipeline  :-1r ~/.vim/mysnippets/pipeline
command! Zpipeline2 :-1r ~/.vim/mysnippets/pipeline2
command! Zcomment   :-1r ~/.vim/mysnippets/comment
command! Zcase      :-1r ~/.vim/mysnippets/case
command! Zmem       :-1r ~/.vim/mysnippets/mem
command! Zdelay     :-1r ~/.vim/mysnippets/delay
command! Zminmax    :-1r ~/.vim/mysnippets/minmax
command! Zsram      :-1r ~/.vim/mysnippets/sram
command! Zcpp       :-1r ~/.vim/mysnippets/cpp

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

"Automatic Banner/Header genration
"Fix it to be more generic and autonomous
"Fix issue of cursor moving to date line when saving after sourcing vimrc
autocmd BufNewFile *.{c,cpp,v,py} silent :0r ~/.vim/mysnippets/header
autocmd BufNewFile *.{c,cpp,v,py} exe "1," . 8 . "g/File Name     :.*/s//File Name     : " .expand("%")
autocmd BufNewFile *.{c,cpp,v,py} exe "1," . 8 . "g/Creation Date :.*/s//Creation Date : " .strftime("%d-%m-%Y")
autocmd BufWritePre,FileWritePre *.{c,cpp,v,py} execute "normal ma"
autocmd BufWritePre,FileWritePre *.{c,cpp,v,py} exe "1," . 8 . "g/Last Modified :.*/s/Last Modified :.*/Last Modified : " .strftime("%c")
autocmd BufWritePost,FileWritePost *.{c,cpp,v,py} execute "normal `a"

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" User defined persistent macros
"let @a='4j6dd'

"CHEATSHEETS for learning :

" 1. Working with windows

    " ctrl-w s 	            split the current window horizontally, loading the same file in the new window
    " ctrl-w v 	            split the current window vertically, loading the same file in the new window

    " :sp[lit] filename 	split the current window horizontally, loading filename in the new window
    " :vsp[lit] filename 	split the current window vertically, loading filename in the new window

    " :q[uit] 	            close the currently active window
    " :on[ly] 	            close all windows except the currently active window

    " ctrl-w w 	            cycle between the open windows
    " ctrl-w h 	            focus the window to the left
    " ctrl-w j 	            focus the window to the down
    " ctrl-w k 	            focus the window to the up
    " ctrl-w l 	            focus the window to the right

    " map <C-h> <C-w>h
    " map <C-j> <C-w>j
    " map <C-k> <C-w>k
    " map <C-l> <C-w>l

    " ctrl-w + 	increase height of current window by 1 line
    " ctrl-w - 	decrease height of current window by 1 line
    " ctrl-w _ 	maximise height of current window
    " ctrl-w | 	maximise width of current window

    " ctrl-w r 	rotate all windows
    " ctrl-w x 	exchange current window with its neighbour
    " ctrl-w H 	move current window to far left
    " ctrl-w J 	move current window to bottom
    " ctrl-w K 	move current window to top
    " ctrl-w L 	move current window to far right

" Mapping w/q/a to their uppercase versions  --> will affect any other command line commands using similar pattern
"command WQ wq
"command Wq wq
"command W w
"command Q q

" Mapping of ; for : --> will affect 'f/F/T/t' functionality
"nnoremap ; :
"nnoremap : ;
"vnoremap ; :
"vnoremap : ;

" Searching tools
 " akdjf
" q/ to see the search command window
" /<CR> to repeat the last search
" //e<CR> to repeat the last search but cursor at end of word
" leaving the first argument of substitute command means to use the previous search by default
" use () to wrap your search to save it into numbered registers \1
" \v for very magic search    all special meaning by default
" \V for very non magic search    no special meaning by default, will match literal characters if not backslashed
" <Ctrl-R>/ in command line inserts the last pattern searched
" <Ctrl-R>{register} in command line inserts the pattern saved in the register
" ctrl-r + ctrl-w to fill out the search pattern for both under the cursor or highlighted search

" Substitution tools
" use gcn flag for search and replace, g-global in line, c-confirmation, e - suppress errors
" use n to find out the total number of occurences of the search pattern in the file
" :%s///n to find the number of occurences for the pattern in previous search
" :%s//\=@0/g use as \=@{register} for pass by reference, rather than inserting all of it's contents in the command line.:w
" :%s//\=@a/g -> set search pattern using:  let @/='' and yank the replacement string in "a" register
" :%s//~/&    can change the range and use the previous search pattern, ~  replacement string and flags
" g&      to do the previous substitute command on the entire file
" :%&&    same as g&
" :&&     apply previous substitute command on the current line
" :'<,'>&&    apply previous substitute command on the visual selection(use gv)

" :%s///gn count the number of previous search pattern

" nnoremap & :&&<CR>
" xnoremap & :&&<CR>

" Extra helpful commands
" @: to repeat the last ex command
" q: to see the command window
" c{motion}{text}<Ctrl-R>"{text}<CR>  to add some text around some other text
" use the expression register to insert values using calculation i<Ctrl-R>=expression<CR>
" use @= to calculate expression and see the output in command line and use the value for normal mode commands
" lookahead and lookbefore search patterns \zs \ze
" q{register}q    to empty a register value
" inserting a pattern of numbers to your code using a macro (or using range)
" use mV to mark vimrc and mB to mark bash_aliases

" Create mapping for CAPS-LOCK to be used as escape key
" au VimEnter ?* :silent !xmodmap -e 'clear Lock' -e 'keycode 0x42 = Escape'
" au VimLeave ?* :silent !xmodmap -e 'clear Lock' -e 'keycode 0x42 = Caps_Lock'
" au VimEnter ?* !xmodmap -e 'clear Lock' -e 'keycode 0x42 = Escape'
" au VimLeave ?* !xmodmap -e 'clear Lock' -e 'keycode 0x42 = Caps_Lock'

" Do something about the swap files
" Read the help manual of Vim
" Learn Vimscript the hard way

" circular windows navigation , since tab=<C-i> it breaks <C-i> usage
" nnoremap <Tab>   <c-W>w
" nnoremap <S-Tab> <c-W>W

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" Saves the undo history, even after file is closed
let s:undoDir = "/tmp/.undodir_" . $USER
if !isdirectory(s:undoDir)
    call mkdir(s:undoDir, "", 0700)
endif
let &undodir=s:undoDir
set undofile

" CTRL-A/X will be forced to use decimal-based arithmetic
set nrformats=

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

autocmd FileType verilog* iabbrev <buffer> w_ wire [:0] w_;<Esc>7ha
autocmd FileType verilog* iabbrev <buffer> r_ reg  [:0] r_;<Esc>7ha

autocmd FileType verilog* iabbrev <buffer> always <Esc>:Zalways<cr>

"For diffing open files run this command in all files
"setlocal diff foldmethod=diff scrollbind nowrap foldlevel=1

set virtualedit=all

```

---

<p align="center">
  <b>
  <a href="https://gs1293.github.io/resource/resource.html"> <font size="-1">Go Back</font></a>
  </b>
</p>
