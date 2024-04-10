# characters and strings
| 'a'              | "abc"               |
| ---------------- | ------------------- |
| char ch ='a';    | char s1[4] = "abc"; |

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
    cout<<s1<<endl;         //No output
    string s2(s0);          //copy one string object into another
    cout<<s2<<endl;         //Matrix Computers
    string s3(s0, 7, 4);    //index,count
    cout<<s3<<endl;         //Comp
    string s4 ("Matrix Computers"); //copy c style string
    cout<<s4<<endl;         //Matrix Computers
    string s5 ("Matrix Computers", 6);  //copy First 6 characters
    cout<<s5<<endl;         //Matrix
    string s6(10, '*');     //copy * 10 times
    cout<<s6<<endl;         //**********
    string s7(s0.begin(), s0.begin()+6);
    cout<<s7<<endl;         //Matrix

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
	if(pos != string::npos)    //npos is -1
		cout<<"Found at "<<pos<<endl;
	else
		cout<<"Not found"<<endl;

    pos=s17.rfind(s18);
	if(pos != string::npos)    //npos is -1
		cout<<"Found at "<<pos<<endl;
	else
		cout<<"Not found"<<endl;

    string s19("");
    cout<<s19.capacity()<<endl;   //15
    s19.append("1234567890123456");
    cout<<s19.capacity()<<endl;   //30
    s19.append("789012345678901");
    cout<<s19.capacity()<<endl;   //60
    s19.shrink_to_fit();
    cout<<s19.capacity()<<endl;     //31
    return(0);
}
```


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


String class in C++
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