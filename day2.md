
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

Question : solve 5-7/14*2-15%6*3-7%9*2+15

## unary operators
### sizeof

```c
#include <stdio.h>

  

int main(){

int a=10;

printf("%u",sizeof(a++));

printf("%d", a);

return 0;

}
```
Output : 4 10

### upcast, downcast

int a = 5.4
float a = 5 (implicit typecast)

### postfix, prefix

a++, ++a


```c
int a=10;

printf("%d",++a);

printf("\n%d", a);
```
Output: 11 11
```c
int a=10;

printf("%d",a++);

printf("\n%d", a);
```
Output: 10 11
```c
int a=10;

int b = ++a;

printf("%d %d", a, b);
```
Output: 11 10
```c
int a=10;

int b = a++;

printf("%d %d", a, b);
```
Output: 11 11
```c
int a=5,b=6,c;

c = a++ * b++;

printf("%d %d %d", a, b, c);
```
Output: 6 7 30
```c
int a=5,b=6,c;

c = ++a * ++b;

printf("%d %d %d", a, b, c);
```
Output: 6 7 42


## volatile keyword
- for consistent output independent of compiler
```c
volatile int a=5,b;

b = a++ * a++;

printf("%d %d", a, b);
```

## printf solves expression right to left, prints LEFT TO RIGHT

```c
int n = 1;
printf("%d %d", 3*n, n++);
```

## relational operator
< > <= >=

## assignment operator (right to left)
= += -+ /= %=

## equality operator
== !=

## logical operator
&& || !

## comma operator
,
```c
int a  = 5;
if( a> 2, a > 4, a > 7)
	printf("Hello");
else
	printf("Bye");
```
- works from LEFT to RIGHT but returns RIGHT MOST VALUE
- i.e a > 7 = false, prints "Bye"
## ternary operator

### max out of 4 numbers
```c
int a= 5, b =10, c=29, d= 24;

int max = a>b?a>c?a>d?a:d:c>d?c:d:b>c?b>d?b:d:c>d?c:d;

printf("%d",max);
```

### leap year
```c
printf(y%100 == 0 ? (y%400 == 0 ? "leap": "not leap") : (y%4 ==0 ? "leap" : "not leap"));
```

## bitwise operator
& and
| or
^ xor
~ one's complement
<< left shift
">>" right shift

