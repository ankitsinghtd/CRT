# characters and strings

| 'a' | "abc" |

| ---------------- | ------------------- |

| char ch ='a'; | char s1[4] = "abc"; |

  

- string declare

```cpp

char s1[20];

```

- string initialise

```cpp

char s1[] = "matrix";

```

- string input in C

```c

scanf("%s", s1); // no & required as s1 is array (array name denotes base address)

```

* scanf() can't input space *

* **use gets(s1); function for string with spaces (in;put ends on 'enter')

  

- string input in C++

```cpp

cin>>name;

```

OR

```cpp

cin.getline(s1, 20); // 20 = size of array

```

  
  

- string output in C

```c

printf("%s", s1);

```

OR

```c

puts(s1); //string.h

```

  

- string output in C++

```cpp

cout<<s1;

```

OR

```cpp

cout.write(s1, strlen(s1));

```

  

## wildcard stuff

- in C, keyboard = stdin

- monitor = stdout

  

## characters and string continued

Following code doesn't work !!!!

```c

int main(){

  

char name[20];

  

int roll;

  

printf("Enter roll no: ");

  

scanf("%d", &roll);

  

printf("Enter name: ");

  

fflush(stdin); // for 'enter'(after roll no input) bug with gets function

  

gets(name);

  

printf("You are %s with roll no %d",name,roll);

  

}

```

  

This works !!

```C

int main(){

  

char name[20];

  

int roll;

  

printf("Enter roll no: ");

  

scanf("%d", &roll);

  

printf("Enter name: ");

  

scanf("\n%[^\n]",name); // skip enter and scan until next 'enter' (fflush alternative)

  

printf("You are %s with roll no %d",name,roll);

  

}

```

  
  

regex for input manipulation

```c

int main(){

  

char name[20];

  

int roll;

  

printf("Enter roll no: ");

  

scanf("%d", &roll);

  

printf("Enter name: ");

  

scanf("\n%[A-Za-z0-9 ]",name); // upper case, lower case, numbers and a space allowed

  

printf("You are %s with roll no %d",name,roll);

  

}

```

  

**Java uses sc.skip("\\r\\n");

  

```cpp

int main() {

  

int roll;

  

char name[20];

  

cout<<"Enter roll no: ";

  

cin>>roll;

  

cin.ignore(); // ignore 'enter' from roll no input

  

cout<<"Enter name: ";

  

cin.getline(name ,20); // inputs strings with space

  

cout<<"You are " <<name<<" with roll no "<<roll<<endl;

  

return 0;

  

}

```

  

## string.h

- strlen

- strlwr

- strupr

- strrev

- strcpy

- strcat

- strcmp

- stricmp (ignore case and compare)

- strstr (searching)

  

```cpp

int main() {

  

char s1[10], s2[10];

  

cout<<"enter first half of string: ";

  

cin.getline(s1, 10);

  

cout<<"enter second half of string: ";

  

cin.getline(s2, 10);

  

cout<<strlen(s1)<<" "<<strlen(s2)<<endl;

  

strcat(s1, s2);

  

cout<<s1<<endl;

  

return 0;

  

}

```

  

### alphabet sorting

- lexographical comparison

  

another code that doesn't work properly

```cpp

int main() {

  

char s1[10], s2[10];

  

cout<<"enter first half of string: ";

  

cin.getline(s1, 10);

  

cout<<"enter second half of string: ";

  

cin.getline(s2, 10);

  

cout<<strlen(s1)<<" "<<strlen(s2)<<endl;

  

strcat(s1, s2);

  

cout<<s1<<endl;

  

int var = strcmp(s1, s2);

  

if(var == 0){

  

cout<<"equal strings";

  

}

  

else if(var == 1) {

  

cout<<" s1 > s2 bro";

  

}

  

else if(var == -1) {

  

cout<<" s1 < s2 bro";

  

}

  

else {

  

cout<<"strcmp returned "<<var;

  

}

  

return 0;

  

}

```

  

### string searching

```cpp

int main() {

  

char s1[50], s2[10];

  

cout<<"enter a string: ";

  

cin.getline(s1, 50);

  

cout<<"enter string to search: ";

  

cin.getline(s2, 10);

  

cout<<strstr(s1, s2)-s1;

  

// strstr returns address

  

// subtract base address from strstr to get index

  

return 0;

  

}

```

  

### manual strlen

  

```cpp

int main() {

  

char s1[50];

  

cout<<"enter a string: ";

  

cin.getline(s1, 50);

  

int i=0;

  

while(s1[i]!='\0'){

  

i++;

  

}

  

cout<<"size of string:"<<i;

  

return 0;

  

}

```

  

### manual strupr

  

```cpp

int main() {

  

char s1[50];

  

cout<<"enter a string: ";

  

cin.getline(s1, 50);

  

int i=0;

  

while(s1[i]!='\0'){

  

if(s1[i] >= 97){

  

s1[i]-=32;

  

}

  

i++;

  

}

  

cout<<"string in upper case: "<<s1;

  

return 0;

  

}

```

  

### manual strrev

  

```cpp

int main() {

  

char s1[50];

  

cout<<"enter a string: ";

  

cin.getline(s1, 50);

  

int i=0, n=strlen(s1)-1;

  

while(i<=n){

  

s1[i] = s1[n] - s1[i] + (s1[n] = s1[i]);

  

i++;

  

n--;

  

}

  

cout<<"reverse of string:"<<s1;

  

return 0;

  

}

```

  

### manual strcpy

```cpp

int main() {

  

char s1[50],s2[50];

  

cout<<"enter a string: ";

  

cin.getline(s1, 50);

  

int i=0;

  

while(s1[i]!='\0'){

  

s2[i] = s1[i];

  

i++;

  

}

  

s2[i]='\0'; // to avoid garbage and end the string properly

  

cout<<"copy of string: "<<s2;

  

return 0;

  

}

```

  
  

## String class in C++


Master program for all string class usage

```cpp

#include<iostream>

#include<string>

using namespace std;

int main(){

string str1("first string");

  

for(auto it1=str1.begin(); it1!=str1.end(); it1++)

cout << *it1;

cout << endl;

  

for(auto it2=str1.rbegin(); it2!=str1.rend(); it2++)

cout << *it2;

cout << endl;

  

for(auto it3=str1.cbegin(); it3!=str1.end(); it3++)

cout << *it3;

cout << endl;

  

for(auto it4=str1.crbegin(); it4!=str1.rend(); it4++)

cout << *it4;

cout << endl;

  

string s0("Matrix Computers");

string s1;

cout<<s1<<endl; //No output

string s2(s0); //copy one string object into another

cout<<s2<<endl; //Matrix Computers

string s3(s0, 7, 4); //index,count

cout<<s3<<endl; //Comp

string s4 ("Matrix Computers"); //copy c style string

cout<<s4<<endl; //Matrix Computers

string s5 ("Matrix Computers", 6); //copy First 6 characters

cout<<s5<<endl; //Matrix

string s6(10, '*'); //copy * 10 times

cout<<s6<<endl; //**********

string s7(s0.begin(), s0.begin()+6);

cout<<s7<<endl; //Matrix

  

string s8("Matrix");

string s9("Computers");

cout<<s8.length()<<endl;//6

cout<<s8.size()<<endl;//6

  

s8.swap(s9);

//or

//swap(s8,s9);

cout<<s8<<endl;//Computers

cout<<s9<<endl;//Matrix

  

char c[10];

s9.copy(c,3,0);

cout<<c<<endl;//Mat

string s10;

cout<<"Enter a line:";

getline(cin,s10);

cout<<s10<<endl;

  

string s11("Matrix");

s11.pop_back();

cout<<s11<<endl;//Matri

s11.push_back('x');

cout<<s11<<endl;//Matrix

cout<<s11.front()<<endl;//M

cout<<s11.back()<<endl;//x

cout<<s11.at(0)<<endl;//M

cout<<s11[0]<<endl;//M

s11+=" Computers";

//or

//s11.append(" Computers")

cout<<s11<<endl;//Matrix Computers

string s12;

//s12=s11;

//or

s12.assign(s11);

cout<<s12<<endl;//Matrix Computers

  

string s13("Matrix");

cout<<s13.substr(2,3)<<endl;//tri

cout<<s13.substr(2)<<endl;//trix

s13.insert(3,"...");

cout<<s13<<endl;//Mat...rix

s13.replace(3,3,"###");

cout<<s13<<endl;//Mat###rix

s13.erase(3,3);

cout<<s13<<endl;//Matrix

cout<<s13.empty()<<endl;//0(false)

s13.clear();

cout<<s13.empty()<<endl;//1(true)

  
  

string s14("ajay");

string s15("ravi");

int ans=s14.compare(s15);

if(ans > 0 )

cout<<"String first is greater"<<endl;

else if(ans < 0 )

cout<<"String second is greater"<<endl;

else if(ans==0)

cout<<"Both are equal"<<endl;

  

if(s14 > s15 )

cout<<"String first is greater"<<endl;

else if(s14 < s15 )

cout<<"String second is greater"<<endl;

else if(s14==s15)

cout<<"Both are equal"<<endl;

  

string s16 = "Matrix Computers";

cout<<s16<<endl;

s16.resize(6);

cout<<s16<< endl;

  

string s17("it is a is and is");

string s18("is");

int pos=s17.find(s18);

if(pos != string::npos) //npos is -1

cout<<"Found at "<<pos<<endl;

else

cout<<"Not found"<<endl;

  

pos=s17.rfind(s18);

if(pos != string::npos) //npos is -1

cout<<"Found at "<<pos<<endl;

else

cout<<"Not found"<<endl;

  

string s19("");

cout<<s19.capacity()<<endl; //15

s19.append("1234567890123456");

cout<<s19.capacity()<<endl; //30

s19.append("789012345678901");

cout<<s19.capacity()<<endl; //60

s19.shrink_to_fit();

cout<<s19.capacity()<<endl; //31

return(0);

}

```


```cpp

#include<iostream>

  

#include<string>

  

using namespace std;

  

int main() {

  

string s1 = "gaurav ", s2 = "saraswat", s3;

  

s3 = s1+s2;

  

cout<<s3;

  

return 0;

  

}

```

input using string class

  
```cpp

int main() {

  

string s1;

  

getline(cin, s1); // to input space as well

  

cout<<s1;

  

return 0;

  

}

```

  
comparing using string class

  
```cpp

int main() {

  

string s1="abc", s2="ABC";

  

if(s1>s2)

  

cout<<"s1 is greater";

  

else if(s2 < s1)

  

cout<<"s2 is greater";

  

else

  

cout<<"Equal :)";

  

return 0;

  

}

```

Output: s1 is greater (ASCII comparison)

  
  

Question:

g

ga

gau

gaur

gaura

gaurav

  

```cpp

int main() {

  

string s1="gaurav";

  

for(int i=0; i<s1.size(); i++){

  

for(int j=0; j<=i; j++){

  

cout<<s1[j];

  

}

  

cout<<endl;

  

}

  

return 0;

  

}

```

# structure
user defined datatype
- struct/union/enum/class(C++)

```CPP
struct Date{

int day, month, year;

};

  

struct Time{

int h, m, s;

};

  

struct Address{

int pno;

char lane[20];

char city[20];

};

  

struct Student {

int roll;

Address add;

Date dob;

string name;

};
```

In C,

```c
struct Date dob, doj;
```

OR

```c
typedef struct Date{
	// stuff
}dt;

dt dob, doj;
```

In C++,

```cpp
struct Date{

int day, month, year;

}; // semicolon is must

  

int main() {

Date dob, doj; // 12 bytes for each object (4x3)

dob.day = 1;

dob.month = 1;

dob.year = 2000;

doj.day = 2;

doj.month = 2;

doj.year = 2020;

cout<<"Date of Birth is "<<dob.day<<"/"<<dob.month<<"/"<<dob.year<<endl;

cout<<"Date of Joining is "<<doj.day<<"/"<<doj.month<<"/"<<doj.year<<endl;

return 0;

}
```

Example 2:
```cpp
struct Student{

int roll;

string name;

float per;

};

int main() {

Student s1, s2;

cout<<"Enter roll no, name and percentage of Student 1: ";

cin>>s1.roll>>s1.name>>s1.per;

cout<<"Enter roll no, name and percentage of Student 2: ";

cin>>s2.roll>>s2.name>>s2.per;

if(s1.per > s2.per)

cout<<s2.name<<" is bad student according to society";

else if(s2.per > s1.per)

cout<<s1.name<<" is bad student according to society";

else

cout<<"both students have bright future according to society";

return 0;

}
```

**+, - don't work on struct objects
= however does work

Initialising a struct object
```cpp
Student s[3]={{101,"ajaykumar", 54.6}, {102,"vijaykumar", 84.6}, {103,"gaurav", 67.6}};
```
- similar to array, partially initialising object results in 0


## padding
```cpp
struct Abc{

int roll;

char c;

}a1;

int main() {

cout<<sizeof(a1);

return 0;

}
```
Output: 8

```cpp
struct Abc{

int roll;

char c;

char y;

char z;

char x;

}a1;
```
Output: also 8

```cpp
struct Abc{

int roll;

char c;

char y;

char z;

char x;

}a1;
```
Output: 12 !!?>??!!?>!?>!>?!



## Swapping objects

By reference

```cpp
struct Complex {

int real;

int imag;

};

void swapp(Complex &c1, Complex &c2){

Complex t=c1;

c1 = c2;

c2 = t;

}

int main() {

Complex c1, c2;

c1.real = 5; c1.imag = 23;

c2.real = 2; c2.imag = 8;

swapp(c1, c2);

cout<<c1.real<<" + "<<c1.imag<<"i"<<endl;

cout<<c2.real<<" + "<<c2.imag<<"i"<<endl;

return 0;

}
```

By Address

```cpp
struct Complex {

int real;

int imag;

};

void swapp(Complex *c1, Complex *c2){

Complex t=*c1;

*c1 = *c2;

*c2 = t;

}

int main() {

Complex c1, c2;

c1.real = 5; c1.imag = 23;

c2.real = 2; c2.imag = 8;

swapp(&c1, &c2);

cout<<c1.real<<" + "<<c1.imag<<"i"<<endl;

cout<<c2.real<<" + "<<c2.imag<<"i"<<endl;

return 0;

}
```

## Arrow operator
structure and pointer

```cpp
struct Student {

int roll;

}s1, *p; // s1 gets 4 bytes (for int) and p gets 4 bytes (for address)

  
	
int main() {

p = &s1;

s1.roll = 5; // standard stuff

// *p.roll = 6 (error, '.' has higher precedence)

(*p).roll = 6; // big brain stuff

p->roll = 8; // godly stuff

// pointer -> member = value;

return 0;

}
```

Swap re-imagined using pointer
```cpp
#include <iostream>

#include <string>

using namespace std;

  

struct Complex

{

  

int real;

  

int imag;

};

  

void swapp(Complex *c1, Complex *c2)

{

  

int t=c1->real;

c1->real = c2->real;

c2->real = t;

t = c1->imag;

c1->imag = c2->imag;

c2->imag = t;

}

  

int main()

{

  

Complex c1, c2;

  

c1.real = 5;

c1.imag = 23;

  

c2.real = 2;

c2.imag = 8;

  

swapp(&c1, &c2);

  

cout << c1.real << " + " << c1.imag << "i" << endl;

  

cout << c2.real << " + " << c2.imag << "i" << endl;

  

return 0;

}
```