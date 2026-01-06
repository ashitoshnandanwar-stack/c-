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
