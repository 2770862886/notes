markdown-mode in emacs
======================

# Keybinding prefix #
C-c C-s
C-c C-x

# Command for doing things #
C-c C-d:
to do something sensible with the object at the point:
1. Jumps between reference links and reference definitions. 
If more than one link uses the same reference label, a window
will be shown containing clickable buttons for jumping to each 
link. Pressing TAB or S-TAB cycles between buttons in this window.
2. Jumps between footnote markers and footnote text.
3. Toggles the completion status of GFM task list items (checkboxes).

# Completion #
C-c C-]: complete markup is in normalized form, which means, for example, the
unerline portion of a setext is the same length as the heading text, or that the
number of leading and trailing hash marks of an ATX header are equal and that
there is no extra whitespace in the header texts. C-c C-] completes the markup
at the point, if it is determinted to be incomplete.

# Command for following links #
C-c C-o: 
1. behave then the point is on an inline or reference link to open the URL
in a browser.
2. When the point is at a wiki link, open it in another buffer (in the current window, or in
the other window with the C-u prefix). Use M-p and M-n to quickly jump to the previous or next
link of any type.

# Editing #

## Headings ##
C-c C-s h/H
inserts a heading with automatically chosen type and level. 

## Promotion and demotion ##
C-c C--: Promotion or decreasing level.
C-c C-=: Demotion or increasing level.

## Text Styles ##
C-c C-s i: make a region or word *italic*
C-c C-s b: for bold
C-c C-s k: for "<kbd>" tags
C-c C-s c: for inline code
C-c C-s q: inserts a blockquote using the active region, if any, or starts a new blockquote
C-c C-s Q: is a variation which always operates on the region, regardless of whether it is active
or not.
C-c C-s p: behaves similarly for inserting preformatted code blocks (with the C-c C-s P being the 
region-only conterpart) and C-c C-s C inserts a GFM style backquote fenced code block.

## Lists ##
  * New list can be inserted by M-RET or C-c C-j.
  * This command determintes the propriate marker (one of the possible unordered list marker or the
  text number in sequence for an ordered lis) and indentation level by the nearby list items. If there
  is no list item before or after by the point, start a new list.
  * Existing list item can be moved up or down by C-c UP or C-c DOWN.

## Subtree ##
  * Entire subtrees of an ATX headings can be promoted or demoted with C-c
  * Subtree can be moved with C-c LEFT and C-c RIGHT
  * And can be moved up and down with C-c UP and C-c DOWN

## Shift Regions ##
  * Text in the region can be indented or outdented as a group using C-c > to
    indent to the next indentation point, and C-c < to outdent to previous indentation
    point.

## Killing Elements ##
  * C-c C-k: 

## Tables ##
  * C-c C-c |: converts the active region to table
  * C-c C-c t: transpose
  * C-c C-c ^: sort lines
  * C-c S-DOWN: insert row
  * C-c S-UP: delete row
  * C-c S-LEFT: delete column
  * C-c S-RIGHT: insert column

| Albert   | Hawking   |    Tesla |
| Relative | BlockHole | Electron |

## Horizontal Rules ##
C-c C-s -: inserts an horitontal line which will translate to "<hr/>"

## Foot notes ##
C-c C-s f:
[^1]
inserts a footnote marker at point, inserts a footnote definition at below, and postions
the point for inserting the footnote text

## Links and Images ##

### Links ###
C-c C-l: is a general command for inserting new link markup or editing existing link markup.
[Github Wiki](2770862886.github.com "Albert Leung")
If both a URL and link text are given, insert an inline link: [text](url).
If both a [reference] label and link text are given, insert a reference link: [text][reference].
If only link text is given, insert an implicit reference link: [text][].
If only a URL is given, insert a plain URL link: <url>.

### Images ###
C-c C-i: is a general command for inserting and editing image markup.
![LOGO](log.png "Albert Leung")
If both a URL and alt text are given, insert an inline image: ![alt text](url).
If both a [reference] label and alt text are given, insert a reference link: ![alt text][reference].

## Wiki links ##
C-c C-s w:
inserts a wiki link of the form of WikiLink. If there is an active region, use the region
as the link text. If the point is at a word, use the word as the link text. If there is no
active region and the point is not at a word, simply insert link markup.

# Markdown and Maintenance #
To summarize:

C-c C-c m: markdown-command > *markdown-output* buffer.
C-c C-c p: markdown-command > temporary file > browser.
C-c C-c e: markdown-command > basename.html.
C-c C-c v: markdown-command > basename.html > browser.
C-c C-c w: markdown-command > kill ring.
C-c C-c o: markdown-open-command.
C-c C-c l: markdown-live-preview-mode > *eww* buffer.

# GitHub Flavored Markdown (GFM) gfm-mode #

The GFM-specific features above apply to README.md files, wiki pages, and other 
Markdown-formatted files in repositories on GitHub. GitHub also enables additional 
features for writing on the site (for issues, pull requests, messages, etc.) that are further
extensions of GFM. These features include task lists (checkboxes), newlines corresponding
to hard line breaks, auto-linked references to issues and commits, wiki links, and so on. 
To make matters more confusing, although task lists are not part of GFM proper, 
since 2014 they are rendered (in a read-only fashion) in all Markdown documents in 
repositories on the site. These additional extensions are supported to varying degrees
by markdown-mode and gfm-mode as described below.

[^1]: 
