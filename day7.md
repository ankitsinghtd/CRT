# classes

| Struct                                                                  | Class                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------- |
| struct keyword                                                          | class keyword                                                     |
| all members of struct are PUBLIC by default                             | all members of class are PRIVATE by default                       |
| functions are defined outside the structure so they are not the members | functions can be defined inside the class so they are the members |
## Access Specifiers (visibility mode)
- public
- private
- protected

```cpp
class Student {

int roll; // default = private

public:

string name;

private:

float per;

protected:

int a;

public: // can have public multiple times

int b;

}; // semi colon is necessary (not in Java though)

  

int main()

{

Student s1;

s1.name = "gaurav";

cout<<s1.name<<"\t"<<endl;

return 0;

}
```

## Encapsulation
- Data and Functions packed inside a class 

OR

- Bundling of member variables(data) as well as member functions(operations) together in a class as a single unit

## security ?

```cpp
class Student {

private:

//data

public:

//function

};
```

## setters and getters

Example 1

```cpp
class Date

{

private:

// data

int day, month, year;

  

public:

// function

void setDay(int d)

{

if (d >= 1 && d <= 31)

day = d;

else

day = 1;

}

void setMonth(int m)

{

if (m >= 1 && m <= 12)

month = m;

else

month = 1;

}

void setYear(int y)

{

if (y >= 1970 && y <= 2020)

year = y;

else

year = 2000;

}

int getDay()

{

return day;

}

int getMonth()

{

return month;

}

int getYear()

{

return year;

}

};

  

int main()

{

Date dob;

dob.setDay(35);

dob.setMonth(23);

dob.setYear(2013);

cout << dob.getDay()<< "/" << dob.getMonth()<< "/" << dob.getYear()<< endl;

return 0;

}
```

 Example 2

```cpp
class Date

{

private:

// data

int day, month, year;

  

public:

// function

void setDate(int d, int m, int y)

{

if (d >= 1 && d <= 31)

day = d;

else

day = 1;

  

if (m >= 1 && m <= 12)

month = m;

else

month = 1;

  

if (y >= 1970 && y <= 2020)

year = y;

else

year = 2000;

}

  

void input() {

cout<<"Enter day, month and year: ";

cin>>day>>month>>year;

}

  

void display(){

cout<<day<<"/"<<month<<"/"<<year;

}

};

  

int main()

{

Date dob, doj;

dob.input();

doj.setDate(19,12,2020);

cout<<"You were born on ";

dob.display();

cout<<" and started working on ";

doj.display();

return 0;

}
```

Example 3

```cpp
class Number

{

private:

int x, y;

  

public:

void setData(int a, int b)

{

x = a;

y = b;

}

void input()

{

cout<<"Enter two integers: ";

cin>>x>>y;

}

void swapp()

{

x = y + x - (y = x);

}

void display()

{

cout<<"X: "<<x<<" Y: "<<y<<endl;

}

};

  

int main()

{

Number n1;

n1.setData(10, 20);

n1.display();

n1.input();

n1.swapp();

n1.display();

return 0;

}
```

Example 4


```cpp
class Array

{

private:

int arr[100], n;

  

public:

void input()

{

cout << "Enter size of array: ";

cin >> n;

cout<<"Enter elements of the array: ";

for(int i=0; i<n; i++){

cin>>arr[i];

}

}

  

void sortt(){

sort(arr, arr+n);

}

void reverse() {

int i = 0, t = n-1;

while(i<=t){

arr[i] = arr[t] - arr[i] + (arr[t] = arr[i]);

i++;

t--;

}

}

  

void display()

{

for(int i=0; i<n; i++){

cout<<arr[i]<<"\t";

}

cout<<endl;

}

};

  

int main()

{

Array a;

a.input();

cout<<"You inputted: "<<endl;

a.display();

a.sortt();

cout<<"After sorting: "<<endl;

a.display();

a.reverse();

cout<<"Reversed array: "<<endl;

a.display();

return 0;

}
```

Example 5


```cpp
class Student

{

private:

int roll, sub1, sub2;

string name;

float per;

  

public:

void setData(int r, string n, int s1, int s2)

{

roll = r;

name = n;

sub1 = s1;

sub2 = s2;

per = (s1 + s2) / 2;

}

  

void input()

{

cout << "Enter roll no: ";

cin >> roll;

cin.ignore();

cout << "Enter name: ";

getline(cin, name);

cout << "Enter marks in 2 subjects: ";

cin>>sub1>>sub2;

per = (sub1+sub2)/2;

}

  

void display()

{

cout<<roll<<"\t"<<name<<"\t"<<sub1<<"\t"<<sub2<<"\t"<<per<<"%"<<endl;

}

};

  

int main()

{

Student s1, s2;

cout<<"Roll no\tName\tSub1\tSub2\tPercentage"<<endl;

s1.setData(11,"l3i",44, 56);

s2.setData(22, "jkas", 88, 92);

s1.display();

s2.display();

s1.input();

s2.input();

s1.display();

s2.display();

return 0;

}
```



**Instantiated = Object Created*


# Features of OOPS
- Object (Anything that has existence in real world or real world enitity. Objects share some properties)
- Class is a group of similar type of objects to store common properties of all the objects
- Data Hiding - by declaring them as private we can hide them from external objects. For security
- Data Abstraction - to hide the internal complex details of a class from external object
- Encapsulation - Bundling of member variables (data) as well as member functions (operations) together in a class as a single unit.

# this pointer/keyword
- "this" is a pointer
- "this" is a keyword
- stores address of the function calling object
- every class contains only one "this" irrespective of number of objects
- this is static member of class (only one copy)

```cpp
class Student

{

private:

int roll;

string name;

  

public:

  

void getData()

{

cin>>this->roll; // same as cin>>roll; (this-> is automatically "applied")

cin>>this->name;

}

  

void display()

{

cout << roll << "\t" << name << endl;

}

};

  

int main()

{

Student s1, s2;

cout << "Enter Roll no\tName" << endl;

s1.getData();

s2.getData();

s1.display();

s2.display();

return 0;

}
```

1. Function call also sends object address (**message passing**) (call by address)
2. Object address is received by 'this'
3. this-> is applied before each variable

## explicit use of this

when local var(arg) name = member name
- instance variable hiding 
```cpp
void setData(int roll, string name)

{

roll = roll; // both roll are local

name = name; // both name are local

}
```

Using this explicitly

```cpp
void setData(int roll, string name)

{

this->roll = roll;

this->name = name;

}
```



```cpp
int x = 2;

class A

{

int x;

  

public:

void f1()

{

x=5; // member variable

int x=10; // local variable

cout<<x<<endl; // 10 (local priority >)

cout<<this->x<<endl; // 5 (this keyword to access member)

cout<<::x<<endl; // 2 (scope resolving global x)

}
};
```
# inline (again?)

- Functions outside class need manual "inline-ing"

```cpp
inline void f2() {

// outside the class

// manually defining if inline or not

}
```


- Functions inside class (member functions) are automatically inline

```cpp
class B{

void f3() {

// defined inside the class

// so automatically becomes inline

}

}
```


- to make class functions not inline, define outside the class and use scope resolution


```cpp
class A

{

int x, y;

void getData();

void display();

};

inline void A::getData()

{

cout << "Enter 2 integers: ";

cin >> x >> y;

}

  

void A::display()

{

cout << x << "\t" << y << endl;

}
```
# STL
## vector and map
### array 

```cpp
#include<iostream>

#include<array>

using namespace std;

int main()

{

array<int,5> a1 = {23,151,6,436,2};

for(int e:a1){

cout<<e<<"\t";

}

a1.fill(69);

for(int e:a1){

cout<<e<<"\t";

}

cout<<endl;

return 0;

}
```

```cpp
cout<<a1.size();
```

### vector

```cpp
#include<iostream>

#include<vector>

using namespace std;

int main()

{

vector<int> v1 = {10, 20, 30};

v1.insert(v1.begin(), 5);

v1.push_back(40);

v1.insert(v1.begin()+2, 15);

for(int e:v1)

cout<<e<<"\t";

cout<<endl;

for(vector <int>::iterator itr = v1.begin(); itr!=v1.end(); itr++){ // OR for(auto itr=v1.begin().....)

cout<<(*itr)++<<"\t";

}

cout<<endl;

for(vector <int>::reverse_iterator itr = v1.rbegin(); itr!=v1.rend(); itr++){

cout<<(*itr)++<<"\t";

}

cout<<endl;

for(vector <int>::const_iterator itr = v1.cbegin(); itr!=v1.cend(); itr++){

cout<<*itr<<"\t";

}

cout<<endl;

for(vector <int>::const_reverse_iterator itr = v1.crbegin(); itr!=v1.crend(); itr++){

cout<<*itr<<"\t";

}

cout<<endl;

return 0;

}
```

#### vector initialization
```cpp
vector<int> v1 = {10,20,30,40,50};
vector<int> v1(5);
vector<int> v1(5, 10);
vector<int> v1 = v2;
```