% Org-mode

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Hello Worg](https://orgmode.org/worg/)


Org-mode is fabulous organizational tool originally built by Casten Dominik that operators on plain text files. Org-mode is part of Emacs.  

# Document Structure #

## Outlines ##
Org is on top of outline-mode  

## Headlines ##
The name defined in `org-footnote-section` is reserved. Do not use it as a title for your own headings.

## Visibility Cycling ##

### Global and local cycling ###

| Action                                                 | Command                    | Keybinding      |
|:-------------------------------------------------------|:---------------------------|-----------------|
| Rotate current subtree among the states                | org-cycle                  | TAB             |
| Rotate the entire buffer among the states              | org-global-cycle           | C-u TAB         |
|                                                        |                            | S-TAB           |
| Switch back to startup visibility                      | org-set-startup-visibility | C-u C-u TAB     |
| Show all, including drawers                            | outline-show-all           | C-u C-u C-u TAB |
| Reveal context around point, showing the current entry | org-reveal                 | C-c C-r         |
| Expose all the headings                                |                            |                 |


### Initial visibility ###

### Catching invisible edits ###

Motion
------

| Action                             | Command | Keybinding |
|:-----------------------------------|:--------|------------|
| Next heading                       |         | C-c C-n    |
| Previous heading                   |         | C-c C-p    |
| Next heading same level            |         | C-c C-f    |
| Previous heading same level        |         | C-c C-b    |
| Backward to heighter level heading |         | C-c C-u    |
|                                    |         |            |

## Structure editing ##

## Sparse trees ##

## Plain lists ##

## Footnotes ##

# Tables #

# Hyperlinks #

# TODO Items #

# Tags #

# Properties and Columns #

# Dates and Times #

# Capture - Refile - Archive #

| Action                      |             Keybinding |
|:----------------------------|-----------------------:|
| org-archive-subtree-default | <kbd>C-c C-x C-a</kbd> |
|                             |                        |

# Agenda Views #

# Markup for Rich Contents #

# Exporting #

# Publishing #

# Working with Source Code #

# Miscellaneous #

# hacking #
## Hooks ##

## Add-on Packages ##

## Adding Hyperlink Types ##

## Adding Export Back-ends ##

## Tables in Arbitary Syntax ##

## Dynamic Blocks ##

## Special Agenda Views ##

## Speeding Up Your Agendas ##

## Extracting Agenda Information ##

## Using the Property API ##

## Using the Mapping API ##

-------------------------------------------------------------------------------

# Building a Second Brain in Org Mode #

P.A.R.A. [Projects areas resourses archives]

+ Projects: A series of tasks linked to a goal, with a deadline
+ Area of responsiblity: A sphere of activity with a standard to be maintained over time
+ Resource: A topic or theme of ongoing interest
+ Archive: Inactive items from the other 3 categories

## File Structure ##

+ inbox.org
+ todo.org
+ somedaymaybe.org
+ agendas.org
+ goals.org

+ Column View
+ Weekly review, Monthly review

## Important Packages ##

+ org-gcal
+ org-cliplink
+ ox-clip
+ org-randomnote

## Reference ##

+ BASB: the seminal course
+ Praxis: Tiago Forte's blog on productivity
+ BASB in Emacs + org and IASB in Emacs + Org: my original posts about
+ Gist with GTD templates: try-them-at-home templates for your own use + workflow
+ My configuration: 


