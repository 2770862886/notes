% Emacs Using & Plugin Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Mastering Emacs](https://www.masteringemacs.org/)  
[Sacha Chua's Blog](https://sachachua.com/blog/)  
[abbrev mode](http://ergoemacs.org/emacs/emacs_abbrev_mode.html)  

# Performance profiler #

<kbd>C-x C-m</kbd> `profiler-start`
<kbd>C-x C-m</kbd> `profiler-report`

# Tramp #

[Tramp Manual](https://www.gnu.org/software/emacs/manual/html_node/tramp/index.html)  
[Fixing tramp hangup](https://blog.karssen.org/2016/03/02/fixing-emacs-tramp-mode-when-using-zsh/)  

TRAMP is for transparently accessing remote file from within Emacs.  

<kbd>C-x C-f</kbd>
`ssh:user@host#port:pathTo`

## Use ssh config option of the access method ##

``` bash
vi .ssh/config

Host xy
    HostName news.my.domain
    User news
    Port 2000
```

# Prerequisite #

## ag (the_silver_searcher) ##

``` shell
sudo add-apt-repository ppa:pgolm/the-silver-searcher
sudo apt-get update
sudo apt-get install silversearcher-ag
```

`brew install the_silver_searcher`

# Hotkeys #

## Help Commands ##

| Description                                  |         Keybinding |
|:---------------------------------------------|-------------------:|
| info emacs maunual, require for an topic     | <kbd>C-h r i</kbd> |
| info emacs maunual, require for an menu item | <kbd>C-h i m</kbd> |
| apropos-command                              |   <kbd>C-h a</kbd> |
| list all keybindings                         |   <kbd>C-h b</kbd> |
| describe function                            |   <kbd>C-h f</kbd> |
| describe key                                 |   <kbd>C-h k</kbd> |
| describe mode                                |   <kbd>C-h m</kbd> |
| describe symbol                              |   <kbd>C-h o</kbd> |
| describe variable                            |   <kbd>C-h v</kbd> |
| print keybindings invoke the command         |   <kbd>C-h w</kbd> |

* Search for documentation topics
  - apropos
  - apropos-command
  - apropos-library
  - apropos-documentation

## Evalution ##

| Description                             |          Keybinding |
|:----------------------------------------|--------------------:|
| evaluate any Emacs Lisp expression      |      <kbd>M-:</kbd> |
| evaluate previous s-expression          |  <kbd>C-x C-e</kbd> |
| evaluate current top-level s-expression |    <kbd>C-M-x</kbd> |
| evaluate current buffer                 |    <kbd>C-x e</kbd> |
| REPL                                    | <kbd>M-x ielm</kbd> |

## mark region ##

press <kbd>S-SPC</kbd> to active command mark, then move the cursor to the point  
and press <kbd>C-x C-x</kbd> to active the region between the two position.  

## Jump over buffers ##

<kbd>C-\<up\>/\<left\>/\<down\>/\<right\></kbd>
<kbd>M-\<#\></kbd>

## recent-jump ##

<kbd>M-\<left\></kbd>
<kbd>M-\<right\></kbd>

## Duplicate line ##

<kbd>C-c d</kbd>

## Narrowing ##

| Action                                                    |         Keybinding |
|:----------------------------------------------------------|-------------------:|
| Narrow down to between point and mark (narrow-to-region). | <kbd>C-x n n</kbd> |
| Widen to make the entire buffer accessible again (widen). | <kbd>C-x n w</kbd> |
| Narrow down to the current page (narrow-to-page).         | <kbd>C-x n p</kbd> |
| Narrow down to the current defun (narrow-to-defun).       | <kbd>C-x n d</kbd> |

## Pages ##

Within some text files, text is divided into pages delimited by the formfeed character (ASCII code 12, 
also denoted as 'control-L'), which is displayed in Emacs as the escape sequence '^L'. 
Insert formfeed <kbd>C-q C-l</kbd>.

| Action                                                             |         Keybinding |
|:-------------------------------------------------------------------|-------------------:|
| Move point to previous page boundary (backward-page).              |   <kbd>C-x [</kbd> |
| Move point to next page boundary (forward-page).                   |   <kbd>C-x ]</kbd> |
| Put point and mark around this page (or another page) (mark-page). | <kbd>C-x C-p</kbd> |

## Indentation ##

| Action                   |            Keybinding |
|:-------------------------|----------------------:|
| kill-back-to-indentation | <kbd>C-M-\<BS\></kbd> |
| back-to-indentation      |        <kbd>M-m</kbd> |
| delete-indentation       |        <kbd>M-^</kbd> |
| indent-rigidly           |    <kbd>C-x TAB</kbd> |

## Toggle the region/word case ##

| Action                        |         Keybinding |
|:------------------------------|-------------------:|
| Upper case char at the point  |     <kbd>M-c</kbd> |
| Lower case the region or word | <kbd>C-x C-l</kbd> |
| Upper case the region or word | <kbd>C-x C-u</kbd> |
| Lower case word at the point  |     <kbd>M-l</kbd> |
| Upper case word at the point  |     <kbd>M-u</kbd> |

## simple overlay ##

| Action                         |     Keybinding |
|:-------------------------------|---------------:|
| symbol-overlay-put             | <kbd>M-i</kbd> |
| symbol-overlay-switch-forward  | <kbd>M-p</kbd> |
| symbol-overlay-switch-backward | <kbd>M-n</kbd> |

# cscope #

| ACTION                                                         |         Keybinding |
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

[Projectile Home](https://docs.projectile.mx/en/latest/)  

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

# yankpad #
[yankpad](https://github.com/Kungsgeten/yankpad)

## Category 1 ##

``` org
* Category 1
** Snippet title
    Here's a text snippet I want to insert.

** Snippet with keybinding                               :last:tag:is:key:o:

    And here's another snippet. This snippet has tags, and the last of these
    tags should be a key. This will bind the snippet to the key (in this case
    "o") when first calling yankpad-map.

** expandword: Snippet with keyword expansion

    This snippet has a keyword; "expandword" in this case. If this category is
    active, and you type the keyword into a buffer and use the "yankpad-expand"
    command, the keyword will be replaced with this snippet.

** more:expands: Multiple keywords

    A snippet can have more than one keyword. This has both "more" and
    "expands".
```

## Category 2 ##

``` org
* Category 2
  Descriptive lists will be treated as snippets. You can set them to be treated
  as =abbrev-mode= abbrevs instead, by setting
  =yankpad-descriptive-list-treatment= to abbrev. If a heading could be
  considered to be a snippet, add the =snippetlist= tag to ignore the snippet
  and scan it for descriptive lists instead.

  - name :: Erik Sjöstrand
  - key :: Typing "key" followed by `yankpad-expand' will insert this snippet.

** Descriptive list example 2                  :snippetlist:

   This heading would normally be considered a snippet, but because of the
   =:snippetlist:= tag, it is scanned for descriptive lists instead.

   - foo :: bar

** Explaining categories

    This snippet belongs to another category (named =Category 2=). Categories
    are useful if you need several yankpads, for instance if you're a teacher
    (like me) working with different courses.

** yasnippet magic

    If you have yasnippet installed (not a requirement), the content in each
    snippet is actually executed by yasnippet! This means that you could run
    elisp inside your snippets: `(+ 3 4)` and have handy tab stop fields.

    | Student | Grade |
    |---------+-------|
    | $1      | $2    |

    That's pretty handy!
    $0

# ** [[file:my_other_snippets.org]]

#   If a heading has a link to another org-file, that file will be scanned for
#   snippets. Those snippets are then appended to the category.

# ** [[file:misc_snippets::*Search]]

#   You can specify a specific headline in another file, which you want to be
#   searched for snippets. It could be a single snippet, or it could have
#   subtrees (in which case all of them will be considered as snippets).

** [[id:38e4c8d2-5ab0-4e78-8e43-ea4a918e5c02]]

   You can also provide the ID of a specific org-mode headline.

** Code snippet examples

    You can organize your snippets inside a category by using subtrees, like
    this one. Only headings without children are considered as snippets.

*** "Litterate programming" snippet                    :src:

     Tagging a snippet with src says that only the content of source blocks
     should be expanded. All other text (like this paragraph) is ignored.

     #+BEGIN_SRC emacs-lisp
     (message "This is part of the snippet")
     #+END_SRC

     If you have several source blocks, their content will be concatenated.

     #+BEGIN_SRC emacs-lisp
     (message "This is also part of the snippet!!!")
     #+END_SRC

*** The source block below will be executed if tag is func :func:
     #+BEGIN_SRC emacs-lisp
     ;; Instead of a src-block, the snippet may be named
     ;; the same as an emacs-lisp function. This will then
     ;; be executed without arguments (see next example).
     (elfeed)
     #+END_SRC

** elfeed                                            :func:e:

```

## Kitchen sink category ##

``` org
* Kitchen sink category
:PROPERTIES:
:INCLUDE:  Category 1|Category 2
:END:

** Include other categories

Snippets from Category 1 and Category 2 will be appended to this category.
This is done by setting the INCLUDE property of the category. Categories
are separated by a pipe.

```

## Marjor-mode category ##

``` org
* org-mode

** Major-mode categories

    If you have a category with the same name as a major-mode, that category will be
    activated when switching major-mode. This only affects the local buffer and does
    not modify the global category.
** uml-snippet
   #+BEGIN_SRC plantuml :file $1
   $0
   #+END_SRC ##
```

## my-projectile-project ##

``` org
* my-projectile-project
** Projectile based categories

    If you have projectile installed (not a requirement) you can give a category
    the same name as one of your projectile projects. That category will be
    activated when using projectile-find-file on a file in the project.

```

## Global category ##

``` org
* Global category                                   :global:
** Always available

    Snippets in a category with the :global: tag are always available for
    expansion.

```

## Default ##

``` org
* Default                                           :global:
** Fallback for major-mode categories

   If you open a file, but have no category named after its major-mode, a
   category named "Default" will be used instead (if you have it defined in your
   Yankpad). It is probably a good idea to make this category global. You can
   change the name of the default category by setting the variable
   yankpad-default-category.
```

# bookmark #

| Description                       |           Keybindins |
|:----------------------------------|---------------------:|
| describe-bookmark                 |     <kbd>C-h M</kbd> |
| jump-other-frame                  |   <kbd>C-x 5 B</kbd> |
|                                   |   <kbd>C-x j 5</kbd> |
| list-jump                         |   <kbd>C-x j B</kbd> |
| jump                              |   <kbd>C-x j j</kbd> |
| file-jump                         |   <kbd>C-x j y</kbd> |
| previous-bookmark-repeat          | <kbd>C-x p C-b</kbd> |
| next-bookmark-repeat              | <kbd>C-x p C-f</kbd> |
| delete-bookmark                   | <kbd>C-x p C-k</kbd> |
| switch-to-bookmark-file           | <kbd>C-x p C-l</kbd> |
| toggle-autonamed-bookmark         | <kbd>C-x p RET</kbd> |
| next-bookmark-this-file           | <kbd>C-x p C-n</kbd> |
| previous-bookmark-this-file       | <kbd>C-x p C-p</kbd> |
| save-bookmark-this-file           | <kbd>C-x p C-s</kbd> |
| unlight-bookmark-here             | <kbd>C-x p C-u</kbd> |
| clone-bookmark                    |   <kbd>C-x p 2</kbd> |
| bookmark-lighted-at-point         |   <kbd>C-x p =</kbd> |
| describe-bookmark-lighted-here    |                      |
| choose-navlist-from-bookmark-list |                      |
| edit-bookmark-record              |   <kbd>C-x p E</kbd> |
| light-bookmarks                   |   <kbd>C-x p H</kbd> |
| insert-location                   |   <kbd>C-x p I</kbd> |
| set-desktop-bookmark              |   <kbd>C-x p K</kbd> |
| switch-bookmark-file-create       |   <kbd>C-x p L</kbd> |
| bookmark-set-no-overwrite         |   <kbd>C-x p M</kbd> |
| unlight-bookmarks                 |   <kbd>C-x p U</kbd> |
| previous-bookmark-repeat          |   <kbd>C-x p b</kbd> |
| delete                            |   <kbd>C-x p d</kbd> |
| edit-bookmarks                    |   <kbd>C-x p e</kbd> |
| next-bookmark-repeat              |   <kbd>C-x p f</kbd> |
| jump                              |   <kbd>C-x p j</kbd> |
| load                              |   <kbd>C-x p l</kbd> |
| bookmark-set-confirm-overwrite    |   <kbd>C-x p m</kbd> |
| next-bookmark-this-file           |   <kbd>C-x p n</kbd> |
| bookmark-jump-other-window        |   <kbd>C-x p o</kbd> |
|                                   |   <kbd>C-x p q</kbd> |
| previous-bookmark-this-file       |   <kbd>C-x p p</kbd> |
| edit-bookmark-name-and-location   |   <kbd>C-x p r</kbd> |
| bookmark-save                     |   <kbd>C-x p s</kbd> |
| unlight-bookmark-this-buffer      |   <kbd>C-x p u</kbd> |
| bookmark-write                    |   <kbd>C-x p w</kbd> |
| bookmark-set-file-bookmark        |   <kbd>C-x p y</kbd> |
|                                   |                      |

# use-package #

[use-package](https://github.com/jwiegley/use-package)


# yas-snippet #

| Description            |         Keybinding |
|:-----------------------|-------------------:|
| yas-new-snippet        | <kbd>C-c C-n</kbd> |
| yas-visit-snippet-file | <kbd>C-c C-v</kbd> |
| yas-insert-snippet     | <kbd>C-c C-s</kbd> |
|                        |                    |

# ivy #

[ivy home](http://oremacs.com/)  
[ivy manual](http://oremacs.com/swiper/)  
[ivy github](https://github.com/abo-abo/swiper)  

## Ivy Generic Help ##

<kbd>M-x</kbd> `ivy-help`

=ivy= is an Emacs incremental completion framework.

- Narrow the list by typing some pattern,
- Multiple patterns are allowed by separating with a space,
- Select with ~C-n~ and ~C-p~, choose with ~RET~.

### Help ###

- ~C-h m~ :: Pop to this generic help buffer.

### Basic Operations ###

#### Key bindings for navigation ####

- ~C-n~ (=ivy-next-line=) :: next candidate.
- ~C-p~ (=ivy-previous-line=) :: previous candidate.
- ~C-v~ (=ivy-scroll-up-command=) :: next page.
- ~M-v~ (=ivy-scroll-down-command=) :: previous page.
- ~M-<~ (=ivy-beginning-of-buffer=) :: first candidate.
- ~M->~ (=ivy-end-of-buffer=) :: last candidate.

#### Key bindings for single selection ####

When selecting a candidate, an action is called on it. You can think
of an action as a function that takes the selected candidate as an
argument and does something with it.

Ivy can offer several actions from which to choose. This can be
independently composed with whether you want to end completion when
the action is called. Depending on this, the short term is either
"calling an action" or "exiting with action".

~C-m~ or ~RET~ (=ivy-done=) - exit with the current action.

~M-o~ (=ivy-dispatching-done=) - select an action and exit with it.

~C-j~ (=ivy-alt-done=) - when the candidate is a directory, enter
it. Otherwise, exit with the current action.

~TAB~ (=ivy-partial-or-done=) - attempt partial completion, extending
the current input as much as possible. ~TAB TAB~ is the same as ~C-j~.

~C-M-j~ (=ivy-immediate-done=) - exit with the current action, calling
it on the /current input/ instead of the current candidate. This is
useful especially when creating new files or directories - often the
input will match an existing file, which you don't want to select.

~C-'~ (=ivy-avy=) - select a candidate from the current page with avy
and exit with the current action.

### Advanced Operations ###
#### Key bindings for multiple selection ####

For repeatedly applying multiple actions or acting on multiple
candidates, Ivy does not close the minibuffer between commands. It
keeps the minibuffer open for applying subsequent actions.

Adding an extra meta key to the normal key chord invokes the special
version of the regular commands that enables applying multiple
actions.

~C-M-m~ (=ivy-call=) is the non-exiting version of ~C-m~ (=ivy-done=).

~C-M-n~ (=ivy-next-line-and-call=) combines ~C-n~ and ~C-M-m~.

~C-M-p~ (=ivy-previous-line-and-call=) combines ~C-p~ and ~C-M-m~.

~C-M-o~ (=ivy-dispatching-call=) is a non-exiting version of ~M-o~
(=ivy-dispatching-done=).

#### Key bindings that alter the minibuffer input ####

~M-n~ (=ivy-next-history-element=) select the next history element or
symbol/URL at point.

~M-p~ (=ivy-previous-history-element=) select the previous history
element.

~C-r~ (=ivy-reverse-i-search=) start a recursive completion session to
select a history element.

~M-i~ (=ivy-insert-current=) insert the current candidate into the
minibuffer. Useful for copying and renaming files, for example: ~M-i~
to insert the original file name string, edit it, and then ~C-m~ to
complete the renaming.

~M-j~ (=ivy-yank-word=) insert the sub-word at point into the
minibuffer.

~S-SPC~ (=ivy-restrict-to-matches=) deletes the current input, and
resets the candidates list to the currently restricted matches. This
is how Ivy provides narrowing in successive tiers.

#### Other key bindings ####

~M-w~ (=ivy-kill-ring-save=) copies the selected candidates to the
kill ring; when the region is active, copies the active region.

#### Saving the current completion session to a buffer ####

~C-c C-o~ (=ivy-occur=) saves the current candidates to a new buffer;
the list is active in the new buffer.

~RET~ or ~mouse-1~ in the new buffer calls the appropriate action on
the selected candidate.

Ivy has no limit on the number of active buffers like these.

Ivy takes care of making these buffer names unique. It applies
descriptive names, for example: =*ivy-occur counsel-describe-variable
"function$*=.

#### Global key bindings ####

=ivy-resume= recalls the state of the completion session just before
its last exit. Useful after an accidental ~C-m~ (=ivy-done=).
Recommended global binding: ~C-c C-r~.

#### Hydra in the minibuffer ####

~C-o~ (=hydra-ivy/body=) invokes Hydra menus with key shortcuts.

When in Hydra, ~C-o~ or ~i~ resumes editing.

Hydra reduces key strokes, for example: ~C-n C-n C-n C-n~ is ~C-o
jjjj~ in Hydra. Besides certain shorter keys, Hydra shows useful info
such as case folding and the current action.

Additionally, here are the keys that are otherwise not bound:

- ~<~ and ~>~ adjust the height of the minibuffer.
- ~c~ (=ivy-toggle-calling=) - toggle calling the current action each
  time a different candidate is selected.
- ~M~ (=ivy-rotate-preferred-builders=) - rotate regex matcher.
- ~w~ and ~s~ scroll the actions list.

Minibuffer editing is disabled when Hydra is active.

# Swiper #


# Counsel #


# Semx-mode #

[Smex Github](https://github.com/nonsequitur/smex)  

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

# Erc #

## Basic Command ##

| Command                    | Desc                                                              |
|:---------------------------|:------------------------------------------------------------------|
| /msg nickserv help         | register nickname                                                 |
| /nick NAME                 | change name                                                       |
| /names CHANNEL             | 查看当前[频道]所有用户                                            |
| /whois NAME                | 常看某人資料                                                      |
| /whoami                    |                                                                   |
| /who ip                    | 常看某IP登錄的所有用戶                                            |
| /Who CHANNEL               | 显示此频道的人                                                    |
| /Who *                     | 显示参加当前频道的人                                              |
| /join #CHANNEL             | 加入這個房間，如果房間不存在，服務器可能會創建這個房間            |
| /part #CHANNEL REASON      | 離開房間，并留下原因                                              |
| /quit REASON               | 退出服務器，并留下原因                                            |
| /away REASON               | 暫時離開，并留下原因                                              |
| /invite NICK #CHANNEL      | 邀請某人到指定房間                                                |
| /kick #CHANNEL NICK REASON | 剔出某人，附上原因，需要權限                                      |
| /topic #CHANNEL TOPIC      | 如果你是房間主持人，可以改變房間的主題                            |
| /me ACTION                 | 向当前聊天室中发送一个动作 (动作使用第三人称陈述，例如 /me jumps) |
| /msg NAME(or #CHANNEL)     | 有要說的話	向某人發信息                                        |
| /query NICK MESSAGE        | 私聊                                                              |
| /notice NICK(or #CHANNEL)  | 要說的話                                                          |
| /list                      | 查看服務器上所有房間及主題                                        |
| /list #ubuntu-cn           | 列出這個房間                                                      |
| /list -MIN a -MAX b        | 查看人數大于a小于b的房間                                          |
| /list * abc *              | 所有行abc字符串的房間                                             |
| /flush                     | 终止当前命令的输出操作                                            |
| /help                      | 显示所有IRC命令                                                   |
| /join                      | 加入/建立聊天室                                                   |
| /leave CHANNEL             | 离开某一频道                                                      |
| /mode +(-)i                | 锁住聊天室                                                        |
| /mode +(-)o                | 设定管理员权限                                                    |
| /knock                     | 要求进入私人聊天室                                                |
| /invite                    | 邀请用户进入私人聊天室                                            |
| /privmsg                   | 悄悄话                                                            |
| /ignore                    | 忽略                                                              |
| /topic                     | 更换聊天室主题                                                    |
| /kick                      | 把用户踢出聊天室                                                  |
| /quit                      | 退出聊天室                                                        |

# cua block #

[CUA Block](http://bamanzi.is-programmer.com/posts/23611.html)  
[LeeXah CUA-mode](http://ergoemacs.org/emacs/modernization_cua-mode.html)  

Emacs's cua-mode, is named after the IBM's Common User Accesss standard. However, according to Wikipedia  
IBM Common User Access the IBM CUA standard does not say cut/copy/paste are X C V keys. Quote:  

# neo-tree #

| Action                      | Keybinding |
|:----------------------------|-----------:|
| quick-look                  |        SPC |
| describe-mode               |          ? |
| stretch-toggle              |          A |
| select-down-node            |          D |
| hidden-file-toggle          |          H |
| select-previous-sibing-node |          S |
| select-up-node              |          U |
| refresh                     |          g |
| describe-mode               |          h |
| next-line                   |          n |
| open-file-in-system-app     |          o |
| previous-line               |          p |
| hide                        |          q |
| select-next-sibling-node    |          s |
| collapse-all                |    C-c C-a |
| change-root                 |    C-c C-c |
| delete-node                 |    C-c C-d |
| find-file-other-window      |    C-c C-f |
| create-node                 |    C-c C-n |
| copy-node                   |    C-c C-p |
| rename-node                 |    C-c C-r |
| dir                         |      C-c c |

# company-mode #

Company: Complete Anything

## 安装 ##

``` elisp
(use-package company
  :ensure t
  :config
  (global-company-mode t)
  (setq company-idle-delay 0)                 # 延迟，可设定为0.3
  (setq company-minimum-prefix-length 3)      # 至少打完3个字才启动
  (setq company-backends
        '((company-files
           company-keywords
           company-capf
           company-yasnippet
           )
          (company-abbrev company-dabbrev))))
```

``` elisp
(add-hook 'emacs-lisp-mode-hook (lambda ()
            (add-to-list (make-local-variable 'company-backends)
            '(company-elisp))))
```

## Company 跟 Yasnippet 按键冲突 ##

``` elisp
(advice-add 'company-complete-common :before (lambda () 
                                (setq my-company-point (point))))
(advice-add 'company-complete-common :after (lambda () 
                                (when (equal my-company-point (point)) (yas-expand))))
```

# calc #
[Calc-Getting-started](https://www.gnu.org/software/emacs/manual/html_node/calc/Getting-Started.html)  
[Calc-Tutorial](https://www.gnu.org/software/emacs/manual/html_node/calc/Tutorial.html)  
[Calc-Manual](https://www.gnu.org/software/emacs/manual/html_node/calc/Getting-Started.html)  

# c/c++ development #

[CProgrammingLanguage](https://www.emacswiki.org/emacs/CProgrammingLanguage)  
[Emacs Tags](https://www.emacswiki.org/emacs/EmacsTags)  
[Indentation](https://www.emacswiki.org/emacs/IndentingC)  
[C++Mode](https://www.emacswiki.org/emacs/CPlusPlusMode)  
[C/C++ Development Environment](http://tuhdo.github.io/c-ide.html)  
[RTags](https://github.com/Andersbakken/rtags)  


[^2]: If someone barfs, they vomit.
[^3]: If you slurp a liquid, you drink it noisily.
