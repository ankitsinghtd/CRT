S
Question - Sort 3 numbers in increasing order

(Using max ,smax)
```c
#include <stdio.h>

int main(){

int a=10,b=5,c=2,max,smax,min;

if(a>b) {

max = a;

smax = b;

}

else {

max = b;

smax = a;

}

if (c > max) {

min = smax;

smax = max;

max = c;

}

else if(c > smax) {

min = smax;

smax = c;

}

else{

min = c;

}

printf("%d %d %d",min, smax, max);

}
```

## weekdays from number (1-7) 
- nested if else
- if else if ladder
- switch case


## days in month from number

- switch case


# switch case rules

- "case x:" is a label
- default is optional
- break is optional but might break logic
- we can shuffle all the cases


| allowed                   | not allowed            |
| ------------------------- | ---------------------- |
| integer constants         | double, string         |
| int expressions (math)    | comma separated values |
| ascii                     | duplicates             |
| range ( case 90 ... 100:) | condition              |

# ASCII 

| ASCII range | Decimal Value |
| ----------- | ------------- |
| 'a' - 'z'   | 97 - 122      |
| 'A' - 'Z'   | 65 - 90       |
| '0' - '9'   | 48 - 57       |
| space       | 32            |
## Lower case to upper case
'a' to 'A'
97 - 32 = 65
## Upper case to lower case

'A' to 'a'
65 + 32 = 97


### Code: Convert case
1. using ascii (plus or minus 32)
2. without using ascii (plus or minus 'A')
3. using predefined functions (toUpper(), toLower(), islower(), isspace(), isdigit())

# operators
- binary
- unary
- ternary

## precedence and associativity

### arithmetic
- (/ * %) > (- +) precedence
- left to right associativity
### modulus
- 5%2 = 1
- 5.1 % 2 = complie time error
- -5 % 2 = -1
- 5 % -2 = 1
- -5 % -2 = -1
- 2 % 5 = 2
- 0 % 5= 0
- 5 % 0 = run time error
- 'a' % 'b' = 97

Question : solve 5-7/14*2-15%6*3-7%9*2+15s