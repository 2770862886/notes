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

du du -h test

du -ah /var/tool/apr

du -c 1.log 2.log

du | sort -nr | more

du -h -d 1 # du -h  --max-depth=1
```
