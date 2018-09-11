% markdown-mode in Emacs
<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Setext](https://en.wikipedia.org/wiki/Setext "Structure Enhanced Text")  
[Aaron Swartz's Atx](https://en.wikipedia.org/wiki/Aaron_Swartz#atx "Atx")  
[Guide to Markdown Mode for Emacs](https://leanpub.com/markdown-mode/read)  
[Pandoc User's Guide](http://pandoc.org/MANUAL.html)  
[Write Better Markdown](http://brettterpstra.com/2015/08/24/write-better-markdown/)  

markdown-mode is a major mode for editing markdown-formatted text.  

The commands for styling text are grouped under <kbd>C-c C-s</kbd>, and toggle commands begin with <kbd>C-c C-x</kbd>, movement and shifting commands tend to be with paired delimiters such as <kbd>M-{</kbd> and <kbd>M-}</kbd> or <kbd>C-c <</kbd> and <kbd>C-c ></kbd>, finally commands for running Markdown or doing maintenance on an open file are grouped under the <kbd>C-c C-c</kbd> prefix. The most commonly used commands are described by pressing <kbd>C-c C-h</kbd>.  

## Quick Reference ##

| Action                                          |                  Keybinding |
|:------------------------------------------------|----------------------------:|
| ***Headings***                                  |                             |
| Insert heading dpending on context              |        <kbd>C-c C-s h</kbd> |
| Insert heading, prefer setext                   |        <kbd>C-c C-s H</kbd> |
| Insert atx heading of level # = 1, 2, ... 6     |        <kbd>C-c C-s #</kbd> |
| Insert setext heading of level 1                |        <kbd>C-c C-s !</kbd> |
| Insert setext heading of level 2                |        <kbd>C-c C-s @</kbd> |
| ***Inline Elements***                           |                             |
| Bold                                            |        <kbd>C-c C-s b</kbd> |
| Italics                                         |        <kbd>C-c C-s i</kbd> |
| Inline code                                     |        <kbd>C-c C-s c</kbd> |
| kbd tags                                        |        <kbd>C-c C-s k</kbd> |
| Wiki link                                       |        <kbd>C-c C-s w</kbd> |
| ***Block Elements***                            |                             |
| Preformatted/code block                         |        <kbd>C-c C-s p</kbd> |
| Preformatted/code block (region)                |        <kbd>C-c C-s P</kbd> |
| Blockquote                                      |        <kbd>C-c C-s q</kbd> |
| Blockquote (region)                             |        <kbd>C-c C-s Q</kbd> |
| GFM code block                                  |        <kbd>C-c C-s C</kbd> |
| Edit code block in indirect buffer              |            <kbd>C-c '</kbd> |
| ***Links and Images***                          |                             |
| Insert or edit link (inline, reference, or URL) |          <kbd>C-c C-l</kbd> |
| Insert or edit image (inline, reference)        |          <kbd>C-c C-i</kbd> |
| Follow link at point                            |          <kbd>C-c C-o</kbd> |
| Jump between reference link and definition      |          <kbd>C-c C-d</kbd> |
| Move to next link                               |              <kbd>M-n</kbd> |
| Move to previouse link                          |              <kbd>M-p</kbd> |
| ***Footnotes***                                 |                             |
| Insert footnote                                 |        <kbd>C-c C-s f</kbd> |
| Jump between footnote and definition            |          <kbd>C-c C-d</kbd> |
| ***List Items & List Editing***                 |                             |
| Insert new list item (same level)               |            <kbd>M-RET</kbd> |
| Insert new list item (same level)               |          <kbd>C-c C-j</kbd> |
| Insert new list item (parent level)             |      <kbd>C-u C-c C-j</kbd> |
| Insert new list item (child level)              |  <kbd>C-u C-u C-c C-j</kbd> |
| Move list item up                               |       <kbd>C-c \<up\></kbd> |
| Move list item down                             |     <kbd>C-c \<down\></kbd> |
| Outdent/promote list item                       |     <kbd>C-c \<left\></kbd> |
| Indent/demote list item                         |     <kbd>C-c \<down\></kbd> |
| Toggle GFM checkbox                             |      <kbd>C-c C-x C-x</kbd> |
| ***Table Editing***                             |                             |
| Converts the active region to table             | <kbd>C-c C-c \<pipe\></kbd> |
| Switch table column and row (transpose)         |        <kbd>C-c C-c t</kbd> |
| Sort lines                                      |        <kbd>C-c C-c ^</kbd> |
| Insert row                                      |   <kbd>C-c S-\<down\></kbd> |
| Delete row                                      |     <kbd>C-c S-\<up\></kbd> |
| Insert column                                   |  <kbd>C-c S-\<right\></kbd> |
| Delete Column                                   |   <kbd>C-c S-\<left\></kbd> |
| ***Horizontal Rules***                          |                             |
| Insert default horizontal rule string           |        <kbd>C-c C-s -</kbd> |
| ***Killing and Yanking***                       |                             |
| Kill element and keep text in kill ring         |          <kbd>C-c C-k</kbd> |
| Yank text back info buffer                      |              <kbd>C-y</kbd> |
| ***Movement by Paragraph***                     |                             |
| Backward paragraph                              |              <kbd>M-{</kbd> |
| Forward paragraph                               |              <kbd>M-}</kbd> |
| Mark paragraph                                  |              <kbd>M-h</kbd> |
| ***Movement by Block***                         |                             |
| Backward block                                  |            <kbd>C-M-{</kbd> |
| Forward block                                   |            <kbd>C-M-}</kbd> |
| Mark block                                      |          <kbd>C-c M-h</kbd> |
| Narrow to block                                 |          <kbd>C-x n b</kbd> |
| Widen                                           |          <kbd>C-x n w</kbd> |
| ***Movement by Section (Defun)***               |                             |
| Beginning of section                            |            <kbd>C-M-a</kbd> |
| End of section                                  |            <kbd>C-M-e</kbd> |
| Mark section                                    |            <kbd>C-M-h</kbd> |
| Mark subtree                                    |        <kbd>C-c C-M-h</kbd> |
| Narrow to section                               |          <kbd>C-x n d</kbd> |
| Narrow to subtree                               |          <kbd>C-x n s</kbd> |
| Widen                                           |          <kbd>C-x n w</kbd> |
| ***Outline & List Movement***                   |                             |
| Next heading or list item                       |          <kbd>C-c C-n</kbd> |
| Previous heading or list item                   |          <kbd>C-c C-p</kbd> |
| Next heading or list item (same level)          |          <kbd>C-c C-f</kbd> |
| Previous heading or list item (same level)      |          <kbd>C-c C-b</kbd> |
| Move up to parent heading or list item          |          <kbd>C-c C-u</kbd> |
| ***Outline Visibility Cycling***                |                             |
| Cycle visibility globally                       |            <kbd>S-TAB</kbd> |
| Cycle visibility of heading at point            |              <kbd>TAB</kbd> |
| ***Outline Subtree Editing***                   |                             |
| Move subtree up                                 |         <kbd>C-c <up></kbd> |
| Move subtree down                               |       <kbd>C-c <down></kbd> |
| Promote subtree                                 |       <kbd>C-c <left></kbd> |
| Demote subtree                                  |      <kbd>C-c <right></kbd> |
| ***Region Editing***                            |                             |
| Indent region                                   |            <kbd>C-c ></kbd> |
| Outdent region                                  |            <kbd>C-c <</kbd> |
| ***Promotion and Demotion***                    |                             |
| Promote element at point                        |            <kbd>C-c -</kbd> |
| Demote element at point                         |            <kbd>C-c =</kbd> |
| ***Markup Completion***                         |                             |
| Complete markup at point or at region           |          <kbd>C-c C-]</kbd> |
| Complete markup in buffer                       |      <kbd>C-c C-c C-]</kbd> |
| ***Markdown & Utility Commands***               |                             |
| Run Markdown, output to temporary buffer        |        <kbd>C-c C-c m</kbd> |
| Run Markdown, export to file                    |        <kbd>C-c C-c e</kbd> |
| Run Markdown, preview in browser                |        <kbd>C-c C-c p</kbd> |
| Run Markdown, export, and preview               |        <kbd>C-c C-c v</kbd> |
| Run Markdown, save to killing ring              |        <kbd>C-c C-c w</kbd> |
| Toggle live preview mode                        |        <kbd>C-c C-c l</kbd> |
| Open external previewer                         |        <kbd>C-c C-c o</kbd> |
| Check references in buffer                      |        <kbd>C-c C-c c</kbd> |
| Renumbered ordered lists in buffer              |        <kbd>C-c C-c n</kbd> |
| ***Toggles and Settings***                      |                             |
| Toggle markup hiding                            |        <kbd>C-c C-x m</kbd> |
| Toggle URL hiding                               |        <kbd>C-c C-x l</kbd> |
| Toggle native code block font lock              |        <kbd>C-c C-x f</kbd> |
| Toggle inline images                            |        <kbd>C-c C-x i</kbd> |
| Toggle LaTeX math support                       |        <kbd>C-c C-x e</kbd> |
| Toggle GFM checkbox                             |        <kbd>C-c C-x x</kbd> |
|                                                 |                             |

## GitHub Flavored Markdown (GFM) ##

A [GitHub Flavored Markdown][GFM] mode, `gfm-mode`, is also
available.  The GitHub implementation differs slightly from
standard Markdown in that it supports things like different
behavior for underscores inside of words, automatic linking of
URLs, strikethrough text, and fenced code blocks with an optional
language keyword.

The GFM-specific features above apply to `README.md` files, wiki
pages, and other Markdown-formatted files in repositories on
GitHub.  GitHub also enables [additional features][GFM comments] for
writing on the site (for issues, pull requests, messages, etc.)
that are further extensions of GFM.  These features include task
lists (checkboxes), newlines corresponding to hard line breaks,
auto-linked references to issues and commits, wiki links, and so
on.  To make matters more confusing, although task lists are not
part of [GFM proper][GFM], [since 2014][] they are rendered (in a
read-only fashion) in all Markdown documents in repositories on the
site.  These additional extensions are supported to varying degrees
by `markdown-mode` and `gfm-mode` as described below.

* **URL autolinking:** Both `markdown-mode` and `gfm-mode` support
  highlighting of URLs without angle brackets.

* **Multiple underscores in words:** You must enable `gfm-mode` to
  toggle support for underscores inside of words. In this mode
  variable names such as `a_test_variable` will not trigger
  emphasis (italics).

* **Fenced code blocks:** Code blocks quoted with backquotes, with
  optional programming language keywords, are highlighted in
  both `markdown-mode` and `gfm-mode`.  They can be inserted with
  <kbd>C-c C-s C</kbd>.  If there is an active region, the text in the
  region will be placed inside the code block.  You will be
  prompted for the name of the language, but may press enter to
  continue without naming a language.

* **Strikethrough:** Strikethrough text is supported in both
  `markdown-mode` and `gfm-mode`.  It can be inserted (and toggled)
  using <kbd>C-c C-s s</kbd>.

* **Task lists:** GFM task lists will be rendered as checkboxes
  (Emacs buttons) in both `markdown-mode` and `gfm-mode` when
  `markdown-make-gfm-checkboxes-buttons` is set to a non-nil value
  (and it is set to t by default).  These checkboxes can be
  toggled by clicking `mouse-1`, pressing <kbd>RET</kbd> over the button,
  or by pressing <kbd>C-c C-d</kbd> (`markdown-do`) with the point anywhere
  in the task list item.  A normal list item can be turned to a
  check list item by the same command, or more specifically
  <kbd>C-c C-s [</kbd> (`markdown-insert-gfm-checkbox`).

* **Wiki links:** Generic wiki links are supported in
  `markdown-mode`, but in `gfm-mode` specifically they will be
  treated as they are on GitHub: spaces will be replaced by hyphens
  in filenames and the first letter of the filename will be
  capitalized.  For example, `[[wiki link]]` will map to a file
  named `Wiki-link` with the same extension as the current file.
  If a file with this name does not exist in the current directory,
  the first match in a subdirectory, if any, will be used instead.

* **Newlines:** Neither `markdown-mode` nor `gfm-mode` do anything
  specifically with respect to newline behavior.  If you use
  `gfm-mode` mostly to write text for comments or issues on the
  GitHub site--where newlines are significant and correspond to
  hard line breaks--then you may want to enable `visual-line-mode`
  for line wrapping in buffers.  You can do this with a
  `gfm-mode-hook` as follows:

    ```lisp
    ;; Use visual-line-mode in gfm-mode
    (defun my-gfm-mode-hook ()
      (visual-line-mode 1))
    (add-hook 'gfm-mode-hook 'my-gfm-mode-hook)
    ```

* **Preview:** GFM-specific preview can be powered by setting
  `markdown-command` to use [Docter][].  This may also be
  configured to work with [Marked 2][] for `markdown-open-command`.

[GFM]: http://github.github.com/github-flavored-markdown/
[GFM comments]: https://help.github.com/articles/writing-on-github/
[since 2014]: https://github.com/blog/1825-task-lists-in-all-markdown-documents
[Docter]: https://github.com/alampros/Docter

## Markdown syntax and pandoc expand ##

### title ###

### list ###

### paragrah ###

### quot ###

### style ###

### link ###

### image ###

### horizontal line ###

### code block ###

