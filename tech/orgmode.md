% Org-mode

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Hello Worg](https://orgmode.org/worg/)


Org-mode is fabulous organizational tool originally built by Casten Dominik that operators on plain text files. Org-mode is part of Emacs.  

Introduction
============

Typesetting conventions
-----------------------

Org mainly uses three types of keywords: TODO keywords, tags and property names.
+ TODO keywords are written with all capitals, even if they are use-defined.


Document Structure
==================

## Outlines ##
Org is on top of outline-mode  

## Headlines ##
The name defined in `org-footnote-section` is reserved. Do not use it as a title for your own headings.

## Visibility Cycling ##

### Global and local cycling ###

| Action                                                 | Command                     |                 Keybinding |
|:-------------------------------------------------------|:----------------------------|---------------------------:|
| Rotate current subtree among the states                | org-cycle                   |             <kbd>TAB</kbd> |
| Rotate the entire buffer among the states              | org-global-cycle            |         <kbd>C-u TAB</kbd> |
|                                                        |                             |           <kbd>S-TAB</kbd> |
| Switch back to startup visibility                      | org-set-startup-visibility  |     <kbd>C-u C-u TAB</kbd> |
| Show all, including drawers                            | outline-show-all            | <kbd>C-u C-u C-u TAB</kbd> |
| Reveal context around point, showing the current entry | org-reveal                  |         <kbd>C-c C-r</kbd> |
| Expose all the headings                                | outline-show-branches       |         <kbd>C-c C-k</kbd> |
| Expose all direct children of the subtree              | outline-show-children       |         <kbd>C-c TAB</kbd> |
| Show the current subtree in an indirect buffer         | org-tree-to-indirect-buffer |       <kbd>C-c C-x b</kbd> |
| Copy the visible text in the region into the kill ring | org-copy-visible            |       <kbd>C-c C-x v</kbd> |
|                                                        |                             |                            |

### Initial visibility ###

``` org
#+STARTUP: overview
#+STARTUP: content
#+STARTUP: showall
#+STARTUP: showeverything
```
| Action                                              |             Keybinding |
|:----------------------------------------------------|-----------------------:|
| Switch back to the startup visibility of the buffer | <kbd>C-u C-u TAB</kbd> |
|                                                     |                        |


### Catching invisible edits ###

Motion
------

| Action                             |         Keybinding |
|:-----------------------------------|-------------------:|
| Next heading                       | <kbd>C-c C-n</kbd> |
| Previous heading                   | <kbd>C-c C-p</kbd> |
| Next heading same level            | <kbd>C-c C-f</kbd> |
| Previous heading same level        | <kbd>C-c C-b</kbd> |
| Backward to heighter level heading | <kbd>C-c C-u</kbd> |

Structure editing
-----------------

Sparse trees
------------

Plain lists
-----------

Footnotes
---------

Tables
======

| Action                                |                        Keybinding |
|:--------------------------------------|----------------------------------:|
| Move cursor to next cell              |                    <kbd>TAB</kbd> |
| Insert a column before current column |          <kbd>M-S-\<right\></kbd> |
| Delete current column                 |           <kbd>M-S-\<left\></kbd> |
| Insert a row before current row       |           <kbd>M-S-\<down\></kbd> |
| Delete current row                    |             <kbd>M-S-\<up\></kbd> |
| Move to next row or create a row      |                    <kbd>C-m</kbd> |
| Move current row up/down              |    <kbd>M-\<up\>/M-\<down\></kbd> |
| Move current column left/right        | <kbd>M-\<left\>/M-\<right\></kbd> |
| Edit current cell                     |                  <kbd>C-c `</kbd> |
| Cut cell content                      |            <kbd>C-c C-x C-w</kbd> |
| Paste clipboard to cell               |            <kbd>C-c C-x C-y</kbd> |
| Paste cell to next row                |           <kbd>S-\<return\></kbd> |
| Force table reorder                   |                <kbd>C-c C-c</kbd> |
| Sort table                            |                  <kbd>C-c ^</kbd> |

Hyperlinks
==========

TODO Items
==========

Tags
====

Properties and Columns
======================

Dates and Times
===============

Capture - Refile - Archive
==========================

Capture
-------

Attachment
----------

RSS feeds
---------

Protocols for external access
-----------------------------

Refile and copy
---------------

Archiving
---------


| Action                      |             Keybinding |
|:----------------------------|-----------------------:|
| org-archive-subtree-default | <kbd>C-c C-x C-a</kbd> |
|                             |                        |

Agenda Views
============


Markup for Rich Contents
========================

Exporting
=========

Publishing
==========

Working with Source Code
========================

Miscellaneous
=============

hacking
=======

Hooks
-----

Add-on Packages
---------------

Adding Hyperlink Types
----------------------

Adding Export Back-ends
-----------------------

Tables in Arbitary Syntax
-------------------------

Dynamic Blocks
--------------

Special Agenda Views
--------------------

Speeding Up Your Agendas
------------------------

Extracting Agenda Information
-----------------------------

Using the Property API
----------------------

Using the Mapping API
---------------------


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
