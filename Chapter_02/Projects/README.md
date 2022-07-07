# 1
Write a program that uses `printf` to display the following picture on the screen:
```
       *
      *
     *
*   *
 * *
  *
```
<br>

### Solution
```c
#include <stdio.h>

int main(void) {
	printf("       *\n");
	printf("      * \n");
	printf("     *  \n");
	printf("*   *   \n");
	printf(" * *    \n");
	printf("  *     \n");

  return 0;
}
```
<br><br>


# 2
Write a program that computes the volume of a sphere with with a 10-meter radius, using the formula v=4/3πr³. Write the fraction 4/3 as `4.0f / 3.0f` 
<br>

### Solution

```c
#include <stdio.h>

int main(void) {
	float volume, r = 10;
	volume = 4.0f / 3.0f * 3.1415 * r * r * r;
	printf("The volume is %f", volume);
}
```
<br><br>


# 3
Modify the program of Programming Project 2 so that it prompts the user to enter the radius of the sphere.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	float volume, r;
  printf("input the radius of the sphere");
  scanf("%f", &r);
	volume = 4.0f / 3.0f * 3.1415 * r * r * r;
	printf("The volume is %f", volume);
}
```
<br><br>


# 4
Write a program that asks the user to enter a dollars-and cents amount, then displays the amount with 5% tax added:
```
Enter an amount: 100.00
With tax added: $105.00
```
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	float dollar;

	printf("Enter an amount: ");
	scanf("%f", &dollar);
	printf("With tax added: $%.2f", dollar * 1.05);
}
```
<br><br>


# 5
Write a program that asks the user to enter a value for `x` and then displays the value of the following polynominal:

3x<sup>5</sup> + 2x<sup>4</sup> - 5x<sup>3</sup> - x<sup>2</sup> + 7x - 6

*Hint*: C doesn't have an exponentiation operator, so you'll need to multiply x
by itself repeatedly in order to compute the powers of x. (For example, `x * x *
x` is `x` cubed.)
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	int x, answer;

	printf("Write a integer x value : ");
	scanf("%d", &x);
	answer = 3 * x * x * x * x * x + 2 * x * x * x * x - 5 * x * x * x - x * x + 7 * x - 6;
	printf("The answer is %d", answer);
}
```
<br><br>


# 6
Modify the program of Programming Project 5 so that polynomial is evaluated using the following formula.
<br>
`((((3x + 2)x-5)x-1)x+7)x-6`

<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	int x, answer;

	printf("Write a integer x value : ");
	scanf("%d", &x);
	answer = ((((3 * x + 2) * x  - 5) * x - 1) * x + 7) * x - 6;
	printf("The answer is %d", answer);
}
```
<br><br>


# 7
Write a program that asks the user to enter a U.S dollar amount and then shows how to pay that amount using the smallest number of $20, $10, $5 and $1 bills:
```
Enter a dollar amount: 93

$20 bills: 4
$10 bills: 1
 $5 bills: 0
 $1 bills: 3
 ```
 
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
	int amount, twinty_dollars, ten_dollars, five_dollars, dollar;
	printf("Enter a dollar amount: ");
	scanf("%d", &amount);
	twinty_dollars = amount / 20;
	ten_dollars = (amount % 20) / 10;
	five_dollars = (amount % 10) / 5;
	dollar = amount % 5;
	printf("\n$20 bills: %d\n", twinty_dollars);
	printf("$10 bills: %d\n", ten_dollars);
	printf(" $5 bills: %d\n", five_dollars);
	printf(" $d bills: %d\n", dollar);
}
```