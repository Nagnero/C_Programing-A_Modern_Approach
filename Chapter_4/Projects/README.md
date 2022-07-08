# 1
Write a program that asks the user to enter a two-digit number, then prints the number with tis digits reversed. A session with the program should have the following appearance:
```
Enter a two-digit number: 28
The reversal is: 82
```
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
  int a, b;

  printf("Enter a two-digit number: ");
  scanf("%1d%1d", &a, &b);
  printf("The reversal is: %d%d", b, a);
  
  return 0;
}
```
<br><br>


# 2
Extend the program in Programming Project 1 to handle *three*-digit numbers.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
  int a;

  printf("Enter a three-digit number: ");
  scanf("%d", &a);
  printf("The reversal is: %d%d%d", a % 10, (a / 10) % 10, a / 100);

  return 0;
}
```
<br><br>


# 3
Rewrite the program in Programming Project 2 so that it prints the reversal of a three-digit number without using arithmetic to split the number into digts. *Hint*: See the upc.c program of Section 4.1
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
  int a, b, c;

  printf("Enter a three-digit number: ");
  scanf("%1d%1d%1d", &a, &b, &c);
  printf("The reversal is: %d%d%d\n", c, b, a);

  return 0;
}
```
<br><br>


# 4
Write a program that reads an integer entered by the user and displays it in
octal (base 8):

```
Enter a number between 0 and 32767: 1953
In octal, your number is: 03641
```

The output should be displayed using five digits, even if fewer digits are
sufficient. *Hint*: To convert the number to octal, first divide it by 8; the
remainder is the last digit of the octal number (1, in this case). Then divide
the original number by 8 and repeat the process to arrive at the next-to-last
digit. (`printf` is capable of displaying numbers in base 8, as we'll see in
Chapter 7, so there's actually an easier way to write this program.)
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {
  int a, b, c, d, e, f, g, h, i, j, k;

  printf("Enter the first 11 digits of a UPC: ");
  scanf("%1d%1d%1d%1d%1d%1d%1d%1d%1d%1d%1d", &a, &b, &c, &d, &e, &f, &g, &h, &i, &j, &k);
  printf("Check digit: %d\n", h);

  return 0;
}
```
<br><br>


# 5
Rewrite the `upc.c` program of Section 4.1 so that the user enters 11 digits at one time, instead of entering one digit, then five digits, and then another five digits.
```
Enter the first 11 digits of a UPC: 01380015173
Check digit: 5
```
<br>

### Solution
```c
#include <stdio.h>

int main(void) {

  int d, i1, i2, i3, i4, i5, j1, j2, j3, j4, j5, sum1, sum2, total;

  printf("Enter the first 11 digits of a UPC: ");
  scanf("%1d%1d%1d%1d%1d%1d%1d%1d%1d%1d%1d", &d, &i1, &i2, &i3, &i4, &i5, &j1, &j2, &j3, &j4, &j5);

  sum1 = d + i2 + i4 + j1 + j3 + j5;
  sum2 = i1 + i3 + i5 + j2 + j4;
  total = 3 * sum1 + sum2;

  printf("Check digit: %d\n", 9 - ((total - 1) % 10));

  return 0;
}
```
<br><br>


# 6
쓸데없이 긴 문제여서 pass