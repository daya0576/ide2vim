# Henry's IDE to VIM Cheatsheet

> Personal cheatsheet when moving from IDE to VIM.
> 
> p.s. some basic commands in vimtutor are ignored.


## IntelliJ IDEA/PyCharm Keymap

### Navigation

```
        IDE                               VIM                              plugin        
 --------------------------------- --------------------------------- ------------------- 
  Back/Forward                      <c-o> / <c-i>                                        
                                                                                         
  Go to Class/Symbol                :Tags                             junegunn/fzf.vim   
  Go to File                        :Files                                               
  Recent Files                      :History                                             
                                                                                         
  File Structure                    :TagbarToggle                     majutsushi/tagbar  
                                                                                         
  Go to Declaration / Usuage        <Plug>(coc-definition)            neoclide/coc.nvim  
  Go to Type Decalaration           <Plug>(coc-type-definition)                          
  Go to Implementations             <Plug>(coc-implementation)                           
  Next/Pre Highlighted Error        <Plug>(coc-diagnostic-prev)  
  
  Scrolling                         ctrl-y/ctrl-e
                                    ctrl-u/ctrl-d
                                    ctrl-b/ctrl-f

  Cursor                            H/M/L
                                    zz/zt/zb
                                    $/0
                                    ^/g_  " first/last character                          
                                    {/}   " next/pre block

  Search                            f/F                       
                                    %     " go parenthesis    
                                    #/*   " pre/next same word
```

### Code

```
        IDE                               VIM                              plugin        
 --------------------------------- --------------------------------- ------------------- 
  Override Methods...               
  Implement Methods...
  
  Code Completion                   NA                                neoclide/coc.nvim
  Live Template                     NA                                coc-snippets
  Surround With...                  S                                 tpope/vim-surround

  Folding                           zM: close all folders
                                    zR: open all folders
                                    za: toggle one folder 
                                    zj/zk: jump folder

  Comment                           <leader>cc        " comment       nerdcommenter
                                    <leader>ci        " uncomment
                                    <leader>c<space>  " toggle
  
  Move Element Left/Right           ??                    

  
  Cursor                            NA                                vim-visual-multi
```

### Window

```
        IDE                               VIM                              plugin        
 --------------------------------- --------------------------------- ------------------- 
  Editor Tabs                       :tabnew filename
                                    (p.s. try buffers)

  Windows                           :split
                                    :vsplit 
                                    ctrl+w_   " maximize vertically
                                    ctrl+w|   "
                                    ctrl+w=   " 
```

### Version Control Systems

```
        IDE                               VIM                              plugin        
 --------------------------------- --------------------------------- ------------------- 
  Diff & Merge                      <Plug>(GitGutterPreviewHunk)      vim-gitgutter
                                    <Plug>(GitGutterStageHunk)
                                    <Plug>(GitGutterUndoHunk)
```


## Questions

1. Tabs or Buffer？   
buffers as the file proxies and tab pages as the workspaces
2. how to debug keymaps   
try `:map <c-k>`
3. file highlight not working?   
try `set filetype=php`

## Reference
1. personal vimrc file: https://github.com/daya0576/dotfile/blob/master/.vimrc 
