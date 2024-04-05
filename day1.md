
# '#' (for header files)
- pre processor directive


# header files

## stdio.h
- printf
- scanf
## math.h
- pow
- sqrt
- sin
- cos
## ctype.h
- toupper
- tolower
## conio.h



# types of integer
- short int (2), "%hd"
- long int (4), "%ld"
- long long int (8), "%lld"
- int (2/4/8) [depends on compiler], "%d"
- unsigned short (extends limit from 0 to double the +ve limit), "%hu"

## largest number
- unsigned long long int
**write LL or L after long integers

## cyclic rotation
- -ve limit to +ve limit : exceeding limit causes cyclic rotation

# scanning
```c
#include <stdio.h>

int main(){

int a,b, sum;

printf("Enter value of a and b: ");

scanf("%d%d", &a, &b);

sum = a + b;

printf("Sum of %d and %d is %d", a,b,sum);

return 0;

}
```
# average
- int / int = int
- float / float = float
- int / float = float
- float / int = float
```c
#include <stdio.h>

  

int main(){

int a,b;

float avg;

printf("Enter value of a and b: ");

scanf("%d%d", &a, &b);

avg = (float)(a + b)/2;

printf("Average of %d and %d is %f", a,b,avg);

return 0;

}
```


# swap numbers

- 3 variables
- plus minus / divide multiply
- single line 



# divide and modulus

- Truncate last 2 digits = / 100
- Display last digit= % 10
- display last 2 digits = %100

Question - Sum of digits of 3 digit no.
Question - Reverse a 3 digits no.
Question - First , mid , last no. of 3 digits no


# control structures
- if, elseif, else
- nested if else ( curly braces are optional)
- switch
- conditional operator ?:

```c
int a = 5;
if (a>2)
	printf("Hello");
	printf("World");
else
	printf("bye");
	
```
Output: error ( else without if)

```c
int a = 5;
if a>2
	printf("hello");
else;
	printf("Bye");
```
Output: no error


## floating bug

```c
#include <stdio.h>

  
int main(){

float a=0.7;

if(a==0.7) {

printf("hello");

}

else{

printf("arpit");

}

}
```
Output: Compiler dependent (uncertain)

# even odd
- %2 == 0
- n^1 == n+1
- n&1 == 0
- 
# max of 2 numbers
- (a + b + abs(a-b)) / 2
- ternary
- if else

# max of 3 numbers


# max of 4 numbers
- many if
- max = a, update max for every if x>max

# second max of 3-4-5-6.... numbers

max = a
smax = b

if c > max:
	smax = max
	max = c
else:
	smax = c