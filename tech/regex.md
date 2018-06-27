% RegEx and tools

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

## sed ##

Stream EDitor

### Typical uses ###

1. Text substitution
2. Selective printing of text files
3. In-a-place editing of text files
4. Non-interactive editing of text files

### Workflow ###

1. Read: SED reads a line from the input stream (file, pipe or stdin) and stores it in its internal buffer called *pattern buffer*.  
2. Execute: All SED commands are applied sequentially on the *pattern buffer*. By default, SED commands are applied on all lines, unless line addressing is specified.  
3. Display: Send the modified data to the output stream. After sending the data, the pattern buffer will be empty.
4. The above process repeats until the file exhausted.

### commands ###

* [s] substitute
`sed -e 's/bbb/eee/g' input.txt > output.txt`
`sed -e 's/aaa/+&+/g'input.txt`
`sed -e 's/.*/output: &/g' input.txt`
`sed -e -g 's/aaa/bbb/' input.txt`

* [d] delete
`sed -e '1,2d' input.txt`
`sed -e 'd' input.txt`
| Addr     |     Func |
|:---------|---------:|
| 3        |          |
| 20,$     |          |
| 10,5     |          |
| /^[0-9]/ |          |
| 15,/Z$/  |          |
| 5,10!    | 1~4,11~$ |

* [y] substitue 1 char
`sed -e 'y/abc/xyz/' input.txt`
aaabbbccc
->
xxxyyyzzz

`sed -e 'y/abcdefghijklmnopqrstuvwxyz/ABCDEFGHIJKLMNOPQRSTUVWXYZ' input.txt`

### flags ###
* [p] print

* [w] file output

### options ###
* -e
`sed -e '2d' -e '2s/bbb/eee/g' input.txt`

* -n
silent, suppress automatic printing of pattern space
`sed -n -e '2/aaa/bbb/g' input.txt`

* -f


### Examples ###

* find ./src -name "*.js" | xargs sed -i "s/require(SRC_PATH + /kgRequire(/g"

## awk ##

## grep ##

## regex syntax ##

".":
"*":
"+":
"?":
"^":
"$":
"[ ]":
