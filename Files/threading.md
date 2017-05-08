# Multithreading
- Threads or thread-like abilities
- How is multitasking accomplished?

## C# Multithreading
>In C#, the System.Threading.Thread class is used for working with threads. It allows creating and accessing individual threads in a multithreaded application. The first thread to be executed in a process is called the main thread.

>When a C# program starts execution, the main thread is automatically created. The threads created using the Thread class are called the child threads of the main thread.

>Threads are created by extending the Thread class. The extended Thread class then calls the Start() method to begin the child thread execution.

The thread constructor takes a ThreadStart object in its constructor. The ThreadStart class takes a function in its constructor. A Thread is started when the start method is called. A thread stops execution when the method from referenced in the ThreadStart object returns or the thread is aborted.

Example of creating a child thread of the main thread
```csharp
using System;
using System.Threading;

namespace MultithreadingApplication
{
   class ThreadCreationProgram
   {
      public static void CallToChildThread()
      {
         Console.WriteLine("Child thread starts");

         // the thread is paused for 5000 milliseconds
         int sleepfor = 5000;

         Console.WriteLine("Child Thread Paused for {0} seconds", sleepfor / 1000);
         Thread.Sleep(sleepfor);
         Console.WriteLine("Child thread resumes");
      }

      static void Main(string[] args)
      {
         ThreadStart childref = new ThreadStart(CallToChildThread);
         Console.WriteLine("In Main: Creating the Child thread");
         Thread childThread = new Thread(childref);
         childThread.Start();
         Console.ReadKey();
      }
   }
}
```
### References
(https://www.codeproject.com/articles/1083/multithreaded-programming-using-c)  
(http://www.tutorialspoint.com/csharp/csharp_multithreading.htm)
## Ruby Multithreading
To create a thread in Ruby you simply associate a block of code with a Thread.new method. The thread will execute and control will return to the main thread.

>A new threads are created with Thread.new. You can also use the synonyms Thread.start and Thread.fork.

>There is no need to start a thread after creating it, it begins running automatically when CPU resources become available.

>The value of the last expression in that block is the value of the thread, and can be obtained by calling the value method of the Thread object. If the thread has run to completion, then the value returns the thread's value right away. Otherwise, the value method blocks and does not return until the thread has completed.

>The class method Thread.current returns the Thread object that represents the current thread.

>You can wait for a particular thread to finish by calling that thread's Thread.join method. The calling thread will block until the given thread is finished.

If an unhandled exception occurs in a thread that is not the main  thread, the thread stops running.  

```ruby
def func1
   i = 0
   while i<=2
      puts "func1 at: #{Time.now}"
      sleep(2)
      i = i+1
   end
end

def func2
   j = 0
   while j<=2
      puts "func2 at: #{Time.now}"
      sleep(1)
      j = j+1
   end
end

puts "Started At #{Time.now}"
t1 = Thread.new{func1()}
t2 = Thread.new{func2()}
t1.join
t2.join
puts "End at #{Time.now}"

#the above code produces this result
Started At Wed May 14 08:21:54 -0700 2008
func1 at: Wed May 14 08:21:54 -0700 2008
func2 at: Wed May 14 08:21:54 -0700 2008
func2 at: Wed May 14 08:21:55 -0700 2008
func1 at: Wed May 14 08:21:56 -0700 2008
func2 at: Wed May 14 08:21:56 -0700 2008
func1 at: Wed May 14 08:21:58 -0700 2008
End at Wed May 14 08:22:00 -0700 2008
```
### References
(http://www.tutorialspoint.com/ruby/ruby_multithreading.htm)

[Back to the Home Page](https://github.com/ersggb/CSharpvsRuby)
