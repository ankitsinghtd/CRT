# complex numbers

```cpp
class Complex

{

int real, imag;

public:

Complex()

{

real = imag = 0;

}

  

Complex operator+(Complex obj)

{

Complex t;

t.real = this->real + obj.real;

t.imag = this->imag + obj.imag;

return t;

}

  

Complex operator*(Complex obj)

{

Complex t;

t.real = this->real * obj.real - this->imag * obj.imag;

t.imag = this->real * obj.imag + obj.real * this->imag;

return t;

}

  

void getdata()

{

cout<<"Enter real: ";cin>>real;

cout<<"Enter imaginary: ";cin>>imag;

}

  

void display()

{

cout<<real<<" + "<<imag<<"i"<<endl;

}

};

  

int main()

{

Complex c1 ,c2, c3, c4;

c1.getdata();

c2.getdata();

c3 = c1+c2;

c4 = c1*c2;

c3.display();

c4.display();

return 0;

}
```

# postfix and prefix increment/decrement
Pro tip:
- Solve 2 operations first, keep adding more 1 by 1

```cpp
int a=5, b;

b = a++ + a++; // b =  5 + 6 (assigned just before each increment)
cout<<a<<","<<b<<endl;
```
Output: 7, 11

```cpp
int a=5,b;

b = ++a + ++a; // b = 7 + 7 (assigned after both increments)
```
Output: 7, 14

```cpp
int a=5,b;

b = ++a + a++;
```
Output: 7, 13

```cpp
int a=5,b;

b = ++a + a++;
```
Output: 7, 12

```cpp
int a=5,b;

b = a++ + ++a + a++;
```
Output: 8, 19

```cpp
int a=5,b;

b = ++a + a++ + ++a;

// 1-> 6 + 6, a = 7

// threfore, update ++a, i.e

// 2-> 7 + 6

// 3-> 7 + 6 + 8
```
Output: 8, 21

# Types of member variables

```cpp
class A

{

public:

int x; // instance member variable

static int y; // static member variable

};

int A::y; // define (for allocating memory)

  

int main()

{

A a1, a2, a3;

// A::x = 7; (error, can't be accessed using class name)

a1.x = 5;

// A::y = 69; (valid)

a1.y = 10; // class variables can be accessed using either objects or class name

a2.x = 15;

a2.y = 20;

a3.x = 25;

a3.y = 30;

cout << a1.x << "\t" << a2.x << "\t" << a3.x << endl;

cout << a1.y << "\t" << a2.y << "\t" << a3.y << endl;

return 0;

}
```
## Instance member variables (object variables)
- There will be as many copies of the instance member variables as there are number of objects
- Default value is garbage
- Can be accessed through object only not through class name

## Static member variables (class variables)
- There  will be only one copy of the static member variable and this copy will be shared by all the objects
- Default value is 0
- Can be accessed through class name as well as object name but it netter to access with class name (cz its static and will be same for everyone anyways


example 1

```cpp
class Circle{
	int r;
	float area;
	static float Pi; // Pi will be same for every object
}c1, c2;
```

example 2

```cpp
class Student {
	int roll;
	string name;
	static int fees;
}
```

example 3 (counting objects)

```cpp
class A

{

static int count;

public:

A(){

count++;

cout<<"Object "<<count<<" created !"<<endl;

}

~A(){

cout<<"Object "<<count<<" destroyed !"<<endl;

count--;

}

};

int A::count;

int main()

{

A a1, a2, a3;

return 0;

}
```
# static member function

```cpp
class A

{

int x;

static int y;

  

public:

void f1()

{

x=5;

y=6;

}

static void f2()

{

x=5;

}

static void f3(A obj){

obj.x = 7;

}

};

int A::y;

int main()

{

A a1, a2;

a1.f1(); // address(&a1) is sent, this receives the address

a2.f1();

a1.f2(); // no address is sent, this doesn't receive the address

A::f3(a1); // valid

return 0;

}
```

# const
## const function

```cpp
class A

{

int x, y;

mutable int counter; // to make it changeable in const functions

  

public:

void getdata(){

cin>>x>>y;

}

void display() const {

// x=111, y = 21; (error, can't update values using const function)

counter++;

cout<<x<<","<<y<<endl;

}

};

  

int main()

{

A a1;

a1.getdata();

a1.display();

return 0;

}
```


# operator overloading
- operator is s keyword
- we can overload any operator except 5 operators ( ::, size of, ?: , . , ->)
- using operator overloading we cannot create any new operator
- we cannot change precedence and associativity


| Binary operator overloading                                        | unary operator overloading                                        |
| ------------------------------------------------------------------ | ----------------------------------------------------------------- |
| a2 + a1<br>this   obj<br>left = calling object<br>right = argument | a1++ (no argument)<br>++a1 (a1 is calling)<br>!a1 (a1 is calling) |

Example 1
```cpp
class A

{

int x;

  

public:

A() : x(0) {}

A(int x) : x(x) {}

A operator+(A obj)

{

A t;

t.x = this->x + obj.x;

return t;

}

void display() {

cout<<x<<endl;

}

};

  

int main()

{

A a1(5), a2(6), a3;

a3 = a1 + a2;

a3.display();

return 0;

}
```
Output: 11


Example 2
```cpp
class Student

{

int roll;

string name;

float per;

  

public:

Student(int roll, string name, float per){

this->roll = roll;

this->name = name;

this->per = per;

}

  

bool operator>(Student obj) {

return this->per > obj.per ? true : false;

}

  

bool operator<(Student obj) {

return this->per < obj.per ? true : false;

}

  

bool operator==(Student obj) {

return this->per == obj.per ? true : false;

}

};

  

int main()

{

Student s1(101, "Ajay", 95.5f);

Student s2(102, "Vijay", 95.5f);

if(s1 > s2)

cout<<"student 1 is better";

else if(s1 < s2)

cout<<"student 2 is better";

else if(s1 == s2)

cout<<"tie";

return 0;

}
```

Example 3
```cpp
class A

{

int x;

  

public:

A(int x)

{

this->x = x;

}

int operator++(int) { // int = dummy parameter to avoid duplicate

return x++;

}

int operator++(){

return ++x;

}

void display()

{

cout << x << endl;

}

};

  

int main()

{

A a1(5);

cout<<a1++;

cout<<++a1;

a1.display();

return 0;

}
```
Output: 577


Example 4
```cpp
class A

{

bool x;

  

public:

A(bool x)

{

this->x = x;

}

bool operator!() { // int = dummy parameter to avoid duplicate

return !x;

}

  

void display()

{

cout << x << endl;

}

};

  

int main()

{

A a1(true);

cout<<!a1;

return 0;

}
```

# Friend Function
- access private data of another class

**A function can be a member of only one class but it can be a friend of more than one classes

**A member function can access private data of its class directly without any object but a friend function can access the private members through object only

## non member (global) function as a friend

```cpp
class B; // declaration needed before using above definition

class A

{

int x;

  

public:

A() : x(0) {}

  

A(int x) : x(x) {}

  

friend int sum(A, B);

};

  

class B

{

int y;

  

public:

B() : y(0) {}

  

B(int y) : y(y) {}

  

friend int sum(A, B);

};

  

int sum(A a1, B b1) // global function non member

{

return a1.x + b1.y;

}

  

int main()

{

A a1(2);

B b1(2);

cout << sum(a1, b1);

return 0;

}
```


## member function as a friend


template
```cpp
class A{
	void f1();
};
class B{
	friend void A::f1();
};
void A::f1(){

}
```


example 1
```cpp
class B; // declaration needed before using above definition

class A

{

int x;

  

public:

A() : x(0) {}

  

A(int x) : x(x) {}

  

int sum(B);

};

  

class B

{

int y;

  

public:

B() : y(0) {}

  

B(int y) : y(y) {}

  

friend int A::sum(B);

};

  

int A::sum(B b1)

{

return x + b1.y;

}

  

int main()

{

A a1(19);

B b1(2);

cout << a1.sum(b1);

return 0;

}
```

- primitive on right
```cpp
class A

{

int x;

  

public:

A() : x(0) {}

  

A(int x) : x(x) {}

  

friend int operator+(int, A);

};

  

int operator+(int y, A obj)

{

return y + obj.x;

}

  

int main()

{

A a1(2);

cout << 5 + a1;

return 0;

}
```