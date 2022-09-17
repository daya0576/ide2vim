# Henry's IDE to VIM Cheatsheet

> Personal cheatsheet when moving from IDEs(IntelliJ IDEA, Pycharm, etc.) to VIM.
> 
> p.s. some basic commands in vimtutor are ignored.

## IntelliJ IDEA/PyCharm Keymap

### Navigation

```
               IDE                                 VIM                           plugin        
 ------------------------------- ---------------------------------------- ---------------------
  Back/Forward                    <c-o>/<c-i>   " Jump older/newer                     
                                                                                         
  Go to Class/Symbol              :Tags                                    junegunn/fzf.vim   
  Go to File                      :Files                                               
  Recent Files                    :History                                             
                                                                                         
  File Structure                  :TagbarToggle                            majutsushi/tagbar  
                                                                                         
  Go to Declaration/Usage         <Plug>(coc-definition)                   neoclide/coc.nvim  
  Go to Type Decalaration         <Plug>(coc-type-definition)                          
  Go to Implementations           <Plug>(coc-implementation)                           
  Next/Pre Highlighted Error      <Plug>(coc-diagnostic-prev)  
  
  Scrolling                       <c-y>/<c-e>  " Scroll lines
                                  <c-u>/<c-d>  " Scroll half a screen
                                  <c-b>/<c-f>  " Scroll a full screen

  Cursor                          H/M/L
                                  zz/zt/zb
                                  $/0
                                  ^/g_         " Go first/last char                          
                                  {/}          " Go pre/next block

  Search                          f/F<char>    " Try ;/, repeat/reverse
                                  %            " Go parenthesis    
                                  #/*          " Go pre/next same word
```

### Code

```
               IDE                                 VIM                           plugin        
 ------------------------------- ---------------------------------------- ---------------------
  Override Methods...               
  Implement Methods...
  
  Code Completion                 NA                                       neoclide/coc.nvim
  Live Template                   NA                                       coc-snippets
  Surround With...                S                                        tpope/vim-surround

  Folding                         zM               " Close all folds
                                  zR               " Open all folds
                                  za               " Toggle one folds 
                                  zj/zk            " Jump next/pre fold

  Comment                         <leader>cc       " Comment               nerdcommenter
                                  <leader>ci       " Uncomment
                                  <leader>c<space> " Toggle comment
  
  Move Element Left/Right         g<               " Move element left     machakann/vim-swap
                                  g>               " Move element right
                                  gs               " Interactive mode
  
  Multiple Cursors                NA                                       vim-visual-multi
```

### Window

```
               IDE                                 VIM                           plugin        
 ------------------------------- ---------------------------------------- ---------------------
  Editor Tabs                     :tabnew filename
                                  (p.s. try buffers)

  Windows                         :split
                                  :vsplit
                                  <c-w>_     " Maximize height
                                  <c-w>|     " Maximize width
                                  <c-w>=     " Make all equal size
                                  <c-w>r     " Rotate windows
```

### [WIP] Version Control Systems

```
               IDE                                 VIM                           plugin        
 ------------------------------- ---------------------------------------- ---------------------
  Diff & Merge                    <Plug>(GitGutterPreviewHunk)             vim-gitgutter
                                  <Plug>(GitGutterStageHunk)
                                  <Plug>(GitGutterUndoHunk)
                                  
```

## Others

### Main Menu | File | New Scratch File
<details>
  <summary>View code</summary>
  
```vim
" Main Menu | File | New Scratch File
function! s:Initialize(...)
  let magic = system('echo $RANDOM | md5sum | head -c 10')

  " Folder
  let folder = '/tmp/scratch/' 

  " File Name
  let file_postfix = get(a:, 0, 0)
  if file_postfix
    let filename = magic . '.' . a:1
  else
    let filename = magic 
  endif

  " File Path
  let filepath = folder . filename
  call system('mkdir -p ' . folder)
  call system('touch ' . filepath)

  " Open File
  execute 'edit ' . filepath
endfunction

command! -nargs=? Scratch :call s:Initialize(<f-args>)
```
</details>

### Main Menu | Run | Run
<details>
  <summary>View code</summary>
  
```vim
" run python code
augroup python_lang
    autocmd!
    autocmd FileType python nnoremap <leader>rp :w!<CR>:call VimuxRunCommand("clear; python3 " . bufname("%"))<CR>
augroup end
```
</details>

## Questions

1. Tabs or Buffer？   
Buffers as the file proxies and tab pages as the workspaces
2. How to debug keymaps   
Try `:map <c-k>`
3. File highlight not working?   
Try `set filetype=php`

## Reference
1. Personal vimrc file: https://github.com/daya0576/dotfile/blob/master/.vimrc 
