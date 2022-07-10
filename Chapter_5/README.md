# 1
Write a program that calculates how many digits a number contains:
```
Enter a number : 374
The number 374 has a 3 digits
```
You may assume that the number has no more than four digits. *Hint:* Use if statements to test the number. For example, if the number is between 0 and 9, it has one digit. If the number is between 10 and 99, it has two digits.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

	int num, digits = 1;

	printf("Enter a number: ");
	scanf("%d", &num);
	for (int temp = num; temp > 9; digits++) {
		temp /= 10;
	}
	printf("The number %d has %d digits", num, digits);

  return 0;
}
```
<br><br>


# 2
Write a program that asks the user for a 24-hour time, then displays the time in 12-hour form:
```
Enter a 24-hour time: 21:11
Equivalent 12-hour time: 9:11 PM
```
Be careful not to display 12::00 as 0:00
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

	int hour24, hour12=0, minute;

	printf("Enter a 24-hour time: ");
	scanf("%d:%d", &hour24, &minute);
	if (hour24 > 12) {
		hour12 = hour24 - 12;
		printf("Equivalent 12-hour time: %d:%d PM\n", hour12, minute);
	}
	else if (hour24 == 12)
		printf("Equivalent 12-hour time: %d:%d PM\n", hour24, minute);
	else
		printf("Equivalent 12-hour time: %d:%d AM\n", hour24, minute);
  
  return 0;
}
```
<br><br>


# 3
Modify the `broker.c` program of Section 5.2 by making both of the following changes:
(a) Ask the user to enter the number of shares and the price per share, instead of the value of the trade. <br>
(b) Add statements that compute the commission charged by a rival broker ($33 plus 3 cents per share fewer than 2000 shares; $33 plus 2 cents per share for 2000 shares or more). Display the rival's commission as well as the commission charged by the original broker
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  float commission, value, share_price, rival;
  int shares;

  printf("Enter number of shares: ");
  scanf("%d", &shares);
  printf("Enter price per share: ");
  scanf("%f", &share_price);

  value = shares * share_price;

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

  printf("Commission: $%.2f\n", commission);

  if (shares < 2000)
    rival = 33.00f + .03f * shares;
  else
    rival = 33.00f + .02f * shares;

  printf("Rival comission: $%.2f\n", rival);

  return 0;
}
```
<br><br>


# 4
Here's a simplified version of the Beaufort scale, which is used to setimate wind force:
| Speed (knots) | Description
| --- | --- |
| Less than 1 | Calm |
| 1-3 | Light air |
| 4-27 | Breeze |
| 28-47 | Gale |
| 48-63 | Storm |
| Above 63 | Hurricane |
Write a program that asks the user to enter a wind speed (in knots), then displays the corresponding description.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  float speed;

  printf("Enter the speed of wind (knot): ");
  scanf("%f", &speed);
  if (speed < 1)
    printf("Calm");
  else if (speed >= 1 && speed < 4)
    printf("Light air");
  else if (speed >= 4 && speed < 28)
    printf("Breeze");
  else if (speed >= 28 && speed < 48)
    printf("Gale");
  else if (speed >= 48 && speed <= 63)
    printf("Storm");
  else
    printf("Hurricane");

  return 0;
}
```
<br><br>


# 5
In one state, single residents are subject to the following income tax:
| Income | Amount of tax|
| --- | --- |
| Not over $750 | 1% of income|
| $750 - $2,250 | $7.50 plus 2% of amount over $750   |
| $2,250 - $3,750 | $37.50 plus 3% of amount over $2,250 |
| $3,750 - $5,250 | $82.50 plus 4% of amount over $3,750 |
| $5,250 - $7,000 | $142.50 plus 5% of amount over $5,250 |
| Over $7,000 | $230.00 plus 6% of amount over $7,000 |
Write a program that asks the user to enter the amount of taxable income, then displays the tax due
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  float income, tax;

  printf("input your income : ");
  scanf("%f", &income);
  if (income <= 750.00f)
    tax = income * 0.01f;
  else if (income <= 2250.00f)
    tax = 7.50f + (income - 750.00f) * 0.02f;
  else if (income <= 3750.00f)
    tax = 37.50f + (income - 2250.00f) * 0.03f;
  else if (income <= 5250.00f)
    tax = 82.50f + (income - 3750.00f) * 0.04f;
  else if (income <= 7000.00f)
    tax = 142.50f + (income - 5250.00f) * 0.05f;
  else
    tax = 230.00f + (income - 7000.00f) * 0.06f;
  printf("your tax due is %.2f", tax);

  return 0;
}
```
<br><br>


# 7
Write a program that finds the largest and smallest of four integers entered by the user
```
Enter four integers: 21 43 10 35
Largest: 43
Smallest: 10
```
Use as few if statements as possible. *Hint:* Four if statements are sufficient.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int num[4], max1, max2, min1, min2;

  printf("Enter four integers: ");
  scanf("%d %d %d %d", &num[0], &num[1], &num[2], &num[3]);
  if (num[0] < num[1]) {
    max1 = num[1];
    min1 = num[0];
  }
  else {
    max1 = num[0];
    min1 = num[1];
  }
  if (num[2] < num[3]) {
    max2 = num[3];
    min2 = num[2];
  }
  else {
    max2 = num[2];
    min2 = num[3];
  }

  printf("Largest: %d\n", max1 < max2 ? max2 : max1);
  printf("Smallest: %d\n", min1 < min2 ? min1 : min2);

  return 0;
}
```
<br><br>


# 8
The following table show the daily flights from one city to another:
| Departure time | Arrival time |
| ---: | ---: |
| 8:00 a.m. | 10:16 a.m. |
| 9:43 a.m. | 11:52 a.m. |
| 11:19 a.m. | 1:31 p.m. |
| 12:47 p.m. | 3:00 p.m. |
| 2:00 p.m. | 4:08 p.m. |
| 3:45 p.m. | 5:55 p.m. |
| 7:00 p.m. | 9:20 p.m. |
| 9:45 p.m. | 11:58 p.m. |

Write a program that asks the user to enter a time (expressed in hours and
minutes, using the 24-hour clock). The program then displays the departure and
arrival times for the flight whose departure time is closest to that entered by
the user:

```
Enter a 24-hour time: 13:15
Closest departure time is 12:47 p.m., arriving at 3:00 p.m.
```

*Hint*: Convert the input into a time expressed in minutes since midnight, and
compare it to the departure times, also expressed in minutes since midnight. For
example, 13:15 is 13 * 60 + 15 = 795 minutes since midnight, which is closer to
12:47 p.m. (767 minutes since midnight) than to any of the other departure
times.
<br>

### Solution
입력한 시간 이후의 departure time을 구함
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int hour24, minute, all;
  
  printf("Enter a 24-hour time: ");
  scanf("%d:%d", &hour24, &minute);
  all = hour24 * 60 + minute;
  if (all <= 8 * 60) {
    printf("Closest departure time is 8:00 a.m\n");
    printf("arriving at 10:16 a.m.\n");
  }
  else if (all <= 9 * 60 + 43) {
    printf("Closest departure time is 9:43 a.m\n");
    printf("arriving at 11:52 a.m.\n");
  }
  else if (all <= 11 * 60 + 19) {
    printf("Closest departure time is 11:19 a.m\n");
    printf("arriving at 1:31 p.m.\n");
  }
  else if (all <= 12 * 60 + 47) {
    printf("Closest departure time is 12:47 a.m\n");
    printf("arriving at 3:00 p.m.\n");
  }
  else if (all <= 14 * 60) {
    printf("Closest departure time is 2:00 p.m\n");
    printf("arriving at 4:08 p.m.\n");
  }
  else if (all <= 15 * 60 + 45) {
    printf("Closest departure time is 3:45 p.m\n");
    printf("arriving at 5:55 p.m.\n");
  }
  else if (all <= 19 * 60) {
    printf("Closest departure time is 7:00 p.m\n");
    printf("arriving at 9:20 p.m.\n");
  }
  else if (all <= 21 * 60 + 45) {
    printf("Closest departure time is 9:45 p.m");
    printf("arriving at 11:58 p.m.");
  }
}
```
<br><br>


# 9
Wirte a program that pormpts the user to enter two dates and then indicates which date comes earlier on the calandar:
```
Enter first date (mm/dd/yyyy): 3/6/08
Enter second date (mm/dd/yyyy): 5/17/07
5/17/07 is earlier than 3/6/08
```
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int month1, month2, day1, day2, year1, year2;

  printf("Enter first date (mm/dd/yyyy): ");
  scanf("%d/%d/%d", &month1, &day1, &year1);
  printf("Enter second date (mm/dd/yyyy): ");
  scanf("%d/%d/%d", &month2, &day2, &year2);

  if (year1 > year2)
    printf("%d/%d/%.2d is earlier than %d/%d/%.2d", month2, day2, year2, month1, day1, year1);
  else if (year1 < year2)
    printf("%d/%d/%.2d is earlier than %d/%d/%.2d", month1, day1, year1, month2, day2, year2);
  else if (month1 > month2)
    printf("%d/%d/%.2d is earlier than %d/%d/%.2d", month2, day2, year2, month1, day1, year1);
  else if (month1 < month2)
    printf("%d/%d/%.2d is earlier than %d/%d/%.2d", month1, day1, year1, month2, day2, year2);
  else if (day1 > day2)
    printf("%d/%d/%.2d is earlier than %d/%d/%.2d", month2, day2, year2, month1, day1, year1);
  else if (day1 < day2)
    printf("%d/%d/%.2d is earlier than %d/%d/%.2d", month1, day1, year1, month2, day2, year2);

  return 0;
}
```
<br><br>


# 10
Using the `switch` statement, write a program that converts a numerical grade into a letter grade:
```
Enter numberical grade: 84
Letter grade: B
```
Use the following grading scale: A = 90-100, B = 80-89, C = 70-79, D = 60-69, F = 0-59. Print an error message if the grade is larger than 100 or less than 0. *Hint:* Break the grade into two digits, then use a `switch` statement to test the ten's digit.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int grade;

  printf("Enter numberical grade: ");
  scanf("%d", &grade);

  if (grade > 100 || grade < 0) {
    printf("The grade is error");
    return 0;
  }
  switch (grade / 10) {
  case 9: case 10:
    printf("Letter grade: A");
    break;
  case 8:
    printf("Letter grade: B");
    break;
  case 7:
    printf("Letter grade: C");
    break;
  case 6:
    printf("Letter grade: D");
    break;
  default:
    printf("Letter grade: F");
  }

  return 0;
}
```
<br><br>


# 11
Write a program that asks the user for a two-digit number, then prints the English word for the number:
```
Enter a two-digit number: 45
You entered the number forty-five
```
*Hint:* Break the number into two digits. Use one `switch` statement to print the word for the first digit ("twenty", "thirty" and so forth). Use a second `switch` statement to print the word for the second digit. Don't forget that the numbers between 11 and 19 require special treatment.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int input;

  printf("Enter a two-digit number: ");
  scanf("%d", &input);
  printf("You entered the number ");
  if (input >= 10 && input <= 19) {
    switch (input) {
    case 10:
      printf("ten\n");
      return 0;
    case 11:
      printf("eleven\n");
      return 0;
    case 12:
      printf("twelve\n");
      return 0;
    case 13:
      printf("tirteen\n");
      return 0;
    case 14:
      printf("fourteen\n");
      return 0;
    case 15:
      printf("fifteen\n");
      return 0;
    case 16:
      printf("sixteen\n");
      return 0;
    case 17:
      printf("seventeen\n");
      return 0;
    case 18:
      printf("eighteen\n");
      return 0;
    case 19:
      printf("nineteen\n");
      return 0;
    }
  }
  else {
    switch (input / 10) {
    case 0:
      break;
    case 2:
      printf("twenty");
      break;
    case 3:
      printf("thirty");
      break;
    case 4:
      printf("fourty");
      break;
    case 5:
      printf("fifty");
      break;
    case 6:
      printf("sixty");
      break;
    case 7:
      printf("seventy");
      break;
    case 8:
      printf("eitghty");
      break;
    case 9:
      printf("ninety");
    }
  }

  if (input % 10 == 0)
    return 0;
  else
    printf("-");

  switch (input % 10) {
  case 1:
    printf("one\n");
    break;
  case 2:
    printf("two\n");
    break;
  case 3:
    printf("three\n");
    break;
  case 4:
    printf("four\n");
    break;
  case 5:
    printf("five\n");
    break;
  case 6:
    printf("six\n");
    break;
  case 7:
    printf("seven\n");
    break;
  case 8:
    printf("eight\n");
    break;
  case 9:
    printf("nine\n");
    break;
  }

  return 0;
}
```