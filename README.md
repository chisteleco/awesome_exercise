| Language | Compiler |
| -------- | -------- |
| ![Language](https://img.shields.io/badge/Language-C-blue) | ![Compiler](https://img.shields.io/badge/Compiler-GCC%20%20%20-blue)
|![Language](https://img.shields.io/badge/Language-C%2B%2B-blue)|![Compiler](https://img.shields.io/badge/Compiler-G%2B%2B-blue)|

## Hello, World! :wave:
```c
#include <stdio.h>
int main() {
    printf("Hello, world!\n");
    return 0;
}
```

## An exciting exercise to improve the programming concepts:-

By going through this exercise, you will be introduced to `C` programming lanuguage behaviour and use it to increase your control on the system.

In this exercise we will go through with some programs that will give the introduction to programming constructs and give you the following takeaways included below:

    1. Introduction to the data type declaration and initialization.

    2. Declaration of functions, using them to modularize the code and improving performance or program.

    3. Header file design, organizing the project by introducing them in the project.

    4. Introduction to the build system, using them to compile and link the necessary files.

    5. Handling large input size and tranforming to dynamic types as requirement of program changes.

    6. Using timer and improving performance of program.

    7. Introducing concurrency in the program to handle mutex semaphor and protecting processing data while multiprocessing.
<br/>

### Exercise structure:
    Number. Statement of problem.
        Take away from this asg:
        ---
        ---
<br/>

## Pathway to get most out of this exercise:

<br/>

###    1. Create an array:


```c
size: 1000, data_type: double.
```
- How to declare a variable of specific data type in the programming language?
-  How to initialize the same value to a large container like array by just an assignment?
```c
double arr[1000] = {0};
```
<br/>

### 2. Store 1000 random values in it:

- Combining takeaways of previous assignment
- How to generate random numbers in programming environment?
```c
int rand(void);
```
<br/>

### 3. Implement functions to calculate min, max and average value.

- How to design functions, taking formal arguments by pass by value, pass by address?
- Implementing functions to modularize the program.
```c
void foo(void) {
    printf("Hi! You are in foo.\n");
    return;
}
```
<br/>

### 4. Implement sorting algorithms to sort the array.

- Introduction to Sorting Algorithms.
- How to implement them?
```c
mergeSort(arr);
quickSort(arr);
heapSort(arr);
```
<br/>

### 5. Make specific header files for those functions.

- How to use header files in the aspect of data hiding?
- How not to expose array publicly to other files? {private, public and protected is not available in C.}
- Organize the same functions in a single module {header file}.
```c
// bar.h
#ifndef BAR_H
#define BAR_H

void foo(void) {
    printf("foo\n");
    return;
}
void bar(void) {
    printf("bar\n");
    return;
}
void baz(void) {
    printf("baz\n");
    return;
}

#endif
```
<br/>

### 6. Make a build system for all compiling and linking stuff:

- Understand how to compile and link multiple files to generate an executable - on Linux, this would be by using makefiles.

```makefile
all: compile

compile:
    gcc -g -c foo.c main.c bar.h
    gcc -g -o output_file *.o

clean:
    rm -f *.o
    rm -f output_file
```
<br/>

### 7. Change the array size to 500 million.

- How to check the stack size and heap size in the system?
- How to transform the nature of existing static program to dynamic?

- This will compile but in all likelihood will crash (or segfault) when you run it. This exposes you to heap and stack (c arrays are on the stack and the array is now too big to fit on the stack).
```c
double arr[5000000000] = {rand()};
```
<br/>

### 8. Make the array dynamic in nature.

- How to convert dynamic behaviour by using calloc/malloc?

- You’ll need to move the array to the heap and deal with malloc/calloc. This will also expose you to pointers.
```c
double* ptr = (double*) malloc(sizeof(double) * 5000000000);
```
<br/>

### 9. Use timer to get the nitty-gritty details of time consumption of function.

- Put timer code around each of operations.
```c
#include <time.h>
int msec = 0, trigger = 10; /* 10ms */
clock_t t = clock();
```
<br/>

### 10. Improve the performance.

- By turn on various compiler warnings (if using `gcc` or `clang`, `-Wall` and `-Werror`).
- Enjoy fixing up `problems` in your code.
```c
void foo(void) {
    printf("Hi! This is from foo.\n");
    return;
}
```
<br/>

### `Want to feel adventurous? Implement this exercise.`

## Concurrency introduction:

### 11. Make the separate threads for functions-

- Move the operations into separate threads.

- This will expose you to multithreaded issues like sorting the array while trying to find the average.
        i.e. Protect the array using some form of mutex or semaphore).

- The min, max and average can all run in parallel (they don’t responsible for mutation in the array) but the sort operation needs sole access to the array.
```c
#include <pthread.h>
void *thread(void *vargp)
{
    printf("Hi! you have executed the thread ;)\n");
    return NULL;
}

int main()
{
    pthread_t t_id;
    printf("Main function\n");
    pthread_create(&t_id, NULL, thread, NULL);
    pthread_join(t_id, NULL);
    printf("Main Function\n");
    return 0;
}
```
<br/>

    This is useful to understand because it forms the basis of the Rust language’s ownership model.
