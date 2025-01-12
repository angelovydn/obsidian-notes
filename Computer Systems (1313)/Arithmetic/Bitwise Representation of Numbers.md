#arithmetic
#### Sign and Magnitude
MSB is the sign bit
- 0011 = +3
- 1001 = -1
#### Two's Complement
**MSB is negated**
- 1101 = -8+4+1 = -3
- 0110 = 6

Subtracting bits: flip each bit and add a one, ignoring overflow bits.
00001010 - 01010110 = 00001010 + 10101010
#### Biased Offset
Can store 0...2^n-1
- Eliminates negative values by shifting the range using a bias
- Numbers are stored as non-negative values making comparisons easier
- Bias allows range to be symmetrical around zero

Conversion to Biased-128:
- add 128 to the number
- convert result to unsigned binary
- 5+128=133=1000101

#### Floating Point
Contains number and exponent
- 2.5 = 010.1 0000
- 010.1 0000 = 0.101 0010
- 2.5 = 0101 0010

As part of [[Arithmetic]]

