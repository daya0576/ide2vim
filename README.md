# Henry's IDE to VIM Cheatsheet

> Personal cheatsheet when moving from IDE(Idea, Pycharm, etc.) to VIM.
> 
> p.s. some basic commands in vimtutor are ignored.


## IntelliJ IDEA/PyCharm Keymap

### Navigation

```
        IDE                               VIM                                 plugin        
 --------------------------------- ------------------------------------ ------------------- 
  Back/Forward                      <c-o> / <c-i>                                        
                                                                                         
  Go to Class/Symbol                :Tags                                junegunn/fzf.vim   
  Go to File                        :Files                                               
  Recent Files                      :History                                             
                                                                                         
  File Structure                    :TagbarToggle                        majutsushi/tagbar  
                                                                                         
  Go to Declaration / Usuage        <Plug>(coc-definition)               neoclide/coc.nvim  
  Go to Type Decalaration           <Plug>(coc-type-definition)                          
  Go to Implementations             <Plug>(coc-implementation)                           
  Next/Pre Highlighted Error        <Plug>(coc-diagnostic-prev)  
  
  Scrolling                         <c-y>/<c-e>
                                    <c-u>/<c-d>
                                    <c-b>/<c-f>

  Cursor                            H/M/L
                                    zz/zt/zb
                                    $/0
                                    ^/g_       " first/last char                          
                                    {/}        " pre/next block

  Search                            f/F<char>  " ;/, repeat/revert
                                    %          " go parenthesis    
                                    #/*        " pre/next same word
```

### Code

```
        IDE                               VIM                                 plugin        
 --------------------------------- ------------------------------------ ------------------- 
  Override Methods...               
  Implement Methods...
  
  Code Completion                   NA                                   neoclide/coc.nvim
  Live Template                     NA                                   coc-snippets
  Surround With...                  S                                    tpope/vim-surround

  Folding                           zM: close all folders
                                    zR: open all folders
                                    za: toggle one folder 
                                    zj/zk: jump folder

  Comment                           <leader>cc        " comment          nerdcommenter
                                    <leader>ci        " uncomment
                                    <leader>c<space>  " toggle
  
  Move Element Left/Right           ??                    

  
  Cursor                            NA                                   vim-visual-multi
```

### Window

```
        IDE                               VIM                                 plugin        
 --------------------------------- ------------------------------------ ------------------- 
  Editor Tabs                       :tabnew filename
                                    (p.s. try buffers)

  Windows                           :split
                                    :vsplit 
                                    <c-w>_   " maximize vertically
                                    <c-w>|   "
                                    <c-w>=   " 
```

### Version Control Systems

```
        IDE                               VIM                                 plugin        
 --------------------------------- ------------------------------------ ------------------- 
  Diff & Merge                      <Plug>(GitGutterPreviewHunk)         vim-gitgutter
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


## Questions

1. Tabs or Buffer？   
Buffers as the file proxies and tab pages as the workspaces
2. How to debug keymaps   
Try `:map <c-k>`
3. File highlight not working?   
Try `set filetype=php`

## Reference
1. Personal vimrc file: https://github.com/daya0576/dotfile/blob/master/.vimrc 
