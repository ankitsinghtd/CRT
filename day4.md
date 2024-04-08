# loops cont..
## do while

```c
intitialize;
do {
	statement;
	update
}while(condition);
```

# << and >> (left shift, right shift operator)

<< = multiply by 2
">>" = divide by 2

# C and C++
| C                 | C++                                               |
| ----------------- | ------------------------------------------------- |
| sum.c             | sum.cpp                                           |
| #include<stdio.h> | #include<iostream.h> (library or namespace)       |
| printf("%d", a);  | cout<<a<<5<<5.4<<'a'<<"abc"; (insertion operator) |
| scanf("%d", &a);  | cin>>a;                                           |
| "\n"              | endl (manipulator)                                |

```cpp
cout<<5<<1;

cout<<(5<<1);
```
Output: 51 10

## namespace 
- Two variables can't be same name
	
We can use namespace to separate "namespace" ?
```cpp
namespace p1 {

int a = 5;

}

namespace p2 {

int a = 10;

}

  

int main() {

cout<<p1::a<<endl;

cout<<p2::a<<endl;

return 0;

}
```

By using a namespace

```cpp
using namespace p1;
```

Variables can be directly accessed.
```cpp
namespace p1 {

int a = 5;

}

using namespace p1;

namespace p2 {

int a = 10;

}

  

int main() {

cout<<a<<endl;

cout<<a<<endl;

cout<<a<<endl;

cout<<a<<endl;

cout<<a<<endl;

cout<<a<<endl;

cout<<p2::a<<endl;

return 0;

}
```

### std namespace
- cout, cin
```cpp
#include<iostream>
int main() {
	std::cout<<"Hello"<<std::endl;
	std::cout<<"bye"<<std::endl;
	return 0;
}
```

## scope resolution operator
- ::

## local and global variable
- local - initialized with garbage by default
- global - initialized with 0 by default
```cpp
int b = 10; //global scope
int main() {
	int a = 5;
	cout<<a; // 5
}
int fxn () {
	cout<<a; // error
	cout<<b; // 10
}
```

- *namespace variables are also global
```cpp
namespace p1 {

	int a = 10; //global

}

int a = 2; // global

int main() {

	int a = 5; // local

	cout<<a<<endl;

	cout<<::a<<endl;

	cout<<p1::a<<endl;

	return 0;

}
```
Output: 5 2 10

## sum of 2 numbers

```cpp
int main() {

	int a,b,sum;

	cout<<"enter a and b: ";

	cin>>a>>b;

	sum = a + b;

	cout<<"Sum is :" <<sum<<endl;

	return 0;

}
```

## cerr (console error) (std)
```cpp
cerr<<"error message";
```
## <bits/stdc++.h>
- many header files in one



# functions in C++
- eliminates repetition
- predefined functions
- user-defined functions
## custom header files
- put all the functions being used multiple times in a header file

## max function
```cpp
//function definition
int maxx(int a, int b) { //int a, int b = input/arguents/parameters (formal parameters)

return a>b?a:b;

}

int main() {

int a=5,b=10;

int res = maxx(a,b); //function call (actual parameters)

cout<<"maximum of "<<a<<" and "<<b<<" is :"<<res;

return 0;

}
```
##

**Function must be declared before calling
- either declare above and define below
- OR
- define above

**Function declaration doesn't need parameter data types
```cpp
int maxx(int, int); //valid
```
- Bottom up approach (define above, call below)
- Top down approach (declare above, call above, define below)



** A function can accept any number of arguments but can return maximum 1 output

```cpp
int maxx(int a, int b) {

return a+b,a,689;

}

  

int main() {

int a=5,b=10;

cout<<maxx(a,b);

return 0;

}
```
Output: 689 (comma operator returns right most value)


** If a function does not return any value then it is called as void function

```cpp
void square(int a, int b) {

cout<<a*a<<endl<<b*b<<endl<<a*b<<endl;

return ; // return not necessary or can have nothing as value

}

  

int main() {

int a=5,b=10;

square(a,b);

cout<<"end of main";

return 0;

}
```

## call by value
```cpp
void increment(int a) {

a++; //copy variable incremented

}

  

int main() {

int a=5;

increment(a);

cout<<a;

return 0;

}
```
Output: 5

```cpp
int increment(int a) {

a++;

return a++;

}

  

int main() {

int a=5;

cout<<increment(a);

return 0;

}
```
Output: 6

```cpp
void swapp(int a,int b) {

a=b-a+(b=a);

}

  

int main() {

int a=5, b=10;

swapp(a,b);

cout<<a<<b<<endl;

return 0;

}
```

**Demerits of function ?
- slow
## macro function