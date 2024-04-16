# Inheritence
- single-level inhertence
- multi-level inheritence
- multiple inhertence
- hybrid inheritence
- tree inheritence

**Child cannot directly access private members of parent

```cpp
class A

{

int x;

  

public:

void setdata(int x1)

{

x = x1;

}

void getdata()

{

cin >> x;

}

void display()

{

cout << x << endl;

}

};

  

class B : public A

{

int y;

  

public:

void setdata(int x1, int y1)

{

y = y1;

// x=x1; (error, as x is private member of parent)

A::setdata(x1);

}

void display(){

A::display();

cout<<y<<endl;

}

void getdata(){

cin>>y;

A::getdata();

}

};

  

int main()

{

B b1;

b1.setdata(5, 10);

b1.display();

return 0;

}
```


## function overriding
- when there are two fxns, one is defined in parent and other in child class. Name and argument of both fxn sare same, priority will be given to child class fxn. Child overrides parent fxn. We can use :: to call parent function

```cpp

```

## constructor in inheritance
- Constructor calling order is from parent to child but destructor calling order is child to parent
- By default all the constructors of child class will automatically call default constructor of child class if not called by 

```cpp
class A

{

public:

A() {

cout<<"A constructor"<<endl;

}

~A() {

cout<<"A destructor"<<endl;

}

};

  

class B : public A{

public:

B(){

cout<<"B constructor"<<endl;

}

~B(){

cout<<"B destructor"<<endl;

}

};

  

int main()

{

B b1;

return 0;

}
```
Output: 
A constructor
B constructor
B destructor
A destructor