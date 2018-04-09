Emacs Using & Plugin Tips
======

# Hotkeys #

## Jump over buffers ##

C-UP/LEFT/DOWN/RIGHT
M-[NUMBER]

## recent-jump ##

M-[LEFT]
M-[RIGHT]

## Duplicate line ##

C-c d

## Kill back to indentation ##

C-M-BACKSPACE

## cscope ##

C-c s s         Find symbol.
C-c s d         Find global definition.
C-c s g         Find global definition (alternate binding).
C-c s G         Find global definition without prompting.
C-c s c         Find functions calling a function.
C-c s C         Find called functions (list functions called from a function).
C-c s t         Find text string.
C-c s e         Find egrep pattern.
C-c s f         Find a file.
C-c s i         Find files #including a file.

C-c s b         Display *cscope* buffer.
C-c s B         Auto display *cscope* buffer toggle.
C-c s n         Next symbol.
C-c s N         Next file.
C-c s p         Previous symbol.
C-c s P         Previous file.
C-c s u         Pop mark.

## multi-cursor ##

C-<             Mark previous like this
C-> (C-+)       Mark next
C-c C-<         Mark all like this
from active region to multiple cursor:
C-c m r         Set rectangular region anchor
C-c m c         Edit lines
C-c m e         Edit ends of lines
C-c m a         Edit beginnings of lines

## projectile ##

If you want to mark a folder manully as a project just create an empty .projectile file in it.

C-c p C-h: for help
C-c p ESC: buffer
C-c p C: configure project
C-c p D: project dired
C-c p E: edit project locals
C-c p F: find file in known projects
C-c p I: ibuffer
C-c p p: Switch project
C-c p f: find a file in current project
C-c p R: regenerate tags
C-c p S: Save all the buffer related to current project
C-c p T: find test file
C-c p V: browse dirty projects
C-c p a: find other file
C-c p b: switch to buffer
C-c p c: compile current project
C-c p d: find dir
C-c p e: recent file
C-c p f: find file
C-c p e: find file dwin
C-c p i: invalidate cache
C-c p j: find tag
C-c p k: kill buffers
C-c p l: find file in directory
C-c p m: commander
C-c p o: multi occur
C-c p r: replace
C-c p t: toggle between implementation and test
C-c p u: run project
C-c p v: vc
C-c p z: cache current file
C-c p x e: run eshell
C-c p x s: run shell
C-c p x t: run term
C-c p s g: grep
C-c p s s: ag
C-c p 5 D: dired other frame
C-c p 5 a: find other file other frame
C-c p 5 b: switch to buffer other frame
C-c p 5 d: find file dwim other frame
C-c p 5 t: find implementation or test other frame
C-c p 4 C-o: display buffer
C-c p 4 D: dired other window
C-c p 4 a: find other file other window
C-c p 4 b: switch to buffer other window
C-c p 4 d: find dir other window
C-c p 4 f: find file other window
C-c p 4 g: find file dwin other window
C-c p 4 t: find implementation or test other window

## ivy ##
