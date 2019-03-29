% Linux Kernel Learning Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

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
