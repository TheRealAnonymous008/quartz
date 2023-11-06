# Endianness
* **Endianness** pertains to the manner in which we store a sequence of bytes in digital data in memory .
* A **Big Endian** system stores the *most* significant byte at the smallest address. The memory layout ends up storing the number backwards 
* A **Little Endian** system stores the *least* significant byte at the smallest memory address. The memory layout ends up storing the number in reading order. 
# Number Representations 
### NaN
* A **Not a Number** results denotes an  entity which cannot be particular format (i.e., because of indeterminate forms)
	* A **signaling NaN** is a special form of NaN which should raise an invalid operation exception when consumed by most operations. 
	* A **quiet NaN** is a NaN which does not raise any additional exceptions as it propagates through must operations. 

### Extensions
* **Extension** pertains to the process of representing a number that was in $k$ bits to another number in $m$ bits, where $m>k$. 
  
  We have two possible definitions of extensions 
	* **Signed Extension** involves repeatedly adding leading $0$'s if the number is positive and leading $1$'s if the number is negative. 
	* **Zero extension** involves adding leading $0$s.

### Coded Decimals 
* **Unpacked Binary Coded Decimal** encodes the number by representing the digit with its equivalent $8$-bit number in binary.
* **Packed BCD** removes the first four MSb. 
  
  Each digit's representation is shown in the table below
  
  | digit | UBCD      | Packed BCD | 
  | ----- | --------- | ---- | 
  | 0     | 0000 0000 |  0000 | 
  | 1     | 0000 0001 |  0001 | 
  | 2     | 0000 0010 |  0010 |
  | 3     | 0000 0011 |  0011 |
  | 4     | 0000 0100 |  0100 |
  | 5     | 0000 0101 | 0101 | 
  | 6     | 0000 0110 | 0110 | 
  | 7     | 0000 0111 | 0111 | 
  | 8     | 0000 1000 | 1000 | 
  | 9     | 0000 1001 | 1001 | 


# Floating Point Standard 
* Defines the standard for representing floating point numbers.
* Let
  $s$ be the sign bit 
  $e'$ be the stored exponent 
  $m$ be the mantissa. 
  $b$ be the number of bits to be used 
  $b_e$ - the number of bits for the exponent
  $b_m$ the number of bits for the mantissa. 

* The format is given as 
```
 1   |    b_e   |   b_m
sign | exponent | mantissa
```
* The real number is to be represented as 
  $$
  m\times2^e
  $$
  $m$ must be normalized to ensure canonical representation. Thus, we have an implied $1$
  $$
  m = 1.f
  $$

* The **sign bit** represents the sign of $m$. $0$ is positive, $1$ is negative 
* The **stored exponent** is calculated as 
  
  $$
  e'=e+2^{b_e-1}-1
  $$
  
* The **mantissa** represents the remaining $23$ bits and store the significand $f$. 

### Special Values 
* $s\in \{0,1\}$
* $e'=0$
* $m=0$
* Note that $+0$ and $-0$ denote numbers arbitrarily close to but not $0$.

### Infinity 
* $s\in \{0,1\}$
* $e'=2^{b_e} - 1$ (all one's) 
* $m=0$

* Infinity denotes the largest magnitude number representable within the format 

### Subnormal Numbers 
* $s=\{0,1\}$
* $e'=0$
* $m\ne 0$

These numbers are of the form $x$, where  in binary 
$$
\begin{split}
|x|&<1.0\times 2^{-z} \\ 
z&=2^{b-1}-2
\end{split}
$$

### Not a Number 
* $s$ is any value.
* $e'=2^{b_e} - 1$ (all one's) 
* $m$ begins with $01$ for Signaling NaN 
* $m$ begins with $1$ for Quiet NaN



# Links
[How floating point works](https://www.youtube.com/watch?v=dQhj5RGtag0)