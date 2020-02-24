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

scp
---

`scp -P 12345 liangchao@112.168.4.1:~/workspace/lib.so .`
`scp -P 12345 ~/Downloads/123.txt liangchao@112.168.4.1:workspace/`

vnc
---


du
--

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

locales
-------

``` bash
sudo apt-get install locales
sudo dpkg-reconfigure locales
```

> export LC_ALL=en_US.UTF-8
> export LANG=en_US.UTF-8
> export LANGUAGE=en_US.UTF-8

``` bash
source ~/.bashrc
```

应用
====

tmux
----

[Github](https://github.com/tmux/tmux)  
[Man Page](http://man.openbsd.org/OpenBSD-current/man1/tmux.1)  
[tmux & screen](https://blog.csdn.net/taiyang1987912/article/details/41551987)  
[Difference between tmux vs screen](https://wtanaka.com/node/8136)  
[tmux and screen cheat-sheet](http://www.dayid.org/comp/tm.html)  

**tmux** is a terminal multiplexer: it enables a number of terminals to be created, accessed, and controlled from a single screen.  
**tmux** may be detached from a screen and continue running in the background, then later reattached.  
This enables the following features: persistence, multiple windows, and session sharing.  

### Frequent keybindings ###

| Description |     Keybinding |
|:------------|---------------:|
| copy-mode   |   <kbd>[</kbd> |
| past-buffer |   <kbd>]</kbd> |
| last-window | <kbd>TAB</kbd> |
| move-window |   <kbd>.</kbd> |
| resize-pane |   <kbd>z</kbd> |

### Copy-mode keybindings ###

| Description               |         Keybinding |
|:--------------------------|-------------------:|
| begin-selection           | <kbd>C-Space</kbd> |
| clear-selection           |     <kbd>C-g</kbd> |
| cancel                    |     <kbd>C-c</kbd> |
|                           |       <kbd>q</kbd> |
| copy-end-of-line          |     <kbd>C-k</kbd> |
| copy-selection-and-cancel |     <kbd>C-w</kbd> |
|                           |     <kbd>M-w</kbd> |
| search-backward           |     <kbd>C-r</kbd> |
| search-forward            |     <kbd>C-s</kbd> |
| search-again              |       <kbd>n</kbd> |
| search-reverse            |       <kbd>N</kbd> |
| goto-line                 |       <kbd>g</kbd> |
| jump-to-backward          |       <kbd>T</kbd> |
| jump-to-forward           |       <kbd>t</kbd> |
| jump-backward             |       <kbd>F</kbd> |
| jump-forward              |       <kbd>f</kbd> |
| jump-reverse              |       <kbd>,</kbd> |
| jump-again                |       <kbd>;</kbd> |
| page-down                 |     <kbd>C-v</kbd> |
| page-up                   |     <kbd>M-v</kbd> |
| back-to-indentation       |     <kbd>M-m</kbd> |
| middle-line               |     <kbd>M-r</kbd> |
| top-line                  |     <kbd>M-R</kbd> |
|                           |                    |
