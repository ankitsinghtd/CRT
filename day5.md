# Arrays

- A collection of homogeneous elements stored continuously under a single name
```cpp
int arr[3] = {79, 80, 90};
```
- size = datatype x length (4 x 3 = 12 bytes)

print(arr) => prints base address
i.e array name denotes base address


## Ideal way to write numbers in different format ?
- 0b101 for binary (0b-101)
- 057 for octal (0-57)
- 25 for decimal (25)
- 0x61f24 for hexadecimal (0x-61f24)

##
```cpp
int main() {

int arr[5]={10,20,30,40,50};

int n=sizeof(arr)/sizeof(int);

cout<<"base address: "<<arr<<endl; // base address

cout<<"size of array: "<<n<<endl;

for(int i=0; i<n; i++) {

cout<<"Value at index "<<i<<": "<<arr[i]<<endl;

}

for(int i=0; i<n; i++) {

cout<<"address for index "<<i<<": "<<arr+i<<endl;

}

for(int i=0; i<n; i++) {

cout<<"dereferenced value of index "<<i<<" :"<<*(arr+i)<<endl;

}

return 0;

}
```

## "a[i] = i[a]" ????

```cpp
for(int i=0; i<n; i++) {

cout<<"Value at index "<<i<<": "<<i[arr]<<endl; // valid

}
```

## array initialization
- int arr[5]; //garbage value
- int arr[5] = {}; // all values are zero
- int arr[5] = {1} // first value is 1, all else 0
- static int arr[5]; // all values are zero
- (global scope) int arr[5]; // all values are zero
## maximum out of array
```cpp
int arr[100];

int main() {

int n,max;

cout<<"enter total elements: ";

cin>>n;

for(int i=0; i<n;i++) {

cout<<"Enter element "<<i<<" : "<<endl;

cin>>arr[i];

}

max = arr[0];

for(int i=0; i<n;i++) {

if(max < arr[i])

max = arr[i];

}

cout<<"\nMaximum number in this array is: "<<max;

return 0;

}
```

**When a pointer receives base address of an array then that can behave like an array

## dynamic array

| Static Array                   | Dynamic Array                          |
| ------------------------------ | -------------------------------------- |
| int arr[100]; cin>>n; (old)    | int *arr, n; cin>>n; arr = new int[n]; |
| int n; cin>>n; int a[n]; (new) |                                        |


```cpp
int *arr;
arr = new int[n];
//code
delete []arr;
```
## for each loop

```cpp
for(e:arr) {
	cout<<e;
}
```

## predefined function

```cpp
#include<algorithm>

using namespace std;

  

int main() {

int arr[] = {10, 20, 5 , 7, 30};

int n = sizeof(arr)/sizeof(int);

cout<<*max_element(arr, arr+n)<<endl;

cout<<*min_element(arr, arr+n)<<endl;

sort(arr, arr+n);

for(int e:arr)

cout<<e<<"\t";

cout<<endl;

reverse(arr, arr+n);

for(int e:arr)

cout<<e<<"\t";

cout<<endl;

return 0;

}
```

reverse print using vector
```cpp
int main() {

vector<int> v1 = {10,20,30,40,50};

for(auto itr=v1.rbegin(); itr!=v1.rend(); itr++){

cout<<*itr<<endl;

}

return 0;

}
```

# searching
## Linear Search
```cpp
int linear_search(int arr[], int n, int item) {

for(int i= 0; i<n; i++) {

if(arr[i] == item)

return i;

}

return -1;

}

  

int main() {

int n, pos, item;

cout<<"enter total numbers: ";

cin>>n;

int arr[n];

for(int i=0;i<n;i++){

cout<<"enter element "<<i<<endl;

cin>>arr[i];

}

cout<<"enter element to search: ";

cin>>item;

pos = linear_search(arr, n, item);

if(pos)

cout<<"found at: "<<pos;

return 0;

}
```

## Binary search
```cpp
int binary__search(int arr[], int n, int item) {

int low=0, high = n;

while(low<high){

int mid = (low+high)/2;

if(arr[mid] == item)

return mid;

else if(arr[mid] < item)

low = mid+1;

else

high = mid - 1;

}

return -1;

}

  

int main() {

int n, pos, item;

cout<<"enter total numbers: ";

cin>>n;

int arr[n];

for(int i=0;i<n;i++){

cout<<"enter element "<<i<<endl;

cin>>arr[i];

}

sort(arr, arr+n);

cout<<"enter element to search: ";

cin>>item;

cout<<"Sorted array :"<<endl;

for (int e:arr){

cout<<e<<" ";

}

pos = binary__search(arr, n,item);

if(pos!=-1)

cout<<"found at: "<<pos;

else

cout<<"not found !";

return 0;

}
```

# Sorting
## selection sort
	
https://www.geeksforgeeks.org/selection-sort/

 Lets consider the following array as an example: **arr[] = {64, 25, 12, 22, 11}**
 
 **First pass:**
 
 - For the first position in the sorted array, the whole array is traversed from index 0 to 4 sequentially. The first position where **64** is stored presently, after traversing whole array it is clear that **11** is the lowest value.
 - Thus, replace 64 with 11. After one iteration **11**, which happens to be the least value in the array, tends to appear in the first position of the sorted list.
 
 ![Selection Sort Algorithm | Swapping 1st element with the minimum in array](https://media.geeksforgeeks.org/wp-content/uploads/20230524115038/1.webp)
 
 Selection Sort Algorithm | Swapping 1st element with the minimum in array
 
 **Second Pass:**
 
 - For the second position, where 25 is present, again traverse the rest of the array in a sequential manner.
 - After traversing, we found that **12** is the second lowest value in the array and it should appear at the second place in the array, thus swap these values.
 
 ![Selection Sort Algorithm | swapping i=1 with the next minimum element](https://media.geeksforgeeks.org/wp-content/uploads/20230526165135/2.webp)
 
 Selection Sort Algorithm | swapping i=1 with the next minimum element
 
 **Third Pass:**
 
 - Now, for third place, where **25** is present again traverse the rest of the array and find the third least value present in the array.
 - While traversing, **22** came out to be the third least value and it should appear at the third place in the array, thus swap **22** with element present at third position.
 
 ![Selection Sort Algorithm | swapping i=3 with the next minimum element](https://media.geeksforgeeks.org/wp-content/uploads/20230526165200/3.webp)
 
 Selection Sort Algorithm | swapping i=2 with the next minimum element
 
 **Fourth pass:**
 
 - Similarly, for fourth position traverse the rest of the array and find the fourth least element in the array 
 - As **25** is the 4th lowest value hence, it will place at the fourth position.
 
 ![Selection Sort Algorithm | swapping i=3 with the next minimum element](https://media.geeksforgeeks.org/wp-content/uploads/20230526165244/4.webp)
 
 Selection Sort Algorithm | swapping i=3 with the next minimum element
 
 **Fifth Pass:**
 
 - At last the largest value present in the array automatically get placed at the last position in the array
 - The resulted array is the sorted array.
 
 ![Selection Sort Algorithm | Required sorted array](https://media.geeksforgeeks.org/wp-content/uploads/20230526165320/5.webp)
 
```cpp
// C++ program for implementation of 
// selection sort 
#include <bits/stdc++.h> 
using namespace std; 

// Function for Selection sort 
void selectionSort(int arr[], int n) 
{ 
	int i, j, min_idx; 

	// One by one move boundary of 
	// unsorted subarray 
	for (i = 0; i < n - 1; i++) { 

		// Find the minimum element in 
		// unsorted array 
		min_idx = i; 
		for (j = i + 1; j < n; j++) { 
			if (arr[j] < arr[min_idx]) 
				min_idx = j; 
		} 

		// Swap the found minimum element 
		// with the first element 
		if (min_idx != i) 
			swap(arr[min_idx], arr[i]); 
	} 
} 

// Function to print an array 
void printArray(int arr[], int size) 
{ 
	int i; 
	for (i = 0; i < size; i++) { 
		cout << arr[i] << " "; 
		cout << endl; 
	} 
} 

// Driver program 
int main() 
{ 
	int arr[] = { 64, 25, 12, 22, 11 }; 
	int n = sizeof(arr) / sizeof(arr[0]); 

	// Function Call 
	selectionSort(arr, n); 
	cout << "Sorted array: \n"; 
	printArray(arr, n); 
	return 0; 
} 


```


# 2D Array
- multi-dimension array
```cpp
int m[3][4]; // 3 rows, 4 columns
int n[5][3][4]; // 5 matrices, 3 rows, 4 columns
```

```cpp
int m[3][4] = {{1,1,1,1},{2,2,2,2},{3,3,3,3}};
```
