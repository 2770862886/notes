% Org-mode

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Hello Worg](https://orgmode.org/worg/)  
[Org Mode - Organize Your Life In Plain Text!](http://doc.norang.ca/org-mode.html)  
[Bebel](https://orgmode.org/worg/org-contrib/babel/index.html)  

Introduction
============

Org-mode is fabulous organizational tool originally built by Casten Dominik that operators on plain text files. Org-mode is part of Emacs.  

## Typesetting conventions ##

Org mainly uses three types of keywords: TODO keywords, tags and property names.

+ TODO keywords are written with all capitals, even if they are use-defined.
+ Tags are case-sensitive. User-defined tags are written in lowercase; built-in tags with special meaning are written as they should appear in the document, usually with all capitals.
+ User-defined properties are capitalized; built-in properties with special meaning are written with all capitals.
+ Keywords and blocks are written in uppercase to enhance their readability, but you can use lowercase in your Org files.

Document Structure
==================

Headlines
---------

The name defined in `org-footnote-section` is reserved. Do not use it as a title for your own headings.

Visibility Cycling
------------------

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

Structure editing
-----------------

Sparse trees
------------

Plain lists
-----------

Drawers
-------

Blocks
------

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

Timestamps, Deadlines and Scheduling
------------------------------------

- Plain timestamp; Event; Appointment

  ``` org
  * Meet Peter at the movies
    <2006-11-01 Wed 19:15>
  * Discussion on climate change
    <2006-11-02 Thu 20:00-22:00>
  ```

- Timestamp with repeater interval

  ``` org
  * Pick up Sam at school
    <2007-05-16 Wed 12:30 +1w>
  ```

- Diary-style sexp entries

  ``` org
  * 22:00-23:00 The nerd meeting on every 2nd Thursday of the month
    <%%(diary-float t 4 2)>
  ```

- Time/Date range

  ``` org
  ** Meeting in Amsterdam
     <2004-08-23 Mon>--<2004-08-26 Thu>
  ```

- Inactive timestamp

  ``` org
  * Gillian comes late for the fifth time
    [2006-11-01 Wed]
  ```

Creating Timestamps
-------------------

* Keybinding for creating timestamp

| Action                                                                          |               Keybinding |
|:--------------------------------------------------------------------------------|-------------------------:|
| Prompt for a date and insert corresponding timestamp.                           |         <kbd>C-c .</kbd> |
| With a prefix, use the alternative format which containes date and time         |     <kbd>C-u C-c .</kbd> |
| With two prefix, insert an active timestamp with current time without prompting | <kbd>C-u C-u C-c .</kbd> |
| Insert an inactive timestamp                                                    |         <kbd>C-c !</kbd> |
| Normalize timestamp, insert or fix day name if missing or wrong                 |       <kbd>C-c C-c</kbd> |
| Insert a timestamp corresponding to point date in the calendar                  |        <kbd>C-c \<</kbd> |
| Access the Emacs calendar for the current date.                                 |        <kbd>C-c \></kbd> |
| Access the agenda for the date given by the timestamp or -range at point        |       <kbd>C-c C-o</kbd> |
| Change date at point by one day.                                                |        <kbd>S-LEFT</kbd> |
|                                                                                 |       <kbd>S-RIGHT</kbd> |
| On the beginning or enclsing bracket of a timestamp, change its type. Within a  |          <kbd>S-UP</kbd> |
| timestamp, change the item under point.                                         |        <kbd>S-DOWN</kbd> |
| Evaluate a time range by computing the difference between start and end.        |       <kbd>C-c C-y</kbd> |

* Keybinding for operation on calendar

| Action                               |               Keybinding |
|:-------------------------------------|-------------------------:|
| Choose date at point in calendar.    |       <kbd>\<RET\></kbd> |
| One day forward                      |   <kbd>S-\<RIGHT\></kbd> |
| One day backward                     |    <kbd>S-\<LEFT\></kbd> |
| One week forward                     |    <kbd>S-\<DOWN\></kbd> |
| One week backward                    |      <kbd>S-\<UP\></kbd> |
| One month forward                    | <kbd>M-S-\<RIGHT\></kbd> |
| One month backward                   |  <kbd>M-S-\<LEFT\></kbd> |
| Scroll calendar forward by on month  |            <kbd>\></kbd> |
| Scroll calendar backward by on month |            <kbd>\<</kbd> |
| Scroll calendar forward by 3 months  |           <kbd>M-v</kbd> |
| Scroll calendar backward by 3 months |           <kbd>C-v</kbd> |

Deadlines and Scheduling
------------------------
* DEADLINE
  On the deadline date, the task is listed in the agenda. In addition, the agenda for today carries a warning about the  
  approaching or missed deadline, starting `org-deadline-warning-days` before the due date, and continuing until the  
  entry is marked *DONE*.  

  ``` org
  *** TODO write article about the Earth for the Guide
      DEADLINE: <2004-02-29 Sun>
      The editor in charge is [[bbdb:Ford Prefect]]
  ```

  You can specify a differenct lead time for warnings for specific deadlines using the following syntax.  

  ``` org
  DEADLINE: <2004-02-29 Sun -5d>
  ```
  This warning is deactivated if the task gets scheduled and you set `org-agenda-skip-deadline-prewarning-if-scheduled`.

* SCHEDULED
  A reminder that the scheduled date has passed is present in the compilation for *today*, until the entry is marked *DONE*.

  ``` org
  *** TODO Call Trillian for a date on New Years Eve.
      SCHEDULED: <2004-12-25 Sat>
  ```
  If you want to delay the display of this task in the agenda, use `SCHEDULED: <2004-12-25 Sat -2d>`: the task is  
  still scheduled on the 25th but will appear two days later.  

### Inserting deadlines or schedules  ###

| Action                                                               |         Keybinding |
|:---------------------------------------------------------------------|-------------------:|
| Insert *DEADLINE* keyword along a stamp                              | <kbd>C-c C-d</kbd> |
| Insert *SCHEDULED* keyword along with a stamp                        | <kbd>C-c C-s</kbd> |
| Create a sparse tree with all deadlines that are either past-due,    | <kbd>C-c / d</kbd> |
| or will become due within `org-deadline-warning-days`. Also could    |                    |
| with C-u prefix, show all deadlines in the file. With numberic check |                    |
| that many days.                                                      |                    |
| Sparse tree for deadlines and scheduled items before a given date.   | <kbd>C-c / b</kbd> |
| Sparse tree for deadlines and scheduled items after a given date.    | <kbd>C-c / a</kbd> |

### Repeated tasks ###

``` org
** TODO Pay the rent
   DEADLINE: <2005-10-01 Sat +1m>
```

You can use yearly, monthly, weekly, daily and hourly repeat cookies by using the ‘y’, ‘w’, ‘m’, ‘d’ and ‘h’ letters.  

``` org
 ** TODO Call Father
    DEADLINE: <2008-02-10 Sun ++1w>
    Marking this DONE shifts the date by at least one week, but also
    by as many weeks as it takes to get this date into the future.
    However, it stays on a Sunday, even if you called and marked it
    done on Saturday.

 ** TODO Empty kitchen trash
    DEADLINE: <2008-02-08 Fri 20:00 ++1d>
    Marking this DONE shifts the date by at least one day, and also
    by as many days as it takes to get the timestamp into the future.
    Since there is a time in the timestamp, the next deadline in the
    future will be on today's date if you complete the task before
    20:00.

 ** TODO Check the batteries in the smoke detectors
    DEADLINE: <2005-11-01 Tue .+1m>
    Marking this DONE will shift the date to one month after today.
```

To mark a task with a repeater as *DONE*, use <kbd>C-u -1 C-c C-t</kbd>

Clocking Work Time
------------------

Org mode allows you to clock the time you spend on specific tasks in a project. When you start working  
on an item, you can start the clock. When you stop working on that task, or when you mark the task done,  
the clock is stopped and the corresponding time interval is recorded. It also computes the total time spent on  
each subtree of a project.

To save the clock history across Emacs sessions, use:

``` org
(setq org-clock-persist 'history)
(org-clock-persistence-insinuate)
```

### Clocking commands ###

| Action                                                                               |             Keybinding |
|:-------------------------------------------------------------------------------------|-----------------------:|
| Start the clock on the current item (clock-in).                                      | <kbd>C-c C-x C-i</kbd> |
| Stop the clock (clock-out).                                                          | <kbd>C-c C-x C-o</kbd> |
| Re-clock the last clocked task. With one `C-u` prefix argument,                      | <kbd>C-c C-x C-x</kbd> |
| select the task from the clock history. With two `C-u` prefixes, force               |                        |
| continuous clocking by starting the clock when the last clock stopped.               |                        |
| Update the effort estimate for the current clock task.                               | <kbd>C-c C-x C-e</kbd> |
| Recompute the time interval after changing one of the timestamps. This is            |     <kbd>C-c C-c</kbd> |
| only necessary if you edit the timestamps directly                                   |  or <kbd>C-c C-y</kbd> |
| On *CLOCK* log lines, increase/decrease both timestamps so that the clock            |      <kbd>C-S-UP</kbd> |
| duration keeps the same value.                                                       |    <kbd>C-S-DOWN</kbd> |
| Changing the *TODO* state of an item to *DONE* automatically stops the clock         |     <kbd>C-c C-t</kbd> |
| if it is running in this same time.                                                  |                        |
| Cancel the current clock. This is useful if a clock was started by mistake, or       | <kbd>C-c C-x C-q</kbd> |
| if you ended up working on something else.                                           |                        |
| Jump to the headline of the currently clocked in task.                               | <kbd>C-c C-x C-j</kbd> |
| Display time summaries for each subtree in the current buffer. The overlay disappear | <kbd>C-c C-x C-d</kbd> |
| when you change the buffer or press <kbd>C-c C-c</kbd>                               |                        |

### The clock table ###

Org mode can produce quite complex reports based on the time clocking information. Such a report is called  
a clock table, because it is formatted as one or several Org tables.  

| Action                                                                      |                Keybinding |
|:----------------------------------------------------------------------------|--------------------------:|
| Insert a dynamic block containing a clock report as an Org mode table into  |    <kbd>C-c C-x C-r</kbd> |
| the current file.                                                           |                           |
| Update dynamic block at point. Point needs to be in the *BEGIN* line of the |        <kbd>C-c C-c</kbd> |
| dynamic block.                                                              | or <kbd>C-c C-x C-u</kbd> |
| Shift the current *:block* interval and update the table.                   |         <kbd>S-LEFT</kbd> |
|                                                                             |        <kbd>S-RIGHT</kbd> |

### Resolving idle time and continuous clocking ###

You can also check all the files visited by your Org agenda for dangling clocks  
at any time using `M-x org-resolve-clocks RET` (or <kbd>C-c C-x C-z</kbd>).


Effort Estimates
----------------

| Action                                        |           Keybinding |
|:----------------------------------------------|---------------------:|
| Set the effort estimate for the current entry | <kbd>C-c C-x e</kbd> |
|                                               |                      |

Taking Notes with a Relative Timer
----------------------------------

| Action                                                                               |           Keybinding |
|:-------------------------------------------------------------------------------------|---------------------:|
| Start or reset the relative timer.                                                   | <kbd>C-c C-x 0</kbd> |
| Start a countdown timer.                                                             | <kbd>C-c C-x ;</kbd> |
| Insert a relative time into the buffer                                               | <kbd>C-c C-x .</kbd> |
| Insert a description list item with current relative time                            | <kbd>C-c C-x -</kbd> |
| Once the timer list is started, you can also use <kbd>M-RET</kbd> to insert          |     <kbd>M-RET</kbd> |
| new timer items.                                                                     |                      |
| Pause the timer, or continue it if it is already paused.                             | <kbd>C-c C-x ,</kbd> |
| Stop the time. After this, you can only start a new timer, not continue the old one. | <kbd>C-c C-x _</kbd> |
|                                                                                      |                      |

Capture - Refile - Archive
==========================

Capture
-------

### Setting up capture ###

``` elisp
(setq org-default-notes-file (concat org-directory "/notes.org"))
```

### Using capture ###

| Action                                                    |               Keybinding |
|:----------------------------------------------------------|-------------------------:|
| Display the capture templates menu                        |         <kbd>C-c c</kbd> |
| Finalize and then jump to the captured item               |       <kbd>C-c C-c</kbd> |
| Finalize and refile the note to a different place         |       <kbd>C-c C-w</kbd> |
| Ablort the capture process and return the previous state. |       <kbd>C-c C-k</kbd> |
| Visit the target location of a capture template.          |     <kbd>C-u C-c c</kbd> |
| Visit the last stored capture item in its buffer.         | <kbd>C-u C-u C-c c</kbd> |

### Capture templates ###

#### Template elements ####

* keys
  The keys that selects the template, as a string, characters only, for example '"a"', for a template  
  to be selected with a single key, or '"bt"' for selection with two keys. When using several keys, kyes  
  using the same prefix key must be sequential in the list and preceded by a 2-element entry explaning the  
  prefix key.

* description
  A short string describing the template, shown during selection.  

* type
  The type of entry, a symbol. Valid values are:  
  |:-------------|---------------------------------------------------------------------------------------|
  | *entry*      | An Org mode node, with headline. Will be filed as the child of the target entry or as |
  |              | a top-level entry. The target file should be an Org file.                             |
  | *item*       | A plain list item, placed in the first plain list at the target location.             |
  |              | Again the target file should be an Org file.                                          |
  | *checkitem*  | A checkbox item. This only differs from the plain list item by the default template.  |
  | *table-line* | A new line in the first table at the target location. Where exactly the line will be  |
  |              | inserted depends on the properties `:prepend` and `:table-line-position`              |
  | *plain*      | Text to be inserted as it is.                                                         |
  |:-------------|---------------------------------------------------------------------------------------|

* target
  Specification of where the captured item should be placed. In Org files, targets usually define a node.  
  Entries will become children of this node. Other types will be added to the table or list in the body of  
  this node. Most target specifications contain a file name. If that file name is the empty string, it defaults  
  to **org-default-notes-file**. A file can also be given as a variable or as a function called with no argument. 
  When an absolute path is not specified for a target, it is taken as relative to **org-direcotry**.  
  
  + `(file "path/to/file")`
    Text will be placed at the beginning or end of that file.  
  + `(id "id of existing org entry")`
    Filing as child of this entry, or in the body of the entry.  
  + `(file+headline "filename" "node headline")`
    Fast configuration if the target heading is unique in the file.  
  + `(file+olp "filename" "Level 1 heading" "Level 2" ...)`
    For non-unique headings, the full path is safer.  
  + `(file+regexp "filename" "regexp to find location")`
    Use a regular expression to postion point.  
  + `(file+olp+datetree "filename" ["Level 1 heading" ...])`
    This target creates a heading in a date tree for today's date. If the optional outline path is given,  
    the tree will be built under the node it is pointing to, instead of at top level. Check out the  
    `:time-prompt` and `:tree-type` properties below for additional options.  
  + `(file+function "filename" function-finding-location)`
     A function to find the right location in the file.  
  + `(clock)`
    File to the entry that is currently being clocked.  
  + `(function function-finding-location)`
    Most general way: write your own function which both visits the file and moves point to the  
    right location.  

* template
  The template for creating the capture item. If you leave this empty, an appropriate default template will  
  be used. Otherwise this is a string with escape codes, which will be replaced depending on time and context  
  of the capture call. The string with escapes may be loaded from a template file, using the special syntax  
  `(file "template filename")`  

* properties
  The rest of the entry is a property list of additional options. Recognized properties are:  
  + `:prepend`
    Normaly new captured information will be appended at the target location (last child, last table line, 
    last list item, ...). Setting this property changes that.  
  + `:immediate-finish`
    When set, do not offer to edit the information, just file it away immediately. This makes sense if the  
    template only needs information that can be added automatically.  
  + `:empty-lines`
    Set this to the number of lines to insert before and after the new item. Default 0, and the only other  
    common value is 1.  
  + `:clock-in`
    Start the clock in this item.  
  + `:clock-keep`
    Keep the clock running when filing the captured entry.  
  + `:clock-resume`
    If starting the captrue interrupted a clock, restart that clock when finish with the capture.  
    Note that: `clock-keep` has precedence over `:clock-resume`. When setting both to non-nil, the  
    current clock will run and the previous one will not be resumed.  
  + `:time-prompt`
    Prompt for a date/time to be used for date/week trees and when filling the template. Without this  
    property, capture uses the current date and time. Even if this property has not been set, you can  
    force the same behavior by calling **org-capture** with a <kbd>C-1</kbd> prefix argument.  
  + `:tree-type`
    When **week** make a week tree instead of the month tree, i.e., place the heading for each day under  
    a heading with the current **ISO** week.  
  + `:unnarrowed`
    Do not narrow the target buffer, simply show the full buffer. Default is to narrow it so that you only  
    see the new material.  
  + `:table-line-pos`
    Specification of the location in the table where the new line should be inserted. It should be a string like  
    'II-3' meaning that the new line should become the third line before the second horizontal separator line.  
  + `:kill-buffer`
    If the target file was not yet visited when capture was invoked, kill the buffer again after capture is  
    completed.  
  + `:no-save`
    Do not save the target file after finishing the capture.  

#### Template expansion ####
 * `%[FILE]`
 * `%(EXP)`
 * `%<FORMAT>`
 * `%t`
   Timestamp, date only.  
 * `%T`
   Timestamp, with date and time.  
 * `%u`, `%U`
   Like `%t`, `%T` above, but inactive timestamps.  
 * `%i`
   Initial content, the region when capture is called while the region is active. If there is text before  
   on the same line, such as indentation, and `%i` is not inside a `%(exp)` form, that prefix is added before  
   every line in the inserted text.  
 * `%a`
   Annotation, normally the link created with **org-store-link**.
 * `%A`
   Like `%a`, but prompt for the description part.  
 * `%l`
   Link `%a`, but only insert the literal link.  
 * `%c`
   Current kill ring head.  
 * `%x`
   Content of the **X** clipboard.  
 * `%k`
   Title of the currently clocked task.  
 * `%K`
   Link to the currently clocked task.  
 * `%n`
   User name (taken from **user-full-name**).
 * `%f`
   File visited by current buffer when **org-capture** was called.  
 * `%F`
   Full path of the file or directory visited by current buffer.  
 * `%:keyword`
   Specific information for certain link types, see below.  
 * `%^g`
   Prompt for tags, with completion on tags in target file.  
 * `%^G`
   Prompt for tags, with completion all tags in all agenda files.  
 * `%^t`
   Like `%t`, but prompt for date. Similarly `%^T`, `%^u`, `%^U`. You may define a prompt like `$^{Birthday}t`  
 * `%^C`
   Interactive selection of which kill or clip to use.  
 * `%^L`
   Like `%^C`, but insert as link.  
 * `%^{PROP}p`
   Prompt the user for a value for property PROP.  
 * `%^{PROMPT}`
   Prompt the user for a string and replace this sequence with it. You may specify a default value and  
   completion table with `%^{prompt|default|completion2|completion3...}`. The arrow keys access a  
   prompt-specific history.  
 * `%\N`
   Insert the text entered at the Nth `%^{PROMPT}`, where N is a number, starting from 1.  
 * `%?`
   After completing the template, position point here.  

 For specific link types, the following keywords are defined:  
 | Link type    | Available keywords                                       |
 |:-------------|----------------------------------------------------------|
 | bbdb         | `%:name`, `%:company`                                    |
 | irc          | `%:server`, `%:port`, `%:nick`                           |
 | mh, rmail    | `%:type`, `%:subject`, `%:message-id`                    |
 |              | `%:from`, `%:fromname`, `%fromaddress`                   |
 |              | `%:to`,`%:toname`, `%:toaddress`                         |
 |              | `%:date`(message date header field),                     |
 |              | `%:date-timestamp`(date as active timestamp),            |
 |              | `%:date-timestamp-inactive`(date as inactive timestamp), |
 |              | `%:fromto`(either "to NAME" or "fomr NAME")              |
 | gnus         | `%:group`, for messages also all email fields            |
 | w3, w3m      | `%:url`                                                  |
 | info         | `%:file`, `%:node`                                       |
 | calendar     | `%:date`                                                 |
 | org-protocol | `%:link`,`%:description`,`%:annotation`                  |

#### Templates in contexts ####

``` elisp
(setq org-capture-templates-contexts
    '(("p" (in-mode . "message-mode"))))
```

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

Hacking
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


Building a Second Brain in Org Mode
===================================

P.A.R.A. [Projects areas resourses archives]

+ Projects: A series of tasks linked to a goal, with a deadline
+ Area of responsiblity: A sphere of activity with a standard to be maintained over time
+ Resource: A topic or theme of ongoing interest
+ Archive: Inactive items from the other 3 categories

File Structure
--------------

+ inbox.org
+ todo.org
+ somedaymaybe.org
+ agendas.org
+ goals.org

+ Column View
+ Weekly review, Monthly review

Important Packages
------------------

+ org-gcal
+ org-cliplink
+ ox-clip
+ org-randomnote

Reference
---------

+ BASB: the seminal course
+ Praxis: Tiago Forte's blog on productivity
+ BASB in Emacs + org and IASB in Emacs + Org: my original posts about
+ Gist with GTD templates: try-them-at-home templates for your own use + workflow
+ My configuration: 
