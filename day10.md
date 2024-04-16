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


# protected keyword
- private for non child class, public for child class
- doesn't work for object

# types of derivation
class B: public A
- No change in visibility 

class B: private A
- Changes every member to private

class B: protected A
- Changes public -> protected

# Map
## ordered map
- log(n)
- Keys are sorted automatically
- Default value of unknown keys = 0
- no duplicates

```cpp
#include<iostream>

#include<map>

using namespace std;

int main() {

map<int, float> m1;

pair<int, float> p1(101, 75.5f);

pair<int, float> p2(102, 90.9f);

pair<int, float> p3(103, 23.2f);

m1.insert(p1);

m1.insert(p2);

m1.insert(p3);

m1.insert(pair<int, float>(104, 87.4f));

m1.insert({105, 82.3f});

m1[106] = 51.2f;

for(auto i:m1){

cout<<i.first<<"\t"<<i.second<<endl;

}

  

// OR

  

for(map<int, float>::iterator itr = m1.begin(); itr!=m1.end(); itr++){ // can use auto

cout<<itr->first<<"\t"<<(*itr).second<<endl;

}

int roll;

cin>>roll;

cout<<"Marks :"<<m1[roll];

return 0;

}
```

Example 2:
```cpp
int main() {

map<string, float> m1;

string name;

pair<string, float> p1("Gaurav Paaji", 75.5f);

m1.insert(p1);

m1.insert(pair<string, float>("Arpit Paaji", 87.4f));

m1.insert({"Shiv Paaji", 82.3f});

m1["Ajay"] = 51.2f;

int roll;

cout<<"Enter student name: ";

getline(cin, name);

cout<<"Marks :"<<m1[name];

return 0;

}
```


Frequency counter

```cpp
#include <iostream>

#include <map>

using namespace std;

int main()

{

int arr[] = {2, 3, 5, 3, 1, 2, 3, 4, 1, 2, 4, 1, 2, 4, 3, 4};

map<int, int> count;

for (int i = 0; i < sizeof(arr) / sizeof(int); i++)

{

count[arr[i]]++;

}

cout<<"Element\tFrequency"<<endl;

for (auto i:count)

{

cout<<" "<<i.first<<"\t"<<i.second<<endl;

}

return 0;

}
```


## unordered map
- not sorted keys
- Hashing
- Best case: O(1) | Worst case: O(n)
- no duplicates

```cpp
#include <iostream>

#include <unordered_map>

#include <vector>

using namespace std;

int main()

{

vector<int> arr= {2, 3, 5, 3, 1, 2, 3, 4, 1, 2, 4, 1, 2, 4, 3, 4};

unordered_map<int, int> count;

for (int i = 0; i < arr.size(); i++)

{

count[arr[i]]++;

}

cout << "Element\tFrequency" << endl;

for (auto i : count)

{

cout << " " << i.first << "\t" << i.second << endl;

}

return 0;

}
```

## multimap
- duplicates allowed
- useless

# set
- no keys, just value
## unordered_set
## multiset


# Virtual Function

## Binding
- Binding is a process by which a function call is linked to its definition after comparing it with several functions

### types of binding
- Compile-Time binding (early binding/ static binding)
- Run-Time binding (late binding / dynamic binding)

**In C++, default = compile time binding
To do run time binding, use virtual keyword

- Parent pointer can have address of child object
- Child pointer cannot have address of parent object
```cpp
A *p; // pointer of parent
p = new B(); // object of child
// can only be used to call common functions
```

```cpp
#include<iostream>

using namespace std;

  

class Sim {

public:

virtual void calling() {

cout<<"no sim"<<endl;

}

virtual void sms() {

cout<<"no sim"<<endl;

}

};

  

class Jio:public Sim{

public:

void calling() {

cout<<"Jio calling"<<endl;

}

void sms() {

cout<<"Jio sms"<<endl;

}

};

  

class Airtel:public Sim{

public:

void calling() {

cout<<"Airtel calling"<<endl;

}

void sms() {

cout<<"Airtel sms"<<endl;

}

};

  

class BSNL:public Sim{

public:

void calling() {

cout<<"BSNL calling"<<endl;

}

void sms() {

cout<<"BSNL sms"<<endl;

}

};

  

int main(){

int ch;

cout<<"1 for Jio\n2 for BSNL\n3 for Airtel\nEnter you choice: ";

cin>>ch;

Sim *p;

if(ch == 1)

p = new Jio();

else if(ch == 2)

p = new BSNL();

else if(ch == 3)

p = new Airtel();

p -> calling();

p -> sms();

return 0;

}
```
In above program:
- virtual prevents compile time binding causing "no sim" for every call
- calling and sms function are needed in Sim class because only common functions can be called with parent pointer having child object


## pure virtual function
- dummy function
- cannot be called
```cpp
class Sim {

public:

virtual void calling() = 0;

virtual void sms() =0;

};
```
