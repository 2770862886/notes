% Emacs Using & Plugin Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

## Prerequisite ##

### ag (the_silver_searcher) ###

`brew install the_silver_searcher`

## Hotkeys ##

### Jump over buffers ###

<kbd>C-\<up\>/\<left\>/\<down\>/\<right\></kbd>
<kbd>M-\<#\></kbd>

### recent-jump ###

<kbd>M-\<left\></kbd>
<kbd>M-\<right\></kbd>

### Duplicate line ###

<kbd>C-c d</kbd>

### Kill back to indentation ###

<kbd>C-M-\<BS\></kbd>

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

| Action                                  |         Keybinding |
|:----------------------------------------|-------------------:|
| Mark previous like this                 |     <kbd>C-<</kbd> |
| Mark next                               |     <kbd>C-></kbd> |
| Mark all like this                      | <kbd>C-c C-<</kbd> |
| *from active region to multiple cursor* |                    |
| Set rectangular region anchor           | <kbd>C-c m r</kbd> |
| Edit lines                              | <kbd>C-c m c</kbd> |
| Edit ends of lines                      | <kbd>C-c m e</kbd> |
| Edit beginnings of lines                | <kbd>C-c m a</kbd> |

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

## ivy ##

## Scheme ##

geiser + paredit-mode 是玩Racket 的好环境

## Erc ##

## figlet ##

## cua block ##
