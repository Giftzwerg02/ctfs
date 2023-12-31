# [Talking Web](https://pwn.college/cse365-f2023/talking-web)

## [Web Basics](https://youtu.be/17zJ91OdwCM)

### URI
**Syntax**: `<scheme>:<authority>/<path>?<query>#<fragment>`

What happens if you meet a string like:
`https://example.com/test/example:1.html?/adam`

How can this be parsed? Answer: You don't

#### URI Encoding (Percent Encoding)
Reserved Characters:
- `:`
- `/`
- `?`
- `#`
- `[`, `]`
- `@`
- ...

If you want to use these characters in the URI (not for parsing reasons above), you need to encode them first.


Percent Encoding must be used for anything that is **not** of the following:
- Alpha ([a-zA-Z])
- Digit ([0-9])
- `-`
- `.`
- `_`
- `~`

Percent Encoding works by replacing the wanted byte with `%<hexadecimal-representation-of-byte>`.
Example: We want to encode `?`.
1. Lookup the hexadecimal repr of this character (e.g. via `man ascii` or `ascii -x`)
    -   ```
    $ nix shell nixpkgs#ascii
    $ ascii -x
       00 NUL    10 DLE    20      30 0    40 @    50 P    60 `    70 p 
       01 SOH    11 DC1    21 !    31 1    41 A    51 Q    61 a    71 q 
       02 STX    12 DC2    22 "    32 2    42 B    52 R    62 b    72 r 
       03 ETX    13 DC3    23 #    33 3    43 C    53 S    63 c    73 s 
       04 EOT    14 DC4    24 $    34 4    44 D    54 T    64 d    74 t 
       05 ENQ    15 NAK    25 %    35 5    45 E    55 U    65 e    75 u 
       06 ACK    16 SYN    26 &    36 6    46 F    56 V    66 f    76 v 
       07 BEL    17 ETB    27 '    37 7    47 G    57 W    67 g    77 w 
       08 BS     18 CAN    28 (    38 8    48 H    58 X    68 h    78 x 
       09 HT     19 EM     29 )    39 9    49 I    59 Y    69 i    79 y 
       0A LF     1A SUB    2A *    3A :    4A J    5A Z    6A j    7A z 
       0B VT     1B ESC    2B +    3B ;    4B K    5B [    6B k    7B { 
       0C FF     1C FS     2C ,    3C <    4C L    5C \    6C l    7C | 
       0D CR     1D GS     2D -    3D =    4D M    5D ]    6D m    7D } 
       0E SO     1E RS     2E .    3E >    4E N    5E ^    6E n    7E ~ 
       0F SI     1F US     2F /    3F ?    4F O    5F _    6F o    7F DEL 
    ```
    As we can see the Hex-Value for `?` is `3F`.
2. Therefore, the Percent-Encoded String is now `%3F`



