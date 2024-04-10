# loops
- entry controlled
- exit controlled
## while loop
```c
initialize;
while(condition) {
	statement;
	update;
}
```

"\\b" -> moves cursor
"\\b " -> remove last character from output (for if we want comma separated values and there is extra comma)

```c
int main() {
	int n, i;
	printf("Enter how man terms: ");
	scanf("%d", &n);
	i=n;
	while(i)
		printf("%d", --i);
	return(0);
}
```

Questions:
- print 1 2 3 4 5 [print i]
- print 1 4 9 16 25 [print i x i]
- print 1 8 27 64 125 [print i x i x i]
- print 1 3 5 7 9 [print 2 x i - 1]
- print 0 2 4 6 8 [print 2 x i - 2]
- print 1 0 1 0 1 (binary) [print i%2]

```c
term = count = 1;
while(count <= n) {
	printf("%d",term);
	term += 2;
	count++;
}
```


```c
int n=10;

unsigned long long int term,count;

term = 9;

count = 1;

while(count <= n) {

printf("%llu, ", term);

term =term * 10 + 9;

count++;

}
```
Output: 9, 99, 999, 9999 ....

```c
int n=10;

int term,count;

term = 1;

count = 1;

while(count <= n) {

printf("%d, ", term);

term = -term;

count++;

}
```
Output: 1, -1, 1, -1, 1, -1 ....


```c
term = !term;
```

OR 

```c
term = 1 - term;
```

Output: 1 0 1  0 1 0 1 ...

```c
int term1,count, term2,sum;

term1 = count = term2 = 1;

while(count <= n) {

printf("%d, ", term1);

sum = term1 + term2;

term1 = term2;

term2 = sum;

count++;

}
```

Fibonacci

Question: tribonacci

```c
while() {
	//code
}
```
error

```c
while(1) {
	//code
}
```
infinite loop


## for loop
syntax
```c
for ( initialize; condition; update) {
	statement;
}
```

OR 

```c
for ( initialize1, initialize2, ...; condition1 && condition2 || condition3; update1, update2, update3){
	statement;
}
```

Question : 9, 99, 999, 9999 .....

```c
for(int n=10,term=9,count=1; count<=n; count++, term = term * 10 + 9){

printf("%d ", term);

}
```

## nested loop
- matrix ( rows and columns) / multidimension stuff

Question: 

print letter H:
```c
int n=5,i,j,mid;

mid = (n+1) / 2;

for(i=1;i <=n; i++){

for(j=1; j<=n; j++) {

if(i == mid || j == 1 || j == n)

printf("*");

else

printf(" ");

}

printf("\n");

}
```

print letter E:
```c
int n=5,i,j,mid;

mid = (n+1) / 2;

for(i=1;i <=n; i++){

for(j=1; j<=n; j++) {

if(i == mid || i == 1 || i == n || j == 1)

printf("*");

else

printf(" ");

}

printf("\n");

}
```

print letter X:
- leetcode 1572, 2312
```c
for(i=1;i <=n; i++){

for(j=1; j<=n; j++) {

if( == i || i + j == n+1)

printf("*");

else

printf(" ");

}

printf("\n");

}
```

print letter Z:
```c
for(i=1;i <=n; i++){

for(j=1; j<=n; j++) {

if( i == 1 || i + j == n+1 || i == n)

printf("*");

else

printf(" ");

}

printf("\n");

}
```

Question: half triangle
```c
for(i=1;i <=n; i++){

for(j=1; j<=i; j++) {

printf("*");

}

printf("\n");

}
```

```c
for(i=1;i <=5; i++){

for(j=i; j>=1; j--) {

printf("%d ", j);

}

printf("\n");

}
```
Output:
1 
2 1 
3 2 1 
4 3 2 1 
5 4 3 2 1


```c
for(i=1;i <=5; i++){

for(j=i; j>=1; j--) {

printf("%d ", j%2);

}

printf("\n");

}
```
Output:
1 
0 1 
1 0 1 
0 1 0 1 
1 0 1 0 1


Question:
print
1
2 6
3 7 0
4 8 1 3
5 9 2 4 5

Question:
full triangle

Question:
swastik
```c
for(i=1; i<=9; i++){

for(j=1; j<=9; j++){

if(i == 5|| j== 5 || (i==1 && j >5) || (j == 1 && i < 5) || (j == 9 && i > 5) || (i == 9 && j < 5))

printf("*");

else

printf(" ");

}

printf("\n");

}
```

## jump statements
### break keyword
- used to terminate a switch or loop


```c
if (a>2) {

printf("hello");

break;

printf("Bye");

}
```
Output : error [can't use break without switch or loop]

Question: half triangle using break

```c
for(i=1; i<=5;i++) {

for(j=1;j<=5; j++) {

  

if (j>i) {

break;

}

printf("%d", j);

}

printf("\n");

}
```

### continue keyword
- skips all the remaining statements of a loop and jumps to next round

Question:
ABCDEDCBA
ABCD DCBA
ABC   CBA
AB     BA
A       A
A       A
AB     BA
ABC   CBA
ABCD DCBA
ABCDEDCBA

```c
for(i=n; i>=1;i--) {

for(j=1;j<=i; j++) {

printf("%c", j+64);

}

for(k=1; k<= (2*(n-i)-1); k++){

printf(" ");

}

for(l=i; l>=1 ; l--){

if(l == n)

continue;

printf("%c", l+64);

}

printf("\n");

}

for(i=1; i<=n;i++) {

for(j=1;j<=i; j++) {

printf("%c", j+64);

}

for(k=1; k<= (2*(n-i)-1); k++){

printf(" ");

}

for(l=i; l>=1 ; l--){

if(l == n)

continue;

printf("%c", l+64);

}

printf("\n");

}
```

