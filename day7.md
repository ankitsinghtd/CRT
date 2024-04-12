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

# Features of OOPS
- Object (Anything that has existence in real world or real world enitity. Objects share some properties)
- Class is a group of similar type of objects to store common properties of all the objects
- Data Hiding - by declaring them as private we can hide them from external objects. For security
- Data Abstraction - to hide the internal complex details of a class from external object
- Encapsulation - Bundling of member variables (data) as well as member functions (operations) together in a class as a single unit.

