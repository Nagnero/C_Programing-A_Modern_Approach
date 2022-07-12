# 1
Wirte a program that finds the largest in a series of numbers entered by the user. The program must prompt the user to enter numbers one by one. When the user enters 0 or a negative number, the program must display the largest nonnegative number entered:
```
Enter a number: 60
Enter a number: 38.3
Enter a number: 4.89
Enter a number: 100.62
Enter a number: 75.2295
Enter a number: 0

The largest number entered was 100.62
```
Notice that the numbers aren't necessarily integers.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  float num = 1, large;

  printf("Enter a number: ");
  scanf("%f", &large);

  while (num > 0) {
    printf("Enter a number: ");
    scanf("%f", &num);
    if (num < large)
      continue;
    else
      large = num;
  }
  printf("\nThe largest number entered was %.2f", large);

  return 0;
}
```
<br><br>


# 2 (Hard)
Write a program that asks the user to enter two integers, then calculates and displays their greatest common divisor (GCD):
```
Enter two integers: 12 28
greatest common divisor: 4
```
*Hint:* The classic algorithm for compution the GCD, known as Euclid's algorithm, goes as follows: Let `m` and `n` be variables containing the two numbers. If `n` is 0, then stop: `m` contains the GCD. Otherwise, compute the remainder when `m` is divided by `n`. Copy `n` into `m` and copy the remainder into `n`. Then repeat the process, starting with testing whether `n` is 0.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int num1, num2, temp=0;

  printf("Enter two integers: ");
  scanf("%d %d", &num1, &num2);
  while (1) {
    if (num1 == 0) {
      printf("Greatest common divisor: %d\n", num2);
      break;
    }
    else {
      temp = num2 % num1;
      num2 = num1;
      num1 = temp;
    }
  }

  return 0;
}
```
<br><br>


# 3
Write a program that asks the user to enter a fraction, then reduces the fraction to lowest term:
```
Enter a fraction: 6/12
In lowest terms: 1/2
```
*Hint:* To reduce a fraction to lowest terms, first compute the GCD of the numerator and denominator. Then divide both the numerator and denominator by the GCD
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int up, down, up_origin, down_origin, temp;

  printf("Enter a fraction: ");
  scanf("%d/%d", &up, &down);
  up_origin = up;
  down_origin = down;
  while (up != 0) {
    temp = down % up;
    down = up;
    up = temp;
  }
  printf("In lowest terms: %d/%d", up_origin / down, down_origin / down);

  return 0;
}
```
<br><br>


# 4
Add a loop to the `broker.c` program of Section 5.2 so that the user can enter more than one trade and the program will calculate the commission on each. The program should terminate when the user enters 0 as the trade value:
```
Enter value of trade: 30000
Commission: $166.00

Enter value of trade: 20000
Commission: $144.00

Enter value of trade: 0
```
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  float commission, value;

  printf("Enter value of trade: ");
  scanf("%f", &value);

  while (value > 0) {

    if (value < 2500.00f)
      commission = 30.00f + .017f * value;
    else if (value < 6250.00f)
      commission = 56.00f + .0066f * value;
    else if (value < 20000.00f)
      commission = 76.00f + .0034f * value;
    else if (value < 50000.00f)
      commission = 100.00f + .0022f * value;
    else if (value < 500000.00f)
      commission = 155.00f + .0011f * value;
    else
      commission = 255.00f + .0009f * value;

    if (commission < 39.00f)
      commission = 39.00f;

    printf("Commission: $%.2f\n\nEnter value of trade: ", commission);
    scanf("%f", &value);
  }

  return 0;
}
```
<br><br>


# 5
Programming Project 1 in Chapter 4 asked you to write a program that displays a two-digit number with its digits reversed. Generalize the program so that the number can have one, two, three, or more digits. *Hint:* Use a `do` loop that repeatedly divides the number by 10, stopping when it reaches 0.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int num;

  printf("Enter a number: ");
  scanf("%d", &num);
  printf("digits reversed is: ");
  do {
    printf("%d", num % 10);
    num /= 10;
  } while (num != 0);

  return 0;
}
```
<br><br>


# 6
Write a program that prompts the user to enter a number `n`, then prints all even squares between 1 and `n`. For example, if the user enters 100, the program should print the following:
```
4
16
36
64
100
```
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int num;

  printf("Enter a number: ");
  scanf("%d", &num);

  for (int i = 2; i * i <= num; i += 2)
    printf("%d\n", i * i);

  return 0;
}
```
<br><br>


# 7
Rearrange the `square3.c` program so that the `for` loop initializes `i`, tests `i`, and increments `i`. Don't rewrite the program; in particular, don't use any multiplications.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int i, n, odd, square;

  printf("This program prints a table of squares.\n");
  printf("Enter number of entries in table: ");
  scanf("%d", &n);

  odd = 3;
  for (i = 1, square = 1; i <= n; odd += 2, ++i) {
    printf("%10d%10d\n", i, square);
    square += odd;
  }
  return 0;
}
```
<br><br>


# 8
Write a program that prints a one-month calendar. The user specifies the number of days in the month and the day of the week on which the month begins:
```
Enter number of days in month: 31
Enter starting day of the week (1=Sun, 7=Sat) : 3
       1  2  3  4  5
 6  7  8  9 10 11 12
13 14 15 16 17 18 19
20 21 22 23 24 25 26
27 28 29 30 31
```
*Hint:* This program isn't as hard as it looks. The most important part is a `for` statement that uses a variable `i` to count from `1` to `n`, where n is the number of days in the month, printing each value of `i`. Inside the loop, an `if` statement tests whether `i` is the last day in a week; if so, it prints a new-line character.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int tot_date, day, init_day;

  printf("Enter number of days in month: ");
  scanf("%d", &tot_date);
  printf("Enter starting day of the week (1=Sun, 7=Sat) : ");
  scanf("%d", &day);
  init_day = day--;
  
  for (int i = 1; i <= tot_date; ) {
    if (i < init_day--)
      printf("   ");
    else {
      printf("%3d", i++);
      day++;
    }
    if (day % 7 == 0)
      printf("\n");
  }

  return 0;
}
```
<br><br>


# 10
Programming Projecct 9 in Chapter 5 asked you to write a program that determines which of two dates comes earlier on the calendar. Generalize the program so that the user may enter any number of dates. The user will enter 0/0/0 to indicate that no more dates will be entered:
```
Enter a date (mm/dd/yy) : 3/6/08
Enter a date (mm/dd/yy) : 5/17/07
Enter a date (mm/dd/yy) : 6/3/07
Enter a date (mm/dd/yy) : 0/0/0
5/17/07 is the earliest date
```
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int m1, m2, d1, d2, y1, y2;
  
  printf("Enter a date (mm/dd/yy): ");
  scanf("%d/%d/%d", &m1, &d1, &y1);
  while (1) {
    printf("Enter a date (mm/dd/yy): ");
    scanf("%d/%d/%d", &m2, &d2, &y2);

    if (m2 == 0 && d2 == 0 && y2 == 0)
      break;
    if (y2 < y1 || (y1 == y2 && m2 < m1) || (y1 == y2 && m1 == m2 && d2 < d1)) {
      y1 = y2;
      m1 = m2;
      d1 = d2;
    }
  } 

  printf("%d/%d/%d is the earliest date", m1, d1, y1);

  return 0;
}
```
<br><br>


# 11
The value of the mathematical constant `e` can be expressed as an infinite series: <br>
`e` = 1 + 1/1! + 1/2! + 1/3! + ... <br>
Write a program that approximates `e` by computing the value of<br>
1 + 1/1! + 1/2! + 1/3! + ... + 1/n! <br>
where `n` is an integer entered by the user.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int n, fac = 1;
  float sum = 1;

  printf("Enter the value : ");
  scanf("%d", &n);
  for (int i = 1; i < n; i++) {
    for (int j = 1; j <= i; j++) {
      fac *= j;
    }
    sum += (1.0f / fac);
    fac = 1;
  }
  printf("%f", sum);

  return 0;
}
```