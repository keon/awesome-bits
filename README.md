# awesome-bits [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

> A curated list of awesome bitwise operations and tricks
>
> Maintainer - [Keon Kim](https://github.com/keonkim)
> Please feel free to [pull requests](https://github.com/keonkim/awesome-nlp/pulls)




## Integers
**Set n-th bit**
```
x | (1<<n)
```
**Unset n-th bit**
 ```
 x & ~(1<<n)
 ```
**Toggle n-th bit**
```
x ^ (1<<n)
```
**Round up to the next power of two**
```
unsigned int v; //only works if v is 32 bit
v--;
v |= v >> 1;
v |= v >> 2;
v |= v >> 4;
v |= v >> 8;
v |= v >> 16;
v++;
```
**Get the maximum integer**
```
int maxInt = ~(1 << 31);
int maxInt = (1 << 31) - 1;
int maxInt = (1 << -1) - 1;
```
**Get the minimum integer**
```
int minInt = 1 << 31;
int minInt = 1 << -1;
```
**Get the maximum long**
```
long maxLong = ((long)1 << 127) - 1;
```
**Multiplied by 2**
```
n << 1; // n*2
```
**Divided by 2**
```
n >> 1; // n/2
```
**Multiplied by the m-th power of 2**
```
n << m;
```
**Divided by the m-th power of 2**
```
n >> m;
```
**Check Equality**

it's 35% faster in JS
```
(a^b) == 0; // a == b
```
**Check odd number**
```
(n & 1) == 1;
```
**Exchange (swap) two values**
```
a ^= b;
b ^= a;
a ^= b;
```
**Get absolute value**
```
//version 1
x < 0 ? -x : x;

//version 2
(x ^ (x >> 31)) - (x >> 31);
```
**Get the max of two values**
```
b & ((a-b) >> 31) | a & (~(a-b) >> 31);
```
**Get the min of two values**
```
a & ((a-b) >> 31) | b & (~(a-b) >> 31);
```
**Check whether both have the same sign**
```
(x ^ y) >= 0;
```
**Flip sign**
```
i = ~i + 1; // or
i = (i ^ -1) + 1; // i = -i
```
**Calculate 2^n**
```
1 << n;
```
**Whether is factorial of 2**
```
n > 0 && (n & (n - 1)) == 0;
```
**Modulo 2^n against m**
```
m & (n - 1);
```
**Get the average**
```
(x + y) >> 1;
((x ^ y) >> 1) + (x & y);
```
**Get the m-th bit of n (from low to high)**
```
(n >> (m-1)) & 1;
```
**Set the m-th bit of n to 0 (from low to high)**
```
n & ~(1 << (m-1));
```
**Check if n-th bit is set**
```
if (x & (1<<n)) {
  n-th bit is set
}
else {
  n-th bit is not set
}
```
**Isolate (extract) the right most 1 bit**
```
x & (-x)
```
**Isolate (extract) the right most 0 bit**
```
~x & (x+1)
```

**Right most 0 bit to 1**
```
x | (x+1)
```

**n + 1**
```
-~n
```
**n - 1**
```
~-n
```
**Get the contrast number**
```
~n + 1;
(n ^ -1) + 1; 
```
**if (x==a) x=b; if (x==b) x=a;**
```
x = a ^ b ^ x;
```

## Strings

**Convert letter to lowercase:**
```
OR by space => (x | ' ')
Result is always lowercase even if letter is already lowercase
eg. ('a' | ' ') => 'a' ; ('A' | ' ') => 'a'
```

**Convert letter to uppercase:**
```
AND by underline => (x & '_')
Result is always uppercase even if letter is already uppercase
eg. ('a' & '_') => 'A' ; ('A' & '_') => 'A'
```
**Invert letter's case:**
```
XOR by space => (x ^ ' ')
eg. ('a' ^ ' ') => 'A' ; ('A' ^ ' ') => 'a'
```
**Letter's position in alphabet:**
```
AND by chr(31)/binary('11111')/(hex('1F') => (x & "\x1F")
Result is in 1..26 range, letter case is not important
eg. ('a' & "\x1F") => 1 ; ('B' & "\x1F") => 2
```
**Get letter's position in alphabet (for Uppercase letters only):**
```
AND by ? => (x & '?') or XOR by @ => (x ^ '@')
eg. ('C' & '?') => 3 ; ('Z' ^ '@') => 26
```
**Get letter's position in alphabet (for lowercase letters only):**
```
XOR by backtick/chr(96)/binary('1100000')/hex('60') => (x ^ '`')
eg. ('d' ^ '`') => 4 ; ('x' ^ '`') => 25
```

## ETC

**Fast color conversion from R5G5B5 to R8G8B8 pixel format using shifts**
```
R8 = (R5 << 3) | (R5 >> 2)
G8 = (R5 << 3) | (R5 >> 2)
B8 = (R5 << 3) | (R5 >> 2)
```
Note: using anything other than the english letters will produce garbage results

For more Complicated Stuffs [Read This](https://graphics.stanford.edu/~seander/bithacks.html)
