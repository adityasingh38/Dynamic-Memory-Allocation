# Memory Allocation in C

Memory allocation refers to the process by which a computer program or operating system assigns portions of a computer's memory (RAM) to store data or instructions for execution. Memory allocation is a critical aspect of computer programming and operating system design, as it determines how memory is organized and utilized by programs.

Memory allocation can be done in multiple ways:

1. Static memory allocation: In this method, memory is allocated at compile-time or during program initialization, and the size of memory is fixed and determined before the program starts running. The allocated memory remains reserved for the program's entire execution, even if it is not fully utilized, which can result in wasted memory.

An example of static memory allocation in C:

```
int globalVar; // Memory for 'globalVar' is allocated statically

void function() {
    static int staticVar; // Memory for 'staticVar' is allocated statically
    //...
} // Memory for 'staticVar' is deallocated when program exits
```

2. Dynamic memory allocation: In this method, memory is allocated during runtime, as needed by the program. Dynamic memory allocation allows for more efficient use of memory, as memory can be allocated and deallocated based on the program's requirements. Common dynamic memory allocation techniques include using functions such as malloc(), calloc(), and realloc() in C/C++ or new and delete operators in C++.

An example of dynamic memory allocation in C:

```
int* dynamicVar = (int*)malloc(sizeof(int)); // Memory for 'dynamicVar' is allocated dynamically on the heap

if (dynamicVar != NULL) {
    *dynamicVar = 20; // Memory is accessed and modified
    //...
    free(dynamicVar); // Memory is deallocated when no longer needed
}
```

## Memory allocation functions supported by C

- malloc(size_t size): This function allocates a block of memory of the specified size in bytes and returns a pointer to the first byte of the allocated memory. The allocated memory is not initialized, meaning it may contain garbage values. The function returns NULL if the memory allocation fails.

- calloc(size_t nmemb, size_t size): This function allocates a block of memory for an array of nmemb elements, each of size bytes, and returns a pointer to the first byte of the allocated memory. The allocated memory is initialized to zero. The function returns NULL if the memory allocation fails.

- realloc(void* ptr, size_t size): This function changes the size of the previously allocated memory block pointed to by ptr to the specified size bytes. If the new size is larger than the old size, the contents of the newly allocated memory are uninitialized. If the new size is smaller than the old size, the contents of the truncated memory may be lost. The function returns a pointer to the first byte of the reallocated memory. If ptr is NULL, then the function behaves like malloc(size). If size is 0 and ptr is not NULL, then the function behaves like free(ptr).

- free(void* ptr): This function deallocates the memory block pointed to by ptr, which must have been previously allocated by malloc(), calloc(), or realloc(). If ptr is NULL, the function has no effect. It is important to deallocate memory when it is no longer needed to avoid memory leaks.

These memory allocation functions are declared in the <stdlib.h> header file in C, and it is important to include this header file in your C program if any of these functions need to be used. Additionally, it is crucial to properly manage the dynamically allocated memory to avoid memory leaks or accessing freed memory, which can lead to undefined behavior.

Memory allocation is an important consideration in programming, as efficient memory management can help improve the performance and reliability of a program. It is crucial to properly allocate and deallocate memory to avoid issues such as memory leaks, segmentation faults, and inefficient memory usage. Different programming languages and operating systems may have their own memory allocation techniques and best practices, so it's important to understand the memory allocation mechanisms and guidelines relevant to the specific programming environment being used.

The program in this repository demonstrates the usage of memory allocatino functions such as malloc() and calloc().

### Code:

```
/* Memory allocation can be done using the following functions:
	1. malloc
	2. calloc
	3. realloc
	4. free
	The above functions are available in the stdlib.h  library.

	malloc(size_of_data_type_in_bytes) is a like a pointer. To access this memory: 
	int *ptr = (int*) malloc(4); -> for integer memory allocation
	*ptr = <some_integer_value>;
	printf("%d %d", *ptr, ptr);
	
	malloc() allocates memory one memory location at a time whereas calloc() allocates the entered amount of memory at once. 
	However, malloc() keeps the allocated memory uninitialized whereas calloc() initializes the memory with zero value.
	Hence, malloc() is faster.
*/


#include <stdio.h>
#include <stdlib.h>

int main()
{
	// malloc()
	
	printf("dynamic memory allocation using malloc():\n\n");
	
	char *ptr = (char*) malloc(2);
	
	*ptr = 'a';
	printf("%c %d\n", *ptr, ptr);
	
	ptr++;
	
	*ptr = 'b';
	printf("%c %d\n\n\n\n", *ptr, ptr);
	
	
	
	// calloc()
	
	printf("dynamic memory allocation using calloc():\n\n");
	
	int i, n;
	
	int *ptr2 = (int*) calloc(3, 4);
	
	for(i = 0; i < 3; i++)
	{
		printf("Enter a number: ");
		scanf("%d", &ptr2[i]);
	}
	
	printf("\nEntered array of numbers with their memory addresses:\n\n");
	
	for(i = 0; i < 3; i++)
	{
		printf("%d %d\n", ptr2[i], &ptr2[i]);
	}
	
	return 0;
}
```

### Output:

![OP1](https://user-images.githubusercontent.com/88421625/234431749-23c0b70f-1b1a-4aa6-9c95-bc943f670ee8.png)
