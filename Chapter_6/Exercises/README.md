# 6
Translate the program fragment of Exercise 1 into a single `for` statement.
<br>

### Solution
```c
#include <stdio.h>

int main(void){
  for(int i = 1; i <= 128; i *= 2)
    printf("%d ", i);
  
  return 0;
}
```
<br><br>


# 7
Translate the program fragment of Exercise 2 into a sigle `for` statement.
<br>

### Solution
```c
#include <stdio.h>

int main(void) {

  for (int i = 9384; i > 0; i /= 10)
    printf("%d ", i);

  return 0;
}
```
<br><br>


# 9
Translate the `for` statement of Exercise 8 into an equivalent `while` statement. You will need one statement in addition to the `while` loop itself.
<br>

### Solution
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void) {

  int i = 10;

  while (i >= 1) {
    printf("%d ", i++);
    i /= 2;
  }

  return 0;
}
```