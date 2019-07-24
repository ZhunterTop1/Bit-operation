# Bit-operation
Tell you why Bit operation can get such result

# int number >> int number
# eg: 5 >> 2  = 1 ; -5 >> 2 = -2
# why can we get such result?
The number exists in the original code, the inverse code, and the complement code.
The original code is the binary of its own number; an integer has 4 bytes, which is 32 bits. The first bit is the sign bit, the positive number is 0, and the negative number is 1.
The inverse of the positive number, the complement and the original code are the same; the inverse of the negative number is the opposite of the first bit (the sign bit) (1 corresponds to 0, 0 corresponds to 1); the complement is its inverse code plus 1 (signs are ignored when computing).
eg: 5 : original code ：inverse code ： complement code
    5 ：00000000 00000000 00000000 00000101 ：00000000 00000000 00000000 00000101 ：00000000 00000000 00000000 00000101
   -5 : original code ：inverse code ： complement code
   -5 ：10000000 00000000 00000000 00000101 ：11111111 11111111 11111111 11111010 ：11111111 11111111 11111111 11111011

The direct calculation of data in java is the operation of its complement.
 number1 >> number2
 means number1's complement code  moves number2 units to the right
 eg ：
  5 >> 2
  means : 00000000 00000000 00000000 00000101(complement code) -> 00000000 00000000 00000000 00000001(complement code)->
  00000000 00000000 00000000 00000001(orginal code)=1
  
  -5 >> 2
  means : 11111111 11111111 11111111 11111011(complement code) -> 11111111 11111111 11111111 11111110(complement code)->
  10000000 00000000 00000000 00000010(orginal code)=-2
  
  So we can find that the position where the sign bit is positive and the vacancy is filled with 0, and the position where the sign bit is negative is vacant.
  
summary：
1. If x is positive, then the result of the operation is  x/2^n
  x >> n = x/2^n
2. If x is negative, then the result of the operation is  -(|x|-1)/2^n-1
  x >> n = -(|x|-1)/2^n-1
  
  process:
  If we get the result;it is Z.We can find that Z is a negative.
  reverse code = - (2^31 - |Z|)
  reverse code = -((2^(31+n)-|x|)+1)/2^n + 1
  so : |Z|=(|x|-1)/2^n + 1
  
  
  
 If anyone looks at it, I will continue to write the mathematical logic of other bit operations.
  
  
  
  
