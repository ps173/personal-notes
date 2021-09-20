# Some Cool Vim Commands That I use a lot
---

- `#` on any word will search through all the words in that document(but
  backwards I don't know the other command to search forward).

- `%s/pattern/change/g` is like simple search replace like in other

- In nvim you can do `:set icm=split`. Now this is very useful while doing search
  and replace as it provides a small split which showcases all the words in the
  buffer that should be replaced

- `J` concatanates the next line with current line.
 
- `:set paste` puts vim in paste mode. Check more by doing `:h 'paste'` 
		You can add this particular line in your `.vimrc` to paste stuff 
  `set pastetoggle=<F11>`. But why not just use normal ctrl-shift-v that 
  terminal provides ? Well this may end up doing auto indents as vim interprets
		all those text. For a better explanation check `:h paste`

- You can have mouse support in vim by just doing `set mouse=a`

- You can also remove statusline (if u don't want it for some reason) by doing
		`:set laststatus=-`

# The minimum that every one should know.
---

- Please do vimtutor. It's really good.
- Beside vim tutor something's about configs. Most of the begineers don't know
		how to use it.
  - There is `.vimrc` file for normal `vim` and `.config/nvim/init.vim` for `nvim`
  - In these files u can add ur personal settings for vim. Some simple settings 
   that I recommend are :
   ```vim
   " I Hate errorbells and everyone does
   set noerrorbells

" A menu in command line
   set wildmenu

" If nothing works mouse works
   set mouse=a
   
" These are normal tab settings
			set smartindent
   set expandtab
   set tabstop=2
   set softtabstop=2
   set shiftwidth=2

   set nu 
   set nowrap
   set hlsearch
   set smartcase 

" All these 4 go together
   set noswapfile
   set nobackup
   set undodir=~/.nvim/undodir
   set undofile

" I like seeing the line highlighted
   set cursorline

" Signs in signcolumn
   set signcolumn=yes
			
"	Incremental search see `:h incsearch`
   set incsearch

" this one is gold scrolls down if u are above 8 lines
   set scrolloff=8

"	Show me all the buffers and don't ask me to close them when I want to switch
			set hidden

   set formatoptions-=cro
   set t_Co=256

" For better Coding experience
   set colorcolumn=80

" Good command
   set icm=split
   ```
