% Emacs Using & Plugin Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

## Tramp ##
TRAMP is for transparently accessing remote file from within Emacs.  

<kbd>C-x C-f</kbd>
`ssh:user@host#port:pathTo`


## Prerequisite ##

### ag (the_silver_searcher) ###

``` shell
sudo add-apt-repository ppa:pgolm/the-silver-searcher
sudo apt-get update
sudo apt-get install silversearcher-ag
```

`brew install the_silver_searcher`

## Hotkeys ##

### Help Commands ###
| Description                              |         Keybinding |
|:-----------------------------------------|-------------------:|
| info emacs maunual, require for an topic | <kbd>C-h r i</kbd> |
| describe function                        |   <kbd>C-h f</kbd> |
| describe key                             |   <kbd>C-h k</kbd> |
| describe mode                            |   <kbd>C-h m</kbd> |
| describe symbol                          |   <kbd>C-h o</kbd> |
| apropos-command                          |   <kbd>C-h a</kbd> |


### mark region ###

press <kbd>S-SPC</kbd> to active command mark, then move the cursor to the point
and press <kbd>C-x C-x</kbd> to active the region between the two position.

### Jump over buffers ###

<kbd>C-\<up\>/\<left\>/\<down\>/\<right\></kbd>
<kbd>M-\<#\></kbd>

### recent-jump ###

<kbd>M-\<left\></kbd>
<kbd>M-\<right\></kbd>

### Duplicate line ###

<kbd>C-c d</kbd>

### indentation ###

| Action                   |            Keybinding |
|:-------------------------|----------------------:|
| kill-back-to-indentation | <kbd>C-M-\<BS\></kbd> |
| back-to-indentation      |        <kbd>M-m</kbd> |
| delete-indentation       |        <kbd>M-^</kbd> |
| indent-rigidly           |    <kbd>C-x TAB</kbd> |

### Toggle the region/word case ###

| Action                        |         Keybinding |
|:------------------------------|-------------------:|
| Upper case char at the point  |     <kbd>M-c</kbd> |
| Lower case the region or word | <kbd>C-x C-l</kbd> |
| Upper case the region or word | <kbd>C-x C-u</kbd> |
| Lower case word at the point  |     <kbd>M-l</kbd> |
| Upper case word at the point  |     <kbd>M-u</kbd> |

## cscope ##

| Action                                                         |         Keybinding |
|:---------------------------------------------------------------|-------------------:|
| Find symbol.                                                   | <kbd>C-c s s</kbd> |
| Find global definition.                                        | <kbd>C-c s d</kbd> |
| Find global definition (alternate binding).                    | <kbd>C-c s g</kbd> |
| Find global definition without prompting.                      | <kbd>C-c s G</kbd> |
| Find functions calling a function.                             | <kbd>C-c s c</kbd> |
| Find called functions (list functions called from a function). | <kbd>C-c s C</kbd> |
| Find text string.                                              | <kbd>C-c s t</kbd> |
| Find egrep pattern.                                            | <kbd>C-c s e</kbd> |
| Find a file.                                                   | <kbd>C-c s f</kbd> |
| Find files #including a file.                                  | <kbd>C-c s i</kbd> |
| Display *cscope* buffer.                                       | <kbd>C-c s b</kbd> |
| Auto display *cscope* buffer toggle.                           | <kbd>C-c s B</kbd> |
| Next symbol.                                                   | <kbd>C-c s n</kbd> |
| Next file.                                                     | <kbd>C-c s N</kbd> |
| Previous symbol.                                               | <kbd>C-c s p</kbd> |
| Previous file.                                                 | <kbd>C-c s P</kbd> |
| Pop mark.                                                      | <kbd>C-c s u</kbd> |

# multi-cursor #

| Action                                  |           Keybinding |
|:----------------------------------------|---------------------:|
| Mark previous like this                 |     <kbd>'C-<'</kbd> |
| Mark next                               |     <kbd>'C->'</kbd> |
| Mark all like this                      | <kbd>'C-c C-<'</kbd> |
| *from active region to multiple cursor* |                      |
| Set rectangular region anchor           |   <kbd>C-c m r</kbd> |
| Edit lines                              |   <kbd>C-c m c</kbd> |
| Edit ends of lines                      |   <kbd>C-c m e</kbd> |
| Edit beginnings of lines                |   <kbd>C-c m a</kbd> |

# projectile #

If you want to mark a folder manully as a project just create an empty .projectile file in it.  

| Action                                         |             Keybinding |
|:-----------------------------------------------|-----------------------:|
| for help                                       |   <kbd>C-c p C-h</kbd> |
| buffer                                         |   <kbd>C-c p ESC</kbd> |
| configure project                              |     <kbd>C-c p C</kbd> |
| project dired                                  |     <kbd>C-c p D</kbd> |
| edit project locals                            |     <kbd>C-c p E</kbd> |
| find file in known projects                    |     <kbd>C-c p F</kbd> |
| ibuffer                                        |     <kbd>C-c p I</kbd> |
| switch project                                 |     <kbd>C-c p p</kbd> |
| find a file in current project                 |     <kbd>C-c p f</kbd> |
| regenerate tags                                |     <kbd>C-c p R</kbd> |
| save all the buffer related to current project |     <kbd>C-c p S</kbd> |
| find test file                                 |     <kbd>C-c p T</kbd> |
| browse dirty projects                          |     <kbd>C-c p V</kbd> |
| find other file                                |     <kbd>C-c p a</kbd> |
| switch to buffer                               |     <kbd>C-c p b</kbd> |
| compile current project                        |     <kbd>C-c p c</kbd> |
| find dir                                       |     <kbd>C-c p d</kbd> |
| recent file                                    |     <kbd>C-c p e</kbd> |
| find file                                      |     <kbd>C-c p f</kbd> |
| find file dwim                                 |     <kbd>C-c p g</kbd> |
| invalidate cache                               |     <kbd>C-c p i</kbd> |
| find tag                                       |     <kbd>C-c p j</kbd> |
| kill buffers                                   |     <kbd>C-c p k</kbd> |
| find file in directory                         |     <kbd>C-c p l</kbd> |
| commander                                      |     <kbd>C-c p m</kbd> |
| multi occur                                    |     <kbd>C-c p o</kbd> |
| replace                                        |     <kbd>C-c p r</kbd> |
| toggle between implementation and test         |     <kbd>C-c p t</kbd> |
| run project                                    |     <kbd>C-c p u</kbd> |
| vc                                             |     <kbd>C-c p v</kbd> |
| cache current file                             |     <kbd>C-c p z</kbd> |
| run eshell                                     |   <kbd>C-c p x e</kbd> |
| run shell                                      |   <kbd>C-c p x s</kbd> |
| run term                                       |   <kbd>C-c p x t</kbd> |
| grep                                           |   <kbd>C-c p s g</kbd> |
| ag                                             |   <kbd>C-c p s s</kbd> |
| dired other frame                              |   <kbd>C-c p 5 D</kbd> |
| find other file other frame                    |   <kbd>C-c p 5 a</kbd> |
| switch to buffer other frame                   |   <kbd>C-c p 5 b</kbd> |
| find dir other frame                           |   <kbd>C-c p 5 d</kbd> |
| find file dwim other frame                     |   <kbd>C-c p 5 g</kbd> |
| find implementation or test other frame        |   <kbd>C-c p 5 t</kbd> |
| display buffer                                 | <kbd>C-c p 4 C-o</kbd> |
| dired other window                             |   <kbd>C-c p 4 D</kbd> |
| find other file other window                   |   <kbd>C-c p 4 a</kbd> |
| switch to buffer other window                  |   <kbd>C-c p 4 b</kbd> |
| find dir other window                          |   <kbd>C-c p 4 d</kbd> |
| find file other window                         |   <kbd>C-c p 4 f</kbd> |
| find file dwim other window                    |   <kbd>C-c p 4 g</kbd> |
| find implementation or test other window       |   <kbd>C-c p 4 t</kbd> |

dwim stands for 'Do What I Mean', usually these function try to do the right thing depends on the context.

# ivy #

# Scheme #

racket-mode + paredit-mode

# paredit #

1. Split & Join
| Action              |        Keybind |
|:--------------------|---------------:|
| paredit-splice-sexp | <kbd>M-S</kbd> |
| paredit-join-sexps  | <kbd>M-J</kbd> |

2. Depth-Changing
| Action                               |            Keybinding |
|:-------------------------------------|----------------------:|
| paredit-wrap-round                   |        <kbd>M-(</kbd> |
| paredit-splice-sexp-killing-backward |   <kbd>M-\<up\></kbd> |
| paredit-splice-sexp-killing-forward  | <kbd>M-\<down\></kbd> |
| paredit-raise-sexp                   |        <kbd>M-r</kbd> |

3. Barfage[^2] & Slurpage[^3]
| Action                      |               Keybinding |
|:----------------------------|-------------------------:|
| paredit-forward-slurp-sexp  |           <kbd>C-)</kbd> |
|                             |   <kbd>C-\<right\></kbd> |
| paredit-forward-barf-sexp   |         <kbd>C-}\</kbd\> |
|                             |    <kbd>C-\<left\></kbd> |
| paredit-backward-slurp-sexp |           <kbd>C-(</kbd> |
|                             |  <kbd>C-M-\<left\></kbd> |
| paredit-backward-barf-sexp  |           <kbd>C-{</kbd> |
|                             | <kbd>C-M-\<right\></kbd> |

4. Insert
| Action                          |     Keybinding |
|:--------------------------------|---------------:|
| paredit-comment-dwim            | <kbd>M-;</kbd> |
| paredit-newline                 | <kbd>C-j</kbd> |
| paredit-close-round-and-newline | <kbd>M-)</kbd> |

5. Movement & Navigation
| Action                |       Keybinding |
|:----------------------|-----------------:|
| paredit-forward       | <kbd>C-M-f</kbd> |
| paredit-backward      | <kbd>C-M-b</kbd> |
| paredit-backward-up   | <kbd>C-M-u</kbd> |
| paredit-forward-down  | <kbd>C-M-d</kbd> |
| paredit-backward-down | <kbd>C-M-p</kbd> |
| paredit-forward-up    | <kbd>C-M-n</kbd> |


# irc #

# Erc #

# figlet #

# cua block #

[^2]: If someone barfs, they vomit.
[^3]: If you slurp a liquid, you drink it noisily.

