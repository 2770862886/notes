% Linux Kernel Learning Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Linux Kernel Doc](https://www.kernel.org/doc/)
[Online manual](http://man7.org/index.html)

理论
====

自旋锁（Spin lock）
-------------------

何谓自旋锁？它是为实现保护共享资源而提出一种锁机制。其实，自旋锁与互斥锁比较类似，  
它们都是为了解决对某项资源的互斥使用。无论是互斥锁，还是自旋锁，在任何时刻，最多只能  
有一个保持者，也就说，在任何时刻最多只能有一个执行单元获得锁。但是两者在调度机制上略有不同。  
对于互斥锁，如果资源已经被占用，资源申请者只能进入睡眠状态。但是自旋锁不会引起调用者睡眠，  
如果自旋锁已经被别的执行单元保持，调用者就一直循环在那里看是否该自旋锁的保持者已经释放了锁，  
"自旋"一词就是因此而得名。  


命令
====

## scp ##
`scp -P 12345 liangchao@112.168.4.1:~/workspace/lib.so .`
`scp ~/Downloads/123.txt liangchao@112.168.4.1:workspace/ -P 12345`

## vnc ##


## du ##
* -a, --all
 write counts for all files, not just directories

* -h, --human-readable
  print sizes in human readable format (e.g., 1K 234M 2G)

* -d, --max-depth=N
  print the total for a directory (or file, with --all) only if it is N or fewer levels below the command line argument;  --max-depth=0 is the same as --summarize

* -s, --summarize
  display only a total for each argument

``` shell
du

du /var/tool/apr

du -s

du -h test

du -ah /var/tool/apr

du -c 1.log 2.log

du | sort -nr | more

du -h -d 1 # du -h  --max-depth=1
```

应用
====

tmux
----

**tmux** is a terminal multiplexer: it enables a number of terminals to be created, accessed, and controlled from a single screen.
**tmux** may be detached from a screen and continue running in the background, then later reattached.

### Install ###

`brew install tmux`

### Commands ###

| Command                    | Desc                        |
|----------------------------|-----------------------------|
| tmux new -s <session-name> | Start new session           |
| tmux deattach              | Detach from current session |
|                            |                             |


### Keybindings ###

| Keybinding  | Desc                                                             |
|-------------|------------------------------------------------------------------|
| C-b         | Send the prefix key (C-b) through to the application.            |
| C-o         | Rotate the panes in the current window forwards.                 |
| C-z         | Suspend the tmux client.                                         |
| !           | Break the current pane out of the window.                        |
| "           | Split the current pane into two, top and bottom.                 |
| #           | List all paste buffers.                                          |
| $           | Rename the current session.                                      |
| %           | Split the current pane into two, left and right.                 |
| &           | Kill the current window.                                         |
| '           | Prompt for a window index to select.                             |
| (           | Switch the attached client to the previous session.              |
| )           | Switch the attached client to the next session.                  |
| ,           | Rename the current window.                                       |
| -           | Delete the most recently copied buffer of text.                  |
| .           | Prompt for an index to move the current window.                  |
| 0 to 9      | Select windows 0 to 9.                                           |
| :           | Enter the tmux command prompt.                                   |
| ;           | Move to the previously active pane.                              |
| =           | Choose which buffer to paste interactively from a list.          |
| ?           | List all key bindings.                                           |
| D           | Choose a client to detach.                                       |
| L           | Switch the attached client back to the last session.             |
| [           | Enter copy mode to copy text or view the history.                |
| ]           | Paste the most recently copied buffer of text.                   |
| c           | Create a new window.                                             |
| d           | Detach the current client.                                       |
| f           | Prompt to search for text in open windows.                       |
| i           | Display some information about the current window.               |
| l           | Move to the previously selected window.                          |
| n           | Change to the next window.                                       |
| o           | Select the next pane in the current window.                      |
| p           | Change to the previous window.                                   |
| q           | Briefly display pane indexes.                                    |
| r           | Force redraw of the attached client.                             |
| m           | Mark the current pane (see select-pane -m).                      |
| M           | Clear the marked pane.                                           |
| s           | Select a new session for the attached client interactively.      |
| t           | Show the time.                                                   |
| w           | Choose the current window interactively.                         |
| x           | Kill the current pane.                                           |
| z           | Toggle zoom state of the current pane.                           |
| {           | Swap the current pane with the previous pane.                    |
| }           | Swap the current pane with the next pane.                        |
| ~           | Show previous messages from tmux, if any.                        |
| Page Up     | Enter copy mode and scroll one page up.                          |
| Up, Down    |                                                                  |
| Left, Right |                                                                  |
|             | Change to the pane above, below, to the left, or to the right of |
|             | the current pane.                                                |
|             |                                                                  |

```
tmux new-session -s <会话名称>
tmux new -s <会话名称> 初始命令

tmux attach-session -t <会话名称>
tmux attach -t <会话名称>
tmux a -t <会话名称>

<kbd>C-b d</kbd> 分离会话

tmux new -n <窗口名>
```

* 会话(session)管理

| Action                 |       Keybinding |
|:-----------------------|-----------------:|
| List all the sessions  | <kbd>C-b s</kbd> |
| Rename current session | <kbd>C-b $</kbd> |
| detach current session | <kbd>C-b d</kbd> |

* 窗口(window)管理

| Action                     |         Keybinding |
|:---------------------------|-------------------:|
| Create a new window        |   <kbd>C-b c</kbd> |
| Rename current window      |   <kbd>C-b ,</kbd> |
| List all the windows       |   <kbd>C-b w</kbd> |
| Split window in horizontal |   <kbd>C-b %</kbd> |
| Split window in vertical   |   <kbd>C-b "</kbd> |
| Select next window         |   <kbd>C-b n</kbd> |
| Select previous window     |   <kbd>C-b p</kbd> |
| Select 0~9 window          | <kbd>C-b 0~9</kbd> |

* 窗格(Pane)管理

| Action                             |       Keybinding |
|:-----------------------------------|-----------------:|
| Create a horizontal pane           | <kbd>C-b %</kbd> |
| Create a vertical pane             | <kbd>C-b "</kbd> |
| Display pane number                | <kbd>C-b q</kbd> |
| Jump between panes                 | <kbd>C-b o</kbd> |
| Switch position with next pane     | <kbd>C-b }</kbd> |
| Switch position with previous pane | <kbd>C-b {</kbd> |
| Display current pane in new window | <kbd>C-b !</kbd> |
| Close current pane                 | <kbd>C-b x</kbd> |
