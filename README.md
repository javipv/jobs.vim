# jobs.vim
Run system commands in background.

## Description:

Tool to be used on other plugins to launch system commands in background.

Includes several commands to check the commands in progress (Jobsl).

Stop all commands in background (Jobska)

Choose wich commands in background to stop (Jobsk)

Showw all commands in background related to current vim window (Jobshw)

Showw all commands history (Jobshy)

Use :Jobsh to show command help.

Example:
```vimscript
function! svnTools#Blame()
    let file = expand("%")
    let name = expand("%:t")
    let pos = line('.')
    let ext = s:GetSyntax()

    let command  = "svn blame -v ".l:file
    let callback = "svnTools#SvnBlameEnd(\"".l:pos."\",\"".l:ext."\",\"".l:name."\","
    let l:async = 1

    call jobs#RunCmd(a:command, a:callback, l:async, "svn")
endfunction

function! svnTools#SvnBlameEnd(pos,ext,name,resfile)
    if exists('a:resfile') && !empty(glob(a:resfile))
       " Process the svn blame file
    else
      echo "ERROR. Svn blame empty"
    endif
endfunction
```
 
## Install details
Minimum version: Vim 8.0+

Simplest method:
- Just unzip to your .vim folder.

Plugin manager:
- Either vim-pathogen or Vundle are recommended.
