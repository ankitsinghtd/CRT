# constructors and destructors

- Members variables have garbage value by default in class i.e they need to be initialised before working with them

```cpp
class A

{

int x, y;

  

public:

void init()

{

x=5;

y=10;

}

void display()

{

cout << x << "\t" << y << endl;

}

};

int main()

{

A a1;

// a1.x = 5; error (private)

// a1.y = 10; error (private)

a1.init();

a1.display();

}
```

## constructor
- It is a member function
- It's name is same as of class name
- It is called automatically when an object is created 
- It is used to initialise instance member variables and allocate dynamic memory, open files, open resources and nay other help required by the object.
- It should be defined as public as it is called outside the class (could be private)
- A class can contain more than one constructor if their arguments are different and it is called as constructor overloading

Default Constructor
```cpp
class A

{

int x, y;

  

public:

A()

{

x=5;

y=10;

}

void display()

{

cout << x << "\t" << y << endl;

}

};
```
Con: Initialises variables every time an object is created
### parameterised constructor

```cpp
class A

{

int x, y;

  

public:

A()

{

x=y=0;

}

A(int n)

{

x=y=n;

}

A(int x, int y)

{

this->x = x;

this->y = y;

}

void display()

{

cout << x << "\t" << y << endl;

}

};

int main()

{

A a1, a2(5), a3(5, 10);

a1.display();

a2.display();

a3.display();

}
```

Example 2
```cpp
class A

{

int x, y;

  

public:

A()

{

cout<<"default"<<endl;

}

A(int n):A()

{

cout<<"single para"<<endl;

}

A(int x, int y):A(x)

{

cout<<"double para"<<endl;

}

void display()

{

cout << x << "\t" << y << endl;

}

};

int main()

{

A a3(5, 10);

}
```