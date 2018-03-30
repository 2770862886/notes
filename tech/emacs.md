Emacs Using & Plugin Tips
======

# Hotkeys
## Jump over buffers
C-UP/LEFT/DOWN/RIGHT
M-[NUMBER]
## recent-jump
M-[LEFT]
M-[RIGHT]
## Duplicate line
C-c d
## Kill back to indentation
C-M-BACKSPACE
## cscope
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
## multi-cursor
C-<             Mark previous like this
C-> (C-+)       Mark next
C-c C-<         Mark all like this
from active region to multiple cursor:
C-c m r         Set rectangular region anchor
C-c m c         Edit lines
C-c m e         Edit ends of lines
C-c m a         Edit beginnings of lines
