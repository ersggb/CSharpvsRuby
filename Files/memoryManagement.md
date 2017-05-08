# Memory Management
- How is it handled?
- How does it work?
- Garbage collection?
- Automatic reference counting?

## C# Memory Management
IN C# memory management is handled automatically. Memory is allocated and garbage collection is done automatically.
>The Microsoft .NET common language runtime requires that all resources be allocated from the managed heap. Objects are automatically freed when they are no longer needed by the application.

>When a process is initialized, the runtime reserves a contiguous region of address space that initially has no storage allocated for it. This address space region is the managed heap. The heap also maintains a pointer. This pointer indicates where the next object is to be allocated within the heap. Initially, the pointer is set to the base address of the reserved address space region.

>An application creates an object using the new operator. This operator first ensures that the bytes required by the new object fit in the reserved region (committing storage if necessary). If the object fits, then the pointer points to the object in the heap, this object's constructor is called, and the new operator returns the address of the object.

>Every application has a set of roots. Roots identify storage locations, that refer to objects on the managed heap or to objects that are set to null. For example, all the global and static object pointers in an application are considered part of the application's roots. In addition, any local variable/parameter object pointers on a thread's stack are considered part of the application's roots. Finally, any CPU registers containing pointers to objects in the managed heap are also considered part of the application's roots. The list of active roots is maintained by the just-in-time (JIT) compiler and common language runtime, and is made accessible to the garbage collector's algorithm.
>The garabge collector maintains a graph or all objects reachable from the applications roots and considers anything not in this graph to be garbage. After the last reference to an object in code, the object is no longer a root and is considered garbage; however, it will not be collected until a garbage collection is performed Garbage Collection only happens when the heap is full. It identifies all blocks of memory in the heap that are garage and moves non garbage objects down to fill in these gaps in memory, updating all pointers and references to the objects.

### REFERENCES
(http://www.c-sharpcorner.com/article/memory-management-in-net/)

## Ruby Memory Management
Memory management in Ruby is also handled automatically. It is allocated and garbage collected for the user. Memory is considered garbage when no references to it remain.

Ruby 2.2 introduced incremental garbage collection to shorter pause times due to Garbage collection. It interlaces marking of garbage items with the ruby application so that it does not pause the program for an extended period of time
### REFERENCES
(https://blog.heroku.com/incremental-gc)

[Back to the Home Page](https://github.com/ersggb/CSharpvsRuby)
