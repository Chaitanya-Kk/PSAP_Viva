# C Programming Viva Notes for Turbo C

## 1. Fundamentals
### 1.1 Preprocessor Directives
- **Definition**: Instructions processed before compilation.
- **Common Directives**:
  - `#include`: Includes header files (e.g., `<stdio.h>`, `<conio.h>`).
  - `#define`: Defines constants or macros.
  - `#ifdef`, `#ifndef`, `#endif`: Conditional compilation.
- **Example**: Macro for square.
  ```c
  #include <stdio.h>
  #include <conio.h>
  #define SQUARE(x) (x*x)
  void main() {
      clrscr();
      printf("Square of 5: %d", SQUARE(5)); // Output: Square of 5: 25
      getch();
  }
  ```
- **Viva Tip**: Explain the difference between a macro and a function. Be ready to write a simple macro.

### 1.2 Operators and Expressions
- **Definition**: Operators perform operations on variables/values; expressions combine them to produce a value.
- **Types**:
  - Arithmetic: `+`, `-`, `*`, `/`, `%`
  - Relational: `==`, `!=`, `<`, `>`, `<=`, `>=`
  - Logical: `&&`, `||`, `!`
  - Bitwise: `&`, `|`, `^`, `~`, `<<`, `>>`
  - Assignment: `=`, `+=`, `-=`, `*=`, `/=`
  - Increment/Decrement: `++`, `--`
  - Ternary: `condition ? expr1 : expr2` (e.g., `max = (a > b) ? a : b;`)
- **Key Points**:
  - Precedence: `*`, `/`, `%` > `+`, `-` > relational > logical.
  - Associativity: Left-to-right for most, right-to-left for assignment.
- **Example**:
  ```c
  #include <stdio.h>
  #include <conio.h>
  void main() {
      clrscr();
      int x = 5 + 3 * 2; // Precedence: x = 11
      int a = 10, b = 5;
      int max = (a > b) ? a : b; // Ternary
      printf("x: %d, Max: %d", x, max); // Output: x: 11, Max: 10
      getch();
  }
  ```
- **Viva Tip**: Evaluate expressions like `x = 5 + 3 * 2`. Explain ternary operator with an example.

### 1.3 Algorithm vs. Flowchart
- **Algorithm**: Step-by-step textual procedure (e.g., pseudocode).
- **Flowchart**: Graphical representation using shapes (oval: start/end, diamond: decision).
- **Difference**:
  - Algorithm: Text-based, easier to write.
  - Flowchart: Visual, better for understanding program flow.
- **Example** (Algorithm for swapping):
  ```
  1. Input a, b
  2. temp = a
  3. a = b
  4. b = temp
  5. Output a, b
  ```
- **Viva Tip**: Draw a flowchart for checking if a number is prime or swapping two numbers.

### 1.4 Storage Classes
- **Definition**: Define scope, lifetime, and storage of variables.
- **Types**:
  - **auto**: Default, local scope, stack storage.
  - **static**: Retains value between function calls, data segment.
  - **register**: Suggests CPU register storage for faster access.
  - **extern**: Extends variable scope across files.
- **Example**:
  ```c
  #include <stdio.h>
  #include <conio.h>
  void func() {
      static int count = 0; // Retains value
      count++;
      printf("Count: %d\n", count);
  }
  void main() {
      clrscr();
      func(); // Output: Count: 1
      func(); // Output: Count: 2
      getch();
  }
  ```
- **Viva Tip**: Compare `static` vs. `auto`. Explain variable lifetime and scope.

## 2. Control Structures
### 2.1 Conditional Statements
- **If-else**: Conditional execution.
  ```c
  #include <stdio.h>
  #include <conio.h>
  void main() {
      clrscr();
      int a = 10, b = 5;
      if (a > b) printf("a is greater"); else printf("b is greater");
      getch();
  }
  ```
- **Switch-case**: Multi-way branching.
  ```c
  #include <stdio.h>
  #include <conio.h>
  void main() {
      clrscr();
      int x = 1;
      switch (x) {
          case 1: printf("One"); break;
          default: printf("Other");
      }
      getch();
  }
  ```
- **Viva Tip**: Explain why `break` is needed in switch. Compare if-else vs. switch.

### 2.2 Loops (**Starred Topic**)
- **Types**:
  - **for**: Known iterations.
    ```c
    for (int i = 0; i < 5; i++) printf("%d ", i); // Output: 0 1 2 3 4
    ```
  - **while**: Condition-based.
    ```c
    int i = 0;
    while (i < 5) { printf("%d ", i); i++; }
    ```
  - **do-while**: Executes at least once.
    ```c
    int i = 0;
    do { printf("%d ", i); i++; } while (i < 5);
    ```
- **Key Points**:
  - Use `break` to exit, `continue` to skip iteration.
  - Nested loops for patterns or 2D arrays.
- **Example**: Floyd’s triangle.
  ```c
  #include <stdio.h>
  #include <conio.h>
  void main() {
      clrscr();
      int n = 3, num = 1;
      for (int i = 1; i <= n; i++) {
          for (int j = 1; j <= i; j++) {
              printf("%d ", num++);
          }
          printf("\n");
      }
      getch();
  }
  /* Output:
  1 
  2 3 
  4 5 6 
  */
  ```
- **Viva Tip**: Write a pattern program (e.g., star triangle) or explain `do-while` vs. `while`.

## 3. Data Structures
### 3.1 Arrays (1D & 2D)
- **1D Array**:
  - Declaration: `int arr[5];`
  - Initialization: `int arr[5] = {1, 2, 3, 4, 5};`
  - Access: `arr[0]` (0-based indexing).
- **2D Array**:
  - Declaration: `int matrix[3][3];`
  - Initialization: `int matrix[2][3] = {{1, 2, 3}, {4, 5, 6}};`
  - Access: `matrix[i][j]`.
- **Key Points**: Row-major storage; used for matrices, tables.
- **Example**: Matrix addition.
  ```c
  #include <stdio.h>
  #include <conio.h>
  void main() {
      clrscr();
      int a[2][2] = {{1, 2}, {3, 4}}, b[2][2] = {{5, 6}, {7, 8}}, c[2][2];
      for (int i = 0; i < 2; i++)
          for (int j = 0; j < 2; j++)
              c[i][j] = a[i][j] + b[i][j];
      for (int i = 0; i < 2; i++) {
          for (int j = 0; j < 2; j++) printf("%d ", c[i][j]);
          printf("\n");
      }
      getch();
  }
  /* Output:
  6 8 
  10 12 
  */
  ```
- **Viva Tip**: Explain 2D array memory layout or write code for matrix transpose.

### 3.2 Strings
- **Definition**: Character array terminated by `\0`.
- **Declaration**: `char str[20] = "Hello";`
- **Functions** (`<string.h>`): `strlen`, `strcpy`, `strcmp`, `strcat`.
- **Example**: Reverse a string using pointers.
  ```c
  #include <stdio.h>
  #include <conio.h>
  void main() {
      clrscr();
      char str[20] = "Hello";
      char *p = str, temp;
      int len = 0;
      while (*p) { len++; p++; }
      p--;
      for (char *q = str; q < p; q++, p--) {
          temp = *q; *q = *p; *p = temp;
      }
      printf("Reversed: %s", str); // Output: Reversed: olleH
      getch();
  }
  ```
- **Viva Tip**: Write a program for string palindrome or explain `strcmp`.

### 3.3 Structure & Union
- **Structure**:
  - Groups different data types.
  - Syntax:
    ```c
    struct Student {
        int id;
        char name[20];
        float marks;
    };
    struct Student s1; // s1.id, s1.name
    ```
  - Size: Sum of member sizes (with padding).
- **Union**:
  - Stores one member at a time in shared memory.
  - Syntax:
    ```c
    union Data {
        int i;
        float f;
        char c;
    };
    union Data d; // Size = largest member
    ```
- **Example**:
  ```c
  #include <stdio.h>
  #include <conio.h>
  void main() {
      clrscr();
      struct Student s = {1, "John", 85.5};
      printf("ID: %d, Name: %s, Marks: %.1f", s.id, s.name, s.marks);
      getch();
  }
  ```
- **Viva Tip**: Compare structure vs. union. Explain memory padding in structures.

## 4. Functions
### 4.1 Functions
- **Definition**: Reusable code block.
- **Syntax**:
  ```c
  return_type function_name(parameters) {
      /* code */
      return value;
  }
  ```
- **Parameter Passing**:
  - **Pass by Value**: Copies value; no effect on original.
    ```c
    void swap(int x, int y) { int temp = x; x = y; y = temp; } // No effect
    ```
  - **Pass by Reference**: Uses pointers to modify original.
    ```c
    void swap(int *x, int *y) { int temp = *x; *x = *y; *y = temp; }
    ```
- **Example**:
  ```c
  #include <stdio.h>
  #include <conio.h>
  void swap(int *x, int *y) {
      int temp = *x; *x = *y; *y = temp;
  }
  void main() {
      clrscr();
      int a = 5, b = 10;
      swap(&a, &b);
      printf("a: %d, b: %d", a, b); // Output: a: 10, b: 5
      getch();
  }
  ```
- **Viva Tip**: Explain pass by value vs. reference with code.

### 4.2 Recursion
- **Definition**: Function calling itself with a base case.
- **Example**: Factorial.
  ```c
  #include <stdio.h>
  #include <conio.h>
  int factorial(int n) {
      if (n == 0) return 1;
      return n * factorial(n - 1);
  }
  void main() {
      clrscr();
      printf("Factorial of 5: %d", factorial(5)); // Output: 120
      getch();
  }
  ```
- **Key Points**: Needs base case to avoid stack overflow; uses stack memory.
- **Viva Tip**: Write recursive code for Fibonacci or explain recursion stack.

## 5. Pointers and Memory Management (**Starred Topic**)
### 5.1 Pointers
- **Definition**: Variables storing memory addresses.
- **Declaration**: `int *ptr;`
- **Operations**: Dereferencing (`*ptr`), address-of (`&x`).
- **Example**:
  ```c
  #include <stdio.h>
  #include <conio.h>
  void main() {
      clrscr();
      int x = 10;
      int *ptr = &x;
      printf("Value: %d", *ptr); // Output: Value: 10
      getch();
  }
  ```
- **Viva Tip**: Explain pointer declaration and dereferencing.

### 5.2 Memory Allocation
- **Static Memory**:
  - Allocated at compile time, fixed size, automatic management.
  - Example: `int arr[5];`
  - Advantages: Fast, no leaks.
  - Disadvantages: Fixed size.
- **Dynamic Memory**:
  - Allocated at runtime using `malloc`, `calloc`, `realloc`, freed with `free`.
  - Example:
    ```c
    #include <stdio.h>
    #include <conio.h>
    #include <stdlib.h>
    void main() {
        clrscr();
        int n = 3;
        int *arr = (int *)malloc(n * sizeof(int));
        arr[0] = 1; arr[1] = 2; arr[2] = 3;
        printf("Array: ");
        for (int i = 0; i < n; i++) printf("%d ", arr[i]);
        arr = (int *)realloc(arr, 5 * sizeof(int)); // Resize
        arr[3] = 4; arr[4] = 5;
        printf("\nResized: ");
        for (int i = 0; i < 5; i++) printf("%d ", arr[i]);
        free(arr);
        getch();
    }
    /* Output:
    Array: 1 2 3 
    Resized: 1 2 3 4 5 
    */
  ```
  - Advantages: Flexible size.
  - Disadvantages: Risk of leaks, dangling pointers.
- **Memory Functions**:
  - `malloc`: Allocates uninitialized memory.
  - `calloc`: Allocates and initializes to zero.
  - `realloc`: Resizes memory.
  - `free`: Deallocates memory.
- **Viva Tip**: Compare `malloc` vs. `calloc`. Explain `realloc` usage and memory leaks.

### 5.3 Dangling Pointer
- **Definition**: Pointer to freed or invalid memory.
- **Example**:
  ```c
  #include <stdio.h>
  #include <conio.h>
  #include <stdlib.h>
  void main() {
      clrscr();
      int *ptr = (int *)malloc(sizeof(int));
      *ptr = 10;
      free(ptr); // ptr is dangling
      ptr = NULL; // Avoid dangling pointer
      printf("Pointer set to NULL");
      getch();
  }
  ```
- **Viva Tip**: Explain how to avoid dangling pointers.

### 5.4 Linked List
- **Definition**: Nodes with data and pointer to next node.
- **Structure**:
  ```c
  struct Node {
      int data;
      struct Node *next;
  };
  ```
- **Example**: Create, traverse, and reverse a linked list.
  ```c
  #include <stdio.h>
  #include <conio.h>
  #include <stdlib.h>
  struct Node {
      int data;
      struct Node *next;
  };
  struct Node* reverseList(struct Node *head) {
      struct Node *prev = NULL, *current = head, *next;
      while (current != NULL) {
          next = current->next;
          current->next = prev;
          prev = current;
          current = next;
      }
      return prev;
  }
  void main() {
      clrscr();
      struct Node *head = NULL, *temp, *newNode;
      newNode = (struct Node *)malloc(sizeof(struct Node));
      newNode->data = 10; newNode->next = NULL; head = newNode;
      newNode = (struct Node *)malloc(sizeof(struct Node));
      newNode->data = 20; newNode->next = NULL; head->next = newNode;
      printf("Original: ");
      temp = head;
      while (temp != NULL) {
          printf("%d ", temp->data);
          temp = temp->next;
      }
      head = reverseList(head);
      printf("\nReversed: ");
      temp = head;
      while (temp != NULL) {
          printf("%d ", temp->data);
          temp = temp->next;
      }
      while (head != NULL) {
          temp = head;
          head = head->next;
          free(temp);
      }
      getch();
  }
  /* Output:
  Original: 10 20 
  Reversed: 20 10 
  */
  ```
- **Viva Tip**: Write code for node insertion or explain linked list vs. array.

### 5.5 Function Pointers
- **Definition**: Pointers to functions for callbacks.
- **Example**:
  ```c
  #include <stdio.h>
  #include <conio.h>
  int add(int a, int b) { return a + b; }
  void main() {
      clrscr();
      int (*funcPtr)(int, int) = add;
      printf("Sum: %d", funcPtr(3, 4)); // Output: Sum: 7
      getch();
  }
  ```
- **Viva Tip**: Explain function pointer syntax and use cases (e.g., callbacks).

### 5.6 Pointers in C vs. C++
- **C**: Essential for dynamic memory, pass-by-reference, strings, linked lists.
- **C++**: Raw pointers used, but references (`int &x`), smart pointers, and containers (`std::vector`) reduce reliance.
  - Turbo C++ uses raw pointers (no smart pointers).
- **Example** (Turbo C++):
  ```c
  #include <iostream.h>
  #include <conio.h>
  void main() {
      clrscr();
      int x = 10;
      int *ptr = &x;
      cout << "Value: " << *ptr; // Output: Value: 10
      getch();
  }
  ```
- **Viva Tip**: Explain why C++ references are safer than pointers.

## 6. File Handling (**Starred Topic**)
- **Definition**: Reading/writing data to files.
- **Functions**: `fopen`, `fclose`, `fscanf`, `fprintf`, `fgets`, `fputs`, `fread`, `fwrite`.
- **Modes**: `r` (read), `w` (write), `a` (append), `rb`, `wb` (binary).
- **Example**: Text file read/write.
  ```c
  #include <stdio.h>
  #include <conio.h>
  void main() {
      clrscr();
      FILE *fp = fopen("data.txt", "w");
      if (fp == NULL) {
          printf("Error: File not found");
      } else {
          fprintf(fp, "Hello");
          fclose(fp);
          fp = fopen("data.txt", "r");
          char ch;
          while ((ch = fgetc(fp)) != EOF) printf("%c", ch);
          fclose(fp);
      }
      getch();
  }
  ```
- **Example**: Binary file with structure.
  ```c
  #include <stdio.h>
  #include <conio.h>
  struct Student {
      int id;
      char name[20];
  };
  void main() {
      clrscr();
      struct Student s1 = {1, "John"};
      FILE *fp = fopen("data.bin", "wb");
      fwrite(&s1, sizeof(s1), 1, fp);
      fclose(fp);
      fp = fopen("data.bin", "rb");
      struct Student s2;
      fread(&s2, sizeof(s2), 1, fp);
      printf("ID: %d, Name: %s", s2.id, s2.name);
      fclose(fp);
      getch();
  }
  ```
- **Viva Tip**: Explain file modes (text vs. binary) or write a program to copy file contents.

## 7. Problem Solving (**Starred Topic**)
- **Approach**:
  1. Understand problem.
  2. Write algorithm/flowchart.
  3. Implement in C.
  4. Test output.
- **Common Problems**:
  - Sorting: Bubble, selection.
  - Searching: Linear, binary.
  - Patterns: Star triangle, Floyd’s triangle.
  - String: Reverse, palindrome.
  - Linked List: Reverse, merge.
  - Recursion: Fibonacci, factorial.
- **Example**: Bubble sort.
  ```c
  #include <stdio.h>
  #include <conio.h>
  void bubbleSort(int arr[], int n) {
      for (int i = 0; i < n-1; i++)
          for (int j = 0; j < n-i-1; j++)
              if (arr[j] > arr[j+1]) {
                  int temp = arr[j];
                  arr[j] = arr[j+1];
                  arr[j+1] = temp;
              }
  }
  void main() {
      clrscr();
      int arr[5] = {5, 2, 8, 1, 9};
      bubbleSort(arr, 5);
      for (int i = 0; i < 5; i++) printf("%d ", arr[i]); // Output: 1 2 5 8 9
      getch();
  }
  ```
- **Example**: Fibonacci (recursive and iterative).
  ```c
  #include <stdio.h>
  #include <conio.h>
  int fib(int n) {
      if (n <= 1) return n;
      return fib(n-1) + fib(n-2);
  }
  void main() {
      clrscr();
      printf("Fibonacci (recursive): %d\n", fib(5)); // Output: 5
      int n = 5, a = 0, b = 1, c;
      printf("Fibonacci (iterative): ");
      for (int i = 0; i <= n; i++) {
          printf("%d ", a);
          c = a + b;
          a = b;
          b = c;
      }
      getch();
  }
  ```
- **Viva Tip**: Solve a problem (e.g., array reverse, linked list reversal) and explain the algorithm.

## 8. Additional Topics
### 8.1 Bit Manipulation
- **Definition**: Operations on bits using bitwise operators (`&`, `|`, `^`, `~`, `<<`, `>>`).
- **Example**:
  ```c
  #include <stdio.h>
  #include <conio.h>
  void main() {
      clrscr();
      int a = 5; // 0101
      int b = 3; // 0011
      printf("a & b: %d\n", a & b); // Output: 1 (0001)
      printf("a << 1: %d", a << 1); // Output: 10 (1010)
      getch();
  }
  ```
- **Viva Tip**: Show binary calculations for bitwise AND or left shift.

### 8.2 Command-Line Arguments
- **Definition**: Parameters passed to `main` via `int argc, char *argv[]`.
- **Example**:
  ```c
  #include <stdio.h>
  #include <conio.h>
  void main(int argc, char *argv[]) {
      clrscr();
      printf("Argument count: %d\n", argc);
      for (int i = 0; i < argc; i++) {
          printf("Argument %d: %s\n", i, argv[i]);
      }
      getch();
  }
  ```
- **Viva Tip**: Explain `argc` and `argv`. Note Turbo C requires DOS prompt input (e.g., `program.exe arg1 arg2`).

### 8.3 Basic C++ in Turbo C
- **Definition**: Turbo C++ supports basic C++ (classes, objects) but no modern features (e.g., smart pointers).
- **Example**:
  ```c
  #include <iostream.h>
  #include <conio.h>
  class Student {
  public:
      int id;
      void display() { cout << "ID: " << id; }
  };
  void main() {
      clrscr();
      Student s;
      s.id = 1;
      s.display();
      getch();
  }
  ```
- **Viva Tip**: Explain basic class syntax and why C++ references reduce pointer usage.

## 9. Viva Preparation Tips
- **Turbo C Specifics**:
  - Use `<conio.h>` for `clrscr()`, `getch()`.
  - Use `<stdio.h>`, `<string.h>`, `<stdlib.h>` for C; `<iostream.h>` for C++.
  - Turbo C is 16-bit, limiting memory allocation (e.g., 64 KB per segment).
- **Practice**:
  - Write 2-3 programs per starred topic (loops, pointers, file handling, problem solving).
  - Examples: Linked list reversal, binary file I/O, star pattern, Fibonacci.
  - Test code in Turbo C to ensure compatibility.
- **Theory**:
  - Explain concepts with examples (e.g., dangling pointer, pass by reference).
  - Compare: Structure vs. union, static vs. dynamic memory, C vs. C++ pointers.
  - Handle edge cases: Empty linked list, file not found, zero-size allocation.
- **Flowcharts**: Draw for simple programs (e.g., factorial, linked list insertion).
- **Sample Questions**:
  - **Q**: What is a dangling pointer? **A**: Pointer to freed memory. Avoid by setting to `NULL` after `free`.
  - **Q**: Compare `malloc` vs. `calloc`. **A**: `malloc` allocates uninitialized memory; `calloc` initializes to zero.
  - **Q**: Write a program to reverse a linked list. (See 5.4 example.)
  - **Q**: Explain file modes. **A**: `r` (read), `w` (write), `a` (append), `rb`/`wb` (binary); text stores as ASCII, binary as raw bytes.
