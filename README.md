# c-
language and notes

- In C++, switch statements can only work with integral types: <br>
int, short, long, char  <br>
enum types  <br>
NOT floating-point (float, double)  <br>
NOT strings (in standard C++98/03)  <br>
C++11 added support for strongly-typed enums  <br>

| Feature      | Stack     | Heap    |
| ------------ | --------- | ------- |
| Stability    |  High     |  Lower  |
| Speed        | Fast      | Slower  |
| Management   | Automatic | Manual  |
| Memory leaks |  No       |  Yes    |
| Size         | Limited   | Large   |

## 6. MEMORY MANAGEMENT
```
Memory Sections:
Stack - Local variables, automatic allocation/deallocation
Heap - Dynamic memory allocation
Data Segment - Global/static variables
Code Segment - Executable instructions
```
#### dangling pointer?
- A dangling pointer is a pointer that refers to deallocated memory.
```
int *p = new int(10);
delete p;     // memory freed
// p is now dangling
```
- Dangling pointers cause undefined behavior.
- Array pointer is constant it not modify throughout program.
- Increment and decrement in pointer , increment occur on address as per variable type(eg. for int 4byte added).
- adding and subtract in pointer, adding in pointer means adding in address(eg. ptr + 2 = address + 8 byte (of 2 int)).
  
```
int arr[] = {1,2,3,4,5};

cout<<*arr<<endl; // output : 1; point towards to 0 index
cout<<*(arr + 1)<<endl;  //output : 2
cout<<*(arr + 1)<<endl;  //output : 3
*arr++;
cout<<*(arr); // output : 2
```
- addition of pointer not done, but subtract are carried out
```
int *ptr2;
int *ptr1 = ptr2 + 2;
cout<< ptr1 - ptr2; //output 2
```
- all relational operator are worked in pointer(>,<,== etc).
- Pointer size depends on system architecture, NOT data type! <br>
  32-bit system → All pointers are 4 bytes <br>
  64-bit system → All pointers are 8 bytes <br>

<hr>

##  Math library functions etc.

#include <cmath>
| Function    | Description          | Example             |
| ----------- | -------------------- | ------------------- |
| `sqrt(x)`   | Square root          | `sqrt(16)` → `4`    |
| `pow(x, y)` | x raised to power y  | `pow(2, 3)` → `8`   |
| `abs(x)`    | Absolute value       | `abs(-5)` → `5`     |
| `ceil(x)`   | Smallest integer ≥ x | `ceil(4.2)` → `5`   |
| `floor(x)`  | Largest integer ≤ x  | `floor(4.9)` → `4`  |
| `round(x)`  | Nearest integer      | `round(4.6)` → `5`  |
| `log(x)`    | Natural log (base e) | `log(2.7)`          |
| `log10(x)`  | Log base 10          | `log10(100)` → `2`  |
| `exp(x)`    | e^x                  | `exp(1)` → `2.718…` |
| `sin(x)`    | Sine (radians)       | `sin(0)` → `0`      |
| `cos(x)`    | Cosine (radians)     | `cos(0)` → `1`      |
| `tan(x)`    | Tangent (radians)    | `tan(0)` → `0`      |
| `max(a,b)`  | Maximum              | `max(10,20)` → `20` |
| `min(a,b)`  | Minimum              | `min(10,20)` → `10` |

## 🔹 Comparison: new vs malloc, calloc, realloc

| Feature            | `new` (C++)                    | `malloc()` (C)                        | `calloc()` (C)                           | `realloc()` (C)                  |
| ------------------ | ------------------------------ | -----------------------------------   | ---------------------------------------- | -------------------------------- |
| Language           | C++                            | C / C++                               | C / C++                                  | C / C++                          |
| Memory Allocation  | Allocates memory for objects   | Allocates raw memory                  | Allocates & initializes to zero          | Resizes allocated memory         |
| Initialization     | Calls **constructor**          | No initialization                     | Initializes all bytes to **0**           | No initialization                |
| Type Safety        | Type-safe                      | Returns `void*` (needs cast)          | Returns `void*`                          | Returns `void*`                  |
| Syntax             | `int *p = new int;`            | `int *p = (int*)malloc(sizeof(int));` | `int *p = (int*)calloc(1, sizeof(int));` | `p = (int*)realloc(p, newSize);` |
| Failure Handling   | Throws exception (`bad_alloc`) | Returns `NULL`                        | Returns `NULL`                           | Returns `NULL`                   |
| Deallocation       | `delete p;`                    | `free(p);`                            | `free(p);`                               | `free(p);`                       |
| Works with Objects | Yes (calls constructor)        | No                                    | No                                       | No                               |
| Resize Memory      | No                             | No                                    | No                                       | **Yes**                          |



<hr>


| Access Specifier | Accessible Inside Class | Accessible Outside Class | Inherited by Derived Class |
| ---------------- | ----------------------- | ------------------------ | -------------------------- |
| `public`         | Yes                     | Yes                      | Yes                        |
| `private`        | Yes                     | No                       | No                         |
| `protected`      | Yes                     | No                       | Yes                        |


<hr>

| Data Type | Java Size (Fixed) | C++ Size (Compiler Dependent) |
| --------- | ----------------- | ----------------------------- |
| `byte`    | 1 byte (8-bit)    | — (use `char` = 1 byte)       |
| `short`   | 2 bytes           | 2 bytes (usually)             |
| `int`     | 4 bytes           | 2 or 4 bytes                  |
| `long`    | 8 bytes           | 4 or 8 bytes                  |
| `float`   | 4 bytes           | 4 bytes                       |
| `double`  | 8 bytes           | 8 bytes                       |
| `char`    | 2 bytes (Unicode) | 1 byte                        |
| `boolean` | 1 byte (logical)  | No built-in (`bool` = 1 byte) |

